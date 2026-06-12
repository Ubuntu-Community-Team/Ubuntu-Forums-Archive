---
title: "Dual boot gone terribly wrong"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by markiz on 2010-04-16
Hy

First of all, i have to say that i am a complete noob, so i would appreciate if you could dumb down anything you might have for me.
I have already done searches on the forum, but it has not been answered in any language i can understand.

This is my problem:
I have an HP Pavilion dv6 laptop with win7 32. Out of a whim i decided to give linux a try. i decided on Kubuntu 10.04, which my friend, linux enthusiast, recommended. That and ubuntu, but i liked KDE more from what i saw. Anyway, i made myself a new 10GB partition and installed kubuntu via live USB. I'm not sure 100%, but i think i made that partition primary. After a week, i decided to get rid of it (no time to get used to) and formated that partition with easeus partition manager within windoz. So partition manager restarts my comp and now i can not get into neither kubuntu nor windows.this is the error i get:

error: unknown filesystem
grub rescue>

I had no idea linux messes with the bios.
What i want is to get back to windows 7 and be able to use my computer.
i made myself new live usb and am currently installing kubuntu, but i am to afraid to do anything else.

I know it might be rude to ask this on linux forum, but how do i get rid of it?

---

### Post by zvacet on 2010-04-16
Install Kubuntu and you will have grub back.After that do [this.]("http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe")After that remove Kubuntu.I hope this will work in Windows7.

---

### Post by h4x0rmx on 2010-04-16
You need to restore the MBR. Google "restore MBR".  You used to be able to do this with some windows installation CDs.  I wish I could be of more help, but it's been years since I done it (last time I did it I used a floppy with some DOS utility to restore the MBR).

Good luck!

---

### Post by oldfred on 2010-04-16
Your MBR still has grub in it and grub is looking to the partition you deleted for the rest of its files.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by markiz on 2010-04-17
Better yet, can i make it so that win7 boots automatically, and not kubuntu? I made kubuntu partition logical this time because i thought it would make win the default but it did not..

If not

I should have read some instructions how to make a proper dual boot before i plunged into it.

---

### Post by oldfred on 2010-04-17
But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in this and copy to grub default like this Vista entry:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

Or another GUI way:
Startup manager in synaptic will allow you to set boot default and the timeout even in lucid.

---

### Post by markiz on 2010-04-25
I thought i said dumb it down?
Anyway, a friend will be coming to rid me of my problem if i dont do it myself.

---

