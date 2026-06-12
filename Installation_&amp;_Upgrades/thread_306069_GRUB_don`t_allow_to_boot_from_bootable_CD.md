---
title: "GRUB don`t allow to boot from bootable CD"
date: 2006-11-24
forum: Installation &amp; Upgrades
---

### Post by vr.crawler on 2006-11-24
I have ubuntu installed with GRUB, and windows on other partition.
The problem is that if i try to boot from a bootable cd, windows, or other linux, BSD. it doesnt let me to, the option isn`t there. the option to "press any key to bot from cd" , even if in bios is enabled ! 
what can i do to fix this ? :-k

---

### Post by bulldog on 2006-11-24
You have to hit the button before you see GRUB,to boot from a cd.

If GRUB is loaded you only can choose from the options in GRUB,and there is the cd not listed.

---

### Post by Tamil on 2006-11-24
Boot order of CD should be before hard drive.

---

### Post by vr.crawler on 2006-11-24
it dont works even if i hit the keyboard with the hammer or my head or anything, i even tryed to hit it with the cat, but it dont works .... it just dont show at all the option of boot from cd at all, even if the cd is the firsth boot device in bios. is not about pc, hardware/bios problem, coz i installed it on a athlon xp and a pentium d , .  the same, after ubuntu is  installed with grub the "boot from cd" option is not anymore. 
someone know how to fix it nicely? ](*,)

---

### Post by bulldog on 2006-11-24
It should be a hardware error,because GRUB has nothing to do with that.

Grub is in the MBR of your hard disk,and the option to boot from cd-rom is before you reach the hard disk.
So there's something wrong with your BIOS or your keybord.

Does your keybord works during boot time?
I have a USB keybord and I have to set it in the BIOS to be recognized during boot.[MSI nForce3 MoBo]

---

### Post by ajgreeny on 2006-11-24
Next time you start your computer look carefully for a message right at the first few seconds that says something like "To enter setup press DEL" or "For bios press F2" or something similar.
When you see that press the appropriate key and you should enter BIOS setup where you will find a menu somewhere to set the order of the disks for booting.  Set this to CD as first item and HD as second.  Save the settings and you should be able to boot from the CD.  At the moment it is probably set to boot from the HD first.

---

### Post by wpshooter on 2006-11-24
Is your BIOS on the latest & greatest version ???

---

### Post by vr.crawler on 2006-11-24
it is fiked to boot from cd firsth. i have an MSI mainboard on one pc and on the other is Epox. is nothing wrong with the hardware because it actes the same on both.
i have a flash of something that apear and dissapear ... that might be the option , but it is a flash. a damn milisecond !](*,) 
grub makes something wrong here ! 
i know that some time ago i had installed it and didnt acted like this, but now ...this is weird for me too. is just that the boot from cd option is killed by something. :-#

---

### Post by bulldog on 2006-11-24
Yes I can imagine you think so,but GRUB does nothing during boot.
And at this time your boot selection menu should be available by the BIOS.

When GRUB appears on your screen you're booting from the hard drive and you can't select the cd anymore.
So in my opinion GRUB has nothing to do with it.

Is the cd which you want to boot from,in good health?

---

### Post by vr.crawler on 2006-11-24
i tryed with slax, windows and freebsd :-#

---

### Post by bulldog on 2006-11-24
Only when I'm badly wrong on this,it's not something which GRUB courses.

Should think about your cd player or your keybord malfunctioning.

Check your BIOS if there's nothing set wrong,otherwise I don't have a clough.

---

### Post by MJN on 2006-11-24
If it's not already become clear by now, I'll just add that if you're getting as far as GRUB then your BIOS is not booting from your CD despite it being set to do so. Hence, it's not an issue with GRUB/Ubuntu whatsoever. As mentioned above, GRUB resides on the HDD - the BIOS is booting from it as instructed to do so by your BIOS.

Possible causes could be dodgy CD drive (does it work when an OS is loaded?), bad BIOS settings (are you sure you've set them right?) or a bad CD (I couldn't tell if you'd tried different ones but it sounded like maybe you had).

If you're still not convinced that it's not a GRUB/Ubuntu issues then unplug your hard disk - now you know that whatever happens GRUB/Ubuntu is not playing a role. If you can now boot from the CD then you need to check your BIOS as you must have got your boot order wrong.

Mathew

---

### Post by louieb on 2006-11-24
check this out. [http://puppylinux.org/wikka/BootingFromCD](http://puppylinux.org/wikka/BootingFromCD)

---

### Post by djringjr on 2006-12-04
I am having the exact problem.

Here is what I know about my computer - it is a laptop probably manufactured for someone by Compaq - it has a hidden OS2 partition on the hard disk drive.  I suspect (now given this problem) that this computer - and perhaps his - goes to this OS2 partition to retrieve the setup information.  Also if I select "boot from CD" from BIOS, after about 15 seconds, if no CD is present, the computer boots from the HDD.

I do not notice any delay however when the computer bypasses the CD and goes to GRUB and then boots.

Since I have two partitions (one hidden), I might have installed GRUB to the hidden OS2 partition which is the "first" partition.

I plan on using LILO to overwrite GRUB and see what happens.

I've tried two different "Live" CDs, and both will no longer boot even though they happily did so prior to installing GRUB.

Just to let you know that others have this problem and it isn't as simple as making sure that the BIOS is set to boot from CD.

Best wishes to all.

David

---

### Post by kmicic on 2006-12-04
I had the same problem when I put in a USB floppy drive with a non-bootable diskette in it. Seems like a bug in the BIOS in my case - after I removed the diskette, I got the CD to boot.

---

### Post by djringjr on 2006-12-07
I installed Feather Linux (because I don't know how to use many of the commands from command line) and installed the LILO boot program, then it would boot from CD.  As I understand it, GRUB doesn't have an uninstall commmand.  Then I reinstalled using LILO instead of GRUB and everything is fine.  My computer will now boot from CD or from hard drive at my choice.

Best
D

---

### Post by djringjr on 2006-12-19
S U C C E S S   !!!

The above message tells how I was able to correct the problem of GRUB not booting from the inserted CD in my laptop.

I couldn't find anyone who had even had this problem - nor solved it - except here on this forum.

Best Wishes,

David

---

### Post by billgoldberg on 2007-10-29
I have the same problem. Since grub was installed, i can't boot any cd/usb disk anymore.

I only found out about the problem when i removed linux and tried mutliple live cd's to repair vista mbr or install other os.

Since i can't boot into vista (ubuntu is gone) how can i fix this problem?

(ps: the computer is only 3 month old and wasn't cheap).

Question:
would simple replacing the hard drive fix the problem? 
Thus if i were to remove the old hard drive, and install a new one enable me to install an operating sytem from cd? I think so, not 100% sure. And would i need to use another "seagate" hard drive or could i use any other?

I would however prever keeping the old hard drive and all thats on it (including vista oem without back up)

---

### Post by MJN on 2007-10-29
Does you BIOS boot order show CD before HDD?

Mathew

---

### Post by Flare183 on 2007-10-29
change the "boot from CDROM" to the on position in your bios. GRUB has nothing to do with the cdrom drive.

---

### Post by billgoldberg on 2007-10-29
my bios is set to boot from usb disk first, then cd/dvd, then hard disk

I tried multiple linux distros on usb, none work either. 

What is going on with my pc. Could the bios be damaged or something?

---

### Post by MJN on 2007-10-29
Whoaa.. slow down! It's a bit early to jump to conclusions like that!

What happens if you disable booting from the HDD entirely?

Presumably your CD drive does work? Does its light illuminate momentarily during bootup?

Mathew

---

