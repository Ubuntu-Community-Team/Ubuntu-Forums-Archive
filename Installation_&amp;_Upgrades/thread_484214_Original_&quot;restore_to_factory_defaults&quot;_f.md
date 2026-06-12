---
title: "Original &quot;restore to factory defaults&quot; function destroyed by ubuntu!"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by Mountaingod on 2007-06-25
When I bought my Packard Bell laptop it came with Windows XP and no CDs. Instead, 4gb of my 20gb hard drive was a 'hidden partition' accessed only by a Packard Bell program. This program allowed the user to completely reset the laptop to factory defaults, with a clean HDD and a 'new' copy of XP. I've used this 'clean install' type function a couple of times when my computer has started to get too bogged down with crap and I wanted to start over.

I recently installed Feisty to dual-boot, using the installation disk. I was careful not to touch my 'hidden' partition in the process, so that I had that safety net in case anything went wrong. As is standard, I reduced my windows partition and used the freed space to make my Ubuntu partition.

I now want to restore my laptop to factory defaults using the aforesaid Packard Bell program. I can't however, because it tells me the backup partition no longer exists. I know this to be untrue, so I think it's GRUB that's doing it. At startup, GRUB gives me all the ubuntu booting options, plus Windows XP, plus another one: the 'recovery program'. I think this is what the Packard Bell restore program uses when resetting my laptop, however selecting it from GRUB gives a blue screen of death.

I never asked Feisty to alter that partition. I specifically avoided it doing so during the repartitioning, and yet it has still managed to destroy my ability to restore to factory defaults. As I have no Windows XP disks, this puts my whole copy of that OS in jeopardy.

Can anybody help me restore this functionality to my laptop? I intend to start it all over, then immediately use all the freed space for a bigger Ubuntu partition (which I'll reinstall shortly afterward). I can't do this though if Packard Bell's restoration program is FUBAR.

---

### Post by Yoooder on 2007-06-25
If you have avoided that partition, then it shouldn't have been altered in any way.  As for the "recovery program" GRUB entry, I'm not sure that it would have been automatically added by Feisty--it could just be a poorly configured entry.

First: I would use gparted (a partitioning tool) to ensure that the 4gb restore partiton is in fact present.

Second: I would try to locate a Packard Bell bootdisk, one that will restore their factory MBR (master boot record) which will replace grub with the original boot menu, and should allow you to run their recovery program.

---

### Post by Mountaingod on 2007-06-25
I know the partition is still there because ubuntu gives me the option of mounting and accessing it. Windows doesn't (and with my windows installation, it wasn't supposed to, hence hidden).

The master boot record looks like just what I'm after. You're saying GRUB replaced whatever that was with its own stuff, and I need to get hold of the original replace *GRUB* with *that*?

There's at least one other laptop around here that's identical to mine. We bought 3 identical laptops at the same time. The aforementioned Packard Bell recovery program allowed you to put whatever is in the hidden 4gb partition onto a series of CDs, therefore freeing up the HDD space. I probably should have done this before installing the ubuntu partition. I might create said 'recovery discs' with one of the other laptops around here and see if I can use them to reinstall windows and my entire factory-default setup on this laptop.

I don't see any other way I could get hold of a Packard Bell bootdisk. I'm guessing the set of recovery discs you create has a bootdisk element to them, given the nature of the whole recovery process.

---

### Post by hardyn on 2007-06-25
if you don't NEED the recovery disk.. most really don't...

hit up your local computer shop and get a windows OEM CD, they might charge 5-10$ for service... now this IS legal, because you have purchased the license, you have just "lost" your media.  Use the replacement CD with number that is on the sticker that came with your notebook.

Damaged media happens, and it is very unreasonable that you should buy a new license for lost media.... I upgraded the processor on my sisters machine, and behold, the recovery disk would no longer work; i BT downloaded a replacement disk and installed using her MS license number; i did have to call MS to have XP verified, but that took about 5min.

---

### Post by Mountaingod on 2007-06-25
Hm, that would probably be the easiest way then. All I need to know is where I would find my license number... bearing in mind I got NO original CDs with my laptop.

---

### Post by hardyn on 2007-06-25
it should be a sticker on the bottom of the laptop body.

---

### Post by Yoooder on 2007-06-26
...if you have another identical machine with Windows and the restore partition in tact, then you could copy the MBR from it to your machine to see if it will work.

Here's the process:  You'll need the Ubuntu CD and a floppy or usb flash drive (to store the mbr on, and move it between machines).

Go to the machine with the default Packard Bell installation on it:
1) Insert the Linux CD and boot it up, electing to boot from CD
 - elect the Start/Install option from the GRUB menu that appears (no worries though, we aren't installing)

2) Once Linux is booted, insert your floppy or usb drive and make sure you can see it (it should pop up on the desktop)

3) Open Terminal from the Applications menu

4) Type the following command to make a backup of the machine's MBR:
> dd if=/dev/[hda or sda] of=/home/ubuntu/Desktop/mbr.backup bs=512 count=1

* You'll need to use either hda or sda in the above command, if the laptop is older it will probably be hda, if it's relatively new then it could be sda

At this point you will have a file called mbr.backup on your desktop, this is a copy of the machine's MBR.  Now copy this file to your usb drive or floppy, and take the drive/floppy to your laptop with the *lost* restore partition.

1) Repeat the above process to ensure you have a backup of this machine's MBR.  You'll need the change the "of=/home/ubuntu/Desktop" to "of=/home/[username]/Desktop".  Rename the file to mbr.backup2 and copy it to your removable media.

2) copy the backup (mbr.backup) from the first machine to your Desktop (only so I can give you a more specific command).

3) Again, open Terminal and issue the following command (note that the if and of parameters have been swapped--this will copy your backup overtop of the drive's mbr).
> dd if=/home/[username]/Desktop/mbr.backup of=/dev/[hda or sda] bs=512 count=1

There you go.  You have just copied the MBR from the 1st machine to the 2nd (and made backups of both in the process).  You'll need to reboot the sick computer to see if it's worked.

**If it fails to boot, repeat the second half of the process (without making another backup) to restore your mbr.backup2 to your drive's mbr.  If this happens you could try changing the "bs=512" to "bs=1k", and redoing the whole process.**

**Also, please be very careful with these commands.  "dd" is a means of copying raw data, and if you bugger the parameters it could cross from your mbr into your partition table and/or data and possibly corrupt the filesystem**

---

### Post by Mountaingod on 2007-06-26
OK, I'll have a (cautious) go at that then. It is quite convenient there's like-for-like computers around here. Is there a clear way to tell whether I need 'hda' or 'sda' in the command?

Thanks a lot for all this.

---

### Post by kraigory on 2007-06-28
How big is your hidden partition? If it isn't that big, then it might be a sign that it works similarly to the way I believe my dell system works:

The hidden partition only stores the UTILITY (in my case, norton ghost) that restores the data. The hidden partition on my dell laptop is only a few megabytes, obviously not enough to store an entire backup image or anything. There is also a not-hidden "backup" partition with 20gb or so, that is designed to hold a norton ghost backup image. So you back up your system to the not-hidden partition if you want, and then if you need to use it, you can boot from the hidden one (not sure how, i only found it in GRUB) and it boots into norton ghost and will restore from your backup partition. That's just dells way of giving you the option of using the backup partition (I use it for ubuntu lol) to restore, so it doesn't take up lots of your hard drive with a restore image if you don't want it to. 

Not sure if this is the way yours works at all, just a suggestion.

---

### Post by Mountaingod on 2007-06-30
Copying the MBR over worked perfectly! Thanks everyone for their help. I've somehow got another problem now, but that's for another thread...

thanks again.

---

### Post by dlycklama on 2007-07-27
This is on-topic, but has nothing to do with Ubuntu. I just need to lay an egg.. I had the same problem with a Packard-Bell laptop and a 4GB BACKUP partition. This laptop was bought in Holland, got a virus in Portugal and was reformatted and reinstalled with Portuguese XP Home. It then got another virus. No recover cd. This site helped a little, in that I was able to determine that there WAS a backup partition but, because I don't use Ubunto, I had to find another way of getting the laptop restored to its factory settings. I did, and it's easy as anything:

- Go to [http://support.packardbell.com/cz/mypc/?PibItemNr=6945490100&PibItemParent=platform_J4](http://support.packardbell.com/cz/mypc/?PibItemNr=6945490100&PibItemParent=platform_J4)
- Download BOOTDISK16.EXE, run it and create a bootable CD-R
- Boot from the CD-R
- When it asks for the recovery CDs/DVDs, hit ESCape to go to the DOS prompt.
- Go to drive A: do a directory, and you'll find a batch file called F11.BAT
- Execute the batch file.
- Remove the CD
- Re-boot

This will get you straight into the recovery process.

Sorry to dump this here, but it took me almost 2 hours to figure out. As I said, I needed to lay an egg.

Douwe Lycklama
Portugal

---

### Post by stchman on 2007-07-27
> **Mountaingod said:**
> When I bought my Packard Bell laptop it came with Windows XP and no CDs. Instead, 4gb of my 20gb hard drive was a 'hidden partition' accessed only by a Packard Bell program. This program allowed the user to completely reset the laptop to factory defaults, with a clean HDD and a 'new' copy of XP. I've used this 'clean install' type function a couple of times when my computer has started to get too bogged down with crap and I wanted to start over.

I recently installed Feisty to dual-boot, using the installation disk. I was careful not to touch my 'hidden' partition in the process, so that I had that safety net in case anything went wrong. As is standard, I reduced my windows partition and used the freed space to make my Ubuntu partition.

I now want to restore my laptop to factory defaults using the aforesaid Packard Bell program. I can't however, because it tells me the backup partition no longer exists. I know this to be untrue, so I think it's GRUB that's doing it. At startup, GRUB gives me all the ubuntu booting options, plus Windows XP, plus another one: the 'recovery program'. I think this is what the Packard Bell restore program uses when resetting my laptop, however selecting it from GRUB gives a blue screen of death.

I never asked Feisty to alter that partition. I specifically avoided it doing so during the repartitioning, and yet it has still managed to destroy my ability to restore to factory defaults. As I have no Windows XP disks, this puts my whole copy of that OS in jeopardy.

Can anybody help me restore this functionality to my laptop? I intend to start it all over, then immediately use all the freed space for a bigger Ubuntu partition (which I'll reinstall shortly afterward). I can't do this though if Packard Bell's restoration program is FUBAR.

There should have been a way to make a recovery CDs or DVD of that partition.

You can call M$ and get an XP CD for like $30.  They will ask for your XP WPA key and send you a disc.

---

