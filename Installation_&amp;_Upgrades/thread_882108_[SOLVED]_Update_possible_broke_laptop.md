---
title: "[SOLVED] Update possible broke laptop ??"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by DoubleDee on 2008-08-06
Ok so I've been using ubuntu for a while now, I'm fairly knowledgable when it comes to linux/unix.  So I'm running a Dell latitude D830 with an nvidia graphics card.  I had enabled compiz-fusion, which would freeze when i login in ubuntu but if i restart X a couple times it seems to fix it self (I know xorg and nividia don't exactly get along that well).  Anyway, i had also enable the proposed updates for my software sources and had th 2.6.24.20 kernel, which i know is still beta so i think that might have something to do with my problem.  Anyway, my problem is, there were so updates waiting to be installed when i woke up yesterday, so i installed them before work.  When i got to work and turned on my laptop, all I get now is a blank white screen that fade to black with some coloured stripes, and this is happening before my bios loads and grub opens so i cant even F8 or F12 to boot from a disc or check my bios.

My question is: has this happened to anyone else? If so did you get it working again and how?  Also, could this mean my laptop is bricked?  I believe its still under warrenty so i might try calling dell. Is there any other suggestions that may help?  

Any help is greatly appreciated.

---

### Post by reclinerspud on 2008-08-06
Yes this happehd to me it was caused by a update file that re configured my video card. I use a program calle d ENVY to config ure my video  it works for nvidia and ati cards. but you have to unload it before updating a ny thing to do with video set up then re load it.

---

### Post by SarahKH on 2008-08-06
Keep your fingers crossed this one works.

CTRL+ALT+F1 together and your display should go to the normal text mode login window.  From there login as yourself and sudo nano -w /etc/X11/xorg.conf 

CTRL+W to search and type nvidia 

Change that to read nv

CTRL + X to exit (yes,you want to save).  

sudo /etc/init.d/gdm restart

The X windows system should now restart using the open source nv driver, which will get your back in to the GUI to reapply the Nvidia binaries via Envy.

If the first line doesn't appear to work, then your flying blind I'm afraid.  This *should* work though:
CTRL + ALT + F1 (still blank but hopefully a text console is waiting).
<login> 
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak-new (press enter) 
sudo /etc/init.d/gdm restart (press enter)

And hopefully it should fire up (Xorg can't automagically detect and use the broken binary drivers so will use either vesa or nv).   And again, reapply the binary drivers and reboot.  If it doesn't start up then it probably means Xorg has gone totally belly up and you'll need to boot off of a livecd to poke around at the xorg.conf file.

---

### Post by DoubleDee on 2008-08-06
The problem is, i get a blank screen as soon as i press the power button, it doesnt even do the loading screen the the DELL logo or go into grub, just blank.  I have a feeling its bricked cuz my hard drive stops spinning as well.:confused:

---

### Post by DoubleDee on 2008-08-08
Could this possibly be that my graphics card is trying to boot before my BIOS??

---

### Post by DoubleDee on 2008-08-12
So it turns out that something screwed my bios and mother board, but the friendly people at dell were very helpful and everythings back up and running. :)

---

