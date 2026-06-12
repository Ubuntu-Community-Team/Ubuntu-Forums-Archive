---
title: "Utterly failed new 12.04 installation"
date: 2012-06-18
forum: Installation &amp; Upgrades
---

### Post by Rob Sayer on 2012-06-18
I tried installing Ubuntu 12.04 today on my older laptop.  Not an upgrade, a new installation.  It didn't work.  At all.  My computer specs:

Computer: Compaq presario CQ-104CA
OS: Windows 7 Home 64 bit
CPU: AMD V140
BIOS: latest
Graphics: amd m880g with ati mobility radeon hd 4250
Wireless: atheros ar9285
Internal HD:SATA

I wasn't connected to the internet at the time ... I know of a number of people who have installed ubuntu unconnected and just updated later.  Besides I know someone who has the same wireless device as I do and his worked righted out of the box.  I wasn't expecting any problems there.

It seemed to go normally until I got to the part where I chose to install dual boot linux/windows.  Then, the screen went black and the following text appeared (I left out the [OK]'s):

checking battery state
starting crash report submission daemon
stating cpu interrupts balancing daemon
stopping system V runlevel compatibility
starting configure network device security
stopping configure network device security
stopping cold plug devices
stopping log initial device creation
starting enable remaining boot-time encrypting devices
starting configure network device security
starting save udev log and update rules
stopping save udev log and update rules
stopping enable remaining boot-time encrypted block devices
checking for running unattended-upgrades
            acpid: exiting
speech-dispatcher disabled: edit /etc/default/speech-disorder

At this point, the CD is ejected.  Then it just sat there.

When I pressed the return key it booted Windows.  I don't think that's what's supposed to happen.

Thinking the cd media or dvd drive may have been faulty, I downloaded the .iso again and made a bootable USB stick, as per your instructions.

This time there was no cryptic crash screen.  It just booted windows.

If it have left any log files I can't find  them.

Thinking the amd64 version may have been the wrong one, I tried downloading the x86 version.  Same thing, both from cd and usb drive.

I'm not 100% positive the crash message after using the cd was the same both times but the situation seems to be pretty much the same.

This is supposed to be a simple, transparent install.  I went to the time and trouble of looking up my devices and drivers re ubuntu beforehand, and was prepared to do some configuration but not like this.

Basically I spent over 3 hours trying to install it with only the above to show for it, and I'm glad I didn't try it with my newer laptop.  As I said, I'm not averse to doing a bit of system jiggering but at this point I am *extremely *frustrated.

---

### Post by sudodus on 2012-06-18
Welcome to the Ubuntu Forums :-)

Did you try to run Ubuntu live 'test Ubuntu' from the CD drive before installing it? If you did not, please do it now, because it will give us valuable information without tampering with your hard drive.

If you get it running live, please run the following command and post the output text in a reply.
```
sudo fdisk -lu
```
Put the output text between CODE tags: Mark it and click on the # icon at the top of the editing window.

---

### Post by Rob Sayer on 2012-06-18
Thanks for the reply ... I don't know what CODE tags or #icons are, I'm pretty new to linux, and it's been over 20 years since I've used unix ...

Here's what I got, poorly formatted:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x54dc1e55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   454197247   226893824    7  HPFS/NTFS/exFAT
/dev/sda3       454197248   488183807    16993280    7  HPFS/NTFS/exFAT
/dev/sda4       488183808   488395119      105656    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

Thanks ...

---

### Post by sudodus on 2012-06-18
> **Rob Sayer said:**
> Thanks for the reply ... I don't know what CODE tags or #icons are, I'm pretty new to linux, and it's been over 20 years since I've used unix ...

Here's what you get, better formatted ;-)
If you press the [COLOR="Red"]quote[/COLOR] button, you will see the CODE tags.

```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x54dc1e55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   454197247   226893824    7  HPFS/NTFS/exFAT
/dev/sda3       454197248   488183807    16993280    7  HPFS/NTFS/exFAT
/dev/sda4       488183808   488395119      105656    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

``` 

Your hard drive has 4 primary partitions for Windows. Unfortunately, that makes it impossible for Ubuntu to add its partitions (a root partition and a swap partition).

But you can do something, if you are prepared to edit your partition table. You must delete one partition and shrink one partition, so that you can create an extended partition, and in that extended partition you (or the Ubuntu installer) can make the partitions necessary.

Editing partitions is risky, so if you decide to do it, you should ***backup*** your whole hard drive for example with Clonezilla, or at least backup your private files (documents, pictures, ...) and make a recovery disk for Windows.

---

### Post by Rob Sayer on 2012-06-18
All right ...  that makes sense.  I'm not great with linux commands but that works for me.

I'll get on it tomorrow.  I'm computered out for today.  The drive is cleaned of superflous stuff down to 65Gb or so, defragged, and backed up already ... this isn't my main go to at home computer anyway.

Thanks for the prompt, lucid replies ...

---

### Post by mr.suchy on 2012-06-19
I think my problem is similar, dont U think ? I create a four primary partition. Check this thread [http://ubuntuforums.org/showthread.php?t=2005849](http://ubuntuforums.org/showthread.php?t=2005849)

---

### Post by sudodus on 2012-06-19
> **mr.suchy said:**
> I think my problem is similar, dont U think ? I create a four primary partition. Check this thread [http://ubuntuforums.org/showthread.php?t=2005849](http://ubuntuforums.org/showthread.php?t=2005849)
I'm not sure from your screendump. Are there already four primary partitions when you start installing Ubuntu? In that case yes.

But let us continue the conversation about your problem in your thread!

---

### Post by Rob Sayer on 2012-06-19
We're *up* and *running*.  Thanks for all the help ...

Yes, it was the partitioning.  Damn HP bloatware.  Actually quite simple.

And I don't think that partition is going to last long.  Almost all the Windows software I use is a linux port anyway.  Those don't screw around with your windows registry and add those awful codec packs.

---

### Post by sudodus on 2012-06-19
Congratulations :KS

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

### Post by Rob Sayer on 2012-06-19
OK ... I thought it did that when I tagged 'solved' ...

---

