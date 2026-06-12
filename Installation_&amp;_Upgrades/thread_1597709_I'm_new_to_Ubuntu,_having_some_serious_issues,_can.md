---
title: "I'm new to Ubuntu, having some serious issues, can anyone help me?"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by fsm_derek on 2010-10-15
So, I'm trying to install Ubuntu 10.04.1 LTS and I get through all the installation process (purple screen with logo, info, and progress bar) and when it's done, it reboots....but I just get a black screen?  Thinking it was some kind of compatibility issue, I unplugged everything but my keyboard and mouse, still no luck.  It gives a quick flash of text before the screen goes black, something about firmware??  Do any of you know what this is??  I've never used any form of Linux before so I am not familiar with any of this.  Are there any known machines that this OS just doesn't work on??  Does a machine have to be built a certain way (like a mac) to run a Linux OS???  I've been fighting with this for 2 days now, uninstall, reinstall, uninstall, reinstall, etc etc.... it's just not working for me.  Do I just give it up and stick with my trusty ol' Windows or is this fixable or what??  Please help me if you can......PLEASE, I'm ready to try something NEW!!!

Thanks in advance to anyone who's able to help me out :)

Derek

---

### Post by ratcheer on 2010-10-15
Can you boot into recovery mode? Just when the machine boot-up sequence is completing (i.e., just before it is going to start Linux), press and hold the shift key. That should take you to a text screen with some Linux boot options.

Let us know.

Tim

---

### Post by fsm_derek on 2010-10-15
Hey Tim, thanks for the quick response.  Yes, I've tried the recovery option already with no luck.  I've also done a little research about known issues and tried a few command edits.  I have 2 22" Samsung LED monitors and one of the things I read was aspect ratios other than 4:3 sometimes have black screen errors so I tried vga=788...no luck, fb=false.....no luck, then I tried rescue/enable=true for the heck of it...still no luck.  I also read about people with large amounts of RAM having trouble so I tried ram=512m...again, no luck.  I'm not a beginner by any means when it comes to computers but I tell ya, I'm completely stumped on this one........any ideas?

Derek

---

### Post by ratcheer on 2010-10-15
Sorry, I don't know anything about dual monitor configurations. Someone else will have to come in on this one.

Tim

---

### Post by fsm_derek on 2010-10-15
Well crap, thanks anyway Tim :)

I've installed this version on my HP laptop and it runs fine, just can't get it to run on my desktop.  I've tried just one monitor so that's not the issue here.  I have a Hauppage TV Tuner PCI card installed in my desktop, would this cause an issue??  Anyone else have any ideas??

Derek

---

### Post by oldfred on 2010-10-15
Do not know about dual monitors:

I have nvidia and my monitor went to standby & had to do this:
boot from the cd, press F6 and then select the nomodeset option.
(I acutally edited my grub.cfg as I use grub2 to directly boot ISO on USB, or in USB's syslinux.cfg or text.cfg)
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
sudo nvidia-xconfig
Or it should be in System>administration>Hardware drivers.

VGA = has been obsoleted with grub2:
"VGA Deprecated" Message on Boot
[http://ubuntuforums.org/showthread.php?t=1453524](http://ubuntuforums.org/showthread.php?t=1453524)

---

### Post by zuerston on 2010-10-15
> **fsm_derek said:**
> Well crap, thanks anyway Tim :)

I've installed this version on my HP laptop and it runs fine, just can't get it to run on my desktop.  I've tried just one monitor so that's not the issue here.  I have a Hauppage TV Tuner PCI card installed in my desktop, would this cause an issue??  Anyone else have any ideas??

Derek

Why not pull all cards out of your computer and see if it works.
Even video card if you have MOBO video to fall back on.

---

