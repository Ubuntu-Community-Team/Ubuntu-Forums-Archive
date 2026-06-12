---
title: "UUID, fstab, GRUB -moving Ubuntu to ext USB Drive"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by NTL2009 on 2012-05-29
Sorry for the length, but I have done testing and made progress, so I'm detailing the steps that worked for me.

The end goal is to move my current 10.04 install (separate / and /home partitions) to an external USB drive, and to be able to boot from that or my current install with or w/o both drives connected. At that point, after some testing, I will wipe my internal drive and install Xubuntu 12.04. I also want to be able to boot the external on another machine, so I want a GRUB2 on the root of that ext drive. Lets say my internal current install is on sda1 (/) and sda2 (/home), and my external is sdb1, sdb2.

I have attempted this in the past, and always seem to run into boot issues. So I am taking some baby steps here, to verify each step in my processes.

I  plan to use Grsync with proper 'excludes' to copy each partition. I like Grsync as it does not require a same size or larger partition (I have lots of free space on my current install). I think that to boot the copy, there are a few  things I need to do:

A- Find UUIDs of the partitions I copied to (sudo blkid), and update /etc/fstab with those UUIDs in the root of that copy.

That's easy, but the next steps involve installing and updating GRUB2, and I always seem to run into problems here. The problems seem due to the fact that since I can't (yet) boot into the ext, I  have to 'tell' my system where I want the GRUB2 installed and updated. 

B- I see various methods for this, some examples are like:

sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX

and some others guides where you do something similar, then chroot into it, and some include various --bind commands. I'm confused by all these options. None have worked for me to make the external bootable, even though I seem to get around any errors.


So - here are some baby steps, where I created a UUID mismatch, and fixed it, and that DID WORK for me:

I installed 12.04 Xubuntu on the external, and tested that it booted - OK. NOTE- this is a new install with no UUID conflicts with any other drives.

I then CHANGED the UUID on that / (using tune2fs command), and as expected, it would no longer boot.

I edited /etc/fstab to match the new / UUID, and as expected, it still would not boot (still needs a grub install or upgrade).


Since I fail when I try to 'point' another install to the GRUB2 on this external, I then tried this trick:

Returned the UUIDs and fstab to their original values, and boot this install.

_From this running install,_ I change the / UUID to a new value, and edit fstab to match. I was a little surprised it allowed me to change my 'own' / UUID, but it did.

_From this running install,_ I sudo grub-install /dev/sdX (sdb in my example), then sudo update-grub. 

My boot/grub/grub.cfg got updated with the new UUID this time, and it boots!


So to summarize,  my fstab edits & GRUB commands seem to work when I'm in the system that I am updating. But trying to update sdb, when I am running from sda or a LIVE USB/CD, doesn't work for me.

I guess I can do my working process if I move that ext drive copy to another computer, or remove the internal. **But I'd really like to just copy, edit fstab and then update GRUB _from another running install._** Any suggestions as to what I'm doing wrong?

edit/add: FYI, I partitioned my external as GUID, if that makes any difference.

-NTL2009

---

### Post by oldfred on 2012-05-29
GUID or gpt can make a difference. As long as you just copy files that part should be ok, but you cannot use any of the low level tools like dd to copy as Partition structures are different.

With gpt and BIOS you also need another bios_grub partition to get grub to install correctly. It only needs to be 1MB and in gparted add a bios_grub flag, do not format. I use gpt on two of my drives with BIOS and once I create the bios_grub, I have no issues.

If drive is only going to be Ubuntu (never Windows), I would suggest using gpt not MBR as the partitioning scheme. You then do not have any logical partitions, they are all primary and it has a backup in case of problems. You do have to create a tiny bios_grub partition to correctly install grub2's boot loader to the drive.
If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive.

You can set bios_grub flag in gparted or with command line: In GPT fdisk (gdisk), give it a type code of EF02. Or with terminal:
sudo parted /dev/sda set <partition_number> bios_grub on

Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)

If you change fstab & grub.cfg to use new/correct UUIDs you should be ok. With change to gpt you have to also change the insmod commands also.
insmod part_gpt

You can use this to purge & reinstall grub & then it should update correctly (if you have the bios_grub partition). If you need more help post link to your exact configuration.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

If you can boot into your new(copied)  install you can install grub to the MBR with this.

#reinstall from working (not liveCD) system - first find Ubuntu drive (example is drive sdb but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb

You may be able to just run the sudo update-grub to find the copied install.

Grub also remembers the hard drive (& partition) to reinstall to:

#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

#More info here
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by NTL2009 on 2012-05-29
Thanks so much **oldfred**.

I'm glad I added the GPT comment. Interestingly, I formatted this drive as GPT (did not specify any area with a bios_grub flag), then just installed 12.04 Xubuntu from LIVE USB to verify that it booted OK, and it did. But then when I started 'playing' with it, I got some of those 'unreliable blocklist' warnings. At that point, I used gparted and set a 1MB un-allocated section with that bios_grub flag. Then the commands worked w/o that warning.

But that might have left me with a mix of boot stuff, I dunno. I may go back and repartition from scratch if that boot-repair program doesn't help.

I do like the GPT, nice to just set a bunch of primary partitions and not worry so much about extended and mapping everything out.

-NTL2009

---

