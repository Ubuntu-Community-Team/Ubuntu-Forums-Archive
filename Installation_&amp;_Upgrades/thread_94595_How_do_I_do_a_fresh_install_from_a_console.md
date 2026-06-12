---
title: "How do I do a fresh install from a console?"
date: 2005-11-24
forum: Installation &amp; Upgrades
---

### Post by Psquared on 2005-11-24
I have been using Ubuntu since Warty and each time I did a dist-upgrade; first to Hoary and now to Breezy. I did a little too much tweaking and now I can't get xserver to start. I can boot to a console and run commands from there. I have tried to reconfigure xserver but it still won't start. I have all my information and documents backed up so I was thinking of a clean install. I downloaded the Breezy ISO (386 - why no 686 version??)

Rather than boot to the install disk I was wondering if I could do a clean install from the console. I already have Grub working and my partitions setup so can I just boot up Breezy and when xserver fails to load and it drops me back to a console, can I just insert the CD, mount my CDRom and run install? Would it be better to change my sources.list and run sudo apt-get install breezy? If so, would I just rem out all the sources except the CDRom? How should that line read?

Thanks in advance for your help.

---

### Post by aysiu on 2005-11-24
I'm not sure what you mean.
If you do a clean install, it's best to do it completely cleanly--with an installer disk.
If, however, you don't like having to redo all your settings every time you install a new version of Ubuntu, consider creating a separate /home partition--this is where all your settings and preferences are stored.

If you have a separate /home partition, you can get a fresh install **and** keep your settings intact.

---

### Post by Psquared on 2005-11-26
[QUOTE=aysiu]I'm not sure what you mean.
If you do a clean install, it's best to do it completely cleanly--with an installer disk.
If, however, you don't like having to redo all your settings every time you install a new version of Ubuntu, consider creating a separate /home partition--this is where all your settings and preferences are stored.

If you have a separate /home partition, you can get a fresh install **and** keep your settings intact.[/QUOTE]


I can boot the ISO disk I made, but I was just wondering if I could boot to my existing Ubuntu (even thought xserver won't start) then insert the disk and install fresh from a console. (I was hoping to keep as much as I can from the previous install, I was just hoping this would repair the damage by putting the files back where they should be.)

---

### Post by RAOF on 2005-11-26
[QUOTE=Psquared]I can boot the ISO disk I made, but I was just wondering if I could boot to my existing Ubuntu (even thought xserver won't start) then insert the disk and install fresh from a console. (I was hoping to keep as much as I can from the previous install, I was just hoping this would repair the damage by putting the files back where they should be.)[/QUOTE]
If you're trying to do that, why not first try reinstalling the xserver?  You could try running
```
sudo apt-get remove --purge xserver*
```to remove all of the xserver packages, and then
```
sudo apt-get install xserver-xorg
```to install a fresh xorg.

---

### Post by Psquared on 2005-11-28
[QUOTE=RAOF]If you're trying to do that, why not first try reinstalling the xserver?  You could try running
```
sudo apt-get remove --purge xserver*
```to remove all of the xserver packages, and then
```
sudo apt-get install xserver-xorg
```to install a fresh xorg.[/QUOTE]

Now thats an idea. :KS 

How do I tell it to connect to the internet using ethernet so I can use apt-get? By that I mean, what command do I use from the console because I don't have any GUI capability or xserver.

---

### Post by RAOF on 2005-11-28
Um, how do you normally connect to the internet?  With an ethernet card, plugged into an adsl modem/cable modem/router thing?  Then you should automatically have an internet connection at the console.  If it's something different, you'll need to say how you normally connect & I'll try to guide you through doing it at the console :)

---

### Post by Psquared on 2005-12-01
[QUOTE=RAOF]Um, how do you normally connect to the internet?  With an ethernet card, plugged into an adsl modem/cable modem/router thing?  Then you should automatically have an internet connection at the console.  If it's something different, you'll need to say how you normally connect & I'll try to guide you through doing it at the console :)[/QUOTE]

Normally I use wireless, but I have an ethernet port. I connected to the ethernet port and tried to run apt-get update but it claimed it could not "stat the sources." I'll give it another try tomorrow and see what happens.

---

