# Back Redirect

Com esse script sempre que o potencial cliente clicar no back redirect do navegador, ele será apontado para a url definida.

Todos os parâmetros da url serão adicionados automaticamente ao final da url.

```
<script>
    var urlBackRedirect = 'SUA URL AQUI'; // lembre-se de usar a url sem espaços
    // não altere nada abaixo dessa linha
    urlBackRedirect = urlBackRedirect = urlBackRedirect.trim() +
            (urlBackRedirect.indexOf("?") > 0 ? '&' : '?') +
            document.location.search.replace('?', '').toString();
    history.pushState({}, "", location.href);
    history.pushState({}, "", location.href);
    window.onpopstate = function () {
        setTimeout(function () {
            location.href = urlBackRedirect;
        }, 1);
    };
</script>
```

Para usar em múltiplos domínios:

```
var urlBackRedirect = '//' + window.location.hostname + '/PATH_RMKT'
```

# Notificações de Compra (Gatilho da Escassez):

![Notificações de Compra](https://raw.githubusercontent.com/tiagosousaweb/scripts-uteis/main/images/img1.png)

```
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
<link href="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/latest/css/toastr.min.css" rel="stylesheet">
<script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/toastr.js/2.1.4/toastr.min.js"></script>
<script>
    $(document).ready(function onDocumentReady() {
        var URL_FINAL = '#';
        var nome = ['Luciana Oliveira', 'Marcia Araújo', 'Carolina Dias', 'Martha', 'Aline Campos', 'Luciane R Freire', 'Simone Z', 'Laura Campos', 'Carla Dias', 'Mariana Ruas', 'Jessica Ribeiro', 'Karol Lia'];
        nome.sort(() => Math.random() - 0.5);
        var i = 0, qtd = nome.length;
        setInterval(function doThis() {
            if (i == 11) return; // somente 11 eventos serão disparados
            if (i == 1 || i == 8 || i == 10) {
                toastr.info('<a href="' + URL_FINAL + '">Clique e Reserve sua vaga também!</a> ' + (qtd + (i * 3)) + ' novas alunas compraram nos últimos 30min.', {
                    timeOut: 5000,
                    positionClass: "toast-bottom-right",
                });
            }
            toastr.success('<a href="' + URL_FINAL + '">Clique e Reserve sua vaga também!</a> ' + nome[i++] + ' acabou de reservar a vaga dela.', {
                timeOut: 5000,
                positionClass: "toast-bottom-right",
            })
        }, 10 * 1000);   // a cada 10 segundos
    });
</script>
```

Se desejar, altere os nomes.

Altere # para sua url em var URL_FINAL = '#';

# Contador regressivo

![Contador Regressivo](https://raw.githubusercontent.com/tiagosousaweb/scripts-uteis/main/images/img2.png)

Código do contador, coloque onde o contador deverá aparecer:

```
<div class="countdown">
    <div class="label">O desconto encerra em:</div>
    <div class='time'>00:00</div>
</div>
```

No rodapé da página coloque o seguinte código:

```

<script>
    var MINUTOS = 15;
    // Não altere nada abaixo dessa linha
    function startTimer(duration, display) {
        var timer = duration,
                minutes, seconds;
        setInterval(function () {
            minutes = parseInt(timer / 60, 10);
            seconds = parseInt(timer % 60, 10);
            minutes = minutes < 10 ? "0" + minutes : minutes;
            seconds = seconds < 10 ? "0" + seconds : seconds;
            display.forEach(function (el) {
                el.textContent = minutes + ":" + seconds;
            })
            if (--timer < 0) {
                timer = 0;
            }
        }, 1000);
    }
    window.onload = function () {
        var minutesToSeconds = MINUTOS * 60,
                display = document.querySelectorAll('.time');
        startTimer(minutesToSeconds, display);
    };
</script>
<style>
    .countdown {
        font: normal 12px/20px Arial, Helvetica, sans-serif;
        word-wrap: break-word;
        box-shadow: 0 1px 1px 0 rgba(1, 1, 1, 0.4);
        width: 250px;
        height: 90px;
        text-align: center;
        background: #f1f1f1;
        border-radius: 5px;
        margin: 30px auto;
        font-weight: lighter;
    }
    .countdown .label {
        font-size: 12px;
        color: #65584c;
        text-align: center;
        text-transform: uppercase;
        display: inline-block;
        letter-spacing: 2px;
        padding: 7px 0;
    }
    .countdown .time {
        color: #fff;
        position: relative;
        z-index: 1;
        text-shadow: 1px 1px 0px #ccc;
        font-size: 48px;
        text-align: center;
        padding: 20px;
        border-radius: 0 0 5px 5px;
        display: block;
        background: #e5554e;
        box-shadow: 0 1px 2px 0 rgba(1, 1, 1, 0.4);
    }
</style>
```

# Dividir WhatsApp para vários atendentes:

```

<script>
    function getWhatsAppNumber() {
        var mensagemWhats = 'Eu quero testar!';
        var phones = [
            119911111111,
            119911111112,
            119911111113,
            119911111114,
        ];

        var url = 'https://api.whatsapp.com/send?phone='
                + phones[Math.floor(Math.random() * phones.length)]
                + '&text='
                + encodeURIComponent(mensagemWhats);

        window.open(url, '_blank');
    }
</script>
<a href="#" onclick='getWhatsAppNumber()'>Falar com um atendente</a>
```

# Desativar clique com botão direito e inspecionar elemento

```

<script>
    document.addEventListener("keydown", function (e) {
        if (e.keyCode == 123 || (e.ctrlKey && e.shiftKey && e.keyCode == 73)) { 
            e.preventDefault()
        }
    }, true);
    document.addEventListener('contextmenu', function (e) {
        e.preventDefault()
    }, true);
</script>
```
# Script redirecionar depois de determinado tempo

```
<script>
    setTimeout(function() {
    window.location.href = "URL_AQUI";
}, 2000);
</script>
```

<hr/>
Os scripts existentes aqui foram baseados no repositório abaixo:
https://github.com/lzanette/perfect-pay-scripts
