---
title: "Amusing dual-boot shenanigans"
date: 2012-02-20
forum: Installation &amp; Upgrades
---

### Post by flemur13013 on 2012-02-20
Hi - Ubuntu 10.04.3/64 on eMachines ET1831-07 with SATA disk. And one of those noxious 100mb boot partitions.

This is a fun tale about converting from a one-disk dual boot, to a two-disk dual-boot!  (Originally dual-boot with Win7, which I only use to run a couple of DVD programs. )

I moved the NTFS partition to a different position on the same disk (using gparted which screws up Win7 boot partitions!) and it was never to boot again.  Dual booting sucks - there's so many problems with it in this forum...

I had recently discovered that this machine ( a **great machine** for the bux!) has an IDE connector so I could install Win7 on an old spare disk, then choose whether which OS to boot by choosing the disk in BIOS.  Or so I thought.

I plugged the IDE disk in, booted ubuntu and it showed up fine: an empty ext4 partition.

Then I installed Win7 to the new IDE (used) disk - MISTAKE!
(Also got into BIOS to make sure IDE was enabled, disk boot order, etc)

I could boot Win7, but it booted even if I selected the (supposedly untouched!) disk with GRUB pointing to ubuntu. **No more ubuntu**. 

So I physically removed the IDE disk with windows from the computer, and it **still** tried to boot windows.

So I put in the ubuntu LiveCD and selected DVD boot...and it **STILL tried to boot windows**!   It wouldn't (try to) boot ubuntu from the DVD.  I have no idea what was going on here**?!?!?**  And now all I can boot from disk or DVD now is a new install of Win7, which is virtually useless. No LiveCD and no HD ubuntu.

So I booted puppy linux from an SD card (**phew!**) and tried the "pup-partition-copy" (whatever it was called), which **failed** to copy my backup of the 100mb boot partition.  So I deleted all the files on the 100mb partition and just copied the files from the USB backup. 

Now I could boot again from DVD, but not from HD.   **Huh? ** What's up with the apparent connection between **booting from DVD, and the 100mb boo**t partition?!?!?

Since I have complete USB-disk copies of both "/" and "/home" and wanted to **get rid of anything to do with windows** on this disk, and get rid of that stupid 100mb partition, I booted the LiveCD, **deleted all the partitions** on the main SATA drive and created /=15GB  and /home=100GB and a swap and installed ubuntu there.  

And it booted and ran fine, but all the many updates and my many mods were gone. ***_Sigh._***

**So I booted the LiveCD and [B]deleted all the files** from "/" and from /home and **copied USB backups** to / and /home (with nautilus as root - I have links that seem to confuse "cp -a" or "cp -r" no matter what I do, but nautilus works fine...), then I edited /etc/fstab and /boot/grub/grub.cfg to change the UUIDS. (this **actually worked**(!), tho with the hassles below...)

Boot from disk - almost.  There's another uuid to change in grub.cfg!  So I change it.

Boot from disk - almost.  Got errors about **can't mount anything** and "/dev/disk/by-uuid", so I changed fstab to use **LABELS** - which once again proves to be s**uperior to UUIDS** - (using LiveCD yet again). I also changed the links in by-uuid directory to absolute rather than relative...this seemed to fix some stuff, but they changed back.  This directory was empty when I was running from the LiveCD, so there's something tricky going on here...I don't know a whole lot about this..

Now it booted and all the updates (kernel, etc) were there but **X and fluxbox wouldn't start**.  I had to own "/home", and chmod a+w /tmp, then everything worked.  (I don't understand how the permissions change when I make the same sort of installs with exactly the same user name and password, so when I copy the /home-backup to /home, I don't own it anymore?)

Anyway, that was fun. Almost, sorta.  

I'm going to put the IDE disk back in and see if windows will run without screwing up the other drive like the install did.  If not I'll just use my GF's computer for that one program that won't run under wine!

---

### Post by flemur13013 on 2012-02-22
Although the system booted and ran, it turns out that copying "/" from USB -> HD using "nautilus" screwed up the file permissions and affected audio and some other things ("cannot connect to server" from various places).  Next time I'll try rsync or grsync for "/" restore, NOT nautilus.  Anyway I ended up un/re-installing customizations - not too hard if you keep a list - but kept my old /home.

---

### Post by oldfred on 2012-02-22
When you copied to your USB drive what format was the partition? NTFS does not support ownership & permissions so you lose those. You can either use extx or compress the backup with tar and then the permissions & ownership are preserved.

Often BIOS promote IDE drives to sda. Windows (and grub) usually install the boot loader to sda. Many suggest disconnecting the other drive when installing to avoid issues, but even then if Windows is installed to sda, but then the added drive makes it sdb it can cause confusion. 

I like labels also but have not converted to them yet. Few even know you can use labels instead of UUIDs.

---

