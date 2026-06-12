---
title: "Video Problem"
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by proxyviper on 2005-11-20
Hey guys, I am not sure if this has been a pretty popular problem but when I try to boot up ubuntu my screen displayes a lot of random colors in what appears to be rectangular boxes. I hear the start up chime go off but I dont get a display because of all the colors.

---

### Post by proxyviper on 2005-11-21
Anyone able to help a noob in need :)?

---

### Post by proxyviper on 2005-11-21
Hmm, Perhaps I didnt state the question clearly. I was wondering if anyone would be able to help me on this?

Basically when the install finished and I try to boot I get a lot of wierd colors being displayed as opposed to the normal GUI interface... I hear the startup sound go off but the display is still jacked... 

any help?:D

---

### Post by dcstar on 2005-11-21
[QUOTE=proxyviper]Hmm, Perhaps I didnt state the question clearly. I was wondering if anyone would be able to help me on this?

Basically when the install finished and I try to boot I get a lot of wierd colors being displayed as opposed to the normal GUI interface... I hear the startup sound go off but the display is still jacked...

any help?:D[/QUOTE]
Ok, it looks like you graphics settings aren't correct.

Press <CTRL><ALT><F1> to get to a text login screen, and then log in with your user name and password.

Then run: "sudo dpkg-reconfigure xserver-xorg" and go through the process of setting up your video card and screen.

Don't get too confused by all the choices, just accept the defaults and try and auto-detect anything if it offers you the choice.

Once finished, do: "sudo init 6" to reboot your machine and hopefully things will be better.

---

### Post by proxyviper on 2005-11-22
Alright, awesome. I will check that when I get home.

---

### Post by bluerowlf on 2005-11-22
I've had the same exact problem, but the keyboard doesn't respond also. I can see and move the cursor over the strange colors, but key presses don't do jack.  
Since I can boot a linux liveCD, where in the logs should I look for a helpful error message?

related threads?:
[http://ubuntuforums.org/showthread.php?t=25847](http://ubuntuforums.org/showthread.php?t=25847)
[http://ubuntuforums.org/showthread.php?p=512137#post512137](http://ubuntuforums.org/showthread.php?p=512137#post512137)
[http://ubuntuforums.org/showthread.php?p=112845#post112845](http://ubuntuforums.org/showthread.php?p=112845#post112845)
[http://ubuntuforums.org/showthread.php?t=26630](http://ubuntuforums.org/showthread.php?t=26630)
[http://ubuntuforums.org/showthread.php?p=454217](http://ubuntuforums.org/showthread.php?p=454217)

---

### Post by ScaryFast on 2006-02-24
I made an account just to reply in this thread with a picture of what the op is talking about. I am also having this problem. I had it with the 5.04 livecd, and am now experiencing it in 5.10. Everything up to this point works fine, and once I get here I do hear the startup sound, but that's all.

[[IMG]http://img238.imageshack.us/img238/1117/ubuntugeforce6600gt6sg.th.jpg[/IMG]](http://img238.imageshack.us/my.php?image=ubuntugeforce6600gt6sg.jpg)

---

