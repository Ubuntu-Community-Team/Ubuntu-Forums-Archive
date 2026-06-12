---
title: "Forgot to install to MBR during update to 10.04 using Update Manager"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by tedrogers on 2010-06-25
Hi all,

Been a while since my last post. Guess that because I've not been having any issues or I'd learned to stop tinkering with things until I broken them. Well, I guess not, because I'm back! :)

I was updating to 10.04 through the Update Manager, got near to the end, was prompted with the GRUB update questions with a list of HD's and partitions to select, I decided to only tick /sda4 as this is the main boot drive where Ubuntu is installed, and forgot to tick the main /sda logical drive at the top. Doh!

So now, when I try to boot I get to the GRUB RECOVERY prompt and that is all.

How can I fix this situation please?

I think it has to do with running a grub command like "setup hd0,1", but I want to be sure first. 

I have the following partitions under /dev/sda (from memory, probably not totally accurate):

/sda1 - OSX
/sda2 - OSX
/sda3 - /SWAP
/sda4 - /
/sda5 - /HOME

The first two are part of the OSX install. The last three are Linux. I would like to confirm this fully, but also don't know how.

Finally, as you can see this is a dual boot system and I need to be very careful. It is also my work computer and has a lot of important data on it!!! :yikes:

Any and all help greatly appreciated.

Thanks.

---

### Post by darkod on 2010-06-25
Are you using GPT or DOS type partition table? DOS type would need to have one of the partitions between sda1 and sda4 as extended, which means it can't be swap or / partition.

Boot the ubuntu cd in live mode and in terminal check the partitions with:

sudo fdisk -l

And by the way, /dev/sda is NOT a logical drive. It's the MBR of disk /dev/sda. And if in your setup you were using grub2 as main bootloader, it always goes to the MBR, not in sda4.
If on the other hand you are using another bootloader on the MBR, then you did right and this bootloader should chainload to grub2 on sda4.

---

### Post by tedrogers on 2010-06-25
> **darkod said:**
> Are you using GPT or DOS type partition table? DOS type would need to have one of the partitions between sda1 and sda4 as extended, which means it can't be swap or / partition.

Boot the ubuntu cd in live mode and in terminal check the partitions with:

sudo fdisk -l

And by the way, /dev/sda is NOT a logical drive. It's the MBR of disk /dev/sda. And if in your setup you were using grub2 as main bootloader, it always goes to the MBR, not in sda4.
If on the other hand you are using another bootloader on the MBR, then you did right and this bootloader should chainload to grub2 on sda4.

To be honest I'm just fumbling around in the dark a lot of time! 

Here's my fisk -l result....you were right:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          26      204819+  ee  GPT
/dev/sda2   *          26       34852   279740840   af  HFS / HFS+
/dev/sda3           34852       34977     1000000+  82  Linux swap / Solaris
/dev/sda4           34977       36205     9871002   83  Linux

```

So it looks like sda 3 is my swap and sda4 is my root. 

I have sda5 as well as my home (I can mount this from the live cd), but for some reason it is not listed here.

So where from here? I have the live CD open now. Is the a quick solution to this?

Thanks.

---

### Post by darkod on 2010-06-25
If you are sure you were using grub2 on the MBR, to add it from live mode:

sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

But I have never worked on OSX/Ubuntu dual boot, and don't know how it looks like. Can you boot OSX from grub2 like that? How did you make the original dual boot with 9.10 work, any special steps?
You should know more about this than me, you made it work once already. :)

---

### Post by tedrogers on 2010-06-25
> **darkod said:**
> If you are sure you were using grub2 on the MBR, to add it from live mode:

sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

But I have never worked on OSX/Ubuntu dual boot, and don't know how it looks like. Can you boot OSX from grub2 like that? How did you make the original dual boot with 9.10 work, any special steps?
You should know more about this than me, you made it work once already. :)

It's been a while...I can't be sure. I think I was papping it when it did it last time, but had a eureka moment and it was all okay.

I'm going to reinstall from the live CD and do it that way I think.

Thanks.

---

