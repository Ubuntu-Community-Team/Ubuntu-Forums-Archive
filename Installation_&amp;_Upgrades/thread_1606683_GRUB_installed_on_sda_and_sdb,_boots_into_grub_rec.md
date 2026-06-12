---
title: "GRUB installed on sda and sdb, boots into grub recovery"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by akand074 on 2010-10-26
Hey guys,

So I decided to finally install 10.10, been putting it off for a while. I have a 1TB hard drive (my /home drive) and I have another drive (my / drive). When I built my computer I ran it on my 1TB hard drive first so it became sda, while my other hard drive actually running the OS is on sdb. Any ways, prior to 10.10, grub was installed on sda (I guess the MBR is there). I thought, hey why not install it on sdb because that is where the OS is, so I did that (honestly knowing that it would mess everything up but wanted to give it a try anyways). Now when I boot it goes to a command line screen saying "Grub Recovery />" or sum sort. 

I tried reinstalling grub on sda but I couldn't mount it correctly because its just a data partition. So I just reinstalled grub on sdb (using a Live CD) and it didn't change anything. If I do sudo fdisk -l, this is what I get:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe2fb01ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001    5  Extended
/dev/sda5               1      121601   976759969+  83  Linux

Disk /dev/sdb: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63ce5f06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       42010   337443840   83  Linux
/dev/sdb2           42509       43777    10193242+   7  HPFS/NTFS
/dev/sdb3           42011       42508     3998721    5  Extended
/dev/sdb5           42011       42508     3998720   82  Linux swap / Solaris

Partition table entries are not in disk order

```

As you can tell, sdb1 and sda1 are both flagged to boot.. which I would assume to be the cause of the problem. Is there anyway I can remove that flag from sda1 and it would work? Otherwise how would I go about fixing this? I was thinking that I unplug my 1TB hard drive and boot the computer, grub should load fine, and then maybe if I plugged my 1TB drive back in that it would work just fine from then on, but I've already booted into this Live CD for the second time and didn't want to a third time so I decided to see if anyone had any ideas while I'm already here. If not I'll give that a try.

Thanks for any help!

---

### Post by drs305 on 2010-10-26
Let's first try to just reinstall on sdb1, if you haven't done that.

Boot the LiveCD, then mount sdb1. Note in the second command you don't include the partition number:

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

Change your BIOS to boot sdb first.

If this doesn't fix things, you can either attempt to purge/reinstall Grub with the instructions in this thread:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")


or post the contents of RESULTS.txt after running the boot info script from here:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Note: Don't worry about the boot flag. It's not used by Ubuntu. It IS used by Windows. If you really want to remove it, use System, Administration, Disk Utility. Highlight the partition, then Edit Partition in the bottom section and untick "Bootable".

---

### Post by akand074 on 2010-10-26
> **drs305 said:**
> Let's first try to just reinstall on sdb1, if you haven't done that.

Boot the LiveCD, then mount sdb1. Note in the second command you don't include the partition number:

```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```Change your BIOS to boot sdb first.

If this doesn't fix things, you can either attempt to purge/reinstall Grub with the instructions in this thread:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")


or post the contents of RESULTS.txt after running the boot info script from here:
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Note: Don't worry about the boot flag. It's not used by Ubuntu. It IS used by Windows. If you really want to remove it, use System, Administration, Disk Utility. Highlight the partition, then Edit Partition in the bottom section and untick "Bootable".

Wow, set sdb to boot first, I can't believe I didn't think of that. Unfortunately, for some reason my bios wouldn't allow me to switch sdb to boot first. But I selected it manually and now I'm booted in to 10.10 just fine.. I might try to switch it again later maybe now that I have booted into it, it might let me. Otherwise I could try to unplug sda then change the boot order.

Do you think I should still purge all the grubs on both drives? Then reinstall it to sdb? Or its unneccessary if I can get it to boot to this hard drive first anyways I guess.

---

### Post by drs305 on 2010-10-26
> **akand074 said:**
> Do you think I should still purge all the grubs on both drives? Then reinstall it to sdb? Or its unneccessary if I can get it to boot to this hard drive first anyways I guess.

No, I would leave it as it is. If it does what you want, I wouldn't try to 'fix' anything until it breaks.  :-)

You might want to check fstab and your /boot/grub/grub.cfg files to make sure that they use UUIDS, which will be a better option should you move things around again.

If you don't have any more questions, please mark this SOLVED via the 'Thread Tools' link (it's reversible).

---

### Post by akand074 on 2010-10-26
Figured out how to set sdb to boot first, perfect now. I actually have one more question if you don't mind. When I first built this computer I used a monitor at 1680x1050. Lucid was actually booting at a lower resolution so I set it manually to use 1680x1050 on boot, but then removed it when I got my new monitor running at 1920x1080. Anyways what happens now is that my BIOS screen (and previously my boot splash) ran at 1680x1050 even on my 1920x1080 monitor. I figured a clean install should fix it. Now the boot splash is running fine but the BIOS screen is still at 1680x1050, and then after I choose Ubuntu from grub you can tell its still at 1680x1050 but then you can clearly see the screen resolution change to 1920x1080 where its at a black screen for a few seconds, then goes to the ubuntu boot splash for barely a second or two then to the login screen.

Do you think having the MBR on sda has anything to do with it? I mean it really doesn't matter, it just not aesthetically pleasing.

---

### Post by drs305 on 2010-10-26
> **akand074 said:**
> 
Do you think having the MBR on sda has anything to do with it? I mean it really doesn't matter, it just not aesthetically pleasing.

No. 

I've ready about similar issues but haven't experimented with these settings myself. I know I've read (but not bookmarked) posts in these forums that detail how to make a more seemless transition between the various graphic displays. 

Initially experimenters thought that the gfx mode and gfx keep settings were what was going to work but at least initially these proved less than satisfactory. I don't think the solution involved those but I could be wrong, or perhaps they finally do work.

I'm about to log off for the night. If I find time and sufficient brain cells I'll try to remember to poke around a bit in the next day or so and see if I can find the info.

---

### Post by akand074 on 2010-10-26
> **drs305 said:**
> No. 

I've ready about similar issues but haven't experimented with these settings myself. I know I've read (but not bookmarked) posts in these forums that detail how to make a more seemless transition between the various graphic displays. 

Initially experimenters thought that the gfx mode and gfx keep settings were what was going to work but at least initially these proved less than satisfactory. I don't think the solution involved those but I could be wrong, or perhaps they finally do work.

I'm about to log off for the night. If I find time and sufficient brain cells I'll try to remember to poke around a bit in the next day or so and see if I can find the info.

That's fine, it was mere curiosity, maybe I'll post a thread on it in the future, its not part of this thread so I'll mark this one as solved.

---

