---
title: "Flash Player firefox plugin Installation failed"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-10-26
I just follow the instruction on [http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox")

But I got this error:

```
ubuntu@mypc:~$ sudo apt-get install flashplugin-nonfree
Password:
Reading package lists... Done
Building dependency tree... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@mypc::~$ sudo update-flashplugin
Downloading...  done.
installation failed
ubuntu@mypc::~$

```

Hope you can help.

---

### Post by gerowen on 2006-10-26
[Go here and download the Linux "installer",](http://labs.adobe.com/downloads/flashplayer9.html) extract it and put the .so file in your /usr/lib/firefox/plugins folder, then restart firefox.  It's version 9 and works fine for me.  Make sure you get the "installer", it's the browser plugin file actually and doesn't require any installation.

---

### Post by Cynical on 2006-10-26
Download the flash library from the link below and extract it to your desktop.

Then in a terminal type

```
sudo cp /home/username/Desktop/libflashplayer.so /usr/lib/firefox/plugins
```

Or substitute for your firefox plugins directory if its installed somewhere else.

[http://www.mediafire.com/?6v8opnyngb4](http://www.mediafire.com/?6v8opnyngb4)


(This plugin is for flash 9 btw)

---

### Post by textguru on 2006-10-26
Thanks guys. Btw, I already have the file so I dont need to download. I just copy it on the .usr/lib/firefox/plugins

---

### Post by Circus-Killer on 2006-10-26
in future, for additional proprietory stuff like flash, just goto [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats") and you will see perfect instructions on how to install flash and other stuff.

---

