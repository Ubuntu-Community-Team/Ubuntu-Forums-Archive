---
title: "Can't Boot Ubuntu"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by ryan_prior on 2007-02-25
Hi All, I just downloaded Ubuntu 6.10 and burned the ISO using ISO buster. Now when I try to boot to Install Ubuntu on my second HD (first one has XP Pro), it doesn't work. I get the boot options screen, I choose boot or install, and it shows the Ubuntu loading screen, once it loads up, the screen goes black (sometimes solid white) and I hear the chime when the OS starts, but nothing shows up on the screen. 

I tested booting from another PC I had lying around and it works fine. Can someone help me out?

System specs:
P4 1.7 Ghz
1.25 Gb RAM
2 x 80 GB HD's - one seagate, one western Digital
NVIDIA GeForce 6200 256mb video card.

If you need any other system specs, please let me know.

It looks like it is loading, but the GUI is not coming up on the screen. I found something that said to use the boot option: "FB=false Video=VGA16:off" but when I tried this it made no difference. 

I also tried booting is safe graphics mode and have scanned the CD for errors.

Thanks,

ryan

---

### Post by taurus on 2007-02-25
I think the LiveCD is having a little technical difficulty with your graphic card.  Therefore, I think you should use the alternate CD to install it on your machine.  Even though it's a text base installer, it's real easy to follow.

[http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-alternate-i386.iso](http://ubuntu-releases.cs.umn.edu/edgy/ubuntu-6.10-alternate-i386.iso)

---

### Post by Busch on 2007-02-25
yes the alternate CD should do it.  I tend to use that anyway even if the live cd works, i like using the text based since im more used to it.  makes me feel like i have more control over my install :P

---

### Post by Think first on 2007-02-25
I think you've stumbled on the same bug as I have. For some reason the "out of the box" driver for some nVidia cards (and ATI alike) does not support your card.
You have to use the alternate CD to install (I think) and then boot into "Rescue mode" - if you have that option already you don't have to reinstall.
In that mode you end up at a prompt as root.
Type 
nano /etc/X11/xorg.conf
beware that the X in X11 has to be a major X
Now you are editing xorg.conf that controls the X server (graphics "enginge") Look for a section named "Device" only. You should see a line like
Driver = "nv"
Change nv to vesa and save the change. To do that press Ctrl + x and say yes to saving and save it to the xorg.conf you opened.
Write exit att the prompt and you will do just that and enter into a graphic shell, but with very sloppy graphics.
Find the info on how to use "Envy" and use that to install a proper driver - piece of cake

I think this should be sticky as I see lots of questions asked about this.

---

### Post by Think first on 2007-02-25
Better still - follow the advice in this thread I found a few minutes ago

[http://www.ubuntuforums.org/showthread.php?t=367358](http://www.ubuntuforums.org/showthread.php?t=367358)

---

### Post by ryan_prior on 2007-02-27
Hi, I found the problem, I just had to unplug my Wireless USB Mouse and use a PS2 one during the boot up, I could then plug the usb mouse back in and it worked fine.

---

