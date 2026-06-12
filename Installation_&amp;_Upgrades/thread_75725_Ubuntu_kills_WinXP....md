---
title: "Ubuntu kills WinXP..."
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by elefthera on 2005-10-14
Refurbished PC with 40Gb HD... 

Installed Xp into its own 2Gb partition - fine. Installed Ubuntu 5.10 into remaining free space -  fine. Reboot, and select XP at GRUB --> Blue Screen of Death.

Tried this entire procedure twice - first time with XP on FAT32 and Ubuntu; next with NTFS and Kubuntu. Same result each time. Ubuntu loads like a charm, but XP dies at birth. FWIW...

Ubuntu fdisk (fdisk -l /dev/hda) shows:

Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         255     2048256    7  HPFS/NTFS
/dev/hda2             256        4822    36684427+  83  Linux
/dev/hda3            4823        4865      345397+   5  Extended
/dev/hda5            4823        4865      345366   82  Linux swap / Solaris

XP's boot.ini is:

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

Verbose boot on XP (ie selecting "safe mode") shows it loads about 25 .sys files, then chokes loading "Mup.sys", whatever that might be (Muppet driver?).

Any help would be much appreciated...!

---

### Post by gerrit74 on 2005-10-14
Hello,

I managed the first dual boot install with in winxp partitioning the hard drive
with partition magic. I installed ubuntu and ubuntu workes fine.
I googled my problem in ubuntu and found out that pm deactivates the winxp partition. With the diskettes of pm I turned the winxp partition on(set to active) and now everything works fine(on a laptop hp9110). That's to say:I don't work with xp any more for more than 3 months,ubuntu does the job.

---

### Post by elefthera on 2005-10-14
[QUOTE=gerrit74]...pm deactivates the winxp partition...[/QUOTE]

Nope, the partition is active; but XP crashes during load. 

Any other ideas, anyone?

---

### Post by linuxlizard on 2005-10-14
Unfortunately I don't have any advice for how to recover from your present situation, but I do have some very useful advice for how to avoid it, so that you and others reading this can prevent problems in the future.
This used to happen to me almost every time I tried and installed a new distro- grub would mess up windows and I'd have to go in and fix it after the fact. It got very frustrating to have to go in and fix things afterwards. It never happens any more for the past couple of years because I use GAG now. GAG is free.

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

GAG is a boot manager that installs to the mbr. Or to a floppy. You can test it first on a floppy or run it on a floppy forever, and then with a couple of keypresses install it to your mbr once you know it is set up and working properly. 

With GAG installed, you then install linux and write grub to / (root) rather than to the mbr, and then you tell grub to boot linux from /. 

Writing grub to root is very easy  with ubuntu. When you are partitioning the drive, choose to manually edit the partition, rather than automatic. When you set up your root partition, make boot flag active (it's an option you will see).
Later when the installer is ready to write grub, it will ask you if you want to install grub to the mbr. Choose no, and it will then write it to your root partition. When you reboot, you can then set gag up to boot to your root partition (If ubuntu is on your second hard drive (slave), and nothing else is on there, once you are in GAG press s a 2 b n, name it (add description), skip the password setup, press d for the linux icon, press h and save gag, press r and then your setup and ready to run).

Once in ubuntu if you want you can edit grub so there is zero countdown from  grub to load up, which makes the grub screen vanish from the boot-up process. You can do this graphically from the administration menu before you ubdate ubuntu for the first time, but for some reason the icon for whatever the app is dissapears once you update, along with the boot splash (LOL). You can however still go into a terminal, enter 

sudo gedit /boot/grub/menu.lst 
 
enter your password, scroll down just a tiny bit to the section that looks like this:
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

and change the last line to

timeout		0

That's it, now you will have smooth booting.
Before GAG installing linux for me was always a bit scary because I didn't know what would be involved in getting windows back, and I was always afraid of loosing it forever (I did twice too, when I was a noob to linux). Since GAG installing is no big deal, I just make sure to always put grub on the root partition rather than the mbr. I can't believe a couple years after finding GAG grub is still messing up people's windows partitions.:( It's about time that was fixed. But until then, there's always GAG. Mean linux geeks have given me a hard time about using it, but when I still go to boards and see windows boots dying from grub, I sure am glad I use it. It really makes life safe and simple. It's really easy to set up - a couple of minutes.

That's the end of my commercial, I'll move along. LOL

---

### Post by dohtem on 2005-10-14
[QUOTE=linuxlizard]Unfortunately I don't have any advice for how to recover from your present situation, but I do have some very useful advice for how to avoid it, so that you and others reading this can prevent problems in the future.
This used to happen to me almost every time I tried and installed a new distro- grub would mess up windows and I'd have to go in and fix it after the fact. It got very frustrating to have to go in and fix things afterwards. It never happens any more for the past couple of years because I use GAG now. GAG is free.

[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

GAG is a boot manager that installs to the mbr. Or to a floppy. You can test it first on a floppy or run it on a floppy forever, and then with a couple of keypresses install it to your mbr once you know it is set up and working properly. 

With GAG installed, you then install linux and write grub to / (root) rather than to the mbr, and then you tell grub to boot linux from /. 

Writing grub to root is very easy  with ubuntu. When you are partitioning the drive, choose to manually edit the partition, rather than automatic. When you set up your root partition, make boot flag active (it's an option you will see).
Later when the installer is ready to write grub, it will ask you if you want to install grub to the mbr. Choose no, and it will then write it to your root partition. When you reboot, you can then set gag up to boot to your root partition (If ubuntu is on your second hard drive (slave), and nothing else is on there, once you are in GAG press s a 2 b n, name it (add description), skip the password setup, press d for the linux icon, press h and save gag, press r and then your setup and ready to run).

Once in ubuntu if you want you can edit grub so there is zero countdown from  grub to load up, which makes the grub screen vanish from the boot-up process. You can do this graphically from the administration menu before you ubdate ubuntu for the first time, but for some reason the icon for whatever the app is dissapears once you update, along with the boot splash (LOL). You can however still go into a terminal, enter 

sudo gedit /boot/grub/menu.lst 
 
enter your password, scroll down just a tiny bit to the section that looks like this:
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

and change the last line to

timeout		0

That's it, now you will have smooth booting.
Before GAG installing linux for me was always a bit scary because I didn't know what would be involved in getting windows back, and I was always afraid of loosing it forever (I did twice too, when I was a noob to linux). Since GAG installing is no big deal, I just make sure to always put grub on the root partition rather than the mbr. I can't believe a couple years after finding GAG grub is still messing up people's windows partitions.:( It's about time that was fixed. But until then, there's always GAG. Mean linux geeks have given me a hard time about using it, but when I still go to boards and see windows boots dying from grub, I sure am glad I use it. It really makes life safe and simple. It's really easy to set up - a couple of minutes.

That's the end of my commercial, I'll move along. LOL[/QUOTE]


My problem is not quite like the OPs. (I have the Error 5 during GRUB Stage1.5) but I think your solution might work.  Thanks for sharing, I'll gig GAG a shot when I get home. ;)

---

### Post by Dillius on 2005-10-14
I don't really know how to handle this with a single hard drive either. That's why now I keep Windows XP and my Linux install on seperate drives entirely.

---

### Post by linuxlizard on 2005-10-14
Yeah, GAG is preventive medicine, not a fix for a problem there already. The time to install it is when windows is working fine, *before* you install linux. Sorry can't be more help with problems already occurring, but if you follow my instructions there before things are messed up it will prevent grub screwing up windows.
The best part is you don't have to risk the mbr for windows to try gag out because it can be installed on a floppy to start. So you can just boot from the floppy, enter setup and put your windows on there, save it to floppy and try booting. It will boot but if for some reason it doesn't you haven't touched the mbr on the hard drive yet. If it does boot, then just reboot with the floppy, enter setup and copy it to the mbr of the hard drive and your done.

---

