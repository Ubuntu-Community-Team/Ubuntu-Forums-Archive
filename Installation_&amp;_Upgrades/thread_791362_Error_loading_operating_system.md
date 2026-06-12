---
title: "Error loading operating system"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by gophy831 on 2008-05-12
Hi all

First off although I have been using computers for an age and have a fairly good knowledge of how they work I'm very, very new to the Linux community having only installed Ubuntu three days ago (I will confess, and please don't shoot me, that I have always used Windows). 

My problem concerns booting Ubuntu from my hard drive. I installed it from a CD making sure that it occupied the entire Hard drive as this machine was to be a Linux only, single OS computer. I do have two hard drives in the computer; an IDE one and a SATA one and I made sure that the BIOS boots from the SATA one first and that is the one Ubuntu is installed onto.

However when I go to start the computer I get an 'Error loading operating system' message!! No grub interface or anything. If I boot from CD Ubuntu gives me the option to boot from hard drive; I choose it and Ubuntu starts up quite happily from the hard drive.

I have had a look through the forum stickies but can't find any reference to my problem; especially as most of them deal with dual-boot set ups, which I don't have.

At the moment I am assuming the problem is with my BIOS set up but am open to suggestions; either a solution or suggestions as to where to go on the web to find my answer.

Cheers all

---

### Post by hermes0710 on 2008-05-12
Boot ubuntu the way you already do and run a terminal (<alt>+F2 then type "gnome-terminal").

In the terminal type:
```
sudo grub
``` (you will be asked for your password). Then type:
```
find /boot/grub/stage1
```

Let's suppose that running the above command you get "(hda,b)".

Then type the following:

```
root (hda,b)
setup (hda)
quit
```

Then reboot. (Make sure you replace the "a,"b" according to the results of the "find /boot/grub/stage1".

Hope i helped

---

### Post by Aearenda on 2008-05-12
Sounds like Grub has installed to the wrong drive - there are known issues with mixed PATA/SATA configurations where this happens. What happens if you change the BIOS boot order to go to the IDE drive?

EDIT: Try hermes0710's idea first - that's a fix, if it works.

---

### Post by njparton on 2008-05-12
Can you boot windows from the IDE drive?  You may have overwritten the windows bootloader as grub tends to default to hd0 which will be your IDE drive.
 
The bes bet when installing ubuntu is to unhook all other drives in my experience.

---

### Post by gophy831 on 2008-05-12
Thanks for all your help gentlemen my Ubuntu is now booting straight from Hard Drive.

When I followed the shell instructions everything appeared OK but when I booted I got an Error 17 from grub. So I swapped the Hard Drive boot order to the IDE drive first and it now works perfectly.

Cheers again

Hopefully everything else will go swimmingly now.:)

---

