---
title: "Installing Firefox 1.5"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by user1397 on 2006-03-11
Hi 
I just installed breezy as my only os.
I went to the ubuntu wiki and looked up the article "firefoxnewversion"
I was able to install the "libstdc++5" package, but then I tried extracting the tar download of firefox 1.5 to /opt but it says exactly this:
"tar: firefox-1.5.0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors"

Please help! (by the way i'm pretty new to ubuntu so I probably won't understand some things at first-please bear with me)

---

### Post by aysiu on 2006-03-11
You can untar it graphically--just double-click on the .tar.gz and then click [b]Extract[b].

---

### Post by user1397 on 2006-03-11
Thanks for the fast reply,
I did that and told it to extract to the "opt" folder but when i click extract it says 
"Extraction not performed
You don't have the right permissions to extract archives in the folder "/opt"

???

---

### Post by aysiu on 2006-03-11
/opt is owned by root.

Just extract it to your desktop. You can copy it to /opt using the commands in the Wiki.

Otherwise, if you want to copy to /opt graphically, press Alt-F2 and type *gksudo nautilus* to browse as root (or *kdesu konqueror* if you're using Kubuntu).

---

### Post by user1397 on 2006-03-11
I tried the wiki way but still got the same message as before!\
     
     I also tried doing the root method.  It took me to the file browser, but then what do I do?

Thanks again

---

### Post by aysiu on 2006-03-11
The idea is that you don't have permission to copy to /opt because /opt is owned by root.

So instead of opening a regular file browser window (*nautilus*), you're opening a file browser window with root privileges (*gksudo nautilus*), so now you can drag and drop the extracted Firefox folder to the /opt folder and have permissions to do so.

The basic gist of the Wiki commands is this:

1. Unzip the Firefox .tar.gz
2. Copy it to /opt
3. Symlink (or shortcut or alias) /opt/firefox/plugins to /usr/lib/mozilla-firefox/plugins
4. Symlink /opt/firefox/firefox to /usr/bin/firefox

All this can be done graphically, but you have to know what you're doing. With the Wiki, you can copy and paste instructions. Frankly, I'm surprised it didn't work. Maybe the name of the .tar.gz file has changed since the Wiki was last updated?

To Symlink in Nautilus, middle-click-drag the folder to its linking destination and then select "link here."

**Edit**: I checked on the Mozilla website, and the name of the file is the same as the Wiki's. Maybe you should try copying and pasting the Wiki commands instead of re-typing them...? I often mess up when typing.

---

### Post by user1397 on 2006-03-11
Ah I see 
thanks and ill get back to you if it turns out to be a success

---

### Post by user1397 on 2006-03-11
Thank you so much!
Firefox 1.5 is up and running! :D

---

### Post by aysiu on 2006-03-11
I'll explain a bit more...

**1. Unzip the Firefox .tar.gz** The original file from Mozilla is a zipped file. It can't be used until it's unzipped.

**2. Copy it to /opt** This is really just to make room from your desktop. You can put it anywhere. I put mine in /usr/local/bin

**3. Symlink (or shortcut or alias) /opt/firefox/plugins to /usr/lib/mozilla-firefox/plugins** All the plugins (Flash or whatever) you have for Firefox get installed by Synaptic to /usr/lib/mozilla-firefox/plugins, not to /opt/firefox/plugins, so rather than /opt/firefox/plugins being a real folder, you want it to just be a pointer folder that points to /usr/lib/mozilla-firefox/plugins.

**4. Symlink /opt/firefox/firefox to /usr/bin/firefox** The command for launching Firefox (*firefox*) looks for /usr/bin/firefox (which right now is probably Ubuntu's own 1.0.7, not Mozilla's 1.5), so you want to make sure that /usr/bin/firefox points to the Firefox you downloaded instead.

---

### Post by aysiu on 2006-03-11
[QUOTE=erik1397]Thank you so much!
Firefox 1.5 is up and running! :D[/QUOTE] Awesome!

---

