---
title: "GRUB Error 15: file not found booting 'not lucky'"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2007-11-15
```
 Booting 'trying /grub/stage1 /boot/grub/stage1'

selectfile /grub/stage1 /boot/grub/stage1


GRUB Error 15: file not found 
  Booting 'not lucky'

pause SGD has not succeeded :(
SGD has not succeeded :(

```

Well  (pout pout), I guess I'm just not lucky :(

How can I improve my luck?

I've been running around in the Super Grub Disk menus, but I keep running into Error 15.

Here's what happened when I built this dualboot XP/ubuntu system:

Wanting to build a new HDD, without endangering the old HDD, I copied the old XP system to a 10gb partition I'd created on the newHDD (partitioning and copying were done with GpartedCD). Then I allocated partitions for a new Gutsy install for a dualboot.

I brought up Gutsy liveCD and installed it on the new partitions. No problem, so far.

Then I tried booting off the new HDD, which didn't work, of course. So I booted off the SGD and got this result. 

I'm guessing that I have to replace the MBR and maybe ntldr. 

I'm guessing that I've got to supply some info, like 'flist -l' and so on. But which ones?

---

### Post by bulldog on 2007-11-15
If you can boot the live cd and open a terminal and type the next command```
 sudo fdisk -l
```
copy the output to the forum please.It is a small L not a one!!

---

### Post by bliffle on 2007-11-15
OK, I'll do that and come back in a few minutes.

In the meantime I reseated connectors and booted and XP came up (no BOOT script, just straight into XP) and I was able to verify that the XP is OK. So I allocated that partition and copied the XP over successfully.

I'm guessing that I made poor choices when I allocated the Gutsy partitions, and anyone past NOOBEE status will see it right away. In particular about sizes, 'flags' like 'boot', and 'extended'. I allocated an 'extended' because I don't know what I'm doing so I thought that would be a reasonable experiment for this setup.

So I rebooted with the Gutsy liveCD to look at the partitions, and snapped a print of the Partition editor display:

Back  in a few minutes with that " sudo fdisk -l".

---

### Post by bliffle on 2007-11-15
Here's the 'fdisk':

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000edde0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sda2            1276        1883     4883760   82  Linux swap / Solaris
/dev/sda3            1884        6747    39070080    5  Extended
/dev/sda5            1884        3099     9767488+  83  Linux
/dev/sda6            3100        5531    19535008+  83  Linux
/dev/sda7            5532        6747     9767488+  83  Linux

Disk /dev/sdb: 2029 MB, 2029518848 bytes
129 heads, 32 sectors/track, 960 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         961     1981936    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(967, 128, 32) logical=(960, 31, 32)
```

---

### Post by bulldog on 2007-11-15
Some questions and undestandigs,correct me if I'm wrong please.

You installed ubuntu with just one hdd connected?
sdb is a thumb drive?
No error installing grub at the end of the install?
Which partition is the  /  [root]?
Why are there three linux partitions?
Did you put any data to this partitions,or is it only ubuntu installed?

It seems it cost a fair amount of time before you respond,unfortunatly I don't have time at the moment.

What I would do.
Delete all the partitions in the extended partition.
Create a 10GB partition for  /
Create a partition as big as you like for /home
swap you have allready.

Install ubuntu again and **remove the thumbdrive before you do**
when you come to the partition part choose manual
mount the 10GB as / format ext3 set bootflag enable
mount swap as swap and format as swap
mount the partition for /home as /home and format ext3
proceed with the install

This will be much faster as trouble shooting your problem.
If windows is not detected by grub,we can put it manually in the menu.lst [pm me and I post how,include a link to this topic please]

---

### Post by bliffle on 2007-11-15
> **bulldog said:**
> Some questions and undestandigs,correct me if I'm wrong please.

You installed ubuntu with just one hdd connected?



No. The old HDD containing XP (in a 10g partition) was still in the internal bay so I could copy the XP partition to the newHDD with GpartedCD. The copy seemed to work OK, so I allocated partitions and then re-booted the CDROM with Gutsy liveCD and clicked the "install" option on the Desktop of the liveCD after it had booted. Then I rebooted again with the CD removed and the oldHDD still in place and the newHDD on a USB port. Intercepted BIOS so it would try booting from newHDD. Didn't work, so, still leaving the HDDs alone, put the GRUB CD in and rebooted again to try to use it's boot capabilities to boot newHDD. Didn't work.

That's when I got the GRUB Error 15 and initiated this thread..

Tried Super GRUB Disk, etc., couldn't even boot oldHDD. Pulled off the CD and the USB newHDD and verified that oldHDD would still boot in the original configuration. It was a big relief that oldHDD still booted and ran. 

So I pulled oldHDD and set it aside and mounted newHDD in the primary bay. Tried 'natural' boot with only newHDD installed, but it failed (probably an improperly seated connector) and tried some GRUB stunts but no response. REmoved and reseated newHDD and 'natural' boot came up (proving that my XP cloning had worked and that I had an XP boot MBR on newHDD, which surprised me a little, but I was pleased). So I rebooted with Gutsy liveCD to get ubuntu-type info for more debugging, in particular, the snapshot of newHDD partition data that I posted in my second post at 3:01PM.

> 
sdb is a thumb drive?


Yes, i used it to move debug data from the newHDD to an independent internet machine.

> 
No error installing grub at the end of the install?

The Gutsy install didn't do it, apparently, but didn't say anything.
> 

Which partition is the  /  [root]?


I'm not sure. Maybe sda7
> 
Why are there three linux partitions?

My naivete. I was trying to get a '/' and a '/home'.
> 
Did you put any data to this partitions,or is it only ubuntu installed?

No. Gutsy installed as it saw fit.
> 
It seems it cost a fair amount of time before you respond,unfortunatly I don't have time at the moment.

What I would do.
Delete all the partitions in the extended partition.
Create a 10GB partition for  /
Create a partition as big as you like for /home
swap you have allready.

Install ubuntu again and **remove the thumbdrive before you do**
when you come to the partition part choose manual
mount the 10GB as / format ext3 set bootflag enable
mount swap as swap and format as swap
mount the partition for /home as /home and format ext3
proceed with the install

This will be much faster as trouble shooting your problem.
If windows is not detected by grub,we can put it manually in the menu.lst [pm me and I post how,include a link to this topic please]

Makes sense. I'll do that.

I have a couple other projects I've gotta attend to also.

---

### Post by bliffle on 2007-11-16
Aaaah, how good it is! 

Mucho Gracias to Bulldog.

This T60 is  working, now. With it's very-own Gutsy on the newHDD, as well as the XP. Without resorting to a GRUB CD. The Gutsy liveCD did it all.

So, the immediate problem is solved, but I still haven't successfully ridden the GRUB bronco.

I think my original problem was that I tried to employ 'extended' partitions to avoid using my ration of 4 logical partitions prematurely, so I still have to address that concept.

And I started out trying to build the Gutsy on a USB HDD and then test that system before transfering the HDD from the USB box to the T60 internal bay. Maybe I'll succeed next time.

---

### Post by bulldog on 2007-11-16
> **bliffle said:**
> Aaaah, how good it is! 

Mucho Gracias to Bulldog.

This T60 is  working, now. With it's very-own Gutsy on the newHDD, as well as the XP. Without resorting to a GRUB CD. The Gutsy liveCD did it all.

So, the immediate problem is solved, but I still haven't successfully ridden the GRUB bronco.

I think my original problem was that I tried to employ 'extended' partitions to avoid using my ration of 4 logical partitions prematurely, so I still have to address that concept.

And I started out trying to build the Gutsy on a USB HDD and then test that system before transfering the HDD from the USB box to the T60 internal bay. Maybe I'll succeed next time.

If you use the alternate cd,you have the option to install grub were ever you want.
There should be a button advanced,use it and choose were to intall grub.
This alternate cd is a text based installer,not a live cd.
You can get it from here,check the green box at the bottom of the page.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

All you ever have to know about grub is found here,

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by bliffle on 2007-11-16
Thanks again.

I'll do some further GRUBby reading.

I got the Gutsy alternateCD when it first came out, and have already found it useful for installation followup.

Here's a pic of the resulting Gparted layout. Looks good to me.

---

