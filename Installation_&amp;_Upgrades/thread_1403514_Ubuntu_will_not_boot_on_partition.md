---
title: "Ubuntu will not boot on partition"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by louis.roux on 2010-02-10
I installed Ubuntu 9.10 as a 2nd partition on my acer that runs vista (I hate vista but that is a subject for another time).  When I try to boot it goes through the motions but then the screen is just scrambled lines and colors.  Also, I have split screen and only one screen shows those scrambled colors while the other screen is just blank.  What is wrong?

---

### Post by 786souljah on 2010-02-10
I had the same issue after applying an update which I beleive installed a newer revision of the kernel? I have not done another update since just incase this happens again.

Grub was edited to have 2 ubuntu entries instead of 1 that I'd already modified for, so I removed the entry by manually deleting the vmlinuz file that was the new update. Should I risk the new update?

---

### Post by SecretCode on 2010-02-10
louis.roux, Can you boot up fully with an Ubuntu live CD? If so, go to System > Administration > Hardware drivers. It may be that you need a propietary driver to work with your graphics card.

If you can't even boot the live CD, post more details of your computer esp the graphics card.


786souljah, your problem is unlikely to be the same. You should start a new thread.

---

### Post by louis.roux on 2010-02-10
SecretCode, I did try to do a live boot but I had the same problem.  Therefore below is my computer info.  I hope it is what you need to help.  Thanks

Acer Aspire T180 running Vista Home Premium
Processor: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ 2.00 GHz
2.00 GB Ram
32 - bit OS

Graphics Card: NVIDIA GEFORCE 7300 LE

---

### Post by SecretCode on 2010-02-10
Bad news about the live CD. (How did you install it though?)

We'll have to boot to command line then - do you get a GRUB menu when booting? (If not, press Shift.)

You should have a grub menu item with (recovery) after it. Boot that (wait for boot messages to scroll by) and select 'resume' - you should end up at a console-mode login prompt. Log in.

Type
```
sudo aptitude install nvidia-glx-185
```
If this gives an error message, post the contents of file /etc/apt/sources.list

If it works, reboot! I'm not guaranteeing it but it is worth a try.

---

### Post by louis.roux on 2010-02-10
well, sorry to say that didnt seem to work.  First of all, I dont seem to be getting to the GRUB menu as you described.  No recovery menu.  No login promt.  

I did get to a demo menu where I was able to put in the command line you gave me, but there was no glx-185.  the highest was 180 which I unpacked and installed but it didn't help.

I'm beginning to think it is trying to boot up with windows boot commands instead of the GRUB.  What do you think?

---

### Post by SecretCode on 2010-02-11
A demo menu? How did you get to that? I can't even think what that is.

Try pressing Esc instead of Shift when booting (this calls up the grub menu in older versions of grub).

But yes, it could be that the boot manager is still windows. Do you see a boot menu at all?

Also, when you boot from the Ubuntu live CD, do you get a language prompt then an Ubuntu logo with a menu
[B]Try Ubuntu without any change to your computer
Install Ubuntu
Check disk for defects
[/B]etc?

Press F4, cursor down to 'safe graphics mode', press enter, and then (with 'Try Ubuntu without any change to your computer' selected) press enter to boot the Live CD.

---

### Post by louis.roux on 2010-02-11
Great news, that worked.  The only thing now is when it boots up it asks me for a username and password.  I obviously never set this up as this is the first time I was able to see anything but I can get past that.  How do I bypass that and set it up with my own username and password?

---

### Post by SecretCode on 2010-02-11
Again, I am confused. If you've booted via 'Try Ubuntu without any change to your computer' you should never get a password prompt. (Technically you run with the username *ubuntu* and no password.) 

Did you run installation previously? It sounds like you must have done. But you'll probably want to reinstall anyway.

So we can understand the layout of the disk, please boot the live CD as described above, open a terminal (Applications > Accessories > Terminal), enter the following command:
```
sudo fdisk -l
```
and paste the output here.

---

