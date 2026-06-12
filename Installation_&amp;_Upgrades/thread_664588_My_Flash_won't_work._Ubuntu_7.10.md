---
title: "My Flash won't work. Ubuntu 7.10"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by ryrobbo on 2008-01-11
Hi.

I have recently installed Ubuntu 7.10 and I'm on the internet. when i try to watch a video on Youtube it says i need to install Flash player so i clicked the link and get this screen. (SCREENSHOT). I'm new to Linux so i haven't a clue what option to pick so i chose Option 1. Once downloaded I made it open with the default program (Archiver) and got this txt file type screen with multi-coloured codes.
I don't know whether this means its installed but i went back to Youtube and Firefox prompted me to install these plugins so i tried both and got this error. (SCREENSHOT1).

Please help me I'm struggling.

---

### Post by confused57 on 2008-01-11
Just download the .deb file here, double-click & gdebi will automatically install flashplayer:

[http://ubuntuforums.org/showpost.php?p=4080256&postcount=3](http://ubuntuforums.org/showpost.php?p=4080256&postcount=3)

---

### Post by ryrobbo on 2008-01-11
I now have Flash installed but, now when I wait for a youtube video to load it doesn't load, my computer just freezes up and i can't do a thing other then press the reset button. 

Please help me with this issue.

---

### Post by confused57 on 2008-01-11
> **ryrobbo said:**
> I now have Flash installed but, now when I wait for a youtube video to load it doesn't load, my computer just freezes up and i can't do a thing other then press the reset button. 

Please help me with this issue.

If your system is 64-bit, it's my understanding that Adobe flashplayer doesn't support 64-bit,  here's a way to install 32-bit flashplayer on a 64-bit system:
[http://ubuntuforums.org/showthread.php?t=202537](http://ubuntuforums.org/showthread.php?t=202537)

You'll need to uninstall flashplayer first, by opening Synaptic Package Manager, do a search for:
```
flashplugin-nonfree
```

If you still want to try installing the downloaded tar.gz, you should be able to right-click, then select "Extract Here".  Then open a terminal(Applications---Accessories---Terminal):
```
cd Desktop/install_flash_player_9_linux
./flashplayer-installer
```
This way probably won't work either, since the .deb file installs the same package and it's a little more difficult to uninstall if you install with the tar.gz.

---

### Post by ryrobbo on 2008-01-12
My computer is about 5 years old and has an Intel celeron so I'm sure its a 32 bit system.

---

