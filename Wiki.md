## _

* [**userchrome.css** и **userContent.css**](#userchromecss-и-usercontentcss) - что это, где и как использовать?

* [Как очистить гамбургер-меню от лишнего](#Как-очистить-гамбургер-меню-от-лишнего) (FF 58+)   **☰**

* [Как редактировать userchrome.css прямо в браузере и сразу видеть изменения без перезапуска](#Как-редактировать-userchromecss-прямо-в-браузере-и-сразу-видеть-изменения-без-перезапуска)

* [Важные файлы и папки профиля](#Важные-файлы-и-папки-профиля)

* [Я копирую ссылку с кириллицей и получаю кракозябры, что делать](#Я-копирую-ссылку-с-кириллицей-и-получаю-кракозябры-что-делать)? (FF 53+ )

* [Как перезапустить FF](#Как-перезапустить-ff)?

* [Как запускать FF с меню выбора и редактирования профилей](#Как-запускать-ff-с-меню-выбора-и-редактирования-профилей)?
* [Я использую аддон TST, как спрятать горизонтальные вкладки](#Я-использую-аддон-tst-как-спрятать-горизонтальные-вкладки) (57+)
* [Как выключить телеметрию](#Как-выключить-телеметрию)?

* [Как открыть менеджер очистки](#Как-открыть-менеджер-очистки)?

* [Я случайно удалил профиль, как восстановить](#Я-случайно-удалил-профиль-как-восстановить)?

* [Немного об ID аддонов](#Немного-об-id-аддонов)

* [Как затенять выгруженные вкладки](#Как-затенять-выгруженные-вкладки)?

* [Как спрятать кнопку "Закрыть" на вкладках](#Как-спрятать-кнопку-Закрыть-на-вкладках)?

* [Как мне удалить дополнение Download Master-а и т.п.](#Как-мне-удалить-дополнение-download-master-а-и-тп)?

* [Хочу поставить на Новую Вкладку](#Хочу-поставить-на-новую-вкладку) (Ctrl+T) свою вайфу фоном, как?

* [Хочу заменить иконку сайта на Новой Вкладке](#Хочу-заменить-иконку-сайта-на-Новой-Вкладке) (Ctrl+T) с некрасивой на красивую.

* [Что делать, если Новая Вкладка - пустая белая страница](#Что-делать,-если-Новая-Вкладка---пустая-белая-страница) (New Tab, Ctrl+T)

* [Я слышал, что есть плохое, нехорошее место](#Я-слышал-что-есть-плохое-нехорошее-место)

___
## userchrome.css и userContent.css
userchrome.css - используем для настройки интерфейса FF <br>
userContent.css - используем для настройки стилей сайтов и страниц FF<br>
По умолчанию, эти файлы не создаются во время генерации нового профиля.<br>
Их нужно создать руками.
- Узнать адрес профиля: about:profiles
- Жми "Открыть папку" (профиль по умолчанию)
- В папке профиля создать папку chrome
- В папке chrome создать два файла: userchrome.css и userContent.css <br>
(у вас должен быть включён показ расширения файлов в проводнике)
- Редактируем любым текстовым редактором. <br>
Удобно использовать что-то с подстветкой синтаксиса и тёмной темой, например Notepad++ или Sublime Text. <br>
- В userchrome.css добавляем строку: <br>
`@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");`

Документация по userchrome: <br>
http://kb.mozillazine.org/UserChrome.css <br>
http://kb.mozillazine.org/Chrome_element_names_and_IDs <br>
https://www.userchrome.org/what-is-userchrome-css.html <br>

О userContent:<br>
Вы можете копипастить стили для сайтов с ресурсов типа https://userstyles.org

[Вверх](#_)
___
## Как очистить гамбургер-меню от лишнего
Пример:<br>
userChrome.css :<br>
`#appMenu-edit-controls, #appMenu-open-file-button, #appMenu-save-file-button, #appMenu-print-button, #appMenu-fxa-label, .PanelUI-subView toolbarseparator, #appMenu-new-window-button, #appMenu-private-window-button, #appMenu-zoom-controls, #appMenu-find-button, #appMenu-library-button, #appMenu-quit-button, #appMenu-more-button {display:none !important;} `

Расшифруем :<br>
**#appMenu-edit-controls** - Правка <br>
**#appMenu-open-file-button** - Открыть файл <br>
**#appMenu-save-file-button** - Сохранить как <br>
**#appMenu-print-button** - Печать <br>
**#appMenu-fxa-label** - Войти в Синхронизацию <br>
**.PanelUI-subView toolbarseparator** - разделители <br>
**#appMenu-new-window-button** - Новое окно <br>
**#appMenu-private-window-button** - Приватное окно <br>
**#appMenu-zoom-controls** - Масштаб <br>
**#appMenu-find-button** - Найти на этой странице <br>
**#appMenu-library-button** - Библиотека <br>
**#appMenu-quit-button** - Выход <br>
**#appMenu-more-button** - Ещё <br>
**#appMenu-addons-button** - Расширения <br>
**#appMenu-preferences-button** - Настройки <br>
**#appMenu-customize-button** - Персонализация <br>
**#appMenu-developer-button** - Веб-разработка <br>
**#appMenu-help-button** - Справка <br>

**Сортировка пунктов меню.** <br>
Как их поставить в нужной мне последовательности? <br>
Делается с помощью **-moz-box-ordinal-group:номер_пункта**, пример: <br>
userChrome.css : <br>
`#appMenu-preferences-button {-moz-box-ordinal-group:2 !important;}` <br>
`#appMenu-customize-button {-moz-box-ordinal-group:3 !important;}` <br>
`#appMenu-developer-button {-moz-box-ordinal-group:4 !important;}` <br>
`#appMenu-help-button {-moz-box-ordinal-group:1 !important;}` <br>
`#appMenu-addons-button {-moz-box-ordinal-group:5 !important;}` <br>
Последовательность в списке НЕ важна - <br>
иерархию определяет только номер пункта (меньше цифра - выше по списку). <br>
Список должен состоять только из НЕ-скрытых пунктов. <br>

**Как удалить некоторые под-пункты в Справке / Веб-разработке, не удаляя сам пункт?** <br>
По заголовку, например: <br>
`#PanelUI-helpItems [label="Справка Firefox"] {display:none !important;}` <br>
Веб-разработка - аналогично, #PanelUI-developerItems <br>
Или по команде, например: <br>
`#PanelUI-helpItems [oncommand="openHelpLink('firefox-help')"]` - Справка ФФ <br>
`#PanelUI-helpItems [oncommand="openTourPage();"]` - Знакомство с ФФ <br>
`#PanelUI-helpItems [oncommand="openHelpLink('keyboard-shortcuts')"]` - Клавиатурные сокращения <br>
`#PanelUI-helpItems [oncommand="openFeedbackPage()"]` - Отправить отзыв <br>
`#PanelUI-helpItems [oncommand="openUILink(gSafeBrowsing.getReportURL('Phish'), event);"]` - Сообщить о поддельном сайте <br>
[Вверх](#_)
___
## Как редактировать userchrome.css прямо в браузере и сразу видеть изменения без перезапуска
- F12 (окно девтулзов)
- Включить две последние галочки - "Enable browser chrome and add-on debugging toolboxes" и "Enable remote debugging".
- Теперь можно открывать список css, в котором есть userchrome - Ctrl+Shift+Alt+I

Изменения сделанные через Browser Toolbox применяются немедленно, сразу после того как ты вставил/набрал код.  <br>
Но нужно нажимать кнопку "сохранить", чтобы не сбросилось обратно при перезапуске.

[Вверх](#_)
___

## Важные файлы и папки профиля

**key4.db**, **logins.json** - пароли и логины <br>
**places.sqlite** - закладки и история <br>
**prefs.js** - настройки FF в т.ч. настройки about:config <br>
**search.json** - настройки поиска, список поиск.систем и поиск.система по умолчанию <br>
**xulstore.json** - настройки интерфейса FF <br>
**favicons.sqlite** - фавиконки сайтов (раньше хранились в **places.sqlite**). <br>
Если есть какие-то ошибки отображения фавиконов - можно удалить. <br>
**webappsstore.sqlite** - [веб-хранилище](https://ru.wikipedia.org/wiki/Web_Storage),
about: config > dom.storage.enabled > отключить = false<br>
**browser-extension-data** - папка с пользовательскими настройками аддонов <br>
**extensions** - папка с аддонами <br>
**extensions.json** - список аддонов, который также определяет какие из них включены/выключены. <br>
Также здесь хранятся ID аддонов и прочая информация об установленных аддонах.<br>

[Вверх](#_)
___
## Я копирую ссылку с кириллицей и получаю кракозябры, что делать
about:config <br>
browser.urlbar.decodeURLsOnCopy -> true

[Вверх](#_)
___
## Как перезапустить FF
Shift+F2 (внизу FF откроется поле ввода) > печатай "rest" без кавычек > Tab > Enter

[Вверх](#_)
___
## Как запускать FF с меню выбора и редактирования профилей
В путь в свойстве ярлыка FF добавь " -P"

[Вверх](#_)
___
## Я использую аддон TST, как спрятать горизонтальные вкладки
Спрятать горизонтальные табы, <br>
опустить кнопки виндовой рамки окна на уровень FF-кнопок, <br>
забрать виндовую рамку окна. <br>

<a href="http://piccy.info/view3/12381880/ac6e560bb9b035c5a1ff84508809e42c/" target="_blank"><img src="http://i.piccy.info/i9/c101b9ad022c721c2c704c44962408ac/1527972376/10174/1246306/sshot_141.png" alt="Piccy.info - Free Image Hosting" border="0" /></a><a href="http://i.piccy.info/a3c/2018-06-02-20-46/i9-12381880/387x63-r" target="_blank"><img src="http://i.piccy.info/a3/2018-06-02-20-46/i9-12381880/387x63-r/i.gif" alt="" border="0" /></a> <br>
userchrome.css :<br>
`#TabsToolbar {visibility: hidden !important; margin-block-end: -30px !important;}`<br>
`#nav-bar {margin-right: 140px !important;} `

[Вверх](#_)
___
## Как выключить телеметрию
about:config - введи в поиск "telemetry" и:<br>
установи toolkit.telemetry.server на 0.0.0.0, или какой-нибудь несуществующий IP <br>(https://incoming.telemetry.mozilla.org - значение по умолчанию).<br>
установи значение "False" для:<br>
toolkit.telemetry.unified,<br>
toolkit.telemetry.enabled<br>
toolkit.telemetry.archive.enabled.

[Вверх](#_)
___
## Как открыть менеджер очистки
Ctrl+Shift+Delete

[Вверх](#_)
___
## Я случайно удалил профиль, как восстановить?
Хорошо восстанавливается, например, при помощи Recuva (установите в Recuva поиск по папке профиля) <br>
Главное восстановить файлы из пункта [Важные файлы файлы и папки профиля](#Важные-файлы-и-папки-профиля) <br>
Остальное можно регенерировать при первом запуске FF.

[Вверх](#_)
___
## Немного об ID аддонов
У некоторых аддонов ID генерируются индивидуально при установке аддона. <br>
Такие ID представляют собой случайно генерированную комбинацию цифр и английских букв. <br>
У некоторых аддонов ID "зафиксирован" автором. <br>

Также у аддонов есть "Внутренний UUID", но это уже другая история. <br>
Немного о безопасности: <br>
https://www.ghacks.net/2017/08/30/firefox-webextensions-may-identify-you-on-the-internet/ <br>

**Как узнать ID аддона?** <br>
`about:debugging` <br>
Это поможет вам, например, разобраться с содержимым папки профиля extensions <br>
без необходимости лезть в *.xpi архиватором 7zip<br>
чтобы понять какой аддон скрывается под названием типа dfGFfg-435GF535-dfgfdgdTRdfgfJH

**Где хранятся ID аддонов?**<br>
Папка профиля > extensions.json <br>
Открой с notepad++ (например), ищи по названию аддона. <br>

**Как изменить (регенерировать) ID аддона?** <br>
- открыть FF <br>
- удалить аддон <br>
- закрыть FF <br>
- открыть FF <br>
- установить аддон заново <br>

[Вверх](#_)
___
## Как затенять выгруженные вкладки
userChrome.css : <br>
`.tabbrowser-tab[pending] {opacity: .3;}` <br>
Для юзеров TST на FF57+ способ немного иной.

[Вверх](#_)
___
## Как спрятать кнопку "Закрыть" на вкладках
userChrome.css : <br>
`.tab-close-button { display: none !important; }` <br>
Для юзеров TST на FF57+ способ немного иной.

[Вверх](#_)
___
## Как мне удалить дополнение Download Master-а и т.п.
аддоны, которые нельзя удалить через список about:addons ? <br>

Program Files (x86) \ Download Master \ distribution \ bundles - так было раньше (не актуально) <br>

Актуально: <br>
C: \ Users \ хххххххх \ AppData \ Roaming \ Mozilla \ Extensions <br>
Адреса наглых дополнений можно найти в CCleaner. <br>
Tools > Browser Plugins > Firefox <br>
Там же - удалить или отключить. <br>

[Вверх](#_)
___
## Хочу поставить на Новую Вкладку
...картинку фоном. Как?<br>

<a href="http://piccy.info/view3/12381888/3fe85bd55adc9765e57c500890bd2fa8/" target="_blank"><img src="http://i.piccy.info/i9/38469911acf11c36e1640e36594bb2d9/1527972504/16982/1246306/sshot_142_500.jpg" alt="Piccy.info - Free Image Hosting" border="0" /></a><a href="http://i.piccy.info/a3c/2018-06-02-20-48/i9-12381888/486x343-r" target="_blank"><img src="http://i.piccy.info/a3/2018-06-02-20-48/i9-12381888/486x343-r/i.gif" alt="" border="0" /></a> <br>

userContent.css : <br>
@-moz-document url("about:newtab")<br>
{<br>
.activity-stream<br>
	{<br>
		background-image: url('https://avatanplus.com/files/resources/mid/56c610b63d727152f5b147ec.png')!important;<br>
		background-size: 20%!important;<br>
		background-repeat: no-repeat!important;<br>
		background-position: right bottom!important;<br>
		background-attachment: fixed!important;<br>
	}<br>
}<br>

[Вверх](#_)
___
## Хочу заменить иконку сайта на Новой Вкладке
- Идем в папку профиля
- Открываем папку thumbnails
- Ищем нужную "некрасивую иконку"
- Открываем её графическим редактором, изменяем дизайн так, чтобы новое изображение вписывалось в квадрат СЛЕВА.
- Сохраняем.
- Делаем файлу атрибут "только для чтения"
- Перезагружаем FF

<a href="http://piccy.info/view3/12381967/eec4e98ea23b531137ab464af5b3c5a2/" target="_blank"><img src="http://i.piccy.info/i9/da81dbda2783919812c2e30d08d4fd92/1527977994/11045/1246306/sshot_146_500.jpg" alt="Piccy.info - Free Image Hosting" border="0" /></a><a href="http://i.piccy.info/a3c/2018-06-02-22-19/i9-12381967/500x109-r" target="_blank"><img src="http://i.piccy.info/a3/2018-06-02-22-19/i9-12381967/500x109-r/i.gif" alt="" border="0" /></a>

[Вверх](#_)
___
## Что делать, если Новая Вкладка - пустая белая страница
Например конфликт с New Tab Overrider

browser.newtabpage.enabled = true

[Вверх](#_)
___
## Я слышал, что есть плохое, нехорошее место
где прячутся коварные *.xpi файлы "системных" аддонов FF <br>
которые нельзя удалить через список about:addons (они скрыты). Что мне делать? <br>

Текст составлен для 59.0b12 (x64) <br>

⭐ - отмечено то, что при желании можно выключить гарантированно без последствий. <br>

Где размещены эти *.xpi файлы? <br>
Ваш путь установки Mozilla Firefox\browser\features <br>
Аддоны можно удалить оттуда "физически", <br>
можно выключить через Ccleaner: Tools > Browser Plugins > Firefox <br>
можно выключить через about:config (список будет дополнятся) <br>
можно через ветку реестра: `HKEY_CURRENT_USER\Software\Mozilla\Firefox\Extensions` <br>
___
⭐**Activity Stream** <br>
activity-stream@mozilla.org.xpi <br>
https://wiki.mozilla.org/Firefox/Activity_Stream <br>
мусор на Новой Вкладке (Ctrl+T) <br>
Домашняя страница заменена на Activity Stream, где пользователю кроме часто посещаемых сайтов предлагаются новости о Firefox, интернет-культуру и случайные мемы от сервиса Pocket. <br>
✅ Выключить (возвращает прежний вид): <br>
browser.newtabpage.activity-stream.enabled = false <br>
✅ Выключить аддон: <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
**Aplication Update Service Helper** <br>
aushelper@mozilla.org.xpi <br>
https://www.ghacks.net/2016/11/04/application-update-service-helper/ <br>
Это позволяет Mozilla по-тихому вводить обновления в браузер без необходимости обновлять браузер до более новой версии. <br>
Обновления могут изменять настройки браузера и т.д. <br>
Недостаток заключается в том, что пользователи не контролируют их и не знают об их активности. <br>
✅ Выключить аддон: <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
⭐**Firefox Screenshots** <br>
screenshots@mozilla.org.xpi <br>
https://support.mozilla.org/ru/kb/skrinshoty-firefox <br>
Скриншоты Firefox это новая функция, позволяющая делать, скачивать, собирать и передавать скриншоты.  <br>
Чтобы использовать её, щёлкните по меню Действия страницы в адресной строке и выберите screenshots menu icon  <br>
Сделать скриншот в выпадающем меню. <br>
✅ Выключить: <br>
extensions.screenshots.system-disabled = true <br>
extensions.screenshots.disabled = true <br>
✅ Выключить аддон: <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
**Follow-on Search Telemetry** <br>
followonsearch@mozilla.com.xpi <br>
https://support.mozilla.org/ru/kb/otpravka-dannyh-o-proizvoditelnosti-v-mozilla-chto <br>
Для инженеров Mozilla полезно иметь возможность произвести измерения параметров Firefox при его работе на реальных компьютерах пользователей. Такую возможность предоставляет функция телеметрии, которая отправляет нам информацию о производительности и использовании Firefox. В то время, когда вы используете Firefox, функция телеметрии измеряет и собирает обезличенную информацию, такую как потребление памяти, время реакции на действия пользователей и использование его компонентов. Эта информация отправляется в Mozilla ежедневно, и используется, чтобы сделать Firefox ещё хуже. <br>
✅ Выключить: <br>
about:config - search for "telemetry" and: <br>
set toolkit.telemetry.server to 0.0.0.0, or some other non-existent IP (https://incoming.telemetry.mozilla.org by default). <br>
toolkit.telemetry.unified = false <br>
toolkit.telemetry.enabled = false <br>
toolkit.telemetry.archive.enabled = false <br>
✅ Выключить аддон: <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
**Form Autofill** <br>
formautofill@mozilla.org.xpi <br>
Вероятно, это (?): <br>
https://support.mozilla.org/ru/kb/upravlenie-avtomaticheskim-zapolneniem-form-vashej <br>
https://support.mozilla.org/ru/kb/avtomaticheskoe-zapolnenie-vashego-adresa-v-formah <br>
Firefox может запоминать то, что вы вводили в формах на веб-страницах, также известных как текстовые поля. После того как вы ввели что-либо в такую форму на веб-страницу (такую как поле поиска), при следующем посещении вами страницы введенные ранее значения будут доступны для повторного использования. <br>
✅ Выключить аддон: <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
**Photon onboarding** <br>
onboarding@mozilla.org.xpi <br>
http://techdows.com/2017/06/firefox-photon-onboarding-tour.html <br>
Какая-то малополезная штука, типа демонстрации новых фич при первом запуске. <br>
✅ Выключить: <br>
browser.onboarding.enabled = false <br>
browser.onboarding.hidden = true <br>
✅ Выключить аддон: <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
⭐**Pocket** <br>
firefox@getpocket.com.xpi <br>
https://support.mozilla.org/ru/kb/sohranit-veb-stranicy-dlya-posleduyushego-prosmotr <br>
Кнопка Pocket позволяет сохранять веб-страницы и видео в Pocket всего одним щелчком мыши. Pocket удаляет всё ненужное и сохраняет страницу в чистом, строгом виде и позволяет получить доступ к ней через приложение Pocket. Всё, что вам нужно, это бесплатный аккаунт, соединение с интернетом и кнопка Pocket в адресной строке. <br>
✅ Выключить: <br>
extensions.pocket.enabled = false <br>
✅ Выключить аддон: <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
**Shield Recipe Client** <br>
shield-recipe-client@mozilla.org.xpi <br>
https://support.mozilla.org/ru/questions/1159992 <br>
https://wiki.mozilla.org/Firefox/Shield <br>
https://bugzilla.mozilla.org/show_bug.cgi?id=1308656 <br>
The shield-recipe-client is the client component of SHIELD [0]. It is intended to replace the self-repair hidden iframe, and handles fetching, verifying, and executing recipes from the Normandy server [1]. For an overview of the general system, see the Normandy Concepts docs [2]. <br>
The add-on provides a restricted sandbox for recipe actions to execute in, and provides "driver functions" for recipe actions to perform privileged actions. Right now this consists of <br>
* logging facilities <br>
* showing heartbeat prompts <br>
* storing data reliably <br>
* getting information about the client, such as browser version <br>

For a complete list of driver functions, see the Driver API docs [3]. This list of driver functions will grow in the future to accommodate new recipe functionality. <br>
The code for shield-recipe-client is developed at https://github.com/mozilla/normandy-addon. This is written as a SDK addon and built with JPM. The code checked into mozilla-central will be based on the xpi built from this repo. I talked with Rob Helmer about this, and we decided it will be ok for now. In the future we should remove the addon SDK code in favor of standard Firefox frontend code. <br>
Mike Kelly announced our intent to ship this system addon on the Go Faster mailing list [4]. Several security and operations concerns have been covered in that thread. <br>
✅ Выключить аддон: <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
**Web Compat** <br>
webcompat@mozilla.org.xpi <br>
https://superuser.com/questions/1117062/what-is-the-web-compat-firefox-addon-avast-suggest-removing <br>
Urgent post-release fixes for web compatibility <br>
Срочные пост-релизные исправления для совместимости в Интернете. <br>
Команда WebCompat в Mozilla гарантирует, что веб-сайт корректно работает в Firefox, в большинстве случаев. Иногда мы выпускаем изменения Firefox, которые могут нарушать работу некоторых сайтов, и нам нужно что-то сделать (оперативно). Мы используем Web Compat как средство для доставки таких исправлений в случае необходимости (в ваш ФФ). <br>
✅ Выключить аддон (думаю не стоит): <br>
Ccleaner - Tools - Browser Plugins - Firefox - название аддона <br>
___
Этих у меня в 59.0b12 (x64) нет: <br>
 
**Click-to-Play staged rollout**<br>
clicktoplay-rollout@mozilla.org <br>
install.rdf: "Staged rollout for Click-to-Play Flash." <br>
Note: this change from "Always Activate" to "Ask to Activate" should be completed by now. <br>
 
**Multi-process staged rollout**<br>
e10srollout@mozilla.org <br>
install.rdf: "Staged rollout of Firefox multi-process feature." <br>
Note: I think this has been in many, many releases by now. <br>

[Вверх](#_)
