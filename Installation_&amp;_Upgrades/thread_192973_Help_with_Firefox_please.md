---
title: "Help with Firefox please?"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2006-06-09
I have recently upgraded to Dapper and now cannot launch Firefox.  When I try to open FF now I get a dialogue saying 

"**There was an error launching the application. Details: Failed to execute child process "firefox" (No such file or directory)" I notice in my home directory that I have one folder called "firefox" and another called "Firefox". **

The former has a red padlock icon and contains all the browser files while the latter only has a few extension xpi files in it. I would really appreciate some help to get FF working again. Cheers all in advance.

---

### Post by FredB on 2006-06-09
[QUOTE=Julian David Pitt]I have recently upgraded to Dapper and now cannot launch Firefox.  When I try to open FF now I get a dialogue saying 

"**There was an error launching the application. Details: Failed to execute child process "firefox" (No such file or directory)" I notice in my home directory that I have one folder called "firefox" and another called "Firefox". **

The former has a red padlock icon and contains all the browser files while the latter only has a few extension xpi files in it. I would really appreciate some help to get FF working again. Cheers all in advance.[/QUOTE]

Ouch. Well... Did you try to launch firefox from the menu bar ? Or from another icon ?

Can you do a listing of the second directory ?

---

### Post by aysiu on 2006-06-09
I'm confused as to why you have *any* folders called *firefox* (or *Firefox*) in your Home directory.

You should have a hidden folder there called .mozilla, where your Firefox settings live, but your Firefox folder should be in /usr/lib/firefox (for Ubuntu) or /opt/firefox (for Mozilla).

I would use [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) to install Firefox properly.

---

### Post by Julian David Pitt on 2006-06-09
[QUOTE=FredB]Ouch. Well... Did you try to launch firefox from the menu bar ? Or from another icon ?

Can you do a listing of the second directory ?[/QUOTE]
I tried to launch it from "Applications-Internet-Firefox" and also from a desktop icon, same error message both ways Fred

---

### Post by Julian David Pitt on 2006-06-09
[QUOTE=FredB]Ouch. Well... Did you try to launch firefox from the menu bar ? Or from another icon ?

Can you do a listing of the second directory ?[/QUOTE]

Just how do I do a directory listing please, if you mean a screenshot how do I insert the graphic and sorry for all the questions.

---

### Post by aysiu on 2006-06-09
[QUOTE=Julian David Pitt]Just how do I do a directory listing please, if you mean a screenshot how do I insert the graphic and sorry for all the questions.[/QUOTE] In the terminal, type ```
cd
ls
cd firefox
ls
cd ..
cd Firefox
ls
```

---

### Post by Julian David Pitt on 2006-06-09
[QUOTE=aysiu]I'm confused as to why you have *any* folders called *firefox* (or *Firefox*) in your Home directory.

You should have a hidden folder there called .mozilla, where your Firefox settings live, but your Firefox folder should be in /usr/lib/firefox (for Ubuntu) or /opt/firefox (for Mozilla).

I would use [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5) to install Firefox properly.[/QUOTE]
Indeed I do have the folder you mention in /usr/lib. Just tried the script and all worked ok until 

"Linking launcher to new Firefox

Leaving `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
ln: creating symbolic link `/usr/bin/firefox' to `/opt/firefox/firefox': File exists
Previous command did not complete successfully. Exiting.
root@ubuntu:/home/julian/Desktop #"

Your advice is appreciated my friend

---

### Post by aysiu on 2006-06-09
Oh, so you already have Firefox installed in your /opt directory!

Can you try typing these commands? ```
cd /opt/firefox
./firefox
```

---

### Post by Julian David Pitt on 2006-06-09
[QUOTE=aysiu]In the terminal, type ```
cd
ls
cd firefox
ls
cd ..
cd Firefox
ls
```[/QUOTE]

root@ubuntu:/home/julian/firefox # ls
browserconfig.properties  libnss3.so          libxpistub.so
chrome                    libnssckbi.so       mozilla-xremote-client
components                libplc4.so          plugins
defaults                  libplds4.so         readme.txt
extensions                libsmime3.so        removed-files
firefox                   libsoftokn3.chk     res
firefox-bin               libsoftokn3.so      run-mozilla.sh
greprefs                  libssl3.so          searchplugins
icons                     libxpcom_compat.so  updater
libmozjs.so               libxpcom_core.so    updater.ini
libnspr4.so               libxpcom.so         xpicleanup
root@ubuntu:/home/julian/firefox #

root@ubuntu:/home/julian/Firefox # ls
bios_6wmm7_f6..txt         scrapbook-0.17.0-fx.xpi
flashbios_dos.pdf          smoothwheel-0.44.7.20050605-fx+mz+ns+nv+tb.xpi
menu_editor-1.2-fx+tb.xpi  tabbrowser_preferences-1.2.8.5-fx.xpi

Hope this helps and thanks

---

### Post by aysiu on 2006-06-09
That's weird. I don't know why you have a firefox and Firefox in your Home directory *and* a firefox in /opt.

That's a lot of Firefoxes!

---

### Post by FredB on 2006-06-09
Just a simple question. Why are working under root account ?

Using a simple user account is **THE WAY** to work under any unix / linux OS ;)

---

### Post by Julian David Pitt on 2006-06-09
[QUOTE=aysiu]Oh, so you already have Firefox installed in your /opt directory!

Can you try typing these commands? ```
cd /opt/firefox
./firefox
```[/QUOTE]
Hi Aysiu
That worked and FFnow orks but how do I get back all my bookmarks extensions and all the scrapbook pages I had saved previously please4, thanks again.

---

### Post by aysiu on 2006-06-09
It seems the Firefox situation your computer is in is really complicated, for some reason.

So your .mozilla folder is *supposed* to have all your extensions and... scrapbook pages (what are those?) and bookmarks.

I don't know where else they could be, unfortunately.

---

### Post by Julian David Pitt on 2006-06-19
[QUOTE=aysiu]That's weird. I don't know why you have a firefox and Firefox in your Home directory *and* a firefox in /opt.

That's a lot of Firefoxes![/QUOTE]
Hi Aysiu
After having run the script you posted and followed your advice I now seem to have FF working properly and best of all I can access all my bookmarks, so many thanks for your help mate.
Cheers
Julian

---

