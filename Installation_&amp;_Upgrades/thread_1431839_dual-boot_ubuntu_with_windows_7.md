---
title: "dual-boot ubuntu with windows 7"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by mimoza on 2010-03-17
I want to have both installed ubuntu (which I have now) and windows 7.

Right now I have 3 partitons: linux filesystem (where ubuntu is), linux swap and one big, unused ntfs partition wher I want to put windows.

1. I need some help with installing windows without some big mess with primary boot OS and mbr/grub.

2. My first occured problem is booting windows 7 boot cd. It just won't boot. I have via bios put that first boot device is CDROM. And the boot cd is in there.
It has got autorun.exe, which, when I start it with wine, has some error just at the beginning so the installation won't start. Help?

---

### Post by ndefontenay on 2010-03-17
Windows is highly intolerant of over OS on the same computer. It will wipe your Ubuntu installation if you install windows after Ubuntu.

Make sure to do all the backup you need before you try anything.

---

### Post by mimoza on 2010-03-17
I have recently created an image of my ubuntu (with acronis). If windows remove my ubuntu I will just re-install ubuntu from image.

---

### Post by mimoza on 2010-03-17
...

---

### Post by YannBuntu on 2010-03-17
> **mimoza said:**
> 2. My first occured problem is booting windows 7 boot cd. It just won't boot. I have via bios put that first boot device is CDROM. And the boot cd is in there.

From here you have to restart your computer, it should boot on the CD.

Don't try to open the .exe with wine, it is useless.

---

### Post by mimoza on 2010-03-17
I tried that. First time, it just does nothing for a second and then boots ubuntu. Second time, it right away loaded ubuntu in safe mode like root. (?)

---

### Post by srs5694 on 2010-03-17
> **ndefontenay said:**
> Windows is highly intolerant of over OS on the same computer. It will wipe your Ubuntu installation if you install windows after Ubuntu.

That's overly pessimistic, IMHO. Windows will overwrite the *boot loader,* but that's far from wiping the whole installation. It may also be easy to select options to have Windows use the whole disk (which really would wipe out anything else), but my memory of the Windows installer is foggy enough that I'm not sure how easy it would be to mistakenly select such an option. I'm 100% positive that it's possible to install Windows without doing this, though, since I've done it myself several times. Most recently, I re-installed Vista on a disk with at least one other OS on it (and a total of five other OS installations on the computer as a whole), with no problems other than having to re-install GRUB when I was done.

A disclaimer: I've also seen some Windows restore CDs for Windows on pre-installed systems that are different from normal retail Windows CDs. It's conceivable that some of these present fewer options and might make it harder to install without damaging other OSes.

[quote=mimoza]2. My first occured problem is booting windows 7 boot cd. It just won't boot. I have via bios put that first boot device is CDROM. And the boot cd is in there.[/quote]

The Windows installers seem to have a check that's supposed to tell if Windows is already installed. I don't know precisely what it checks for -- valid partitions, a bootable partition, an NTFS partition, key Windows files, etc. In any event, if the installer thinks Windows is installed, it presents a prompt that asks you to press a key to boot from the CD. If you don't press a key within a certain period, the CD redirects the boot process to the hard disk. It's possible that your installer is doing this and you've simply not noticed the prompt (it's only on-screen for a few seconds). Therefore, I recommend you try again, but keep an eye out for such a prompt. IIRC, it appears near the bottom of the screen.

---

### Post by _h_ on 2010-03-17
This guide might help you out:

[http://ubuntuforums.org/showthread.php?t=1035999](http://ubuntuforums.org/showthread.php?t=1035999)

---

### Post by piyushchandrakar on 2010-03-17
After Reinstalling windows how 2 boot ubuntu i.e installed via Wubi perviously on win
I love UBUNTU....i dont wanna lose it...
i Need Help
After Reinstalling windows how 2 boot ubuntu i.e installed via Wubi perviously on windows 7.

I am running Ubuntu 9.10 on my Laptop, where it installed via Wubi on Windows 7.

[windows 7 (Cand ubuntu on the different drive(U(NTFS)*its not a dual boot as installed via wubi].

For some reason My Windows needs a reinstall but in this case i think i will also lost ubuntu because its installed via Wubi.

Part 1 -
****I need to back up all the data that is installed in ubuntu i.e. SMplayer,Graphical GTK theme,Compiz,Emerald. and its setting,means the whole ubuntu system. So that after installing windows and ubuntu as a dual boot (not wubi again)i do not need to configure and install the whole ubuntu data/software again. Its pain for me to downlad again and again the data for ubuntu [Coz low speed connection ]

Part 2 -
****if it is possible that after Reinstalling windows i can boot into ubuntu that is previously installed via Wubi on different drive that please tell me, how could i do that.
****if it is not possible than please show me the way to do backup all the data,software,plugin that is downloaded.etc.

I need to back up the whole Ubuntu because after installing windows i am goin 2 format the ubuntu drive and make it to Ext4 that is currently NTFS and then i will install the Fresh 9.10 on that.

---

### Post by Tom.Gee on 2010-03-17
> **mimoza said:**
> I have recently created an image of my ubuntu (with acronis). If windows remove my ubuntu I will just re-install ubuntu from image.

As a general rule, I tend to create my OS partitions on a stand alone hard drive, then use a utility like acronis (Partition Magic in the past) to move and resize the partition onto the destination drive.  Since you have Acronis already, this circumvents the whole "I'm a bully and want your whole drive" scenario.  Although Acronis comes with a partition boot manager, I prefer OSL2000 for that job.  OSL2000 will even allow you to boot the OS residing on a second or third harddrive, and they claim, (I've not ever needed to try this) an OS on a logical partition.

---

### Post by vader95 on 2010-03-17
Also, if you install Grub on a computer with windows 7 or vista, there will be an error when you go to install a new service pack, it will need ubuntu's boot flag disabled or something like that.  Well, that is what happens with GRUB legacy.

---

