---
title: "Grub prompt after install"
date: 2005-03-06
forum: Installation &amp; Upgrades
---

### Post by karmann on 2005-03-06
I am trying to install Ubuntu on my old 450 MHz Celeron machine.  I have the 4.10 warty warthog release cd and everything seems to go fine, machine boots from CD, I am agreable with all the installation options, etc.  

The problem comes after the first reboot when I take out the CD, the install screen says the computer will reboot, I will be asked a few more questions and then I will be using Ubuntu.  However, the computer boots to a Grub prompt and I don't know what to do next.

No one else seems to have this problem.

I tried pressing ESC before/during the Grub prompt but nothing appears.

Any ideas what went wrong?

Thanks,

---

### Post by alastair on 2005-03-06
It sounds like there is something wrong with the install (or bootloader) config.

You might want to boot the install CD and go into rescue mode - see :

[http://ubuntuguide.org/#rescuemode](http://ubuntuguide.org/#rescuemode)
Q: How to use Ubuntu Installation CD, to gain root user access?

Then look at :

Q: How to restore GRUB menu after Windows installation?

BUT - it is important to know that the grub config file (/boot/grub/menu.lst) is correct. Perhaps you can :

- post it here
- tell us your HDD's (ATA?master/slave? etc.)

---

### Post by karmann on 2005-03-29
I tried it with two different HDs now, and both of these go through the install and then give me Grub "Error 18".

Now what!?

First HD was 12.3 GB, second was 8.4 GB, which I tried to install on twice, performing a fdisk /mbr with a Win 98 disk between installations in case there was an MBR problem and now with a 20 GB HD.

From what I just read, the BIOS might have trouble with the large HDs (>8GB).  And if I'm reading correctly, having a smaller boot partition would fix it?  Does that sound right.

Thanks

---

### Post by Whiffle on 2005-03-29
See this yet? It might apply. I hope... 

[http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes](http://www.ubuntulinux.org/wiki/WartyWarthogInstallNotes)

---

### Post by karmann on 2005-03-29
Thanks, I think that explains it.

I made a boot partition and it worked :)

I was using the Verbose Debian Installer as a guide so I also made a swap partition, but I couldn't find the Swap FS that the verbose installation suggested.  Anyone have any input about that?

---

### Post by karmann on 2005-03-31
Xserver not found ... 

*sigh*

all i get is a login prompt... 

have to install kde or gnome or something?

apt get ... ?

am i on the right track here?

---

### Post by karmann on 2005-03-31
reinstalled!

i'm in!

thanks for everyone's help..

---

