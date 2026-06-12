---
title: "how to Install Hebrew interface firefox?"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by GoldenApe on 2010-09-18
hi all.
I'm working with Ubuntu for several months now, mainly for programming (so I'm pretty newbie), and I really liked it, so I deiced to install it on my old parents PC, so everytime I come home to visit them I won't have to install the entire OS all over again (somehow they manage to kill windows in few month :P).

so for my problem I download the last Hebrew Firefox from Mozilla Israel site -->   firefox-3.6.10.tar.bz2
how do I install it ?

---

### Post by Rubi1200 on 2010-09-18
Hi and welcome to the forums :)

If you extract the tar file you should find a readme text or an installation.sh script which will guide you through the process.

Hope this helps.

---

### Post by GoldenApe on 2010-09-18
those are the files I have inside the folder
```

application.ini             firefox-bin     libplc4.so              platform.ini
blocklist.xml               greprefs        libplds4.so             plugin-container
browserconfig.properties    icons           libsmime3.so            plugins
chrome                      libfreebl3.chk  libsoftokn3.chk         README.txt
components                  libfreebl3.so   libsoftokn3.so          removed-files
crashreporter               libmozjs.so     libsqlite3.so           res
crashreporter.ini           libnspr4.so     libssl3.so              run-mozilla.sh
crashreporter-override.ini  libnss3.so      libxpcom.so             searchplugins
defaults                    libnssckbi.so   libxul.so               Throbber-small.gif
dependentlibs.list          libnssdbm3.chk  LICENSE                 update.locale
extensions                  libnssdbm3.so   modules                 updater
firefox                     libnssutil3.so  mozilla-xremote-client  updater.ini

```

the readme file only direct me to firefox site :S

---

### Post by Rubi1200 on 2010-09-18
From the Mozilla site:

```
 Open a Terminal and go to your home directory: cd ~ 
  
Extract the contents of the downloaded file:tar xjf firefox-*.tar.bz2 
  
Close Firefox if it's open. 
  
To start Firefox, run the firefox script in the firefox folder.~/firefox/firefox

```
Here is the link if you need to check anything:
[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

---

### Post by GoldenApe on 2010-09-18
it's works thanks, but I get this message:
```
<unknown>:3945): Gdk-WARNING **: XID collision, trouble ahead
```and how do I make this as my dfaults firefox?

EDIT: SOLVED
right click on firefox icon on the top --> Properties --> change Command to : /home/user-name/firefox/firefox %u
also go to System --> Preferences --> Preferred Applications --> change Web Browser to Custom and finally change Command to : /home/user-name/firefox/firefox %u

*. still don't know what the warning says, but it's works pretty fine, so I think I take it for now :P

Thanks all for helping (how do I change header to solved ? :P)

---

### Post by Rubi1200 on 2010-09-19
I am glad you got it working :)

Mark the thread as Solved using the Thread Tools near the top of the page.

---

