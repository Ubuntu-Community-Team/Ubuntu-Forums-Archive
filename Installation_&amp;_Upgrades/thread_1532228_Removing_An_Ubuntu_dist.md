---
title: "Removing An Ubuntu dist"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by thelugnut on 2010-07-16
I have multiple Op systems on one hard drive. I now wish to remove one of the Ubuntu o.s.
It so happens that this is the o.s. that loads the GRUB2 loader. 
I would like to switch to another Ubuntu o.s. and use its GRUB2 loader. 
I need some advice on how to accomplish this.

---

### Post by digitalcitizenx on 2010-07-16
The boot loader is in the master boot record of the hard drive - not in the OS.

If you are going to replace the OS on that partition, simply put the disc in the CD drive and tell the installer to use the partition the OS you would like to replace resides.

---

### Post by ajgreeny on 2010-07-16
It will be simpler just to boot to the OS from which you wish to use grub and run ```
sudo grub-install /dev/sda
``` if it's another ubuntu OS that uses sudo.

This assumes that you already have that OS installed, and that /dev/sda is the hard disk in use, of course.  If you are replacing the current OS by a new install, it will all be done for you, as digitalcitizenx said.

---

### Post by thelugnut on 2010-07-17
Thanks for the replies, I'll give it a try this Saturday.:P

---

### Post by Nick_Jinn on 2010-07-17
Couldnt you just use a live disk and delete it with Gparted?

---

### Post by thelugnut on 2010-07-17
To ajgreeny:
Okay, that worked like a champ. Many thanks. I had been trying to designate the partition I wanted and kept receiving the warning message that this wasn't a safe thing to do. When I followed your sage advice and dropped the partition designation, things worked good. Live and learn, sin and burn as they say.
Again, thank you.

---

### Post by ajgreeny on 2010-07-17
> **Nick_Jinn said:**
> Couldnt you just use a live disk and delete it with Gparted?
The OP would still have needed to install grub from somewhere as the deleted partition would have contained all the grub configuration files, so why not change grub before removing the OS partition that is supplying the grub configuration files.

---

### Post by Nick_Jinn on 2010-07-18
> **ajgreeny said:**
> The OP would still have needed to install grub from somewhere as the deleted partition would have contained all the grub configuration files, so why not change grub before removing the OS partition that is supplying the grub configuration files.

Cant you update grub from the command line from a live disk or USB drive? Just type in apt-get update grub or something like that?


I am trying to learn myself. I am not arguing. Im trying to learn.

---

### Post by ajgreeny on 2010-07-18
> **Nick_Jinn said:**
> Cant you update grub from the command line from a live disk or USB drive? Just type in apt-get update grub or something like that?


I am trying to learn myself. I am not arguing. Im trying to learn.
I did not think you were arguing.

I was trying to explain that the easiest way to do what was needed was to put grub from the OS that already was running and was going to remain as the main OS onto the MBR. The old OS partition could then be deleted completely if that was the intention, and no shocks would follow at the next boot when no grub menu appeared.

Why mess around with a live CD install of grub when it was already there on the machine and available with just one simple command?

I hope that helps you understand a bit more about the way grub works.

---

### Post by Nick_Jinn on 2010-07-19
Totally. I was confused for a second thinking things were more difficult than they were.

Are there problems when you have multiple versions of linux? I know some conflict like Mint and Moon conflict, and maybe GOS. If I have XP on the same disk on a different partition and Win7 on a second hard drive, but most of the primary hard drive is devoted to Ubuntu and I also have a few other odd versions of linux, can I get them all to be recognized by grub by typing that command?

---

