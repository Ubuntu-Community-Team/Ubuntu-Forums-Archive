---
title: "Can I install Hardy to a specific partition?"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by bliffle on 2008-07-09
I have a Thinkpad T60 with XP and ubuntu dualbooted from an 80g HDD. There are 4 partitions on the HDD:

sda1 is the NTFS containing XP
sda2 is a linux swap partition
sda3 is the partition I originally installed Gutsy upon
sda4 is an EXT3 partition I had copied my '/home' to.
I have 30g of unallocated space left over

After this setup had been running well for a couple months I had a problem with '3945' problems at startup, but I think those are fixed now.

The XP seems to work OK now.

I updated the ubuntu sda3 with myth.

Now, when I try to startup Gutsy I get an error from 'fsck' (return code "8") and I have to ctrl-D and startup in a 'gnome failsafe' session.

When I use the partition editor to examine the partitions I get an exclamation point in a yellow triangle for both sda3 and sda4.

Nevertheless, ubuntu will boot up, apparently from that damaged sda3.
 
I'm willing to sacrifice whatever is on sda3 in order to get back on track. If I have to I can copy the '/home' to something (like a new partition on the HDD or maybe a USB stick).

I tried upgrading Gutsy to Hardy last night using the internet connection, but after 4 hours it announced failure. Nevertheless I get the Heron logo.

I have the Hardy Alternate CD and the Desktop CD both, and I think there should be a way for me to just clobber that sda3 and install from the Alternate CD to sda3, but I can't see what it is.

How can I direct the Alternate CD to install Hardy on sda3? Is there something else I have to do? Am I overlooking something here?

---

### Post by mikewhatever on 2008-07-09
Well, you simply need to assign mount points to sda3 and sda4. The first would obviously be / and the second /home. It's OK to use both desktop and alt cd, With alt cd you can also mount other partition if you want to and use other options, but that's irrelevant to your question.

---

### Post by bliffle on 2008-07-09
> **mikewhatever said:**
> Well, you simply need to assign mount points to sda3 and sda4.

Should I de-allocate those partitions first, or re-format them?

I'm not that conversant with 'mount' and I can't figure out the right 'mount' command, and I worry about doing it wrong and making a worse mess.

>  The first would obviously be / and the second /home.

Then I would get the '/home' always on sda4, which is probably OK, but not what I started out to do.

>  It's OK to use both desktop and alt cd, With alt cd you can also mount other partition if you want to and use other options, but that's irrelevant to your question.

So, supposing I put the Alt CD into the drive, then do I restart the computer to get it to boot from the CD? And then how will the Alt on the CD know where (partition sda3) to load the system? Will it upgrade any old system on sda3 or will it scratch it and start all over?

---

### Post by mikewhatever on 2008-07-09
If you don't want sda4 as a separate home partition, mount is as something else, for example /media/data, or leave unmounted. In the latter case, you'll only have to mount sda3 as / and specify it's file system as ext3. The partition mounted as / will be formatted before the installation, meaning that all data on it will be lost. Just to say it again, all data will be lost on sda3, and no, the installer does not upgrade. As for other partitions, don't do anything about them. Leave them as is.

If you are not too good with partitioning, I'd very much advise using a live cd. It's easier, and there are fewer options to confuse you. Lastly, whatever CD you use, go with the manual partitioning option. The installer will not know by itself you want to mount sda3 as root.

Good luck.

---

### Post by bliffle on 2008-07-22
1-I put the Hardy 8.04 Alternate CD in the drive and booted up.

2-I ran the CD check: all is OK

3-I chose to install, and I thought that I chose the SDA3 partition.

4-I booted up the GRUB and it showed a bunch of new options! With new kernel versions.

5-I selected the option with the highest kernel version, it came up showing the same desktop icons as the old system, so I figured that it was the best.

6-the WiFi doesn't work. I tried toggling the netwrk enable, etc., with no luck.

7-I copied the "/boot" directory over to the XP NTFS, as well as the "/logs/../fsck" file (because I got an 'fsck' failure during boot and had to press 'ctl-D' to continue.

Here's the /boot/grub/menu.lst (with comment lines removed):

```


title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5b71c0d7-672d-4762-acf3-891e9f9d8b60 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5b71c0d7-672d-4762-acf3-891e9f9d8b60 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=5b71c0d7-672d-4762-acf3-891e9f9d8b60 ro quiet splash
initrd		/boot/initrd.img-2.6.22-15-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-15-generic root=UUID=5b71c0d7-672d-4762-acf3-891e9f9d8b60 ro single
initrd		/boot/initrd.img-2.6.22-15-generic

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b71c0d7-672d-4762-acf3-891e9f9d8b60 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=5b71c0d7-672d-4762-acf3-891e9f9d8b60 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet


title		Other operating systems:
root



title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

Which makes some sense: I think (hd0,2) is the third partition where I had the old gutsy system and where I wanted Heron to go. My old XP is on (hd0,0), the first partition

Here's the 'fsck' logfile I  got:

```

Log of fsck -C3 -R -A -a 
Tue Jul 22 12:15:37 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=dcc0c6c5-bf8d-45f7-ab2c-8326b36f7de1'
fsck died with exit status 8

Tue Jul 22 12:15:37 2008
----------------

```

---

### Post by bliffle on 2008-07-25
When I bootup ubuntu, because I want the latest kernel,  I use this boot entry:

```

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=5b71c0d7-672d-4762-acf3-891e9f9d8b60 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic

```

But the display says "sda4" instead of the "sda3" I would have expected (because of the "(hd0,2)").

---

