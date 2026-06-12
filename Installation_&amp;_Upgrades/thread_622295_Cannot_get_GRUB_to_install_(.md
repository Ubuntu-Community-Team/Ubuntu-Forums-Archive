---
title: "Cannot get GRUB to install :("
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by beezm on 2007-11-24
Well I looked around the forums and I did notice that there were a few other topics dealing with this issue, but towards the end of the install, when the grub-install starts to run, it fails and gives me an error about failing to execute grub-install on hd0, well the second time around i tried telling it to install to hda instead, well still no go. ( i didnt think it would)

I am running on the live cd right now as we speak , I was thinking of downloading the alt. cd, but I believe i will still have this problem, I think it is in part due to my goofed up partitions ? Here they are :

```

/dev/hda
   /dev/hda5 - ntfs - /media/hda5
   /dev/hda2 - ntfs - /media/hda2
   /dev/hda3 - fat32 - /media/hda3
/dev/hdb
   /dev/hdb1 - ntfs - /media/hdb1
   /dev/hdb2 - ext3 - / 
   /dev/hdb3 - swap

```

I have windows XP installed already on /hda5 and the others are various backup partitions and such, as well as the fat32 for some different web docs i need to access in ubuntu as well...

Well i try installing to the hdb2 and it seems to format and copy files over fine but then it gets to the grub-install and fails, I'm sure its probably how i have my table set up because the numbering is a little goofed up. But any suggestions on how to install grub and getting it working would be great :D

one more thing , since it failed on just simply installing grub, shouldn't most if not all the files be there ?? when i go to install now instead of my ext3 partition being blank it now is mounted at /media/hdb2  now and says that 2,700 MB is used on it.

---

### Post by Pumalite on 2007-11-24
There is an 'Advanced Tab' in step 8 where you can install Grub wherever you want. I'm still intrigued that you do not have Grub because it should install to sda1 by default. Can you describe the order of your installations and the method you used to install? Do you have a Raid?

---

### Post by beezm on 2007-11-24
I went ahead and did the manual config for the partition tables.... I do have raid capabilities on my motherboard, but I do not have it set up like that, I just have a simple master and slave drive set up on IDE chan 0 and 1...

During step 7 there is an advanced button where you can choose to install grub to it is by default set to " (hd0) "

The first time i left it alone, it failed, then i changed it to (hda) and it failed... now I am thinking I was being stupid ? and i need to put in a full /dev/hda or something similar ?

And as far as order of installation... Windows XP has been installed on hda5 for a good while now, as well as the other partitions, I'm just now today partitioning the aditional 80 or so free GB on my hdb device.

If i reboot my computer right now I just go straight into windows, but I do believe that ubuntu its files are still on my HD ? or not ? Should I completely re-run the install ? or is there a way to just setup and config grub easier without running through that again ?

---

### Post by Pumalite on 2007-11-24
Try Super Grub and see if you can boot Ubuntu: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by ajgreeny on 2007-11-24
Or running the live CD follow the info below to see if it helps at all. though if your windows is on hda5, I'm not sure; I think it should still work.

Boot into the ubuntu live CD
open a terminal and run :
    sudo grub
This gets you to a simple grub command line.
Then:
    find /boot/grub/stage1
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. Replace the question marks in the following command with the output of the this last command :
    root (hd?,?)
[like : root (hdo,1) ,probably]
then:
    setup (hd0)
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.

Good luck!  I hope it helps.

---

### Post by beezm on 2007-11-24
Alright... i tried the super grub, and I couldn't get much to happen with that...


then when I tried to find my stage1 grub thing, it just tells me it cannot be found...

Grub never even started to install i dont think but all of the files for ubuntu definitely did copy over and such...

Any other suggestions ? :(

---

### Post by Pumalite on 2007-11-24
If you couldn't make Super Grub to work; the possibility is there that you have to reinstall.

---

### Post by beezm on 2007-11-24
I'm not worried about having to reinstall it, i just want it to work, loool...

I just tried the install once again, this time using /dev/hda as a parameter on the last step for the advanced tab .... the 'grub-install /dev/hda' that it runs fails, then tells me this was a fatal error and just exits.............

Any suggestions on how to get grub installed ? I am not trying to repair grub, but merely get it installed. Any ideas ??

So I'm guessing the next step is the alt cd, but I am not seeing how that is going to be any different when it comes to the grub-install ,... ????

---

### Post by Pumalite on 2007-11-24
If you can boot a Live CD; post:
sudo fdisk -lu

---

### Post by beezm on 2007-11-24
```


Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xac55b557

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           16065   123427394    61705665    f  W95 Ext'd (LBA)
/dev/hda2   *   123427395   226082744    51327675    7  HPFS/NTFS
/dev/hda3       226082745   234436544     4176900    c  W95 FAT32 (LBA)
/dev/hda5           16128   123427394    61705633+   7  HPFS/NTFS

Disk /dev/hdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c5c0d

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63   167772527    83886232+  55  EZ-Drive
Partition 1 does not end on cylinder boundary.
/dev/hdb2       167782860   207302759    19759950   83  Linux
/dev/hdb3       207302760   211302944     2000092+  82  Linux swap / Solaris



```

per requested :)

---

### Post by Pumalite on 2007-11-24
You have a partition table problem in hdb. Use TestDisk to fix it: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by beezm on 2007-11-24
AHA!

I found my grub directory! I have a mounted partition on my desktop, duh...
its called /target

My ext3 partition is mounted at /target which has a grub folder inside of it.


What should I do from here ? :)


.... EDIT... downloading testdisk as well... i'm going to keep tweaking with this directory o_O

EDIT again...

i really dont think this test disk is what i need, the EZ-drive crap is because of the brand of the drive i have in but it is the slave, so i'm not trying to modify its mbr.. just hda's and i dont need to recover any files or repair any partitions i dont believe.

I am currently attempting to install grub to /dev/hdb2 which is where /target points to.

---

### Post by Pumalite on 2007-11-24
'target' as far as I know appears only in the Live CD while you are installing. And I don't see it in your fdisk -lu.

---

### Post by torgrot on 2007-11-24
That EZdrive could be the problem.  Doesn't your BIOS support LBA addressing?  I haven't seen EZdrive in years.  It was a driver to allow Dos and Windows to overcome bios limitations on the size of a hard drive.  If you can I would probably remove EZDrive.

torgrot

---

### Post by tojam on 2007-11-24
From the looks of things breezm is trying to install ubuntu to hdb and I seem to be having the same problem.

I just jammed the ubuntu 7.10 server install disk in;- set it to install to my second disk hdb and then had grub install itself to hda...  The install seemed to be successfull but when rebooting grub has blown away my windows boot record and also refuses to boot ubuntu.

I'm not sure how to fix this? Any help would be appreciated.

---

### Post by Pumalite on 2007-11-24
Try Super Grub. It can boot Ubuntu: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by meierfra on 2007-11-24
tojam:  Try the supergrub suggestion. But if  it doesn't work out please start your own thread. Trying to solve two cases in one thread leads to confusion.

---

### Post by tojam on 2007-11-24
Thanks for the suggestion, I'll try supergrub... sorry for hijacking the thread, I thought it might have been related to breezm problem

---

