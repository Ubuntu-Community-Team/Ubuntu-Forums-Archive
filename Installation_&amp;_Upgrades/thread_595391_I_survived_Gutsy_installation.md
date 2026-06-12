---
title: "I survived Gutsy installation"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by megahertz on 2007-10-28
I have my Windows OS on a 80G HD as master on the fist EIDE controller so I added an old 40G HD as slave and installed Ubuntu on this drive, to make it totally independent from the Windows HD.
I'd downloaded Ubuntu 7.10 (Gutsy) when it was launched, and for my surprise, I had many problems to install it.
First, on my wife's computer it didn't boot with the live CD (well, in fact it did by choosing the “Install with driver update CD” option and using the live 7.10 CD).
To install Gutsy on my computer, for safety, the first thing I did was to unplug the flat cable from IDE 1 master (Windows OS). As the HD in IDE 1 slave is configured as “cable select”, BIOS recognized as no HD IDE 1 master and one HD on IDE 1 slave.
To install Ubuntu 7.10 (Gutsy) I booted with the live CD and made the default install (IDE 1 slave (hdb) - partition 1 of IDE 1 slave as Ext3 and partition 5 of IDE 1 slave as Swap).
After installing, Gutsy didn't boot.
For some reason, the HD wasn't even recognized by BIOS. I used a Western Digital Utility's disk to low level partition and format the HD (fat32).
Once again I installed Gutsy with the live CD but I changed the boot loader (advanced tab) to hd1 and once again after installing, Gutsy didn't boot. Once more I had to use Western Digital Utility's disk to low level partition and format the HD (fat32).
My third attempt on installing Gutsy was to install Feisty (same procedure: no HD on IDE 1 master and a HD on IDE 1 slave) and then make an upgrade to Gutsy.
After some crashes booting after Feisty installation, I've updated the system and after a reboot, Feisty was running fine. It was ready to upgrade to Gutsy.
After 5 hours downloading, update crashed during installation. At that moment it was almost 2 o'clock in the morning and after 14 hours I couldn't have a simple task of installing a OS done.
Next morning I've decided to change the way to install Gutsy. As the problem seemed to be that I was trying to install Gutsy on IDE 1 slave HD without IDE 1 master HD, I plugged in an old damaged HD as IDE 1 master.
I booted with the live CD and choose to install on IDE 1 slave (hdb) - partition 1 of IDE 1 slave as Ext3 and partition 5 of IDE 1 slave as Swap and I changed the boot loader (advanced tab) to hd1.
At this time time it began a boot (yeeeeesss), but I was presented with Error 15: File not found. Hitting Esc on boot brings Grub options, and witch ever I choose the answer was  Error 15: File not found. 
I booted with the live CD and everything on my HD was where it should. So, witch file was missing?
After some research on internet I found some documentation on Grub (boot loader) that was very helpful.
- First was to find how Gutsy was looking my Hd's.
Using terminal:
sudo fdisk -l
Disk /dev/hda: 40.0 GB, 40020664320 bytes

255 heads, 63 sectors/track, 4865 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x057b3228



   Device Boot      Start         End      Blocks   Id  System

/dev/hda1   *           1        9729    78148161    b  W95 FAT32
 *(hda1 means HD master, partition 1)


Disk /dev/hdb: 40.0 GB, 40020664320 bytes

255 heads, 63 sectors/track, 4865 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x00075cf8



   Device Boot      Start         End      Blocks   Id  System

/dev/hdb1   *           1        4678    37576003+  83  Linux
   *(hdb1 means HD slave, partition 1)
/dev/hdb2            4679        4865     1502077+   5  Extended

/dev/hdb5            4679        4865     1502046   82  Linux swap / Solaris


- Second was to find where Grub was installed
sudo grub (to enter the grub program)
To find where Grub was installed
grub> find /boot/grub/stage1

 (hd1,0)
 * (hd1,0 is = hdb1 and means HD slave, partition 1)
grub>quit (to quit he grub program)

- Third was to find how was grub instructing to boot (file grub menu file  /boot/grub/menu.lst
)
Using terminal:
 gksu gedit /boot/grub/menu.lst
 ( opens the file /boot/grub/menu.lst
 in gedit)
* at the very end you find the grub boot menu

title		Ubuntu 7.10, kernel 2.6.22-14-generic

root		(hd1,0)

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9593f956-5cd8-4c9c-bb6d-6b049ae6ab98 ro quiet splash

initrd		/boot/initrd.img-2.6.22-14-generic

quiet



title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)

root		(hd1,0)

kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=9593f956-5cd8-4c9c-bb6d-6b049ae6ab98 ro single

initrd		/boot/initrd.img-2.6.22-14-generic



title		Ubuntu 7.10, memtest86+

root		(hd1,0)

kernel		/boot/memtest86+.bin

quiet


Resuming:
- Linux is installed on /dev/hdb1 (HD slave, partition 1)
- /boot/grub/stage1
 is on  (hd1,0)
 * (hd1,0 is = hdb1 and means HD slave, partition 1)
- Grub menu point's to root on  (hd1,0)
 * (hd1,0 is = hdb1 and means HD slave, partition 1)

At this point you have the classic “Everything is all right but nothing works”

At this point I was almost giving up when I remembered that all menu options gave the same  Error 15: File not found and /boot/grub/menu.lst
 has in common on the three options (hd1,0)
So I tried to edit /boot/grub/menu.lst and replace (hd1,0) by (hd0,0) and for my surprise, it worked. Remember that (hd0,0) is my Windows HD.
I would appreciate if someone could explain what is going on.
Ubuntu is a great Linux OS, but to be used by ordinary users, for those who never typed a command line, it will take a long, long way.
Hope my experience can help someone.

---

### Post by Snaglpuss on 2007-10-30
I'm going to add to this as i cannot necessarily reply to his exact problem but mine occurred when i had done all my updates from feisty with all working fine 
[B]my config was Intel p3 512 with 
256 mb ram 20 gig[/B]

the issue with feisty is the partition manager would not run the install correctly off the cd from a blank drive because the install would lock up after a period of time what i found was if i added 128 more and brought it to 384 meg of ram the install from the cd worked fine for feisty. then i was able to take the extra ram out and the machine worked fine in a runtime mode from then on.

 now not thinking the necessity of this extra ram would be a factor i installed the online upgrade from feisty to gutsy. and this occurred as it was running through the gui checkmarks of the installation process it got to a point where it downloaded it and was installing i saw a term window open up saw a script executing and some where along that way it crashed hard. locking up the entire computer. all that was left to do was reboot, which brought me to a blue background with a cursor and no interface. waiting i noticed it was seized so i started the grub recovery mode and had 5 boots to choose from:

[COLOR="Red"]generic
generic ..16 most likely gutsy 
generic recovery ....16
generic
generic recovery .....15 most likely feisty[/COLOR] 

chose pretty much each and found it would load to a point then crash with no choices in recovery...

the error was **"command-not-found has crashed"** yada yada with a command prompt from bash*
no matter what i entered at the time there was no change in the state

reading one like forum on this site i found a suggestion of :
[COLOR="Red"]Try doing a combination of:

'sudo apt-get -f install'

'sudo dpkg --configure -a'

'sudo apt-get upgrade'[/COLOR]


well the first command gave me another error but it was intelligble it saind somethig was void of data and gave me a specific command:
[COLOR="Red"]dpkg: error processing  (dpkg --configure -a) and something else:
E:cache open ()failed . please report
[/COLOR]
to enter and it continued installing 
ok granted it was from a CLI but it kept going

and died again this time at BTdownload 

well before i rebooted i looked inside the machine to see the** processor fan** not having been turned on by the os????? **[COLOR="Red"]whats with that!!!![/COLOR]**  didn't you guys fix this???? (this was an issue with feisty) **you have to leave this thing running before you do an install!!!!!!!!**  get with the program! CLI or not

even tho the machine crashed again on the last successive boot up the machine reloaded to logon point and then was manageable as far as errors, use of internet etc hmm wondered if it cleaned itself up .. never saw that happen

survived with my data intact.. i really just feel luck is all that i didnt have to spend a week down having to figure this out...
:KS
wish list:

an ubuntu cd that can be manipulated to finish installs or upgrades that fail via GUI

a page showing the least install memory necessary to install from a cd or configuration of which flavor will work in what evironments my experience,:

ubuntu main: 384 to load from cd 256 to run well  :: may need that 384 to run the upgrade package via online install a warning should be placed in the package checker or a plan to run the entire install from CLI


xbuntu    : 256 to install from cd but 128 to run well

a manual upgrade cd .

---

