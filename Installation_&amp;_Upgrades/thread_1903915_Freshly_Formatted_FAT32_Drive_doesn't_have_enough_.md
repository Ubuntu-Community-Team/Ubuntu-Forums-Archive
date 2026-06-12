---
title: "Freshly Formatted FAT32 Drive doesn't have enough disk space?"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by GrizzleNizzle on 2012-01-03
I'm trying to revive an older PC with a Ubuntu 10.10 install.  I got an old motherboard from craigslist (ECS 661fx-M) and it will POST just fine and recognize all hardware, including the HDD in question.   I'm trying to boot from a Live USB that works just fine on my other machine.  The BIOS responds just fine and boots with the USB.  I try to start the install and the GUI tells me there is not enough disk space.  The HDD didn't have any OS on it so I removed it, put it in my working machine, reformatted with a primary bootable FAT32 partition with Gparted, then put it back in the old machine.  I get the same message.

Now I know that the Live USB should be able to format the drive by itself, but I was not given the option, or I didn't know where to look.  I tried "fdisk -l" and got no output.  I also tried to use Gparted on the USB and it did not recognize the HDD either, only the USB.   I'm thinking that since it only sees the USB, it thinks I am trying to install on the USB, and hence there is not enough drive space.

I googled my brain out and got no leads.  Help please! 

Many thanks and Happy New Year!

---

### Post by spacecheck on 2012-01-03
Did you notice that there is a pull down menu in the upper right corner of Gparted to select a different drive? Also available in the file menu "Gparted, Devices".

Disk Utility is also a good graphical tool for this and may be installed on the live USB.

cfdisk is also good and fairly simple to use.

What size is the HDD? Why do you need Fat32? Why not a short primary partition for /boot another for / and an extended partition for the rest, with logical partitions for /home and /swap 

Did you look at the man page for fdisk? Pay attention to the DOS 6.1 warning and solution.

Did you try creating a completely new partition table before partitioning the disk ?

---

### Post by GrizzleNizzle on 2012-01-03
> **spacecheck said:**
> Did you notice that there is a pull down menu in the upper right corner of Gparted to select a different drive? Also available in the file menu "Gparted, Devices".

Yes, I saw that and nothing but the USB was available.


> **spacecheck said:**
> What size is the HDD? 

80GB

> **spacecheck said:**
> Why do you need Fat32? Why not a short primary partition for /boot another for / and an extended partition for the rest, with logical partitions for /home and /swap 

I was only formatting so that it was recognizable, and was planning on reformatting again once I got the install going.  I tried several different formatting variants, even one with maybe 5 different partitions of different types hoping that one would be recognized

> **spacecheck said:**
> Did you look at the man page for fdisk? Pay attention to the DOS 6.1 warning and solution.

Yes I did.  I didn't see any DOS 6.1 warnings but I'll try that again.

> **spacecheck said:**
> Did you try creating a completely new partition table before partitioning the disk ?

Yep, did that too...

Thanks for the reply!

---

### Post by spacecheck on 2012-01-03
When you ran fdisk -l did you run

sudo fdisk -l
?

---

### Post by GrizzleNizzle on 2012-01-03
> **spacecheck said:**
> When you ran fdisk -l did you run

sudo fdisk -l
?

Yes I did.  I should have mentioned that...

---

### Post by fdrake on 2012-01-03
> **GrizzleNizzle said:**
> Yes I did.  I should have mentioned that...

"fdisk -l" doesn't work . you have to use sudo. so try "sudo fdisk -l" or even better do:```

sudo apt-get install parted
sudo parted -l

```and post here both outputs (parted and fdisk's output)

---

### Post by darkod on 2012-01-03
Are you definitely sure the HDD works? Because it doesn't sound like it.

In BIOS is it reported as recognized, 80GB disk?

Make sure the cables are connected good. If it's IDE disk I guess, take a look at any jumpers master/slave.

---

### Post by spacecheck on 2012-01-03
This may also be a helpful thread, especially if you do not know the past disk usage:

[http://ubuntuforums.org/showthread.php?t=1324025&page=2](http://ubuntuforums.org/showthread.php?t=1324025&page=2)

---

### Post by GrizzleNizzle on 2012-01-03
> **fdrake said:**
> "fdisk -l" doesn't work . you have to use sudo. so try "sudo fdisk -l" or even better do:```

sudo apt-get install parted
sudo parted -l

```and post here both outputs (parted and fdisk's output)

I did use sudo and got no output.  I have not tried using "sudo parted -l".  I'll try that in a couple hours when I get home.  Thanks!

---

### Post by GrizzleNizzle on 2012-01-03
> **darkod said:**
> Are you definitely sure the HDD works? Because it doesn't sound like it.

In BIOS is it reported as recognized, 80GB disk?

Make sure the cables are connected good. If it's IDE disk I guess, take a look at any jumpers master/slave.

Yes, the BIOS recognizes the drive accurately.  I'm pretty sure the drive works because it formerly had a Windows 7 install that worked ok.  However, I suppose it could have been damaged somehow since then (it sat unused for several months).  I checked the connections many times and they are solid.  There are no jumpers on the mobo for the IDE channels, only for clearing the CMOS and write-protecting the BIOS, which I did use in this process.  The CMOS battery on the used mobo was dying so I replaced it with my old one of the same type.  I cleared the CMOS, restored the defaults, and it POSTs fine.  The jumpers are now in the correct positions according to the mobo manual.  Is it possible that I messed up the BIOS somehow in the process and caused my problem?  The BIOS seems to be working fine and recognizes everything accurately...

---

### Post by GrizzleNizzle on 2012-01-03
> **spacecheck said:**
> This may also be a helpful thread, especially if you do not know the past disk usage:

[http://ubuntuforums.org/showthread.php?t=1324025&page=2](http://ubuntuforums.org/showthread.php?t=1324025&page=2)


The HDD was not in a RAID configuration when I bought this computer (also from craigslist).  I suppose I don't know about its entire history so I'll try "sudo blkid" when I get home and see what happens.

---

### Post by darkod on 2012-01-03
I was talking about a jumper on the HDD itself. IDE disks had the option to select the Master or Slave role with a jumper. There should be an image on the disk about jumper positions.

Otherwise, sudo fdisk -l should show all disks and partitions regardless of the partition types. All functioning disks are listed with fdisk.

---

### Post by GrizzleNizzle on 2012-01-03
> **darkod said:**
> I was talking about a jumper on the HDD itself. IDE disks had the option to select the Master or Slave role with a jumper. There should be an image on the disk about jumper positions.

Otherwise, sudo fdisk -l should show all disks and partitions regardless of the partition types. All functioning disks are listed with fdisk.

Oh Ok.  I'll check it out, but I've never moved a jumper on this drive and it was working as the only drive in the past.  Not sure if that matters though.  I'll take a look.

---

### Post by GrizzleNizzle on 2012-01-03
> **fdrake said:**
> "fdisk -l" doesn't work . you have to use sudo. so try "sudo fdisk -l" or even better do:```

sudo apt-get install parted
sudo parted -l

```and post here both outputs (parted and fdisk's output)

This computer is really acting funny...  It took me about 15 tries to successfully boot from the USB this time.  BIOS wouldn't recognize the USB for some reason even though it did before...  The last thing I did before it worked was enabling "reset configuration data" in the BIOS.  Now that I can boot from USB, I DO get something from fdisk, although just info for the USB drive:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 2003 MB, 2003795968 bytes
32 heads, 63 sectors/track, 1941 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0cdd6103

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1941     1956496+   c  W95 FAT32 (LBA)

```Also, here is the other info you were asking for:

```

ubuntu@ubuntu:~$ sudo parted -l
Model: Kingston DataTraveler 112 (scsi)
Disk /dev/sda: 2004MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  2003MB  2003MB  primary  fat32        boot, lba
```Not sure if any of this helps...  I still can't see the HDD in Gparted...

Also, I pulled a working DVD drive from my working computer and tried to boot with a live CD and couldn't.  The BIOS saw the optical drive, but if I tried to boot from CD it would simply hang up at "Boot from CD:   "  Not sure what this means, or if it helps.  My debugging skills have pretty much run out.  I'm at a loss as to what to try next, other than to toss the whole thing out the window.

I did notice the CMOS clock was losing time, so maybe the CMOS battery I put in is also dying.  I'm not sure if this would cause all these problems though.

Let me know if you have any other ideas.

Thanks!

---

### Post by GrizzleNizzle on 2012-01-03
> **darkod said:**
> Are you definitely sure the HDD works? Because it doesn't sound like it.

In BIOS is it reported as recognized, 80GB disk?

Make sure the cables are connected good. If it's IDE disk I guess, take a look at any jumpers master/slave.

No jumpers on the HDD.

Question:  is it safe to pull my primary HDD from my working computer, put it in this one, and see if it works?  Is there any risk of losing data?

---

### Post by darkod on 2012-01-04
> **GrizzleNizzle said:**
> No jumpers on the HDD.

Question:  is it safe to pull my primary HDD from my working computer, put it in this one, and see if it works?  Is there any risk of losing data?

There should be no risk to the data, just to see if the disk is recognized correctly.

But if you suspect the mobo battery I would say change it with a new battery first. And try with the 80GB disk.

---

### Post by GrizzleNizzle on 2012-01-04
So I tried the HDD from my working computer in the old computer using the old connectors and it shows up just fine in Gparted.  I'm inclined to say that shows the old HDD is bad, but I'm able to see the old drive and reformat it when connected to my new computer.  Soooooo, what the heck does that mean???

---

### Post by darkod on 2012-01-04
I know the new disk worked with the same cables but try the old disk in the old computers but with another set of cables.

This is hardware related, I am running out of ideas. If the old disk is also SATA (I just assumed 80GB is IDE), check the SATA mode in bios, usually you would use AHCI. Or maybe just because it's old disk it works only in IDE sata mode. The new disk can work with AHCI for sure.

Try few different options.

---

### Post by spacecheck on 2012-01-06
Another important consideration is the power output of the PSU. If it able to supply enough power for booting, it may be unable to supply enough power for the higher loading required when the OS has initialized all of the devices and accessories.

I've not seen a definitive answer as to whether IDE or SATA drive, and you mentioned there are no jumpers on the HDD, so I'll point out some devices without jumpers are Master, some are Cable-select, and some are slave.

Not knowing how many devices are installed, or upon which kind of controller and cable, and noting you also have a problem with a DVD-drive in the same system, you may want to review the jumpering and cable requirements for the configuration you are using.

Good luck!

---

### Post by efflandt on 2012-01-06
The cables could be different.  Older computers had no markings on ide cables, and which drive was master or slave was determined by jumpers on the drive.  But if drive plugs were inserted in proper direction, a single drive with no drive jumper should be considered single or master.

IDE cables marked with 0 and 1 or A and B, the lower number or letter would be the master if the drive was jumpered for cable select (CSEL or something similar).

Maybe the old cable is bad (if you can access old drive with newer cable)

I bought an out of the box PC once that had all the drive jumpers messed up (including DVD, and LS120 Super Disk (which was a 120 MB ide connected floppy drive) and nothing would boot until all drives other than hard drive were disconnected (until I fixed drive jumpers).

If an ide (Pata) cable is plugged in the wrong way on one end, I think the drive just spins endlessly (or at least I had that happen once).

Sata cables for more than one drive determine which drive is which from markings on the plugs or cable near them.

---

### Post by GrizzleNizzle on 2012-01-06
Thanks for all of the help guys!  I decided to buy a cheap drive from someone on cragslist and it worked out just fine.  This one uses the ribbon cable instead of the SATA connector.  I've now successfully installed the OS and I'm on my way.  I guess sometimes it's not worth the time to figure out what's wrong and just replace...  :-)

Should I mark this thread as solved if it was only solved by replacement?

Thanks again for the help!!

---

### Post by spacecheck on 2012-01-06
> **GrizzleNizzle said:**
> Thanks for all of the help guys!  I decided to buy a cheap drive from someone on cragslist and it worked out just fine.  This one uses the ribbon cable instead of the SATA connector.  I've now successfully installed the OS and I'm on my way.  I guess sometimes it's not worth the time to figure out what's wrong and just replace...  :-)

Should I mark this thread as solved if it was only solved by replacement?

Thanks again for the help!!
You can mark it as solved if you need no further help.
Now I've seen it's a SATA HDD, I hope you went into the BIOS and made sure the SATA controller was enabled, the specific port (socket for the SATA plug) was enabled, the port was not set to "RAID", etc.

I hope that you checked different SATA cables and different (enabled) SATA ports, because the contacts can get loose or worn.

Have fun!

---

### Post by GrizzleNizzle on 2012-01-06
> **spacecheck said:**
> You can mark it as solved if you need no further help.
Now I've seen it's a SATA HDD, I hope you went into the BIOS and made sure the SATA controller was enabled, the specific port (socket for the SATA plug) was enabled, the port was not set to "RAID", etc.

I hope that you checked different SATA cables and different (enabled) SATA ports, because the contacts can get loose or worn.

Have fun!

Yea I did all that, with no luck.  I tried a different SATA drive changing nothing else (same cables, same BIOS settings) and it worked just fine...  very mysterious.

---

