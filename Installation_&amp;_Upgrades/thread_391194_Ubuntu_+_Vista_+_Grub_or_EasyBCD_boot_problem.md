---
title: "Ubuntu + Vista + Grub or EasyBCD boot problem"
date: 2007-03-22
forum: Installation &amp; Upgrades
---

### Post by gideonidoru on 2007-03-22
First: Thanks for taking the time to read this rather long post and any help you can provide... 

Hi! I recently wanted to get back into linux and tried installing Ubuntu with an existing Vista installation. However no matter how hard I try or what guide I follow (apcstart.com /etc) I can't get Vista to boot with Grub, or Ubuntu 6.10 with EasyBCD... let me break down my setup...

First I have two hard drives, both WDC... one is 200gb the other is 500gb

/dev/sda is my 200gb it has two partitions, Vista is on 0
/dev/sdb is my 500gb it has three partitions, 0 is backup (232gb) 1 is Ubuntu (230gb) 2 is swap (2gb)

First I tried installing grub onto hd0 (sda) via the standard installation, it detects vista and uses the makeactive/chainloader +1 but when I try and boot it it just restarts my computer..

Ok, so then I tried installing it on Ubuntu partition, in this case (hd1,5) or /dev/sdb6.. and using EasyBCD via Vista... again whenever I selected Ubuntu via the boot menu, my PC just restarts..

Here is a breakdown of all my partitions as read through the "Computer Management" snap-in in Vista.
sda 
----partition 1 - 117.18gb NTFS primary, (Vista) flags: System, Boot
----partition 2 - 69.13gb NTFS logical

sdb
----partition 1 - 232.88gb NTFS logical
----partition 2 - 230.92gb ext3 primary, (Ubuntu) no flags 
----partition 3 - 1.95gb swap primary

Currently my MBR is set with Vista's bootmgr, i wouldnt mind keeping this and using EasyBCD however if I have to use grub that wouldnt be heartbreaking.

Again, thanks for taking the time to read this... any help you guys can provide would be greatly appreciated..

---

### Post by zvacet on 2007-03-23
[http://ubuntuforums.org/showthread.php?t=371530&highlight=vista]("http://ubuntuforums.org/showthread.php?t=371530&highlight=vista")

---

### Post by gideonidoru on 2007-03-23
Hi that's basically the exact same guide as the one on apcstart.com minus screenshots. I've followed this guide and it did not solve the problem, grub detects Vista without a problem (which is the purpose of that guide) but as I said, one will not boot the other.. it just reboots

---

### Post by lvleph on 2007-03-23
I know this is not a solution to your problem, but it may tell you if there is something wrong with vista. Try going into Bios and changing your boot preference, so that the Vista Drive is the 1st boot device. If it doesn't want to boot, I would say there may be a problem. However, if your boot.ini (or whatever the boot file is for windows) doesn't exist on that drive any longer then trying to boot to that drive won't work.

---

### Post by gideonidoru on 2007-03-23
Hi, thanks for the reply

There isn't a problem with Vista, because when the bootmgr on sda is set to Vista, vista boots fine, however when it's grub on sda, linux boots fine, but whenever one tries to boot the other the PC just reboots :/

---

### Post by lvleph on 2007-03-23
I am not on my Ubuntu\Vista comp right now, so I don't think I would be of much help until I go home. However, I am only using one HD so... I will post my grub when I get home.

---

### Post by gideonidoru on 2007-03-24
i hate to be a bumper, but id love to boot ubuntu

---

### Post by ssican on 2007-03-24
For just, more information, about Dual Boot, see is link: [http://doc.ubuntu.com/ubuntu/switching/C/dualboot-custom.html](http://doc.ubuntu.com/ubuntu/switching/C/dualboot-custom.html)

---

### Post by ssican on 2007-03-24
If ou see the screen of the GrubMenu on Boot, only press ESC (when the screen of the GrubMenu appear,show up) and GrubMenu  stay on the screen. 
Try to use the arrow to select Ubuntu, and press ENTER
For just to exit of the GrubMenu press ESC

---

### Post by gideonidoru on 2007-03-24
> **ssican said:**
> For just, more information, about Dual Boot, see is link: [http://doc.ubuntu.com/ubuntu/switching/C/dualboot-custom.html](http://doc.ubuntu.com/ubuntu/switching/C/dualboot-custom.html)

Again this is for changing the grub menu..

I think my problem is much more complex, it may lie in my partition tables which is why I provided so much information, and stated all the steps I went through.... 

I tried all the generic guides and none of them seem to work, this is a strange problem because as I said, each can boot they just wont boot each other... (grub for vista, vista for linux)

I've tried pressing 'c' on the grub menu and manually editing the commands... again this did not work

---

### Post by gideonidoru on 2007-03-24
Does anyone think it has anything to do with Ubuntu being partitions #2 and #3 behind a logical partition on disk 2?

---

### Post by gideonidoru on 2007-03-24
I found this on another website, im not at home and am unable to try it at this time but was hoping to get some feedback, specifically if the map command will make a difference

[http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux](http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux)

 Configure GRUB

GRUB is what boots Linux for you. In order to get it to boot to the 2nd drive to let you access Windows as well, edit your grub config (typically /boot/grub/grub.conf) and add this after your Linux boot information:

# Windows Vista
title=Windows Vista
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

---

### Post by confused57 on 2007-03-24
> **gideonidoru said:**
> I found this on another website, im not at home and am unable to try it at this time but was hoping to get some feedback, specifically if the map command will make a difference

[http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux](http://wiki.gtwy.net/index.php/Dual_Boot_Vista_and_Linux)

 Configure GRUB

GRUB is what boots Linux for you. In order to get it to boot to the 2nd drive to let you access Windows as well, edit your grub config (typically /boot/grub/grub.conf) and add this after your Linux boot information:

# Windows Vista
title=Windows Vista
rootnoverify (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
chainloader +1

This entry would work, if you're booting first to your sdb drive; however, you'd need grub installed to sdb mbr.
Grub could be installed to sdb mbr(if it isn't already), using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Of course, if you boot first to sdb, grub would recognize it as your (hd0) drive & you'd need to reconfigure grub to reflect this change.  If you decide to do this, and get a grub menu at bootup to sdb, highlight your grub entry, press "e" to edit, then change root from (hd1,x) to (hd0,x), then press "b" to boot.  This change is temporary, but you can determine if it'll work or not...it can be made permanent in your /boot/grub/menu.lst, if you prefer to set your system up this way.  See the 3rd link in my signature for how I have my system set up.

There is one other grub entry you'd need to change, if you set your system up as I've described:
# groot=(hd1,x)
to
# groot=(hd0,x)
See this guide:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

### Post by ssican on 2007-03-24
Another option, for just get access temporal, transitory, to Ubuntu,  migth to be used -SGD-Super Grub Disk: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)   screenshots on: [http://linux.softpedia.com/progScreenshots/Super-Grub-Disk-Screenshot-8071.html](http://linux.softpedia.com/progScreenshots/Super-Grub-Disk-Screenshot-8071.html)

---

### Post by ssican on 2007-03-24
Do you know this forum?   [http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by gideonidoru on 2007-03-26
Hi , i followed the most recent guide, disconnected my windows drive, and installed Linux.. then updated ubuntu completely

after I reconnected Ubuntu would not boot (just hung at the beginning of the load status bar)

ok... so I tried to load vista via the updated boot menu (with the map commands) it just restarts my PC

help! :confused:

---

### Post by confused57 on 2007-03-26
> **gideonidoru said:**
> Hi , i followed the most recent guide, disconnected my windows drive, and installed Linux.. then updated ubuntu completely

after I reconnected Ubuntu would not boot (just hung at the beginning of the load status bar)

ok... so I tried to load vista via the updated boot menu (with the map commands) it just restarts my PC

help! :confused:
Try booting up the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Did you install Ubuntu on your hard drive connected to sda & then connect your Vista drive to sdb?
Did you add an entry similar to this to boot Vista?:
```
title              Windows Vista
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by gideonidoru on 2007-03-26
> **confused57 said:**
> Try booting up the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Did you install Ubuntu on your hard drive connected to sda & then connect your Vista drive to sdb?
Did you add an entry similar to this to boot Vista?:
```
title              Windows Vista
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Yes that is the exact entry I have, ill run the fdisk command and let you know the output

---

### Post by Solid1986Snake on 2007-03-26
I have the same problem like you, but at the moment I do not a have a working Ubuntu Cd and I can't test it, but I read many Posts on Forums.

Maybe you changed the Partition Size with the Ubuntu Partitioning-Tool? I read that there maybe problems on resizing because Vista uses a new Version of Ntfs. The best way should be to let there be free space after the Vista installtion an only edit this with Ubuntu.

---

### Post by gideonidoru on 2007-03-26
> **Solid1986Snake said:**
> I have the same problem like you, but at the moment I do not a have a working Ubuntu Cd and I can't test it, but I read many Posts on Forums.

Maybe you changed the Partition Size with the Ubuntu Partitioning-Tool? I read that there maybe problems on resizing because Vista uses a new Version of Ntfs. The best way should be to let there be free space after the Vista installtion an only edit this with Ubuntu.

Hi, I did not edit any partition other than the ext3 and swap partitions with the installer..

---

### Post by gideonidoru on 2007-03-26
Hi, here is my result from fdisk -l 

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15297   122871808    7  HPFS/NTFS
/dev/sda2           15298       24321    72485280    f  W95 Ext'd (LBA)
/dev/sda5           15298       24321    72485248+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       60801   488376000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30402   244196001    7  HPFS/NTFS
/dev/sdb6           30403       60546   242131648+  83  Linux
/dev/sdb7           60547       60801     2048256   82  Linux swap / Solaris


and the pertinent parts of my /boot/grub/menu.lst

> title              Windows Vista
rootnoverify       (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

> title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda6 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

also since these are both sata devices I can select which one I want to boot from the bios, which I guess I don't mind... however whenever my Vista drive is plugged in, it wont boot ubuntu (hangs at the beginning of the status bar)

any ideas on that one?

---

### Post by confused57 on 2007-03-26
The only thing I can think of is your device.map:
```
gksudo gedit /boot/grub/device.map
```

It should look something like this(if your bios is set up to boot your Ubuntu drive first):
```
(hd0) /dev/sdb
(hd1) /dev/sda
```

I just noticed your "fdisk -l" output shows:
> Device Boot Start End Blocks Id System
/dev/sdb1 2 60801 488376000 f W95 Ext'd (LBA)
/dev/sdb5 2 30402 244196001 7 HPFS/NTFS
**/dev/sdb6** 30403 60546 242131648+ 83 Linux
/dev/sdb7 60547 60801 2048256 82 Linux swap / Solaris

and your kernel entry in your menu.lst:
> title Ubuntu, kernel 2.6.17-11-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.17-11-generic root=**/dev/sda6** ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

Since, you have your drive with Ubuntu connected to the sdb controller, you may need to change the kernel line to show root=/dev/sdb6...you can test this by pressing "e", then changing it to sdb6, then "b" to boot.  Again, if you're booting first to your sdb Ubuntu drive.

Did you install Ubuntu with the drive connected as sda, then switched the drive to the sdb controller?  Have you tried booting your Ubuntu drive connected to your SATA#1 controller & Vista on the SATA#2 controller?  Just some thoughts that may help, not sure what's going on with your system.

---

### Post by gideonidoru on 2007-03-26
> **confused57 said:**
> The only thing I can think of is your device.map:
```
gksudo gedit /boot/grub/device.map
```

It should look something like this(if your bios is set up to boot your Ubuntu drive first):
```
(hd0) /dev/sdb
(hd1) /dev/sda
```

I just noticed your "fdisk -l" output shows:


and your kernel entry in your menu.lst:


Since, you have your drive with Ubuntu connected to the sdb controller, you may need to change the kernel line to show root=/dev/sdb6...you can test this by pressing "e", then changing it to sdb6, then "b" to boot.  Again, if you're booting first to your sdb Ubuntu drive.

Did you install Ubuntu with the drive connected as sda, then switched the drive to the sdb controller?  Have you tried booting your Ubuntu drive connected to your SATA#1 controller & Vista on the SATA#2 controller?  Just some thoughts that may help, not sure what's going on with your system.

good call, I followed a guide and installed it with my Vista drive disconnected, ill try that change and it should boot, but any ideas for grub loading vista?

---

### Post by confused57 on 2007-03-26
I think your best & easiest option would be to connect your Ubuntu drive to SATA#1 and Vista drive to SATA#2...your current entry should boot Vista.

You can leave the Ubuntu drive connected to SATA#2, but you'd need to make all the changes I've mentioned and you'd probably have to modify your /etc/fstab to reflect root's mountpoint as /dev/sdb6. The current Vista entry would work here also, with all the changes I've mentioned.

Added:  Your /etc/fstab may be OK  if it's mounted with UUID's, instead of by  /dev/sda6.

---

### Post by gideonidoru on 2007-03-27
Thanks for all the advice, I followed everything and now I can boot Vista and Ubuntu. The only thing is I have to change the boot order via the bios.. annoying but not a show stopper...


Again, thanks for the all advice, the reason I wanted to go back and give linux another shot was for the community and you guys have validated that decision :)

---

### Post by figure_eight on 2007-09-13
i had a similar problem this weekend after installing ubuntu on a partition shared with vista. i had no problems shrinking the disk to make the partition, installing ubuntu or booting to either OS via grub. however, i share this computer with others, so i wanted to go back to the vista bootloader.

i managed to reinstall the bootloader with easybcd, but when i tried to boot back into ubuntu from the newly reinstalled vista boot menu, it wouldn't boot. at first, i thought it was because i'd chosen the wrong partition to boot to in easybcd, but the partition was correct.

what i DID overlook was the checkbox that says 'grub is not installed on this partition'. after checking that box & restarting, i got the vista bootloader, chose ubuntu, then got the grub menu & booted up just fine from there.

now, i realize the main difference is that you've got your vista installation & ubuntu installation on separate drives, but i thought i'd share my solution on the off-chance it worked for you, too.

---

