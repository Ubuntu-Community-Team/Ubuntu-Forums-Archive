---
title: "Can't install grub on hd0,0 (Fatal Error)"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by SilverTab on 2008-08-27
For some reasons I can't install Kubuntu 8.04, I keep getting an error at the end of the installation process saying something along the lines of "Grub install failed (Can't install Grub on hd0,0), then a window popups saying "This is a fatal error" and the installation quits, I am logged into KDE (on the live cd I'm guessing) and if I reboot, grub gives me an Error 17...

Now for a bit of background info, this is what my HD looks like:
sda1: Windows Vista (ntfs)
sda2: Linux (ext3)
sda3: Backup (fat32)
sda4: Swap

It's been partitioned that way for a while now and I never had a problem before...

Arch Linux was installed on sda2, and this is why I had Grub already installed... when I formatted the sda2 partition (via Partition Magic, in Windows) to install Kubuntu on it, I had to reboot and Grub gave me an error 17... I decided to reboot and boot on the Kubuntu CD and install it on sda2 anyway... and I got the grub installation error I mentioned in the thread title...

So basically, it is not Kubuntu's grub installation that gives me an error, but the grub that Arch Linux had installed a while back...

I tried re-installing Kubuntu, making sure I had no USB flash drive or any other removable storage in there, same result... somehow Kubuntu isn't able to install Grub and I'm stuck with the old broken Grub (for now I have to use Ultimate Boot CD to boot into vista so that I can do anything with my computer)...

I suppose linux is installed correctly on sda2, I just can't boot it... (it's not even visible from Smart Boot Manager etc... only the vista partition is)...

I know this is a bit long to read but I wanted to give as much details as possible, I'm not so sure what I could try? Perhaps it is a problem with the MBR? I have no idea, but any tips/suggestion will be appreciated!

Thank you!

---

### Post by sandysandy on 2008-08-27
with live Cd open terminal and post output of [COLOR="Blue"]sudo fdisk -lu[/COLOR]

also with live Cd try to install GRUB as shown in the thread below

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

regards

---

### Post by SilverTab on 2008-08-27
wow, I didn't expect a reply so soon! I'll give it a try and report back! :)

---

### Post by SilverTab on 2008-08-27
Well, unfortunately, the grub reinstallation instructions failed on the first step:
```

find /boot/grub/stage1

```
Gave me the following error: "Error 15: File not found"

As for the content of "sudo fdisk -lu" here it is:
```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xfa8665cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   334762469   167381203+   7  HPFS/NTFS
/dev/sda2       334762470   441385874    53311702+  af  Unknown
/dev/sda3       441385875   486255419    22434772+   c  W95 FAT32 (LBA)
/dev/sda4       486255420   488392064     1068322+   5  Extended
/dev/sda5       486255483   488392064     1068291   82  Linux swap / Solaris

```

Somehow I get the feeling that my MBR is screwed up... and for some reasons sda2 is showing up as "Unknown" when it has been formated as Ext3...

---

### Post by sandysandy on 2008-08-27
> /dev/sda2       334762470   441385874    53311702+  af  Unknown

ur file system type is shown as unknown. 

can i suggest u re-format it again as ext3 using gparted (gparted is available on ubuntu live Cd and hopefully should also be on ur kubuntu live CD)

its also available at

[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

(burn it as iso image to make bootable CD. then pop in CD drive and reboot computer.)

see tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

### Post by SilverTab on 2008-08-27
Well, I got it to work finally... here's what I did:

-Used cfdisk to re-format the partition in Ext3...

-Tried installing Kubunty, got an error saying the disk wasn't writable.

-Re-started the installation, but I re-formatted the partition in the Kubuntu installer... this time it worked...!

Thanks for the help sandysandy!

---

