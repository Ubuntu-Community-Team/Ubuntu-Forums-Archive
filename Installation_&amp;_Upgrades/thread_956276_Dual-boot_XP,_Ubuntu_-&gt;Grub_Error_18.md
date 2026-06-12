---
title: "Dual-boot XP, Ubuntu -&gt;Grub Error 18"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by luckytwitch on 2008-10-23
As the thread title says, I'm trying to dualboot with XP and Ubuntu.  I tried to install plain ubuntu first, but it failed to install, dropping out to initram I think it was.  After reading through the forums, I think it is because of my Mobo, which can have sata or ide drives, but I'm trying to boot off an ide drive.  I have the sata drive unplugged since it's storing all my backed up data.  (note, all ubuntu installs tried were using version 8.04)
After the Ubuntu install failed, I tried Kubuntu, but that didn't work either.  I read here on the forums to try Xubuntu.  I successfully installed Xubuntu, but then when I restarted I got Grub Error 18.
In the forums here, I also found the following thread:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
which tells how to fix grub.  I tried this and it seemed as if it would work, but it doesn't changed anything.  I just get the same error when I restart.
The following thread was also helpful to me, but hasn't helped me fix my comp yet.
[http://ubuntuforums.org/showthread.php?t=934666&highlight=dual+boot+xp+grub+error+18]("http://ubuntuforums.org/showthread.php?t=934666&highlight=dual+boot+xp+grub+error+18")

I'm not sure how to show the output that I got from my desktop doing this, but I'll see if I can do that tomorrow night after work or something.

Any help is much appreciated.
Here is the system I'm trying to install on, let me know if I need to add any other information:
MoBo: Gigabyte GA-P35-DS3L/SRL
Ram: 2 x 1 Gb DDR2 mem
Processor: Intel S775 C2d E6550 2.33 GHz
Video Card : EVGA 8400GS 256Mb PCIE

---

### Post by caljohnsmith on 2008-10-23
Grub error 18 usually means that you have a BIOS that can't see anything on the HDD past either 8 GB or 137 GB, in which case your Grub boot files would be "out of reach" from the BIOS. From your Live CD, if you can open a terminal (in Ubuntu its under applications > accessories > terminal, in Xubuntu I don't know), then please post the output of:
```
sudo fdisk -lu
```
And we can work from there. :)

---

### Post by luckytwitch on 2008-10-23
for sudo fdish -lu I get the following:

```

Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0f740f73

   Device  Boot     Start        End     Blocks   Id  System
/dev/sda1   *          63  155396744   77698341    7  HPFS/NTFS
/dev/sda2       155396745  490223474  167413365    5  Extended
/dev/sda5       155396808  478078334  161340763+  83  Linux
/dev/sda6       478078398  490223474    6072538+  82  Linux swap / Solaris

```

When I go into grub and look for the stage1 file, it finds it on hd(0,4)
```

grub> find /boot/grub/stage1
  (hd0,4)
```
I'm about to be leaving for work, so I will be able to answer questions about what I did last night, but I won't be able to try anything new for the next 12 hours.  Thanks for your help.

---

### Post by caljohnsmith on 2008-10-23
OK, whenever you get home, first make sure that Grub is installed OK to the HDD MBR (Master Boot Record):
```
sudo grub
grub> root (hd0,4)
grub> setup (hd0)
```
And then so we can see where your Grub stage2 and menu.lst files physically are:
```
grub> blocklist /boot/grub/stage2
grub> blocklist /boot/grub/menu.lst
grub> quit
```
Please post the output of all the above commands. :)

---

### Post by luckytwitch on 2008-10-23
So when I ran the code, I got the following.
```

grub> root (hd0,4)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded. succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,4)/boot/grub/stage2/boot/grub/menu.lst"...succeeded
Done.

grub> blocklist /boot/grub/stage2
(hd0,4)303797952+96,303798056+116

grub> blocklist /boot/grub/menu.lst
(hd0,4)303798176+9

grub> quit

```

---

### Post by caljohnsmith on 2008-10-24
Because both your Grub stage2 and menu.lst files are at about the 155 GB point on your HDD, it looks like your BIOS has the 137 GB limitation, and that is why you are getting the Grub error 18. So if that is the case, the only option to get Grub to work is to move the Grub files within the 137 GB limit. 

For your situation I would recommend making a small ~200 MB ext3 partition right before your Ubuntu partition sda5 where you can put your entire /boot directory; that will put them way before the 137 GB point on your HDD. To make the partition, you'll need to do it from your Live CD so the HDD isn't mounted, and open Ubuntu's partition editor with:
```
gksudo gparted
```
You can make the partition a primary partition, or you can make it a logical partition within your sda2 extended partition. Let me know if you can get that far, and then I can help you move Grub to the new partition. :)

---

### Post by luckytwitch on 2008-10-24
I'll try it again, but I tried this earlier when I saw your directions on another thread.  The problem I ran into was in the partition editor.  When I hit apply changes it ran into an error, but I forget what it was.  I'll try again and get back to you on it.
If I install Ubuntu first onto my hard drive, then install XP, would that solve this problem too?  Just wondering.
*edit*
I think I know what was wrong, I forgot to unmount both partitions of the hd.  I only unmounted the xp partition. I'll be trying this shortly.

---

### Post by caljohnsmith on 2008-10-24
> **luckytwitch said:**
> I'll try it again, but I tried this earlier when I saw your directions on another thread.  The problem I ran into was in the partition editor.  When I hit apply changes it ran into an error, but I forget what it was.  I'll try again and get back to you on it.
If I install Ubuntu first onto my hard drive, then install XP, would that solve this problem too?  Just wondering.
*edit*
I think I know what was wrong, I forgot to unmount both partitions of the hd.  I only unmounted the xp partition. I'll be trying this shortly.
Make sure you are using gparted from your Live CD, and not from Ubuntu on your HDD; also make sure your important files are backed up in case anything goes wrong. And I wanted to also mention that the Live CD will usually use any swap partition it can find on your HDD, so you may have to select the swap partition on your HDD in gparted and choose "swapoff" or whichever the option is. Good luck and let me know how it goes.

---

### Post by luckytwitch on 2008-10-24
How do I know if I'm using gparted from the live cd vs the HDD? I'm running Ubuntu from the live cd.  I tried the swapoff option, but I still get an error.
```

Shrink /dev/sda1 from 74.1 Gib to 73.9 Gib
 > calibrate /dev/sda1
 > calculate new size and position of /dev/sda1
 > check filesystem on /dev/sda1 for errors and if possible fix them   (-)

```
also, whenever I unmount sda1, sda5 gets automounted again, and vice versa.  Could that be causing the problem?

---

### Post by caljohnsmith on 2008-10-24
> **luckytwitch said:**
> How do I know if I'm using gparted from the live cd vs the HDD? I'm running Ubuntu from the live cd.  I tried the swapoff option, but I still get an error.
```

Shrink /dev/sda1 from 74.1 Gib to 73.9 Gib
 > calibrate /dev/sda1
 > calculate new size and position of /dev/sda1
 > [COLOR="Red"]check filesystem on /dev/sda1 for errors and if possible fix them [/COLOR]  (-)

```
As long as you are running Ubuntu on the Live CD, you are using gparted from the Live CD, so you should be fine about that. So when you hit the "apply" button in gparted, exactly what error does it give? From the output you show above, that last line about checking the file system for errors doesn't necessarily mean gparted can't shrink the sda1 NTFS partition I think, it just means you might have to check the NTFS partition when your done. If you can provide a screen shot that might help (the "PrtScrn" button).

---

### Post by luckytwitch on 2008-10-24
I've tried to take a screenshot, but apparently there is something wrong with the keyboard driver being used because prtscrn isn't working.  
When I run gparted, i get the following that shows up in the terminal, plus what I described happening in the gui window.
"an error occured while applying the operations
see the details for more information"
and I listed the details in my last post.
```

=====================
libparted : 1.7.1
=====================
Unable to open /dev/scd0 read-write (Read-only file system). /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 read-write (Read-only file system). /dev/scd0 has been opened read-only.
unable to open /dev/scd0 - unrecognized disk label.

```

If I were to reinstall XP and Ubuntu, could I get around this grub problem by just installing Ubuntu first, or would that not work?

---

### Post by luckytwitch on 2008-10-24
Sorry, I found more info on the error:
```

shrink /dev/sda1 from 74.10 Gib to 73.90 Gib
 > calibrate /dev/sda1
 > calculate new size and position of /dev/sda1
 \/ check filesystem on /dev/sda1 for errors and (if possible) fix them
       \/ ntfsresize -P -i -f -v /dev/sda1
             ntfsresize v2.0.0 (libntfs 10:0:0)
             ERROR: Device '/dev/sda1' is mounted read-write.  You must 'umount' it first.

```
So there's the problem, the drive isn't unmounted, but I clicked the unmount box within the gparted window.  Do I need to unmount it within the terminal first?

---

### Post by caljohnsmith on 2008-10-24
> **luckytwitch said:**
> 
If I were to reinstall XP and Ubuntu, could I get around this grub problem by just installing Ubuntu first, or would that not work?
You would accomplish the same thing we are trying to do if you were to install Ubuntu to the first partition at the front of the HDD, and install Windows to some other primary partition. You would want to install XP first, then Ubuntu, so that XP doesn't overwrite Grub with its own boot loader. 

So you are sure you are running gparted as root user, i.e. using gksudo:
```
gksudo gparted
```
If so, before you run gparted, try:
```
sudo umount /dev/sda1 
```
And then try gparted. Let me know if that works.

---

### Post by caljohnsmith on 2008-10-24
In case you decide to resize your partitions rather than do a reinstall, I fixed my previous post where I recommended doing the ~10 MB Grub partition, because that isn't enough; you need to put all your boot files within the reach of BIOS, so that means your entire /boot directory. So if you do decide to make a new partition, make it ~200 MB so it can handle all the boot files.

---

### Post by luckytwitch on 2008-10-25
I tried unmounting the hard drive first, and got the same error.  I think I'm just going to reinstall again, loading up Ubuntu first, then loading windows xp onto the second partition.

---

### Post by groceryheist on 2008-10-25
Hello!

I think i may be having a similar problem so i will post in this thread instead of making a new one.

I have 2 harddrives, one with windows XP and one with hardy
when I choose my hardy installation in grub i get error 18.
I can boot into the recovery mode, however.

---

### Post by bulldog on 2008-10-25
Maybe this link is useful for you.

[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by groceryheist on 2008-10-25
now i can't get in at all. I get either error 16 or 18. 
I reinstalled ubuntu and reformatted the harddrive. I also tried reinstalling grub. I think i need to put grub on it's own partition, but im not sure what partitioner i should use.

---

### Post by caljohnsmith on 2008-10-26
> **groceryheist said:**
> now i can't get in at all. I get either error 16 or 18. 
I reinstalled ubuntu and reformatted the harddrive. I also tried reinstalling grub. I think i need to put grub on it's own partition, but im not sure what partitioner i should use.
So you get the Grub error 16 or 18 before seeing a Grub menu on start up, correct? From your Live CD, open a terminal (applications > accessories > terminal) and post:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage2
```
And for whichever (hdX,Y) the above Grub find command returns, do:
```
grub> root (hdX,Y)
grub> blocklist /boot/grub/stage2
grub> blocklist /boot/grub/menu.lst
```
And we can work from there.

---

### Post by C.S.Cameron on 2008-11-01
I got Boot error 18.
I think it is due to some BIOS not seeing partitions larger than 32 GB.
I ran gparted Live CD, reduced the Windows partition to 15 GB.
Then I reduced the Ubuntu partition to 15 GB and moved it to the left.
Then moved swap to left and closed the extended partition.
Ubuntu booted fine as default and Windows booted fine at the grub menu.

---

