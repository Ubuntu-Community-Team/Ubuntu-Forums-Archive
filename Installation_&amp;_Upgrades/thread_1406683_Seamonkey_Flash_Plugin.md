---
title: "Seamonkey Flash Plugin"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by TomyVk on 2010-02-14
Well, i think that some people might want to play the facebook poker, but its kinda not working well.

I was browsing some posts and guides and got it to work on seamonkey.

I'll post a small guide here to get it all working.

First of all be sure that you don't have seamonkey installed.

1. Download ubuntuzilla from [http://sourceforge.net/projects/ubuntuzilla/files/ubuntuzilla](http://sourceforge.net/projects/ubuntuzilla/files/ubuntuzilla)

Install the .deb package for your system

2. Install Seamonkey

sudo [COLOR=blue]ubuntuzilla.py -a install -p seamonkey[/COLOR]

3. Or just upgrade your firefox flash player (you need to have flash installed from the software manager)

You have to run it under sudo cause it wont have the permissions to install.

Follow trough the process (might take some time)
When it asks to link the firefox plugins select "no"

After the installation is finished just copy the file to:

Download [http://filebeam.com/0adecd130a0379e32503db8d28e498db](http://filebeam.com/0adecd130a0379e32503db8d28e498db)

- extract it to desktop or wherever you want.
- copy it in to those folders

/opt/seamonkey/plugins
/usr/lib/firefox/plugins
/usr/lib/firefox-3.5.7/plugins
/usr/lib/flashplugin-installer

(i did it like that cause i didn't really know where exactly to put in the file, but its working)

After you are done with that just start seamonkey. It should work without any problems.

I'm not good in writing guides, but i hope everyone understands how to do it.

It should work for the normal ubuntu version too but i'm using the 64 bit one so i've posted it here.

I've tried it in opera but it was making some problems.
[INDENT][COLOR=blue]





[/COLOR][LEFT]
[/LEFT]
[/INDENT]

---

### Post by panosdotk on 2010-03-31
This works with Chrome too. Thanks

---

### Post by Blue DaNoob on 2010-04-05
I have Seamonkey 2.0.4 Installed in Karmic 68AMD. I installed the flash 10 player 64 bit alpha version. I put libflashplayer.so file into every plug in folder I can find. It works in Firefox, but not Seamonkey. Seamonkey prompts for a missing plug-in download, but that doesn't work. I moved my seamonkey profile over from a Mac, everything works great but flash plugin. Any advice? thanks!

---

### Post by Blue DaNoob on 2010-04-06
Installing the new [Flash Release Candidate 10.1]("http://labs.adobe.com/downloads/flashplayer10.html") fixed my problem with Seamonkey 2.0. Unpacked and copied the .so file to .mozilla/plugins. Restarted Seamonkey and I am now very happy.

---

