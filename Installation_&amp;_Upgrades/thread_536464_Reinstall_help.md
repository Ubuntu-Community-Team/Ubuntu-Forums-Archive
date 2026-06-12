---
title: "Reinstall help"
date: 2007-08-27
forum: Installation &amp; Upgrades
---

### Post by bulazeem on 2007-08-27
Hi, i have my computer set up for a dual boot of Ubuntu 7.04 and windows xp.  i did this so that i could gradually learn how to use Ubuntu and make gradually get off of windows (its been real hard so far :().  Anyways, i messed up my video drivers in Ubuntu and it said i had no screens found and i searched on these forums and found some different things to try and help.

sudo nano /etc/X11/xorg.conf
sudo dpkg-reconfigure xserver-xorg

So after messing with it for a few hours i finally gave up.  i was able to get back to my desktop with a horrible resolution and i couldn't figure out how to get my old nvidia drivers working properly. I tried to do sudo apt-get install nvidia-glx-new and then sudo nvidia-glx-config enable but after restarting my pc it just led me back to the error message that said i had no screens.

So down to the main question and purpose of this thread.  Will i be able to reinstall Ubuntu over the current partition that i have it set up in right now without losing the grub boot menu and without losing any of my windows xp files.  If yes, do i just throw the disc in and then select to install over the current partition?

---

### Post by pdavit on 2007-08-27
Similar problem here.

My story:

I am an owner of an ATI Radeon 9600 graphics card.

The default driver of Ubuntu (v7.04) could give me the desktop effects while some other issues did not work 100% correct. eg. the fade effect when asked for an admin password wasn't smooth but showed blocks. In addition the screen has a small pixels shift to the left and I has to use my monitor's Auto button to correct it which set the shift problem on Windows and I had to use to Auto feature there too. 

Anyway, the proprietary official ATI drive solved the above problems but introduced a restriction on the Desktop Effects which are not possible to activate now. I'm getting a "Composite/Component...missing" something message when trying to activate (cannot remember the exact error message). Playing around to correct the problem I deselected the 3D acceleration option in the restrictive driver section and now I get a blank screen when Ubuntu boots up
in the login screen and I cannot continue from that point.

Can you suggest any solution please? Anything I can do from the "Safe mode" command prompt? Can I revert to the default Ubuntu driver somehow? Can I uninstall my video driver and force Ubuntu to relocate my graphics card? Will bulazeem's reinstallation suggest help here as well without configuration and/or data loss? By the way, I have updated to Tribe 5 of v7.10. How's that complicating the whole thing?

---

### Post by Pumalite on 2007-08-27
Gutsy is in testing and not for newbies. Stick to 7.04 for now. Choose Alternate CD

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check box below 'Start Downloading'

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by logos34 on 2007-08-27
> **bulazeem said:**
> So down to the main question and purpose of this thread.  Will i be able to reinstall Ubuntu over the current partition that i have it set up in right now without losing the grub boot menu and without losing any of my windows xp files.  If yes, do i just throw the disc in and then select to install over the current partition?


Yes, provided you tell ubuntu not to install grub.  If you're using the alternate install cd it's easy--you'll be prompted toward the end whether you want to install grub.  If the live cd, then when you get to the "Ready to install' screen, click 'Advanced' button lower right and delete '(hd0)'.  It will complain at the end about 'Fatal error' but ignore it.

  
Just make sure that during the install setup you format only the root (/) partition and swap, not XP!

---

### Post by bulazeem on 2007-08-27
ty vm for the help.  rebooting to try it right now =]

---

### Post by bulazeem on 2007-08-27
hi, right now i am using my ubuntu live cd because when i finished installing i got an error.  i rebooted and the computer said grub 1.5  grub loading and then error 15.  i did everything as i was told and deleted the (hd0) setting in advanced and got the expected error.  a bit of good news through all of this is that i can still see my windows xp files from the live CD and they are safe and sound :D

please help me fix this issue and please try to be very basic.  i'm probably the biggest noobie on these forums :(

edit:  when looking in /boot folder i do not see the grub folder and so there is no menu.lst.  so i cant give any feedback as to how grub is set up b/c it seems as though its not set up at all =(





ok FIXED :)    since i had nothing to lose on the ubuntu partition i just decided to reformat it again but this time i did not change the advanced option and i left (hd0) in the box.  after it finished and i restarted everything was working great.   thanks for the tips and great help everyone.  the support here is amazing

---

### Post by logos34 on 2007-08-28
> **bulazeem said:**
> hi, right now i am using my ubuntu live cd because when i finished installing i got an error.  i rebooted and the computer said grub 1.5  grub loading and then error 15.  i did everything as i was told and deleted the (hd0) setting in advanced and got the expected error.  a bit of good news through all of this is that i can still see my windows xp files from the live CD and they are safe and sound :D

please help me fix this issue and please try to be very basic.  i'm probably the biggest noobie on these forums :(

edit:  when looking in /boot folder i do not see the grub folder and so there is no menu.lst.  so i cant give any feedback as to how grub is set up b/c it seems as though its not set up at all =(





ok FIXED :)    since i had nothing to lose on the ubuntu partition i just decided to reformat it again but this time i did not change the advanced option and i left (hd0) in the box.  after it finished and i restarted everything was working great.   thanks for the tips and great help everyone.  the support here is amazing


Sorry, that was my mistake, I don't know what I was thinking: I forgot that when I do it Grub is pointing to /boot/grub/menu.lst on my permanent installation root partition (I'm multibooting at least two other linux distros at any given time).  Ordinarily I then boot into Feisty and add the entry for the new install to menu.lst if I haven't done so already. When you skip the grub install it doesn't create a menu.lst, but in your case you had only the one root partition which grub was pointing to, and you reinstalled over it...Duh.  For future reference, if you don't want to touch the mbr, put it on a floppy (if possible) with '(fd0)'.

---

### Post by pdavit on 2007-08-28
> **Pumalite said:**
> Gutsy is in testing and not for newbies. Stick to 7.04 for now.

Well the source of the problem wasn't a bug in Gutsy but "uninstalling" the video driver. Even if Feisty was running I would probably have ended up in the same black screen result. The question is how to safely recover from that.

---

### Post by Pumalite on 2007-08-28
I'm writing to you from Tribe 4. Gutsy will be stable in October.

---

