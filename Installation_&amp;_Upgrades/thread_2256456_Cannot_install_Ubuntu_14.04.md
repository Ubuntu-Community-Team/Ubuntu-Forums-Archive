---
title: "Cannot install Ubuntu 14.04"
date: 2014-12-12
forum: Installation &amp; Upgrades
---

### Post by avhation2 on 2014-12-12
My set up is: Dual boot Win XP and Ubuntu, 2 hard drives (one for data, one for operating systems), bags of htz, RAM and space on discs but unsure of partition sizes. spaces.
Problem: Ubuntu was only partially accepting updates, then GRUB stopped working  - keyboard would sometimes not work so could not choose which OS to use. 
Solutions tried: Used Shift during start up to get GRUB to work sometimes. Used Recovery mode to reload apps - took a long time but did not help.  Decided to make a new installation of 14.04 from DVD. Chose default options when loading, hoping not to lose the Win XP installation and expecting 14.04 to sit alongside earlier versions of Ubuntu.  After several hours no progress beyond spinning cursor.  If I knew how, I would delete all Ubuntu packages, format former Ubuntu partitiions and start again.
Any advice please?

P.S. This is a screenshot of the disc set up:
[COLOR=white][/COLOR]
 
Conversation opened. 2 messages. All messages read.







[TABLE="class: ae6"]
[TR]
[TD="class: aBC"][COLOR=white]
[/COLOR]

 






[TABLE="class: ae6"]
[TR]
[TD="class: aBC"][/TD]
[/TR]
[/TABLE]


[TABLE="class: Bs nH iY"]
[TR]
[TD="class: Bu yM"][/TD]
[TD="class: Bu y3"][/TD]
[/TR]
[/TABLE]














crhot from 2014-12-12 19:38:59.png




[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=bab7e8b2be&view=fimg&th=14a400973f66cb2a&attid=0.1&disp=inline&realattid=f_i3lysfer0&safe=1&attbid=ANGjdJ9tY4ierHie0pvc_tPo_B1VW2CzbD9bYGH44bJ165JnVIMekJ9XGwKuliTn7ilm5dDRNs0M4HDU02xBMogdntaF4gn3NhT92Na4D72iqwSsrgUKwVyIEh9ysjE&sz=w1600&ats=1418422268824&rm=14a400973f66cb2a&zw[/IMG]
[IMG]https://mail.google.com/mail/u/0/?ui=2&ik=bab7e8b2be&view=fimg&th=14a400973f66cb2a&attid=0.1&disp=inline&realattid=f_i3lysfer0&safe=1&attbid=ANGjdJ9tY4ierHie0pvc_tPo_B1VW2CzbD9bYGH44bJ165JnVIMekJ9XGwKuliTn7ilm5dDRNs0M4HDU02xBMogdntaF4gn3NhT92Na4D72iqwSsrgUKwVyIEh9ysjE&sz=s0-l75&ats=1418422268824&rm=14a400973f66cb2a&zw[/IMG]






Zoom in

[/TD]
[/TR]
[/TABLE]


[TABLE="class: Bs nH iY"]
[TR]
[TD="class: Bu yM"][/TD]
[TD="class: Bu y3"][/TD]
[/TR]
[/TABLE]

















Zoom in

---

### Post by ajgreeny on 2014-12-12
Your screenshot did not work, or at least, I do not see it, so it's difficult to know what you are trying to show us.

---

### Post by avhation2 on 2014-12-13
Is this any better (see below)?
Additional info: the Grub appears to be 2.02 Beta2 Ubuntu9 I think.
Most times when starting I cannot use the arrows to choose between Ubuntu and WinXP.
Late last night I happened to get the option to choose an earlier version of Ubuntu which worked OK. Curiously, when I looked for system details it said that it was running 14.04.  Now I cannot get past Grub.
If I let the system choose WinXP and countdown it sometimes starts OK, even though I cannot move the cursor.
Not sure how this might help if at all.
The system works fine with the DVD copy of 14.04.  Perhaps I need to reload or update Grub in some way before worrying about cleaning off old versions of Ubuntu??

Regards,
Avhation
[IMG]https://gm1.ggpht.com/rgs19duTBnk1L1QZ5Qm8jTHgOp_TLEIWVlgQb53Il09P6AmBMtvMouDxQsP0S8Vx3GvIUUdH1SMtS24YYQvAluUfcLiLWyPaQiNJEzoXnvvzOI3e6I_LvXNuGzRo6pZ1MWikd53wuMqsEdb5FVlyO7RMImLMredEEOvh-WKsY1d-cheyiUfiufBM3a60Y8j9qf4wif3viGbr0-tkiL6cnamGVHTTDR_VZmNlnhYd-NCLYHRaudQQTHe3MUwhBXKSjMWWyycQVBvK7afVANb7FKX5-96GjHDovt_b2A9j57IhYyqjYmzrM7hrNWw4IGKX_RhLoVkFx9AZkGUWvrAdIPrJ5HPKca7Jo6gkgvWT9u_daARbTQ0E4IMNlhppbBlw3xg6ddrakcxCK3yXJ_sIM4-DR2YLhxURzrym7bPrg8lZ5h3CYn11zQhEgfkxZmSw3ia9EWhHgeuSpdhBmViq2TWVfpwnNRYJYfWR19Uo37z1qp2WDstsWDQvmpgzuIzYzwi8rItU1fBUeuHGDbww27OuKkPAAXEOVLC3nfnN-sYErtZP99pHJ5Y6b0kH3hOivE-IPBY=w1600-l75-ft[/IMG]

---

### Post by fantab on 2014-12-13
Lets try re-installing grub using the Live Ubuntu DVD. Follow [this simple tutorial]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd").
or if you can boot into your installed copy of Ubuntu then from terminal run the following:
```
sudo dpkg-reconfigure grub-pc
```

If re-installing grub doesn't help then re-installing Ubuntu may be simpler and time saving.

Since you are using Windows Xp, I must ask how old is your PC?

If you want to us to take a look at your partitions then post the output of the following:
```
sudo parted -l
sudo fdisk -l
sudo df -h
```

Run the third, 'df-h', command if you have booted ubuntu from the HDD.

---

### Post by sudodus on 2014-12-13
Windows XP has passed end of life and does not receive security updates. Use it only locally if you need it for certain peripheral devices. Never connect XP to the internet !!!

Do you want to create a dual boot system with Ubuntu and Windows XP? If the computer is old, it might be better to use a flavour of Ubuntu with a lighter foot-print,

- Xubuntu - medium light
- Lubuntu - ultra light
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

See also this link: [Old hardware brought back to life]("http://ubuntuforums.org/showthread.php?t=2130640")

And then, when you install, select ***Something else*** at the partitioning window. (It is safest method.)

-o-

It is often easier to re-install than to repair a failed installation. If the installation seems good, but there are stiil problems, you may have problems some some driver for hardware, typically the graphics chip or wifi chip. It makes it much easier to give relevant advice, if you specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

---

### Post by AVHATION on 2014-12-14
Hi Fantab and Sudodus,
Thanks for these pointers.  I like the idea of re-installing grub. Snag is that I can only run Ubuntu from the DVD so when trying via Terminal sudo reconfigure etc and fdisk and parted I get rejection messages. I don't have the option to re-install 14.04 - see my first post above. I am tempted by the "something else" option but am totally unsure which partition of the 2 shown above, revealed by Gparted, I should choose - advice welcome. Currently Win XP is working and I don't want to lose it! All my data is on a separate disk so hopefully not at risk.
The PC is a Dell Workstation 380 with 4gb RAM, 2 x pentium4. The wifi and graphics work fine when using the DVD version of 14.04 so I presume they are sufficiently modern. I will look up the specs via Aida32 at the next opportunity.
Regards,
Henry

---

### Post by Mark Phelps on 2014-12-14
> Currently Win XP is working and I don't want to lose it!

In that case, be sure NOT to choose any option to "replace" the current Ubuntu install.  Unfortunately, the Replace option in the Ubuntu installer completely reformats the entire drive, effectively erasing what's there.  This option would remove the XP partitions.

---

### Post by fantab on 2014-12-15
Boot Ubuntu from DVD, open Terminal, run the following and post the output here:
```
sudo parted -l
sudo fdisk -l
```

Since we cannot see your screenshots in the first post... I can't tell what exactly is going on.

'Something Else' is always a good and safer option to choose. Lets look at your present partitions.

---

### Post by AVHATION on 2014-12-15
Thanks Fantab.



I have done as you asked and I have copied the reult below:
(Substituted an l for the 1 that I was using and got a better result!)

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST3250318AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  174GB  174GB   primary   ntfs         boot
 2      174GB   250GB  76.4GB  extended               lba
 5      174GB   250GB  76.4GB  logical   fat32


dModel: SONY DVD RW DRU-830A (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      131kB  4140MB  4140MB  primary               boot, hidden


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcd80cd80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   339100019   169549978+   7  HPFS/NTFS/exFAT
/dev/sda2       339100020   488279609    74589795    f  W95 Ext'd (LBA)
/dev/sda5       339100083   488279609    74589763+   b  W95 FAT32
ubuntu@ubuntu:~$ 

Fingers crossed that you can identify where I should insert grub or a new installation without losing WinXP
Regards,
Henry

---

### Post by fantab on 2014-12-16
You have not made a linux partition nor have you left any 'unallocated' space for Ubuntu Install.
Since we want to use 'Something Else' option, lets partition the HDD for Ubuntu:

With Ubuntu booted from a DVD, open Gparted and Delete your third FAT32 partition which is numbered as /dev/sda5. Apply changes.
Now create a new partition of 72Gb and format it with 'EXT4 journaling system'. Make another paritition, about 4Gb and use it as 'linux_Swap'.

Install Ubuntu from desktop. At the "Installation Type' dialog, choose the 'Something Else' option.
Select your 72Gb Ext4 parittion and hit 'Change', set up the partition with following parameters:
Use As = Ext4 journaling system
Mountpoint = /
format = yes.

Apply changes... continue with the Ubuntu install. (Before you continue, at the bottom of the 'Installation Type' dialog, you'll set the location for boot-loader grub install, the default will be /dev/sda. That is where grub should be, so just leave it.)


[Gparted Tutorial]("http://www.dedoimedo.com/computers/gparted.html").

---

### Post by AVHATION on 2014-12-17
Thanks again Fantab. I followed your instructions OK.
First the good news - Ubuntu 14.04 comes up as the first option in Grub, the countdown proceeds from apprx 10 secs and then Ubuntu launches and works.
There are 2 bits of bad news.  First, my data HDD is not listed under the Files button, and secondly the keyboard which is not a USB one, cannot be used to control Grub and thus launch WinXP.
Is this something you can help me with, or should I choose another part of the forum please?
Regards,
Henry

---

### Post by AVHATION on 2014-12-19
Faced with a non-functioning keyboard via which to look at the BIOS and Boot settings, I unplugged the mains and USB printer, pressed power button for 20 secs, reconnected power (but not USB connectors) and can now view BIOS and select from Grub the OS I require (14.04 or WinXP).  The reason for the data HDD not showing up is that it is not as I thought a separate HDD so probably  I have inadvertantly over-written all my data files with Ubuntu which was a mistake.  Hopefully the HDD that contained  the data until 2013 can be used to restore most of the data, if I connect it via USB.

---

### Post by fantab on 2014-12-19
You don't have a second HDD according to the 'parted -l' you posted earlier:
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST3250318AS (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      32.3kB  174GB  174GB   primary   ntfs         boot
 2      174GB   250GB  76.4GB  extended               lba
 **5      174GB   250GB  76.4GB  logical   fat32**
```

If fat32 partition was the partition you are talking about then its gone... perhaps I should have warned you. My bad.
If you have lost any important data and want to recover it then boot from Ubuntu DVD and install [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") and [photorec]("http://www.cgsecurity.org/wiki/PhotoRec"), read their respective documentations for detailed info, to recover whatever you can.
100% data recovery may not be possible. There are other tools you can use.

---

