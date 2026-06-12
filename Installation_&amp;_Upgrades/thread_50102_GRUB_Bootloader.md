---
title: "GRUB Bootloader"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by miickEe on 2005-07-19
I just installed Ubuntu (again) and the GRUB boot manager. The GRUB does not come up when I boot my machine up, rather it goes straight to XP. This is an extreme inconvenience and I would SERIOUSLY like to use UBUNTu because as soon as I used the LiveCD I fell in love with it.
The HDD that has Ubuntu on it is Master, while I get my XP HDD to boot first. However, when i disable all but my Ubuntu HDD it comes up with Error 17.. I did research on what this means but to no avail.

HOW CAN I BOOT INTO UBUNTU?!

miickEe./

---

### Post by mingus on 2005-07-19
Before giving any advice on the problem, we need more information.  This will be easiest if you can boot into Ubuntu, for example, from CD.  Do you know how to do that?

---

### Post by kalle314 on 2005-07-28
[QUOTE=mingus]Do you know how to do that?[/QUOTE]

Please tell me, because I got a similar problem today.

I did what the "unofficial ubuntu guide" said to get a splash image, and edited grub/menu.lst . But then it was assumed that the location of Ubuntu boot partition was hd0,1. 
Probably the location was different for me, because I do not get a Grub menu now - the computer boots to the default OS directly, and that is set to Windows.

edit: This is what happens at booting:
* I see two lines flashing by, I think it says Grub loading, please wait.
* I see abou five line flashing by (it is not the OS select menu).

It does not help to press escape.

---

### Post by mingus on 2005-07-28
[QUOTE=kalle314]Please tell me, because I got a similar problem today.

I did what the "unofficial ubuntu guide" said to get a splash image, and edited grub/menu.lst . But then it was assumed that the location of Ubuntu boot partition was hd0,1. 
Probably the location was different for me, because I do not get a Grub menu now - the computer boots to the default OS directly, and that is set to Windows.

edit: This is what happens at booting:
* I see two lines flashing by, I think it says Grub loading, please wait.
* I see abou five line flashing by (it is not the OS select menu).

It does not help to press escape.[/QUOTE]

It may be that grub is still OK.  You may have made a change to menu.lst that messed up the Ubuntu boot, and grub is then going to the next choice which probably is to "chain-load" Windows.

Before trying to re-install grub, do you have a Live-CD (easier) or install CD to boot in with?  We need to see the menu.lst file.  Also be helpful to have your disk partition layout (use the command fdisk -l).

---

### Post by kalle314 on 2005-07-28
Hello, 

I have both the live CD and the installation CD, but I'm not sure about how to boot with them - I do not know what to type when the installation CD says "boot: ".

Can I see (and restore) the "menu.lst" file if I boot with the live CD?

edit: I am in a live session now, but I can not access "menu.lst" - I can only access the files on the live CD.  :|
Maybe I can mount the ubuntu partition by writing "sudo mount [something]" but I do not know what this [something] should be.


Anyway, I'm pretty sure the only difference from the original menu.lst file is the line
"splashimage (hd0,1)/boot/grub/images/ubuntu.xpm.gz"
after the first four lines, so I would like to remove that.

[SIZE=1]
(This is what I did: [Q: How to display Splash Image for GRUB menu on boot-up?](http://www.ubuntuguide.org/#displaysplashimagegrub))[/SIZE]

edit again: I learned it the hard way - I had to write "sudo fdisk -l" to list the partitions, and then mount the ubuntu partition, and edit the "menu.lst" file. 
The problem simply was that hd0,1 was not the ubuntu partition.

---

### Post by mingus on 2005-07-30
*The problem simply was that hd0,1 was not the ubuntu partition.*

Or more specifically, that the splash image path was incorrect.  Congratulations on working thru the problem "the hard way."

---

