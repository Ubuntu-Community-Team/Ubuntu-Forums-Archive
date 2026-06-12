---
title: "Uninstalling Ubuntu, It's pratically no good with my laptop"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Raderick on 2007-10-30
I have come to the realization that Ubuntu will not work with my laptop, despite all of the help I have received. One it goes through the splash screen, the screen goes back and does nothing until I have to unplug the power cord and then remove the battery, which isn't healthy to it.

So how do I uninstall it?

---

### Post by ldesilva on 2007-10-30
Reboot back to Windows. Delete the partition that was created by Ubuntu. Fix the boot record/MBR using the Windows recovery CD.

---

### Post by Pumalite on 2007-10-30
Just wipe the hard drive with Gparted and restore your Windows MBR

---

### Post by erginemr on 2007-10-30
You may also give a try to PCLinux OS (a KDE based distro), I have tried it on a Toshiba laptop and it performed much better than Ubuntu on it. Besides, it supposedly has WiFi support.

You may download its live CD from [www.pclinuxos.com](www.pclinuxos.com) and try your laptop before the actual installation.

---

### Post by Pumalite on 2007-10-30
I also use LinuxMint and it's excellent. It comes with all the goodies pre installed and is very good on recognizing hardware, so you might want to give it a try too.

---

### Post by Anbog on 2007-10-31
Two questions:

- What if I have just f*ucked up my Ubuntu installation so much I want to overwrite it with a clean install - do I have to delete partition AND fix MBR for Windows first, to avoid confusing the grub bootloader, or would it be enough to kill the Ubuntu partition and install again from the Live CD?

- I dont have a recovery CD for windows, but an standard WinXP Home CD. Will it do the job of fixing the MBR? Are there other options for doing the job?

---

### Post by tact on 2007-10-31
just boot the liveCD and reinstall is enough...  grub wont be confused

when you get to the part where it asks about partitioning your system..  choose "Manual" and then select the existing borked linux partition.... let it format that partition...  be careful not to format the windows partition...  and happy you will be.

if you had a separate partition for /home you dont need to format that.  (unless you also want to get rid of all previous configs and data)

---

### Post by Anbog on 2007-10-31
Thank you! I had been messing around with drivers (ATi card...) and after trying a few guides I ended up without a GUI and no (good) idea what to do. Nice to know I can start over this easily - I'm sure it will come in handy several times as I try to get to know Linux :)

---

### Post by Raderick on 2007-11-07
Could someone explain it step by step for a newbie like me?

---

### Post by erginemr on 2007-11-08
> **Raderick said:**
> Could someone explain it step by step for a newbie like me?

I would strongly suggest you to stick to Linux, even if Ubuntu does not go along well with your laptop. I have used PC Linux OS on a Toshiba laptop for a while, and have witnessed that it performed better than Ubuntu on that machine. 

It is a Live CD, so you can try it out first ([www.pclinuxos.com](www.pclinuxos.com)) Granted it is KDE based, but if you are a Gnome person like me, who does not find the KDE interface to his tastes, then you may try the Gnome version of PC Linux OS, too ([www.linuxgator.org](www.linuxgator.org)).

Finally, you may give a try to Linux Mint ([www.linuxmint.com](www.linuxmint.com)), which is based on Ubuntu.

---

### Post by erginemr on 2007-11-08
If you really really believe you need to go back to the Windows world, then  I would suggest you to use GParted Live CD ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)). You need to do several things with it:

You will need to reformat your ext3 / reiserfs (a format that Linux understands) partition to NTFS / FAT32 (a format that Windows understands). You will also need to do the same for your swap partition (whichis used for temporary memory swapping tasks under Linux). You can use GParted to reformat your Linux partitions. 

GParted will show the format of your Windows drive(s), they can be NTFS or FAT32. You should reformat your Linux to comply with your Windows partitions.

After the repartitioning is over, there is an option in GParted that will allow you to "re-combine" your existing partitions. But that is a very subtle process that can also destroy your Windows partition easily, if you are not careful.

Before attempting this delicate task, boot into Windows and check for any errors in your hard drive(s) first, by right-clicking on each hard drive under My Computer and selecting tools or something. Then do a defragmentation of your hard drive(s), which will gather all data to the first part of your hard drive. And backup any important information in your hard drive to say a CD-R or pen drive (I said it will be dangerous, so you are warned.)

Then, boot into GParted Live CD again and look for an option to combine the existing hard drives. Let the program do its dirty work. Reboot into Windows, which will greet you with errors stating hard drive size has been mis-reported (because you have changed its size). Let Windows do the hard-drive checks as necessary (sometimes more than once), and reboot untill everything works correctly and the combined hard-drive size has been reported correctly under My Computer or Windows Explorer.

...

---

### Post by erginemr on 2007-11-08
Finally, you will need a Windows Setup CD to fix the MBR (master boot record) part of your hard disk, where Grub sits at present. 

Assuming that you are using Windows XP, when you boot up your Windows XP setup disk, there should be an option to boot into the "recovery console". When you see the command line under recovery console, write "fixmbr" (without the quotes), which will supposedly free your MBR from Grub (Linux boot menu) and reinstall Windows boot options.

Finally (and hopefully), you will be all set...

P.S. I can see that this is very complex and exhaustive for a new user. Any better (shorter and easier) method by other forum lurkers are most welcome...

---

### Post by Raderick on 2007-11-11
> **erginemr said:**
> If you really really believe you need to go back to the Windows world, then  I would suggest you to use GParted Live CD ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)). You need to do several things with it:

You will need to reformat your ext3 / reiserfs (a format that Linux understands) partition to NTFS / FAT32 (a format that Windows understands). You will also need to do the same for your swap partition (whichis used for temporary memory swapping tasks under Linux). You can use GParted to reformat your Linux partitions. 

GParted will show the format of your Windows drive(s), they can be NTFS or FAT32. You should reformat your Linux to comply with your Windows partitions.

After the repartitioning is over, there is an option in GParted that will allow you to "re-combine" your existing partitions. But that is a very subtle process that can also destroy your Windows partition easily, if you are not careful.

Before attempting this delicate task, boot into Windows and check for any errors in your hard drive(s) first, by right-clicking on each hard drive under My Computer and selecting tools or something. Then do a defragmentation of your hard drive(s), which will gather all data to the first part of your hard drive. And backup any important information in your hard drive to say a CD-R or pen drive (I said it will be dangerous, so you are warned.)

Then, boot into GParted Live CD again and look for an option to combine the existing hard drives. Let the program do its dirty work. Reboot into Windows, which will greet you with errors stating hard drive size has been mis-reported (because you have changed its size). Let Windows do the hard-drive checks as necessary (sometimes more than once), and reboot untill everything works correctly and the combined hard-drive size has been reported correctly under My Computer or Windows Explorer.

...

I already have Windows Vista alongside Ubuntu on different partitions.

---

### Post by Raderick on 2007-11-11
> **erginemr said:**
> I would strongly suggest you to stick to Linux, even if Ubuntu does not go along well with your laptop. I have used PC Linux OS on a Toshiba laptop for a while, and have witnessed that it performed better than Ubuntu on that machine. 

It is a Live CD, so you can try it out first ([www.pclinuxos.com](www.pclinuxos.com)) Granted it is KDE based, but if you are a Gnome person like me, who does not find the KDE interface to his tastes, then you may try the Gnome version of PC Linux OS, too ([www.linuxgator.org](www.linuxgator.org)).

Finally, you may give a try to Linux Mint ([www.linuxmint.com](www.linuxmint.com)), which is based on Ubuntu.

I don't want to use a LiveCD for Linux (I want it installed on my computer) and I don't want to use Linux as my OS of choice, as I want Vista to be my primary OS, because all of the programs I need is on it, and Linux when I want to fool around with it.

All I want right now is how to get rid of Ubuntu off my computer, step by step, as in Step one, do this. Step two, do this. Step three etc. etc., something like me can get done with ease.

---

### Post by erginemr on 2007-11-11
> **Raderick said:**
> I don't want to use a LiveCD for Linux (I want it installed on my computer) and I don't want to use Linux as my OS of choice, as I want Vista to be my primary OS, because all of the programs I need is on it, and Linux when I want to fool around with it.

All I want right now is how to get rid of Ubuntu off my computer, step by step, as in Step one, do this. Step two, do this. Step three etc. etc., something like me can get done with ease.

To your first question, PC Linux OS is not a Live CD only. You can install it on top of the Ubuntu partitions by letting it reformat them, and I strongly recommend trying it.

To your second question, unfortunately there is no simple guide to uninstall Ubuntu step 1 do this, step 2 do that. It is a quite complicated and exhaustive task, which you need to venture first and find your own way through it. There may be other ways, by my way (that it, if I wanted to remove Ubuntu from my computer) requires the use of GParted as a Live / Rescue CD, whose steps I already explained before. 

As I said, it is not a simple task, you have to take the first step, boot into GParted and fiddle with the settings in trying to reformat Linux drives (main and swap partitions) and combine them with your partition which houses Vista.

---

### Post by erginemr on 2007-11-11
I have found the following link that explains ways of uninstalling Ubuntu in detail:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

---

