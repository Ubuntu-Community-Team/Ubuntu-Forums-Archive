---
title: "Problem installing with RAID 1"
date: 2006-11-17
forum: Installation &amp; Upgrades
---

### Post by treydock on 2006-11-17
I've read all sorts of posts and tutorials on installing using the Software RAID on the installation CD.  I'm trying to install Ubuntu 6.06 Server , LAMP server.  I did the installation now about 10 times, same result everytime.  After the installation completes and computer reboots it says "Failure loading operating system".

I have 2 hard drives, they are the same model and size.  On each one I would put 100mb /boot , 1500mb swap , and 158gb / .  The problem I've read is there is a problem GRUB being loaded onto the RAID.

What I did was create those 3 partitions with their sizes and set them as RAID partitions, then added the MDs, set one to /boot , one to swap and one to /.  Everything goes through , installation continues but I can't boot into Linux.

What am I missing...Do I have to install non-RAID and then setup the RAID after install?

Please help.
Thanks

---

### Post by wkulecz on 2006-11-17
I installed 6.06 to a raid1 array partitioned much like you describe, but I've given up on the need for boot partition since large drive support is in all BIOSes that can support disks greater than 128GB.

My install when smoothly (used the alternate install CD), but later when trying to add another array using a SIL680raid (Medley) PCI IDE controller I failed because data was being corrupted (even with just a normal single drive ext3 filesystem!).  If you are using a SIL680 controller this could be your issue.  I know of no fix.  I got some IDE to SATA adaptors and used the SATA controller on the MB to make the RAID5 array.

If you are using SATA there are issues with certain chipsets, use the search.

Installing non-raid could be a good test to see if your controller has issues.

Good luck!
--wally.

---

### Post by treydock on 2006-11-17
EDIT:  When installing LAMP server , how do I tell it to use LILO and not GRUB ?  I read a few posts and articles that said LILO is better suited for raid.

I have an Asus A8N which I believe uses marvel raid.  I know it worked cause I used to have win2k3 on that computer.

When you say you did your installation like mine but without a boot sector, how did you setup the partitions?  Did you make / bootable or how did it work?

Thanks for response

---

### Post by treydock on 2006-11-17
Doing some reading , is it true that Ubuntu does not support SATA RAID?  My raid is onboard ASUS A8N-VM , and I tried many installs with the raid already built in bios and a few installs without raid being put together.

I really want to use Ubuntu, but I cant get it to work with a simple 2 disk RAID-1 as a LAMP server, but read a few articles that say FC6 and openSUSE can do SATA RAID-1 and LAMP.

But I'd prefer Ubuntu, just need to know how to make it work.

ALL my install attempts either the OS can't be found, or loads improperly and what not.

Please Help 

Thanks

---

