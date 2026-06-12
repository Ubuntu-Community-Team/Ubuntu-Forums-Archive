---
title: "[64-bit] Firefox totally &amp; mysteriously  hosed, can't re-install"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2009-12-23
I somehow have managed to delete one or more files essential to the installation of Firefox. 

I discovered I was running 32-bit Firefox-3.5.6 on a new 64-bit Wild Dog Performance desktop unit from System76.

I deleted *that* Firefox (before re-installing correctly via the Synaptic Package Manager) only to discover (*after* installation via the SPM) that I had *another* 32-bit Firefox still installed.

I then deleted some Firefox files -- because at least one (and probably both, I don't remember) of the 32-bit Firefoxes was installed *not* from the package manager.  (And I'm not completely sure of this, but my thinking was that if it wasn't installed via the SPM, it couldn't be un-installed via the SPM.)

Then I tried to re-install Firefox-3.5 a second time from the Synaptic Package Manager.

I also re-installed:

xulrunner-1.9.1,
xulrunner-1.9.1-gnome-support,
firefox-3.5-gnome-support,
and firefox-3.5-branding.

BUT, when I click on the Firefox icon in the gnome panel (or when I click on Applications --> Internet --> Firefiox Web Browser), I get an error-message box:

**Could not launch 'Firefox Web Browser'  Failed to execute child process "firefox" (No such file or directory)**

I have a file in /opt/firefox/  called "removed-files".  It has 531 lines, one file per line.  I'm going to include it here in hopes that something useful might be spotted.  I also include the /opt/firefox directory.

 I know: the situation is quite a mess.  Any/all suggestions very welcome at this point.

This is the /opt/firefox/ dir:

```

    4 drwxr-xr-x 13 root root     4096 2009-12-22 17:14 ./
    4 drwxr-xr-x  4 root root     4096 2009-12-19 20:02 ../
    4 -rw-r--r--  1 root root     2126 2009-12-02 00:42 application.ini
    0 -rw-r--r--  1 root root        0 2009-12-02 00:42 .autoreg
    4 -rw-r--r--  1 root root     2552 2009-12-02 00:42 blocklist.xml
    4 -rw-r--r--  1 root root      232 2009-12-02 00:42 browserconfig.properties
    4 drwxr-xr-x  3 root root     4096 2009-12-02 00:42 chrome/
    4 drwxr-xr-x  2 root root     4096 2009-12-02 00:42 components/
   48 -rwxr-xr-x  1 root root    45912 2009-12-02 00:42 crashreporter*
    4 -rw-r--r--  1 root root     3801 2009-12-02 00:42 crashreporter.ini
    4 -rw-r--r--  1 root root      583 2009-12-02 00:42 crashreporter-override.ini
    4 drwxr-xr-x  5 root root     4096 2009-12-02 00:42 defaults/
    0 lrwxrwxrwx  1 root root       24 2009-12-19 20:02 dictionaries -> /usr/share/myspell/dicts/
    4 drwxr-xr-x  2 root root     4096 2009-12-02 00:42 dictionaries_2009-12-19T20:02:58-0500/
    4 drwxr-xr-x  3 root root     4096 2009-12-02 00:42 extensions/
    4 drwxr-xr-x  2 root root     4096 2009-12-02 00:42 greprefs/
    4 drwxr-xr-x  2 root root     4096 2009-12-02 00:42 icons/
    4 -rw-r--r--  1 root root      478 2009-12-02 00:42 libfreebl3.chk
  320 -rwxr-xr-x  1 root root   321140 2009-12-02 00:42 libfreebl3.so*
  828 -rwxr-xr-x  1 root root   839912 2009-12-02 00:42 libmozjs.so*
  204 -rwxr-xr-x  1 root root   200736 2009-12-02 00:42 libnspr4.so*
  848 -rwxr-xr-x  1 root root   863000 2009-12-02 00:42 libnss3.so*
  336 -rwxr-xr-x  1 root root   338076 2009-12-02 00:42 libnssckbi.so*
    4 -rw-r--r--  1 root root      478 2009-12-02 00:42 libnssdbm3.chk
  128 -rwxr-xr-x  1 root root   122908 2009-12-02 00:42 libnssdbm3.so*
   84 -rwxr-xr-x  1 root root    78800 2009-12-02 00:42 libnssutil3.so*
   16 -rwxr-xr-x  1 root root    13180 2009-12-02 00:42 libplc4.so*
   12 -rwxr-xr-x  1 root root     8748 2009-12-02 00:42 libplds4.so*
  128 -rwxr-xr-x  1 root root   125644 2009-12-02 00:42 libsmime3.so*
    4 -rw-r--r--  1 root root      478 2009-12-02 00:42 libsoftokn3.chk
  196 -rwxr-xr-x  1 root root   194128 2009-12-02 00:42 libsoftokn3.so*
  444 -rwxr-xr-x  1 root root   447000 2009-12-02 00:42 libsqlite3.so*
  164 -rwxr-xr-x  1 root root   160140 2009-12-02 00:42 libssl3.so*
   12 -rwxr-xr-x  1 root root    12160 2009-12-02 00:42 libxpcom.so*
13892 -rwxr-xr-x  1 root root 14204400 2009-12-02 00:42 libxul.so*
    4 drwxr-xr-x  2 root root     4096 2009-12-02 00:42 modules/
   12 -rwxr-xr-x  1 root root    10996 2009-12-02 00:42 mozilla-xremote-client*
    4 -rw-r--r--  1 root root      112 2009-12-02 00:42 old-homepage-default.properties
    4 -rw-r--r--  1 root root      136 2009-12-02 00:42 platform.ini
    0 lrwxrwxrwx  1 root root       24 2009-12-19 20:02 plugins -> /usr/lib/mozilla/plugins/
    4 drwxr-xr-x  2 root root     4096 2009-12-02 00:42 plugins_2009-12-19T20:02:58-0500/
    4 -rw-r--r--  1 root root      177 2009-12-02 00:42 README.txt
   16 -rw-r--r--  1 root root    15861 2009-12-02 00:42 removed-files
    4 drwxr-xr-x  6 root root     4096 2009-12-02 00:42 res/
   12 -rwxr-xr-x  1 root root    10450 2009-12-02 00:42 run-mozilla.sh*
    4 drwxr-xr-x  2 root root     4096 2009-12-02 00:42 searchplugins/
    4 -rw-r--r--  1 root root      825 2009-12-02 00:42 Throbber-small.gif
    4 -rw-r--r--  1 root root        6 2009-12-02 00:42 update.locale
   76 -rwxr-xr-x  1 root root    70472 2009-12-02 00:42 updater*
    4 -rw-r--r--  1 root root      143 2009-12-02 00:42 updater.ini

```

And this is the /opt/firefox/removed-files file:

```

chrome/US.jar
chrome/en-win.jar
chrome/help.jar
chrome/chrome.rdf
chrome/installed-chrome.txt
chrome/app-chrome.manifest
chrome/overlayinfo/
chrome/m3ffxtbr.manifest
chrome/m3ffxtbr.jar
defaults/pref/all.js
defaults/pref/security-prefs.js
defaults/pref/winpref.js
defaults/pref/xpinstall.js
defaults/pref/bug307259.js
defaults/pref/bug259708.js
defaults/profile/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
defaults/profile/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/
defaults/profile/extensions/Extensions.rdf
defaults/profile/extensions/installed-extensions.txt
defaults/profile/extensions/
defaults/profile/search.rdf
defaults/profile/US/
extensions/{641d8d09-7dda-4850-8228-ac0ab65e2ac9}/install.rdf
extensions/{641d8d09-7dda-4850-8228-ac0ab65e2ac9}/
searchplugins/dictionary.src
searchplugins/dictionary.png
searchplugins/amazondotcom.src
searchplugins/amazondotcom.png
searchplugins/creativecommons.src
searchplugins/creativecommons.png
searchplugins/answers.src
searchplugins/answers.png
searchplugins/eBay.src
searchplugins/eBay.gif
searchplugins/google.src
searchplugins/google.gif
searchplugins/yahoo.src
searchplugins/yahoo.gif
searchplugins/
libxpcom_core.so
components/libjar50.so
components/libjsd.so
components/libxpinstall.so
libxpistub.so
component.reg
components/compreg.dat
components/libmyspell.so
components/libspellchecker.so
components/libspellchk.so
components/xpti.dat
components/xptitemp.dat
components/nsBackgroundUpdateService.js
components/nsCloseAllWindows.js
components/autocomplete.xpt
libzlib.so
components/BrandRes.dll
components/fullsoft.dll
components/master.ini
components/qfaservices.dll
components/qfaservices.xpt
components/talkback-l10n.ini
components/talkback.cnt
components/talkback.exe
components/talkback.hlp
components/libqfaservices.so
components/talkback/master.ini
components/talkback/talkback
components/talkback/talkback.so
components/talkback/XTalkback.ad
extensions/reporter@mozilla.org/install.rdf
extensions/reporter@mozilla.org/chrome.manifest
extensions/reporter@mozilla.org/chrome/reporter.jar
extensions/reporter@mozilla.org/defaults/preferences/reporter.js
extensions/inspector@mozilla.org/install.rdf
extensions/inspector@mozilla.org/components/inspector-cmdline.js
extensions/inspector@mozilla.org/chrome.manifest
extensions/inspector@mozilla.org/chrome/inspector.jar
extensions/inspector@mozilla.org/defaults/preferences/inspector.js
extensions/inspector@mozilla.org/platform/WINNT/chrome/icons/default/winInspectorMain.ico
extensions/inspector@mozilla.org/components/inspector.xpt
extensions/inspector@mozilla.org/components/libinspector.so
extensions/inspector@mozilla.org/chrome/icons/default/winInspectorMain.ico
uninstall/UninstallFirefox.exe
uninstall/UninstallDeerPark.exe
uninstall/uninst.exe
uninstall/uninstall.exe
components/myspell/en-US.dic
components/myspell/en-US.aff
searchplugins/centrum-cz.xml
searchplugins/eBay-fy-NL.xml
searchplugins/eBay-nl.xml
searchplugins/eBay-zh-CN.xml
searchplugins/eBay-zh-TW.xml
searchplugins/filesearchru.xml
searchplugins/goo.xml
searchplugins/google-ar.xml
searchplugins/grandiccionari.xml
searchplugins/lingvo.yandex.ru.xml
searchplugins/nana.xml
searchplugins/netex.xml
searchplugins/nosaltres.xml
searchplugins/pbi-pl.xml
searchplugins/taobao.xml
searchplugins/wikipedia-en-CN.xml
searchplugins/wikipedia-zh.xml
searchplugins/yahoo-jp-shopping.xml
searchplugins/yahoo-ru.xml
searchplugins/yahoo-zh-CN.xml
searchplugins/DRAE.src
searchplugins/DRAE.png
searchplugins/DRAE.gif
searchplugins/MediaDICO-fr.src
searchplugins/MediaDICO-fr.png
searchplugins/MediaDICO-fr.gif
searchplugins/allegro-pl.src
searchplugins/allegro-pl.png
searchplugins/allegro-pl.gif
searchplugins/amazon-de.src
searchplugins/amazon-de.png
searchplugins/amazon-de.gif
searchplugins/amazon-en-GB.src
searchplugins/amazon-en-GB.png
searchplugins/amazon-en-GB.gif
searchplugins/amazon-france.src
searchplugins/amazon-france.png
searchplugins/amazon-france.gif
searchplugins/amazon-jp.src
searchplugins/amazon-jp.png
searchplugins/amazon-jp.gif
searchplugins/amazondotcom.src
searchplugins/amazondotcom.png
searchplugins/amazondotcom.gif
searchplugins/amazondotcom-zh-TW.src
searchplugins/amazondotcom-zh-TW.png
searchplugins/amazondotcom-zh-TW.gif
searchplugins/answers.src
searchplugins/answers.png
searchplugins/answers.gif
searchplugins/google-es-ES.src
searchplugins/google-es-ES.png
searchplugins/google-es-ES.gif
searchplugins/atlas-sk.src
searchplugins/atlas-sk.png
searchplugins/atlas-sk.gif
searchplugins/baidu.src
searchplugins/baidu.png
searchplugins/baidu.gif
searchplugins/bok-NO.src
searchplugins/bok-NO.png
searchplugins/bok-NO.gif
searchplugins/bolcom-nl.src
searchplugins/bolcom-nl.png
searchplugins/bolcom-nl.gif
searchplugins/bookplus-fi.src
searchplugins/bookplus-fi.png
searchplugins/bookplus-fi.gif
searchplugins/caplex-NO.src
searchplugins/caplex-NO.png
searchplugins/caplex-NO.gif
searchplugins/centrum-cz.src
searchplugins/centrum-cz.png
searchplugins/centrum-cz.gif
searchplugins/creativecommons.src
searchplugins/creativecommons.png
searchplugins/creativecommons.gif
searchplugins/creativecommons-fi.src
searchplugins/creativecommons-fi.png
searchplugins/creativecommons-fi.gif
searchplugins/creativecommons-it.src
searchplugins/creativecommons-it.png
searchplugins/creativecommons-it.gif
searchplugins/creativecommons-zh-TW.src
searchplugins/creativecommons-zh-TW.png
searchplugins/creativecommons-zh-TW.gif
searchplugins/daum-ko.src
searchplugins/daum-ko.png
searchplugins/daum-ko.gif
searchplugins/demauro-it.src
searchplugins/demauro-it.png
searchplugins/demauro-it.gif
searchplugins/dictionary-en-GB.src
searchplugins/dictionary-en-GB.png
searchplugins/dictionary-en-GB.gif
searchplugins/dunaj-sk.src
searchplugins/dunaj-sk.png
searchplugins/dunaj-sk.gif
searchplugins/eBay.src
searchplugins/eBay.png
searchplugins/eBay.gif
searchplugins/eBay-de.src
searchplugins/eBay-de.png
searchplugins/eBay-de.gif
searchplugins/eBay-en-GB.src
searchplugins/eBay-en-GB.png
searchplugins/eBay-en-GB.gif
searchplugins/eBay-france.src
searchplugins/eBay-france.png
searchplugins/eBay-france.gif
searchplugins/eBay-gu.src
searchplugins/eBay-gu.png
searchplugins/eBay-gu.gif
searchplugins/eBay-nl.src
searchplugins/eBay-nl.png
searchplugins/eBay-nl.gif
searchplugins/eBay-zh-CN.src
searchplugins/eBay-zh-CN.png
searchplugins/eBay-zh-CN.gif
searchplugins/eBay-zh-TW.src
searchplugins/eBay-zh-TW.png
searchplugins/eBay-zh-TW.gif
searchplugins/ebay-it.src
searchplugins/ebay-it.png
searchplugins/ebay-it.gif
searchplugins/filesearchru.src
searchplugins/filesearchru.png
searchplugins/filesearchru.gif
searchplugins/goo.src
searchplugins/goo.png
searchplugins/goo.gif
searchplugins/google.src
searchplugins/google.png
searchplugins/google.gif
searchplugins/google-NO.src
searchplugins/google-NO.png
searchplugins/google-NO.gif
searchplugins/google-ar.src
searchplugins/google-ar.png
searchplugins/google-ar.gif
searchplugins/google-bg.src
searchplugins/google-bg.png
searchplugins/google-bg.gif
searchplugins/google-ca.src
searchplugins/google-ca.png
searchplugins/google-ca.gif
searchplugins/google-de.src
searchplugins/google-de.png
searchplugins/google-de.gif
searchplugins/google-dk.src
searchplugins/google-dk.png
searchplugins/google-dk.gif
searchplugins/google-en-GB.src
searchplugins/google-en-GB.png
searchplugins/google-en-GB.gif
searchplugins/google-eu.src
searchplugins/google-eu.png
searchplugins/google-eu.gif
searchplugins/google-fi.src
searchplugins/google-fi.png
searchplugins/google-fi.gif
searchplugins/google-gu.src
searchplugins/google-gu.png
searchplugins/google-gu.gif
searchplugins/google-it.src
searchplugins/google-it.png
searchplugins/google-it.gif
searchplugins/google-jp.src
searchplugins/google-jp.png
searchplugins/google-jp.gif
searchplugins/google-ko.src
searchplugins/google-ko.png
searchplugins/google-ko.gif
searchplugins/google-lt.src
searchplugins/google-lt.png
searchplugins/google-lt.gif
searchplugins/google-nl.src
searchplugins/google-nl.png
searchplugins/google-nl.gif
searchplugins/google-pl.src
searchplugins/google-pl.png
searchplugins/google-pl.gif
searchplugins/google-ro.src
searchplugins/google-ro.png
searchplugins/google-ro.gif
searchplugins/google-ru.src
searchplugins/google-ru.png
searchplugins/google-ru.gif
searchplugins/google-sl.src
searchplugins/google-sl.png
searchplugins/google-sl.gif
searchplugins/google-zh-TW.src
searchplugins/google-zh-TW.png
searchplugins/google-zh-TW.gif
searchplugins/grandiccionari.src
searchplugins/grandiccionari.png
searchplugins/grandiccionari.gif
searchplugins/huuto-fi.src
searchplugins/huuto-fi.png
searchplugins/huuto-fi.gif
searchplugins/jyxo-cz.src
searchplugins/jyxo-cz.png
searchplugins/jyxo-cz.gif
searchplugins/lingvo.yandex.ru.src
searchplugins/lingvo.yandex.ru.png
searchplugins/lingvo.yandex.ru.gif
searchplugins/llibres.src
searchplugins/llibres.png
searchplugins/llibres.gif
searchplugins/mall-cz.src
searchplugins/mall-cz.png
searchplugins/mall-cz.gif
searchplugins/mercadolivre-com-br.src
searchplugins/mercadolivre-com-br.png
searchplugins/mercadolivre-com-br.gif
searchplugins/merlin-pl.src
searchplugins/merlin-pl.png
searchplugins/merlin-pl.gif
searchplugins/najdi-si.src
searchplugins/najdi-si.png
searchplugins/najdi-si.gif
searchplugins/naver-ko.src
searchplugins/naver-ko.png
searchplugins/naver-ko.gif
searchplugins/nosaltres.src
searchplugins/nosaltres.png
searchplugins/nosaltres.gif
searchplugins/pbi-pl.src
searchplugins/pbi-pl.png
searchplugins/pbi-pl.gif
searchplugins/google-pt-BR.src
searchplugins/google-pt-BR.png
searchplugins/google-pt-BR.gif
searchplugins/priceru.src
searchplugins/priceru.png
searchplugins/priceru.gif
searchplugins/pwn-pl.src
searchplugins/pwn-pl.png
searchplugins/pwn-pl.gif
searchplugins/qxl-NO.src
searchplugins/qxl-NO.png
searchplugins/qxl-NO.gif
searchplugins/rakuten.src
searchplugins/rakuten.png
searchplugins/rakuten.gif
searchplugins/seznam-cz.src
searchplugins/seznam-cz.png
searchplugins/seznam-cz.gif
searchplugins/sigov-gov-si.src
searchplugins/sigov-gov-si.png
searchplugins/sigov-gov-si.gif
searchplugins/slunecnice-cz.src
searchplugins/slunecnice-cz.png
searchplugins/slunecnice-cz.gif
searchplugins/submarino-com-br.src
searchplugins/submarino-com-br.png
searchplugins/submarino-com-br.gif
searchplugins/taobao.src
searchplugins/taobao.png
searchplugins/taobao.gif
searchplugins/telefonkatalogen-NO.src
searchplugins/telefonkatalogen-NO.png
searchplugins/telefonkatalogen-NO.gif
searchplugins/universal-pt.src
searchplugins/universal-pt.png
searchplugins/universal-pt.gif
searchplugins/vandale-nl.src
searchplugins/vandale-nl.png
searchplugins/vandale-nl.gif
searchplugins/walla_sites.src
searchplugins/walla_sites.png
searchplugins/walla_sites.gif
searchplugins/wikipedia-bg.src
searchplugins/wikipedia-bg.png
searchplugins/wikipedia-bg.gif
searchplugins/wikipedia-ca.src
searchplugins/wikipedia-ca.png
searchplugins/wikipedia-ca.gif
searchplugins/wikipedia-de.src
searchplugins/wikipedia-de.png
searchplugins/wikipedia-de.gif
searchplugins/wikipedia-es-ES.src
searchplugins/wikipedia-es-ES.png
searchplugins/wikipedia-es-ES.gif
searchplugins/wikipedia-eu.src
searchplugins/wikipedia-eu.png
searchplugins/wikipedia-eu.gif
searchplugins/wikipedia-fi.src
searchplugins/wikipedia-fi.png
searchplugins/wikipedia-fi.gif
searchplugins/wikipedia-fr.src
searchplugins/wikipedia-fr.png
searchplugins/wikipedia-fr.gif
searchplugins/wikipedia-fy.src
searchplugins/wikipedia-fy.png
searchplugins/wikipedia-fy.gif
searchplugins/wikipedia-he.src
searchplugins/wikipedia-he.png
searchplugins/wikipedia-he.gif
searchplugins/wikipedia-it.src
searchplugins/wikipedia-it.png
searchplugins/wikipedia-it.gif
searchplugins/wikipedia-lt.src
searchplugins/wikipedia-lt.png
 searchplugins/wikipedia-lt.gif
searchplugins/wikipedia-nl.src
searchplugins/wikipedia-nl.png
searchplugins/wikipedia-nl.gif
searchplugins/wikipedia-pl.src
searchplugins/wikipedia-pl.png
searchplugins/wikipedia-pl.gif
searchplugins/wikipedia-ru.src
searchplugins/wikipedia-ru.png
searchplugins/wikipedia-ru.gif
searchplugins/wikipedia-sk.src
searchplugins/wikipedia-sk.png
searchplugins/wikipedia-sk.gif
searchplugins/wp-pl.src
searchplugins/wp-pl.png
searchplugins/wp-pl.gif
searchplugins/yahoo.src
searchplugins/yahoo.png
searchplugins/yahoo.gif
searchplugins/yahoo-NO.src
searchplugins/yahoo-NO.png
searchplugins/yahoo-NO.gif
searchplugins/yahoo-ar.src
searchplugins/yahoo-ar.png
searchplugins/yahoo-ar.gif
searchplugins/yahoo-ca.src
searchplugins/yahoo-ca.png
searchplugins/yahoo-ca.gif
searchplugins/yahoo-cn.src
searchplugins/yahoo-cn.png
searchplugins/yahoo-cn.gif
searchplugins/yahoo-de.src
searchplugins/yahoo-de.png
searchplugins/yahoo-de.gif
searchplugins/yahoo-dk.src
searchplugins/yahoo-dk.png
searchplugins/yahoo-dk.gif
searchplugins/yahoo-en-GB.src
searchplugins/yahoo-en-GB.png
searchplugins/yahoo-en-GB.gif
searchplugins/yahoo-es-ES.src
searchplugins/yahoo-es-ES.png
searchplugins/yahoo-es-ES.gif
searchplugins/yahoo-fi.src
searchplugins/yahoo-fi.png
searchplugins/yahoo-fi.gif
searchplugins/yahoo-france.src
searchplugins/yahoo-france.png
searchplugins/yahoo-france.gif
searchplugins/yahoo-gu.src
searchplugins/yahoo-gu.png
searchplugins/yahoo-gu.gif
searchplugins/yahoo-it.src
searchplugins/yahoo-it.png
searchplugins/yahoo-it.gif
searchplugins/yahoo-jp.src
 searchplugins/yahoo-jp.png
searchplugins/yahoo-jp.gif
searchplugins/yahoo-jp-auctions.src
searchplugins/yahoo-jp-auctions.png
searchplugins/yahoo-jp-auctions.gif
searchplugins/yahoo-jp-shopping.src
searchplugins/yahoo-jp-shopping.png
searchplugins/yahoo-jp-shopping.gif
searchplugins/yahoo-kr.src
searchplugins/yahoo-kr.png
searchplugins/yahoo-kr.gif
searchplugins/yahoo-nl.src
searchplugins/yahoo-nl.png
searchplugins/yahoo-nl.gif
searchplugins/google-ga-IE.src
searchplugins/google-ga-IE.png
searchplugins/google-ga-IE.gif
searchplugins/yahoo-pt-BR.src
searchplugins/yahoo-pt-BR.png
searchplugins/yahoo-pt-BR.gif
searchplugins/yahoo-tw.src
searchplugins/yahoo-tw.png
searchplugins/yahoo-tw.gif
searchplugins/yandex.src
searchplugins/yandex.png
searchplugins/yandex.gif
searchplugins/zoznam-sk.src
searchplugins/zoznam-sk.png
searchplugins/zoznam-sk.gif
components/sidebar.xpt
components/xmlextras.xpt
components/xpcom.xpt
components/bookmarks.xpt
components/history.xpt
components/nsBookmarkTransactionManager.js
extensions/talkback@mozilla.org/
extensions/talkback@mozilla.org/install.rdf
extensions/talkback@mozilla.org/chrome.manifest
extensions/talkback@mozilla.org/components/qfaservices.xpt
extensions/talkback@mozilla.org/components/libqfaservices.so
extensions/talkback@mozilla.org/components/talkback/talkback
extensions/talkback@mozilla.org/components/talkback/XTalkback.ad
extensions/talkback@mozilla.org/components/talkback/master.ini
extensions/talkback@mozilla.org/components/talkback/talkback.so
components/airbag.xpt
components/nsUrlClassifierTable.js
res/cmessage.txt
res/html/gopher-audio.gif
res/html/gopher-binary.gif
res/html/gopher-find.gif
res/html/gopher-image.gif
res/html/gopher-menu.gif
res/html/gopher-movie.gif
res/html/gopher-sound.gif
res/html/gopher-telnet.gif
res/html/gopher-text.gif
res/html/gopher-unknown.gif
res/fonts/mathfontCMEX10.properties
res/fonts/mathfontCMSY10.properties
res/fonts/mathfontMath1.properties
res/fonts/mathfontMath2.properties
res/fonts/mathfontMath4.properties
res/fonts/mathfontMTExtra.properties
res/fonts/mathfontPUA.properties
res/fonts/mathfontSymbol.properties
res/fonts/fontEncoding.properties
res/fonts/pangoFontEncoding.properties
res/fonts/fontNameMap.properties
libxpcom_compat.so
components/nsDictionary.js
components/nsXmlRpcClient.js
components/nsInterfaceInfoToIDL.js
components/nsScriptableIO.js
chrome/chromelist.txt
modules/JSON.jsm
readme.txt
chrome/icons/default/default.xpm
dictionaries/PL.dic
dictionaries/PL.aff
libjemalloc.so
xpicleanup
chrome.manifest
install.rdf

```

---

### Post by watchpocket on 2009-12-23
For now, I've installed (32-bit) Firefox as follows, as per outlined by scouser73 at: <http://ohioloco.ubuntuforums.org/showthread.php?t=1317822> 

First, I deleted my entire .mozilla folder (bookmarks etc. are saved elsewhere).

Then I downloaded Firefox from getfirefox.com, and did as follows:

1 - Right click & Extract the Firefox tar.bz2

2 - Enter gksudo nautilus in Terminal

3 - Copy & paste the Firefox file that you have just extracted to /opt

4 - Right click on the Ubuntu start logo, select Edit Menus, 

5 - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

6 - In the Name field, type Firefox

7 - In the Command field type /opt/firefox/firefox

8 - In the Comment field type Firefox


This still leaves me with a 32-bit Firefox on a 64-bit machine (and no FF icons, neither in the panel nor in Apps --> Internet --> Firefox).

I've tried several times to install Firefox from the repository, but I always get the same error message after installation, even after removing ~/.mozilla/ .

Maybe with the 32-bit version that I now have working, I can update it with various Firefox packages from the repository and see if it can be made into the 64-bit version that way.  Apart from experimenting with it trial-and-error style, I'm at a loss as to how to install a working 64-bit Firefox and don't know what could be causing the error message with every repository install.

---

### Post by michael37 on 2009-12-23
> **watchpocket said:**
> For now, I've installed (32-bit) Firefox as follows, as per outlined by scouser73 at: <http://ohioloco.ubuntuforums.org/showthread.php?t=1317822> 

First, I deleted my entire .mozilla folder (bookmarks etc. are saved elsewhere).

Then I downloaded Firefox from getfirefox.com, and did as follows:

1 - Right click & Extract the Firefox tar.bz2

2 - Enter gksudo nautilus in Terminal

3 - Copy & paste the Firefox file that you have just extracted to /opt

4 - Right click on the Ubuntu start logo, select Edit Menus, 

5 - Highlight the Internet sub menu & click New Item

You will now see a small dialogue box appear

6 - In the Name field, type Firefox

7 - In the Command field type /opt/firefox/firefox

8 - In the Comment field type Firefox


This still leaves me with a 32-bit Firefox on a 64-bit machine (and no FF icons, neither in the panel nor in Apps --> Internet --> Firefox).

I've tried several times to install Firefox from the repository, but I always get the same error message after installation, even after removing ~/.mozilla/ .

Maybe with the 32-bit version that I now have working, I can update it with various Firefox packages from the repository and see if it can be made into the 64-bit version that way.  Apart from experimenting with it trial-and-error style, I'm at a loss as to how to install a working 64-bit Firefox and don't know what could be causing the error message with every repository install.

Now you tell us!  It's much easier to uninstall something when you know how it was installed.  So, based on the scouser73 description, here is a procedure for complete and bullet proof uninstall of 32-bit Firefox.  

[LIST=1]
[*]Enter gksudo nautilus in Terminal

[*]Delete whole /opt/firefox directory

[*]Right click on the Ubuntu start logo, select Edit Menus,

[*]Highlight the Internet sub menu 

[*]Click on item named Firefox

[*]Delete it

[*]Verify that there is an item named Firefox Web Browser

[*]Click on the Properties button

[*]Verify that command is listed as firefox %u, and close dialogue
[/LIST]

You will now have 32-bit Firefox uninstalled.

---

### Post by watchpocket on 2009-12-23
> **michael37 said:**
>  . . .  It's much easier to uninstall something when you know how it was installed.  So, based on the scouser73 description, here is a procedure for complete and bullet proof uninstall of 32-bit Firefox. [. . .]
You will now have 32-bit Firefox uninstalled.


My point in that last post is that I'd already gotten to a state where I had no Firefox files on my machine.  (At least based on doing a search on "firefox" and having zero files come up.)  Meaning that any 32-bit Firefox had been completely deleted.

It was at that point (when I was sure I had no FF files) that I grabbed Ubuntu Firefox from the repository (it comes with a total of 4 different packages, if I'm not mistaken) in the hopes of it being a working **64-bit FF**.  After that download, that's when I still got the error message. It never installed.

What I'm basically saying is that I've been unsuccessful in getting any functioning 64-bit FF onto my machine (I've never yet seen the right info for 64-bit in Help --> About), so for the moment I've (temporarily) gone back to using the 32-bit FF, just so I could at least have some working FF up.

I have a feeling I'll just experience the same thing if I delete the 32-bit FF and try to download yet again from the repository.   But, maybe I'll try that anyway.

So, a question to your statement that "You will now have 32-bit Firefox uninstalled" is: How do I get a working 64-bit FF installed?

If the answer to that question is simply, "download it from the SPM, and it ***will be*** the 64-bit FF."  I can only say that I've done that, *with* the 32-bit FF Un-installed, and I got the error message I cited previously. Thanks for following all this.

---

### Post by watchpocket on 2009-12-25
> **michael37 said:**
> 
Verify that command is listed as firefox %u, and close dialogue


I got the 32-bit FF un-installed, but with the Properties command as "firefox %u", I still got the error message when I tried to launch the FF icon.

What finally got 64-bit Firefox to run was that I replaced "firefox %u" with "/usr/lib64/firefox-3.5.6/firefox-3.5" as the command in Properties.

My only question about that is, although it's what got 64-bit FF working, are there any potential negative consequences to having that as the command instead of what you suggested? (I don't know what the "%u" in the command signifies.) 

For example could the "/usr/lib64/firefox-3/5/6/firefox-3.5" command cause FF to --  I don't know -- not get automatically updated or anything like that?

---

### Post by michael37 on 2009-12-25
> **watchpocket said:**
> I got the 32-bit FF un-installed, but with the Properties command as "firefox %u", I still got the error message when I tried to launch the FF icon.

What finally got 64-bit Firefox to run was that I replaced "firefox %u" with "/usr/lib64/firefox-3.5.6/firefox-3.5" as the command in Properties.

My only question about that is, although it's what got 64-bit FF working, are there any potential negative consequences to having that as the command instead of what you suggested? (I don't know what the "%u" in the command signifies.) 

For example could the "/usr/lib64/firefox-3/5/6/firefox-3.5" command cause FF to --  I don't know -- not get automatically updated or anything like that?

What you did will work, but it will not work well through updates.  As you can get firefox-3/5/6 refers to the specific version.

Here is what I don't quite understand.  Command firefox should have referred to /usr/bin/firefox, and the latter should have referred to the latest version of firefox in /usr/lib64.

please run the following commands to help me understand this problem.

```
which firefox
ls -l /usr/bin/firefox
ls -l /usr/bin/firefox-3.5
dpkg -S /usr/bin/firefox
dpkg -S /usr/bin/firefox-3.5

```

---

### Post by watchpocket on 2009-12-25
Small correction --  I meant that I changed the Properties command to:

/usr/lib64/firefox-3.5.6/firefox-3.5

not:

/usr/lib64/firefox-3/5/6/firefox-3.5


Here are the results of your suggested commands
(my prompt shortened for readability):

```

[rj-desktop:~] --> [COLOR=Blue]which firefox[/COLOR]                                             
[COLOR=Red]**firefox not found**[/COLOR] 
[rj-desktop:~] --> 
[rj-desktop:~] -->[COLOR=Blue] ls -l /usr/bin/firefox [/COLOR]
[COLOR=Red]**0 lrwxrwxrwx 1 root root 20 2009-12-19 20:02 /usr/bin/firefox -> /opt/firefox/firefox**[/COLOR] 
[rj-desktop:~] --> 
[rj-desktop:~] --> [COLOR=Blue]ls -l /usr/bin/firefox-3.5[/COLOR] 
[COLOR=Red]**0 lrwxrwxrwx 1 root root 31 2009-12-25 03:55 /usr/bin/firefox-3.5 -> ../lib/firefox-3.5.6/firefox.sh***[/COLOR]
[rj-desktop:~] --> 
[rj-desktop:~] --> [COLOR=Blue]dpkg -S /usr/bin/firefox [/COLOR]
[COLOR=Red][B]local diversion from: /usr/bin/firefox 
local diversion to: /usr/bin/firefox.ubuntu 
firefox-3.5: /usr/bin/firefox[/B][/COLOR] 
[rj-desktop:~] --> 
[rj-desktop:~] --> [COLOR=Blue]dpkg -S /usr/bin/firefox-3.5[/COLOR] 
[COLOR=Red]**firefox-3.5: /usr/bin/firefox-3.5**[/COLOR]
[rj-desktop:~] -->  
[rj-desktop:~] -->

```

---

### Post by michael37 on 2009-12-25
Ah, something is holding your /usr/bin/firefox hostage (intentionally and functioning as desired: you installed that package therefore you must have wanted that at some point of time).  We just need to tell Ubuntu that you no longer want that diversion.

How about ```
dpkg -S /opt/firefox/firefox
```?

Also, how about ```
sudo apt-get remove --purge ubuntuzilla
```

---

### Post by watchpocket on 2009-12-25
```
[rj-desktop:~] -->[COLOR=Blue] dpkg -S /opt/firefox/firefox[/COLOR]
[COLOR=Red]dpkg: /opt/firefox/firefox not found.[/COLOR]
[rj-desktop:~] --> [COLOR=Blue]sudo apt-get remove --purge ubuntuzilla[/COLOR]
[COLOR=Red][sudo] password for rj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ubuntuzilla is not installed, so not removed
The following packages were automatically installed and are no longer required:
  lirc libftdi1 libnspr4-dev libiso9660-5 libnss3-dev libdvbpsi5 setserial libvlc2 libsdl-image1.2 mplayer-skins vlc-nox libmatroska0 lsdvd libnotify-bin
  vdr vlc liblua5.1-0 vlc-data libtar libvlccore2 libvcdinfo0 libebml0 vlc-plugin-pulse
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/COLOR]
[rj-desktop:~] -->

```

---

### Post by michael37 on 2009-12-26
How about 
```
dpkg -l | grep firefox
dpkg -l | grep ubuntuzilla

```

---

### Post by watchpocket on 2009-12-26
The holding hostage of /usr/bin/firefox was done by me by total accident.

```

[rj-desktop:~] -->[COLOR=Blue] dpkg -l | grep firefox
**[COLOR=Black]grep: firefox: No such file or directory[/COLOR]**
[/COLOR]  [rj-desktop:~] -->[COLOR=Blue] dpkg -l | grep ubuntuzilla[/COLOR]
[COLOR=Blue][B][COLOR=Black]grep: firefox: No such file or directory
[/COLOR][/B][/COLOR][rj-desktop:~] -->

```A few further investigations:

```
[rj-desktop:~] -->[COLOR=Blue] ls -l  /opt/firefox/firefox[/COLOR]
**ls: cannot access /opt/firefox/firefox: No such file or directory**
[rj-desktop:~] -->
[rj-desktop:~] -->[COLOR=Blue]  ls -l  /opt/firefox[/COLOR]
**ls: cannot access /opt/firefox/: No such file or directory**
[rj-desktop:~] -->
[rj-desktop:~] -->[COLOR=Blue] ls -l /opt/[/COLOR]
[B]total 4
4 drwxr-xr-x 3 root root 4096 2009-11-02 10:50 system76/[/B]
[rj-desktop:~] -->

```And the only "firefox"-es  that are in /usr/bin/ are three symlinks (the first of which links to a directory that doesn't exist):

```

[rj-desktop:~] -->[COLOR=Blue] ls -l /usr/bin[/COLOR]/
[...]
[B]   0 lrwxrwxrwx 1 root   root          20 2009-12-19 20:02 [COLOR=Sienna]firefox[/COLOR] -> /opt/firefox/firefox
   0 lrwxrwxrwx 1 root   root          31 2009-12-25 03:55 [COLOR=Sienna]firefox-3.5[/COLOR] -> [COLOR=Red]../lib/firefox-3.5.6/firefox.sh[/COLOR]*
   0 lrwxrwxrwx 1 root   root          11 2009-12-25 03:55 [COLOR=Sienna]firefox.ubuntu[/COLOR] -> [COLOR=Red]firefox-3.5[/COLOR]*[/B]
[...]
[rj-desktop:~] -->

```

---

### Post by michael37 on 2009-12-26
> **watchpocket said:**
> The holding hostage of /usr/bin/firefox was done by me by total accident.

We can fix that.

> **watchpocket said:**
> 
```

[/COLOR]  [rj-desktop:~] -->[COLOR=Blue] dpkg -l | grep ubuntuzilla[/COLOR]
[COLOR=Blue][B][COLOR=Black]grep: firefox: No such file or directory
[/COLOR][/B][/COLOR][rj-desktop:~] -->

```

Eh?  How is that output possible for this command?

Anyways, here is what I think will finally fix it.

```
sudo dpkg-divert --rename --remove /usr/bin/firefox

```
After that, make sure that ls -l /usr/bin/firefox* looks good
and hopefully command firefox will work.

---

### Post by watchpocket on 2009-12-26
A bit more:

 ([COLOR=Blue]commands: blue[/COLOR];  
**[COLOR=Sienna]symlinks: brown-bold[/COLOR]**; 
 **[COLOR=Red]executables: red-bold[/COLOR]**; 
all other** results of commands: black-bold**):

```

[rj-desktop:~] --> [COLOR=Blue]ls /usr/lib/[/COLOR]
. . . 
[B]firefox/
firefox-3.5.6/[/B]
. . .
[B]mozilla/
mozilla-firefox/[/B]
. . .
[rj-desktop:~] --> 
[rj-desktop:~] -->[COLOR=Blue] ls -l /usr/lib/firefox/[/COLOR]
[B]total 4
4 drwxr-xr-x 2 root root 4096 2009-12-22 00:24 plugins/[/B]
[rj-desktop:~] -->[COLOR=Blue] ls -l /usr/lib/firefox/plugins/
[B][COLOR=Black]total 0
0 lrwxrwxrwx 1 root root 31 2009-12-20 23:30[COLOR=Sienna] xineplugin.so[/COLOR] -> ../../xine-plugin/xineplugin.so
[/COLOR][/B][/COLOR][rj-desktop:~] -->[COLOR=Blue]
[COLOR=Black][rj-desktop:~] -->[/COLOR] ls -l /usr/lib/firefox-3.5.6/[/COLOR]
[B]total 164
 0 lrwxrwxrwx 1 root root     7 2009-12-25 03:55 [COLOR=Sienna]abrowser[/COLOR] ->[COLOR=Red] firefox[/COLOR]*
 0 lrwxrwxrwx 1 root root     7 2009-12-25 03:55 [COLOR=Sienna]abrowser-3.5[/COLOR] -> [COLOR=Red]firefox[/COLOR]*
 4 -rw-r--r-- 1 root root  2027 2009-12-15 19:35 application.ini
 4 -rw-r--r-- 1 root root  2552 2009-12-15 19:35 blocklist.xml
 4 -rw-r--r-- 1 root root    49 2009-12-15 19:35 browserconfig.properties
 4 drwxr-xr-x 3 root root  4096 2009-12-25 03:55 chrome/
 4 drwxr-xr-x 2 root root  4096 2009-12-25 03:55 components/
 4 drwxr-xr-x 3 root root  4096 2009-12-25 03:55 defaults/
 0 lrwxrwxrwx 1 root root    25 2009-12-25 03:55 [COLOR=Sienna]dictionaries[/COLOR] -> ../../share/myspell/dicts/
 4 drwxr-xr-x 2 root root  4096 2009-12-25 03:55 distribution/
 0 lrwxrwxrwx 1 root root    28 2009-12-25 03:55 [COLOR=Sienna]extensions[/COLOR] -> ../firefox-addons/extensions/
12 -rwxr-xr-x 1 root root 10560 2009-12-15 19:36[COLOR=Red] ffox-35-beta-profile-migration-dialog[/COLOR]*
92 -rwxr-xr-x 1 root root 89072 2009-12-15 19:36[COLOR=Red] firefo[/COLOR]x*
 0 lrwxrwxrwx 1 root root     7 2009-12-25 03:55[COLOR=Sienna] firefox-3.5[/COLOR] -> [COLOR=Red]firefox[/COLOR]*
 4 -rw-r--r-- 1 root root   460 2009-12-15 19:34 firefox-3.5-restart-required.update-notifier
 8 -rwxr-xr-x 1 root root  4277 2009-12-15 19:34[COLOR=Red] firefox.sh[/COLOR]*
 4 drwxr-xr-x 2 root root  4096 2009-12-25 03:55 icons/
 4 drwxr-xr-x 2 root root  4096 2009-12-25 03:55 modules/
 0 lrwxrwxrwx 1 root root    25 2009-12-25 03:55 [COLOR=Sienna]plugins[/COLOR] -> ../firefox-addons/plugins/
12 -rwxr-xr-x 1 root root 10450 2009-12-15 19:35 [COLOR=Red]run-mozilla.sh[/COLOR]*
 0 -rw-r--r-- 1 root root     0 2009-12-15 19:35 update.locale


[/B][rj-desktop:~] --> 
[rj-desktop:~] -->[COLOR=Blue] ls -l /usr/lib/mozilla[/COLOR]
[B]total 8
4 drwxr-xr-x 3 root root 4096 2009-12-25 03:55 extensions/
4 drwxr-xr-x 2 root root 4096 2009-12-25 05:54 plugins/[/B]
[rj-desktop:~] --> 
[rj-desktop:~] --> [COLOR=Blue]ls -l /usr/lib/mozilla/extensions
[B][COLOR=Black]total 4
4 drwxr-xr-x 2 root root 4096 2009-12-25 03:55 {ec8030f7-c20a-464f-9b0e-13a3a9e97384}/

[/COLOR][/B][/COLOR][rj-desktop:~] --> 
[rj-desktop:~] --> [COLOR=Blue][COLOR=Blue]ls -l /usr/lib/mozilla/extensions/\{ec8030f7-c20a-464f-9b0e-13a3a9e97384\}/[/COLOR][B][COLOR=Black]
total 0
0 lrwxrwxrwx 1 root root 24 2009-12-25 03:55 [COLOR=Sienna]ubufox@ubuntu.com[/COLOR] -> ../../../../share/ubufox/
[/COLOR][/B][/COLOR][rj-desktop:~] --> 
[rj-desktop:~] -->[COLOR=Blue] ls -l  /usr/share/ubufox[/COLOR]
[B]total 28
4 drwxr-xr-x 2 root root 4096 2009-12-25 03:55 chrome/
4 -rw-r--r-- 1 root root 2180 2009-10-12 10:15 chrome.manifest
4 drwxr-xr-x 2 root root 4096 2009-12-25 03:55 components/
4 drwxr-xr-x 3 root root 4096 2009-12-25 03:55 defaults/
4 -rw-r--r-- 1 root root 1220 2009-10-12 10:15 install.rdf
4 drwxr-xr-x 2 root root 4096 2009-10-12 10:15 plugins/
4 drwxr-xr-x 2 root root 4096 2009-12-25 03:55 searchplugins/[/B]
[rj-desktop:~] --> 
[rj-desktop:~] -->[COLOR=Blue] ls -l /usr/lib/mozilla/plugins [/COLOR]
[B]total 9372
9364 -rwxr-xr-x 1 rj   rj   9570952 2009-10-28 00:04[COLOR=Red] libflashplayer.so[/COLOR]*
   8 -rw-r--r-- 1 root root    6120 2009-11-03 05:58 librhythmbox-itms-detection-plugin.so
   0 lrwxrwxrwx 1 root root      31 2009-12-20 23:30 [COLOR=Sienna]xineplugin.so[/COLOR] -> ../../xine-plugin/xineplugin.so[/B]
[rj-desktop:~] --> 
[rj-desktop:~] -->[COLOR=Blue] ls -l /usr/lib/mozilla[/COLOR] 
[B]total 8
4 drwxr-xr-x 3 root root 4096 2009-12-25 03:55 extensions/
4 drwxr-xr-x 2 root root 4096 2009-12-25 05:54 plugins/[/B]
[rj-desktop:~] --> 
 [rj-desktop:~] -->[COLOR=Blue] ls -l /usr/lib/mozilla-firefox [/COLOR]
[B]total 4
4 drwxr-xr-x 2 root root 4096 2009-12-23 04:20 plugins/
[/B][rj-desktop:~] --> 
  [rj-desktop:~] --> [COLOR=Blue] ls -l /usr/lib/mozilla-firefox/plugins/
[B][COLOR=Black]total 0
0 lrwxrwxrwx 1 root root 31 2009-12-20 23:30 [COLOR=Sienna]xineplugin.so[/COLOR] -> ../../xine-plugin/xineplugin.so
[/COLOR][/B][/COLOR][rj-desktop:~] --> 
[rj-desktop:~] -->
[rj-desktop:~] --> 
[rj-desktop:~] -->

```[COLOR=Blue]
[/COLOR]

---

### Post by watchpocket on 2009-12-26
> **michael37 said:**
> 
Eh?  How is that output possible for this command?


I copied the wrong line.  That should have read (and did, in reality, read):
```
[rj-desktop:~] -->[COLOR=Blue] dpkg -l | grep ubuntuzilla[/COLOR] 
**grep: ubuntuzilla: No such file or directory**

```Here is the result of the rename-remove command:
```

[rj-desktop:~] -->[COLOR=Blue] sudo dpkg-divert --rename --remove /usr/bin/firefox                            pts/4  Saturday  2009/12/26  02:33:23 
[B][COLOR=Black][sudo] password for rj: 
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg-divert: rename involves overwriting `/usr/bin/firefox' with
  different file `/usr/bin/firefox.ubuntu', not allowed
[/COLOR][/B][/COLOR]
```[COLOR=Blue][B][COLOR=Black]

[/COLOR][/B][COLOR=Black]Hm, "not allowed" -- that doesn't look good:
[/COLOR][/COLOR]```
[rj-desktop:~] --> [COLOR=Blue]ls -l /usr/bin/firefox[/COLOR] 
**0 lrwxrwxrwx 1 root root 20 2009-12-19 20:02 [COLOR=Sienna]/usr/bin/firefox[/COLOR] -> /opt/firefox/firefox**
[rj-desktop:~] -->
[rj-desktop:~] -->[COLOR=Blue] ls -l /opt/[/COLOR] 
[B]total 4
4 drwxr-xr-x 3 root root 4096 2009-11-02 10:50 system76/[/B]

```I'm going to think twice before I download anything again from a nonrepository source.  Also need to get up to speed asap w/the Ubuntu documentation.  About my only good news is I at least got 64-bit Flash working thanks to your script.

---

### Post by michael37 on 2009-12-26
> **watchpocket said:**
> 
Here is the result of the rename-remove command:
```

[rj-desktop:~] -->[COLOR=Blue] sudo dpkg-divert --rename --remove /usr/bin/firefox                            pts/4  Saturday  2009/12/26  02:33:23 
[B][COLOR=Black][sudo] password for rj: 
Removing `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
dpkg-divert: rename involves overwriting `/usr/bin/firefox' with
  different file `/usr/bin/firefox.ubuntu', not allowed
[/COLOR][/B][/COLOR]
```[COLOR=Blue][B][COLOR=Black]

[/COLOR][/B][COLOR=Black]Hm, "not allowed" -- that doesn't look good:
[/COLOR][/COLOR]```
[rj-desktop:~] --> [COLOR=Blue]ls -l /usr/bin/firefox[/COLOR] 
**0 lrwxrwxrwx 1 root root 20 2009-12-19 20:02 [COLOR=Sienna]/usr/bin/firefox[/COLOR] -> /opt/firefox/firefox**


So, this diversion is the last remaining problem.  Everything else looks good.  If you really care, you can work around the upgrade problem now by running command firefox.ubuntu right now.
Let's try to figure out how to fix the diversion.   What does this command say?
[CODE]grep firefox /var/lib/dpkg/diversions -C 2

```

---

### Post by watchpocket on 2009-12-27
> **michael37 said:**
> So, this diversion is the last remaining problem. 

I have right now at least two bogus symlinks / diversions:
```

**[COLOR=Sienna]/usr/bin/firefox [/COLOR]-> /opt/firefox/firefox**

and

**[COLOR=Sienna]/usr/lib/firefox-3.5.6/firefox-3.5[/COLOR] -> /usr/bin/firefox **
(created somehow yesterday by mistake)

```What I don't get is why, when I run these 2 dpkg-divert commands:
```

[COLOR=Blue]sudo dpkg-divert --divert /usr/lib/firefox-3.5.6/firefox /usr/lib/firefox-3.5.6/firefox-3.5[/COLOR]

and

[COLOR=Blue]sudo dpkg-divert --divert /usr/lib/firefox-3.5.6/firefox-3.5 /usr/bin/firefox[/COLOR]

(*after* having done a  [COLOR=Blue]sudo dpkg-divert --remove . . .[/COLOR]  on both of them)
```the dpkgd-divert program tells me that it's "added" the diversions,  but, immediately after that, when I "list" them, they still point to the old, non-existent files:

```
[COLOR=Blue][COLOR=Black][rj-desktop:~] -->[/COLOR] ls -l /usr/bin/firefox
[B][COLOR=Black]0 lrwxrwxrwx 1 root root 20 2009-12-26 04:52 [COLOR=Sienna]/usr/bin/firefox[/COLOR] -> /opt/firefox/firefox
[/COLOR][/B]
[/COLOR][COLOR=Blue] [COLOR=Black][rj-desktop:~] -->[/COLOR] ls -l /usr/lib/firefox-3.5.6/firefox-3.5
[B][COLOR=Black]0 lrwxrwxrwx 1 root root 16 2009-12-26 04:30 /[COLOR=Sienna]usr/lib/firefox-3.5.6/firefox-3.5[/COLOR] -> /usr/bin/firefox
[/COLOR][/B][/COLOR]
```Apparently, changing or creating a diversion is not the same as changing or creating the symlink itself. 

 How do I get rid of any mention or reference to **/opt/firefox/firefox**?  It doesn't exist. 

And** /opt/firefox** doesn't exist.

 ( **/opt/** does exit, of course. )

At the moment, in fact,  the distinction between symlink and diversion is somewhat lost on me. Is the whole concept of "diversion" strictly an Ubuntu thing?  It's new to me (but that could be my fault).

I ***think*** that what I want is** this**:

```
[COLOR=Sienna]/usr/bin/firefox[/COLOR] -> /usr/lib/firefox-3.5.6/firefox-3.5

instead of:

[COLOR=Sienna]/usr/bin/firefox[/COLOR] -> /opt/firefox/firefox

and** this**:

[COLOR=Sienna]/usr/lib/firefox-3.5.6/firefox-3.5[/COLOR] -> /usr/lib/firefox-3.5.6/firefox

instead of:

[COLOR=Sienna]/usr/lib/firefox-3.5.6/firefox-3.5[/COLOR] -> /usr/bin/firefox
```for both symlink and diversion.  I just don't have the correct command-combo yet to make it happen.

> If you really care, you can work around the upgrade problem now by running command firefox.ubuntu right now.Because "**[COLOR=Sienna]firefox.ubuntu[/COLOR]**" in /usr/bin is a symlink that points to "**[COLOR=Sienna]firefox-3.5[/COLOR]**" in /usr/bin, and /usr/bin/[COLOR=Sienna]**firefox-3.5**[/COLOR] points to /usr/**lib**/firefox-3.5.6/firefox.sh

> Let's try to figure out how to fix the diversion.   What does this command say?
```
grep firefox /var/lib/dpkg/diversions -C 2

```Okay, the command itself is grepping or searching in the file /var/lib/dpkg/diversions for any lines containing the string "firefox", with 2 lines of context (presumably one above, & one  below, any line containing "firefox").

The *output* of the command first says:
**grep: firefox: No such file or directory**

and then prints out the file.  And that's another somewhat confusing thing, because the diversions file has (once I ran the 2 dpkg-divert commands) this line, for example,  that ***does*** contain a file "firefox":

```
/var/lib/dpkg/diversions:/usr/lib/firefox-3.5.6/firefox
```Here is the entire diversions file (the last 6 lines being of interest):

```
[rj-desktop:~] --> grep firefox /var/lib/dpkg/diversions -C 2                                    pts/4  Sunday  2009/12/27  01:05:50 
grep: firefox: No such file or directory
/var/lib/dpkg/diversions:/bin/sh
/var/lib/dpkg/diversions:/bin/sh.distrib
/var/lib/dpkg/diversions-dash
/var/lib/dpkg/diversions-/usr/share/man/man1/sh.1.gz
/var/lib/dpkg/diversions:/usr/share/man/man1/sh.distrib.1.gz
/var/lib/dpkg/diversions-dash
/var/lib/dpkg/diversions:/usr/share/dict/words
/var/lib/dpkg/diversions:/usr/share/dict/words.pre-dictionaries-common
/var/lib/dpkg/diversions:dictionaries-common
/var/lib/dpkg/diversions:/usr/share/dbus-1/services/org.freedesktop.Notifications.service
/var/lib/dpkg/diversions:/usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd
/var/lib/dpkg/diversions:notify-osd
/var/lib/dpkg/diversions:/usr/share/applications/ubiquity-gtkui.desktop
/var/lib/dpkg/diversions:/usr/share/ubiquity/ubiquity-gtkui.desktop.diverted
/var/lib/dpkg/diversions:oem-config-gtk
/var/lib/dpkg/diversions:/usr/lib/libGL.so.1
/var/lib/dpkg/diversions:/usr/lib/nvidia/libGL.so.1.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib/libGL.so.1.2
/var/lib/dpkg/diversions:/usr/lib/nvidia/libGL.so.1.2.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib/xorg/modules/extensions/libglx.so
/var/lib/dpkg/diversions:/usr/lib/nvidia/libglx.so.xserver-xorg-core
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib32/libGL.so
/var/lib/dpkg/diversions:/usr/lib32/nvidia/libGL.so.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib32/libGL.so.1
/var/lib/dpkg/diversions:/usr/lib32/nvidia/libGL.so.1.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib32/libGL.so.1.2
/var/lib/dpkg/diversions:/usr/lib32/nvidia/libGL.so.1.2.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib/xorg/modules/extensions/libGLcore.so
/var/lib/dpkg/diversions:/usr/lib/nvidia/libGLcore.so.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/share/vim/vim72/doc/help.txt
/var/lib/dpkg/diversions:/usr/share/vim/vim72/doc/help.txt.vim-tiny
/var/lib/dpkg/diversions:vim-runtime
/var/lib/dpkg/diversions:/usr/share/vim/vim72/doc/tags
/var/lib/dpkg/diversions:/usr/share/vim/vim72/doc/tags.vim-tiny
/var/lib/dpkg/diversions:vim-runtime
/var/lib/dpkg/diversions:/usr/share/vim/syntax/zsh.vim
/var/lib/dpkg/diversions:/usr/share/vim/syntax/zsh.vim.original
/var/lib/dpkg/diversions-zsh-lovers
/var/lib/dpkg/diversions:/usr/bin/mozilla-firefox
/var/lib/dpkg/diversions:/usr/bin/mozilla-firefox.ubuntu
/var/lib/dpkg/diversions-:
/var/lib/dpkg/diversions:/usr/lib/firefox-3.5.6/firefox-3.5
/var/lib/dpkg/diversions:/usr/lib/firefox-3.5.6/firefox
/var/lib/dpkg/diversions-:
```

---

### Post by michael37 on 2009-12-27
Diversion is the automated management of the symlinks, making sure that packages don't interfere with each other.

Let's just try to remove them

```
sudo dpkg-divert --remove /usr/lib/firefox-3.5.6/firefox-3.5 
sudo dpkg-divert --remove /usr/bin/firefox

```
If that doesn't work, try

```
sudo dpkg-divert --local --remove /usr/lib/firefox-3.5.6/firefox-3.5 
sudo dpkg-divert --local --remove /usr/bin/firefox

```

---

### Post by watchpocket on 2009-12-27
> 
                                                                      Originally Posted by **michael37**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8565082#post8565082")                 
                 * . . . Let's just try to remove them . . .*I think I got things straightened out.  (For the most part, at least.)  I now have:

firefox %u

as the Firefox "Launcher Properties" command, and with that now in place, the browser launches fine.

 I created these two symlinks:
```
[COLOR=Sienna]/usr/bin/firefox[/COLOR] -> [COLOR=Red]/usr/lib/firefox-3.5.6/firefox-3.5[COLOR=Black]*[/COLOR][/COLOR]
and 
[COLOR=Sienna]/usr/lib/firefox-3.5.6/firefox-3.5[/COLOR] ->[COLOR=Red] firefox[COLOR=Black]*[/COLOR][/COLOR]
```Then I made this diversion:
```
[COLOR=Blue]sudo dpkg-divert --divert /usr/lib/firefox-3.5.6/firefox-3.5 /usr/bin/firefox[/COLOR]
```And I have these symlinks in /usr/bin/ :

```
[COLOR=Sienna]firefox[/COLOR] ->[COLOR=Red] /usr/lib/firefox-3.5.6/firefox-3.5[COLOR=Black]*[/COLOR][/COLOR]
[COLOR=Sienna]firefox-3.5[/COLOR] -> .[COLOR=Red]./lib/firefox-3.5.6/firefox.sh[/COLOR]*
[COLOR=Sienna]firefox.ubuntu[/COLOR] -> [COLOR=Red]firefox-3.5[COLOR=Black]*[/COLOR][/COLOR]
```The diversions file now looks like this:
```
grep firefox /var/lib/dpkg/diversions -C 2                                     
**grep: firefox: No such file or directory**
/var/lib/dpkg/diversions:/bin/sh
/var/lib/dpkg/diversions:/bin/sh.distrib
/var/lib/dpkg/diversions-dash
/var/lib/dpkg/diversions-/usr/share/man/man1/sh.1.gz
/var/lib/dpkg/diversions:/usr/share/man/man1/sh.distrib.1.gz
/var/lib/dpkg/diversions-dash
/var/lib/dpkg/diversions:/usr/share/dict/words
/var/lib/dpkg/diversions:/usr/share/dict/words.pre-dictionaries-common
/var/lib/dpkg/diversions:dictionaries-common
/var/lib/dpkg/diversions:/usr/share/dbus-1/services/org.freedesktop.Notifications.service
/var/lib/dpkg/diversions:/usr/share/dbus-1/services/org.freedesktop.Notifications.service.notify-osd
/var/lib/dpkg/diversions:notify-osd
/var/lib/dpkg/diversions:/usr/share/applications/ubiquity-gtkui.desktop
/var/lib/dpkg/diversions:/usr/share/ubiquity/ubiquity-gtkui.desktop.diverted
/var/lib/dpkg/diversions:oem-config-gtk
/var/lib/dpkg/diversions:/usr/lib/libGL.so.1
/var/lib/dpkg/diversions:/usr/lib/nvidia/libGL.so.1.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib/libGL.so.1.2
/var/lib/dpkg/diversions:/usr/lib/nvidia/libGL.so.1.2.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib/xorg/modules/extensions/libglx.so
/var/lib/dpkg/diversions:/usr/lib/nvidia/libglx.so.xserver-xorg-core
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib32/libGL.so
/var/lib/dpkg/diversions:/usr/lib32/nvidia/libGL.so.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib32/libGL.so.1
/var/lib/dpkg/diversions:/usr/lib32/nvidia/libGL.so.1.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib32/libGL.so.1.2
/var/lib/dpkg/diversions:/usr/lib32/nvidia/libGL.so.1.2.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/lib/xorg/modules/extensions/libGLcore.so
/var/lib/dpkg/diversions:/usr/lib/nvidia/libGLcore.so.xlibmesa
/var/lib/dpkg/diversions:nvidia-glx-185
/var/lib/dpkg/diversions:/usr/share/vim/vim72/doc/help.txt
/var/lib/dpkg/diversions:/usr/share/vim/vim72/doc/help.txt.vim-tiny
/var/lib/dpkg/diversions:vim-runtime
/var/lib/dpkg/diversions:/usr/share/vim/vim72/doc/tags
/var/lib/dpkg/diversions:/usr/share/vim/vim72/doc/tags.vim-tiny
/var/lib/dpkg/diversions:vim-runtime
/var/lib/dpkg/diversions:/usr/share/vim/syntax/zsh.vim
/var/lib/dpkg/diversions:/usr/share/vim/syntax/zsh.vim.original
/var/lib/dpkg/diversions-zsh-lovers
/var/lib/dpkg/diversions:/usr/bin/firefox
/var/lib/dpkg/diversions:/usr/lib/firefox-3.5.6/firefox-3.5
/var/lib/dpkg/diversions-:
```And, though I still don't quite get why it's saying:** firefox: No such file or directory **at the top, my thinking is that the current setup shouldn't interfere with upgrades, and I'm wondering if you see anything that might indicate otherwise, and if it looks right to you generally.

---

### Post by michael37 on 2009-12-28
Only one way to tell.  Wait till next upgrade and see if it upgrades OK.  I am not convinced your issue is resolved correctly.

---

### Post by nanotube on 2009-12-28
ubuntuzilla diverts /usr/bin/firefox to /usr/bin/firefox.ubuntu as part of the firefox install process. all you needed to do to go back to the repos version was to run "ubuntuzilla.py -a remove -p firefox", which would have automatically removed the mozilla build of 32bit firefox, and undiverted the /usr/bin link. 

well, too late now, but... for future reference, there it is for you.

---

