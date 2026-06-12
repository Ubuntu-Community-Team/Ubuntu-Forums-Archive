---
title: "Install hangs at black screen after install bar finishes"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by MarkPat on 2006-12-17
I'm trying to install Ubuntu for the first time.

The install screen loads all it's different drivers and the bar goes all the way to the end then it goes to a screen change, (I think ?), and it's black with the the curser is a solid white dash at the top left screen. It's been that way for about 3 hours now.

I'm using the 6.06 desktop for amd64

System:

CPU: AMD 64 4000+
MoBO: MSI K8N NEO4 Platinum SLI 
RAM: 2 gb Corsair XMS DDR400 
Video: XFX 7600 Nvidia SLI'd (2)
HDD: WD Caviar SE 160gb SATA 

DVD-rom
CD-RW

Any ideas or help would be appreciated!!
Thanks

---

### Post by taurus on 2006-12-17
Sounds to me like it is having a slight problem with your graphic/video card!  Boot into recovery mode from the GRUB menu and at the prompt, type

```
dpkg-reconfigure -phigh xserver-xorg
startx
```
By the way, what video card do you have?

---

### Post by MarkPat on 2006-12-17
ok, I'm a HUGE noob at this. I know a lot about windows but this is my first attempt at Linux.

My video cards are (2) XFX nvidia 7600's in SLI mode.

How do I access the "GRUB" menu?

Oh, and to do anything I'm going to have to hit the reset button and start over. At least that's what I've done twice before this time.

Thanks!

---

### Post by taurus on 2006-12-17
When your computer first boot up (or reboot), you will see a GRUB with time counting down on the right.  That's your GRUB sos just hit Esc before time expires, 3 seconds.  It will bring up a menu and the second option is called recovery mode.  Use the down arrow hit to highlight that option and hit Enter.  Wait for it to finish booting and at the prompt, type those two commands.

If **startx** works, then reboot into normal mode and you are all set...

---

### Post by MarkPat on 2006-12-17
[SIZE="6"]SORRY---![/SIZE]

It's not working for me!!! :-? 

Everything I try at the GRUB menu keeps telling me that it can't find the kernel.
For anything I type!

It's acting like nothing has installed on the HD.

I'm wondering if this may be part of the problem. The HD is still formatted in the Windows XP NTF cluster. 

Thanks AGAIN for any help!

OH---------------
I almost forgot--- When I hit esc to enter the GRUB menu I don't get a drop down menu. All I get is the command prompt.

---

