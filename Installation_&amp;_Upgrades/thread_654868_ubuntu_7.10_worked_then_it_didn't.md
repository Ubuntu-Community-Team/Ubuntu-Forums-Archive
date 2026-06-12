---
title: "ubuntu 7.10 worked then it didn't"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by kevmore on 2007-12-31
I installed ubuntu 7.10 in my desktop computer on it's own drive in my win xp system.  I have win xp on a seperate drive.  Anyway, it all worked fine, I could start either one just fine.  But when Ubuntu decided that I needed some files to make the display work better, I said yea go ahead and get them, and after the update I started ubuntu again and just got a black screen forever.  I tried waiting a good long time like 10 min.  I can not boot into ubuntu anymore, but win xp works fine.  My question is:  How do I rollback the drivers that got loaded in?  

Thanks in advance.
Kevin.

---

### Post by bromix on 2007-12-31
You could boot into recovery mode, which should leave you at a terminal.  Then entter this command

sudo dpkg-reconfigure xserver-xorg

It will have you  reconfigure the xserver again.  It's always worked for me in the past.

---

### Post by kevmore on 2007-12-31
thanks bromix, that probably would have helped, but I ended up re-installing ubuntu and didn't choose the restricted driver option for my vid card.  Then I tried to download the ati driver right from ati, and  I still can't get it to work.  I have the file downloaded and I can navigate to the file but when I try to enter the command to make it install i just get a bad command error.

---

### Post by Partyboi2 on 2008-01-01
Have you tried envy?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
can make installing restricted ati and nvidia drivers alot easier.

---

### Post by kevmore on 2008-01-01
Thanks partyboi, but after I used envy the computer rebooted and I got the computer to fully boot up but no display, just black.  I know it booted up because the music played and there was lots of hd activity.  The last several attempts have ended up hanging with a partially booted machine and a black screen.  
When I try to use the ati download from their server I can't get the file to open once it is downloaded.

When I use the restricted driver method the computer hangs every time.

Does anybody know the keyboard shortcut to restart the machine????  In windoze it's just a simple win key, u, u and the computer shuts down.  This would come in very handy when my computer keeps booting up with a dead display.

I'm getting ready to bash my head into the monitor and cut my wrists with the broken pieces of plastic.

Help.

When I restart and use "Sudo dpkg-reconfigure xserver-xorg"  and answer all the questions, the computer starts in low graphics mode and will not accept the changes.

The only thing I can think of is when I use the "Sudo dpkg-reconfigure xserver-xorg" it asks where the graphics card is located and it is pci 0 or something like that, but my card is an AGP card and I don't know how to enter the ispci option.  Maybe that's it????

---

### Post by kevmore on 2008-01-01
Thanks to Alberto Milone and all the helpful people out there.  I am now stylin with 1680 by 1050 res .  Thanks Again:guitar:

Correction.  I tried to pick 1680 X 1050 but that's not what I got.  It seems 1280 X 1024 is all I am going to get.  What's up with that?

---

