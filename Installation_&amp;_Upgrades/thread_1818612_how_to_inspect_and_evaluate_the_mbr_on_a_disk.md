---
title: "how to inspect and evaluate the mbr on a disk"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by danh-h on 2011-08-05
How can i inspect and evaluate the mbr on a disk in a computer?

I'm interested in how to do this in general.

I can use gparted to see the partitions on a disk, but i don't know how to use it, or any other tool, to see just what is in the mbr.

The particular situation i'm in is that i have two disks in my computer.  One has ubuntu 10.10 on a single partition, and one has 11.04 on one of 4 partitions.

The 11.04 disk used to be bootable, but somehow i messed up the disk: longer story: i installed another os on another partition, and the other os redid the mbr and installed a different version of grub, and i tried to reinstall grub but ended up with a disk that wouldn't boot.  So i put my old 10.10 disk back into the machine so that i could at least boot and look around on the 11.04 disk.

Now, there are probably ways that i could recover the 11.04, but i would like very much to be able to systematically analyze the 11.04 disk to determine its exact current state before modifying it.

Since the disk is not mounted it seems like this should be in reach: i want to be able to (a) capture the mbr from the 11.04 disk [into, say, a file on the 10.10 disk] (b) get an analysis of what the mbr would do (where it points to etc, and what is at where it points to) (c) get any high level information which can easily be determined from (a) and (b).

Maybe gparted can do all this but i am just too clumsy with it?

Thanks in advance for any info!

dan

---

### Post by YesWeCan on 2011-08-05
Hi there.
Google for "bootinfoscript". This will produce a comprehensive summary of boot related information for your disks.

Be aware that Grub replaces the normal MBR boot code and works completely differently. Grub boot code ignores the partition table and only boots another Grub program that is usually located in an "unused area" between the MBR and the start of the first partition, about 50 sectors.

---

### Post by Herman on 2011-08-05
If you only want to see your MBR,
```
sudo dd if=/dev/sda count=1 | hexdump -C
```You would need special training and practice to be able to make much sense out of hex code, but some people would be able to.

If you copy and paste that output to a plain text file and store the examples of hex codes from various kinds of MBRs with descriptive file names you can use meld diff viewer to compare the saved files and observe what's different between one kind of MBR and another, or the same MBR after various changes.
There is information on the internet which can help you identify different areas of the MBR, notably [The Starman's Realm]("http://www.oocities.com/thestarman3/index.html").
            
```
sudo dd if=/dev/sda | hexdump -C | less
```The above code will show you your MBR in hexadecimal code, and you can  use your up and down arrow keys to scroll along and scan your hard disk. GRUB writes its core.img to the first track of the hard disk, (about the first 49 or so sectors that follow the MBR, there are 62 of these available and they are normally empty, but may sometimes be used by some other programs and even viruses too). With practice you'll be able to see if the first track is empty or if there's some code before the first sector of the first partition. You can learn to recognize a boot sector when you see one too, with a little experience.

To make a backup copy of your MBR, (excluding the partition table),
```
sudo dd if=/dev/sda of=/home/danh-h/11-08-05_MBR.img bs=446 count=1
```To make a backup of the first track of your hard disk, (exluding the MBR),
```
sudo dd if=/dev/sda skip=1 of=/home/danh-h/first_62_sda.img bs=512 count=62
```To restore the first track,
```
sudo dd if=home/danh-h/first_62_sdb.img skip=1 of=/dev/sda bs=512 count=62
```To restore the MBR from a backup, (excluding the partition table),
```
sudo dd if=/home/danh-h/11-08-05_MBR.img of=/dev/sda bs=446 count=1
```The reason I choose not to include the partition table in any MBR backup is because if the partitions are changed and the MBR restored from an old backup it can cause users to lose access to their data and anyway one can always use TestDisk to write an new partition table, (if the person knows how). I would rather they not need to learn on my account though. Most websites which give the command for making MBR backups do include the partition table and neglect to provide any warnings. 

And finally, the simple answer is (last but not least), you just need to re-install GRUB from whatever operating system you want to be your main boot operating system.  :)

---

### Post by danh-h on 2011-08-05
Thanks YesWeCan and Herman for your replies.

YesWeCan: The boot_info_script is awesome, imvho.

It certainly does identify exactly what is in the MBR, by name.  (It confirms that indeed the new os i put in wrote in the MBR, and that my attempt at repair was not successful, because the new os's version of grub is still parked in the mbr.)

Herman --- thanks for suggesting using dd to get the raw bytes.   I may still end up doing this, because it seems worthwhile to see just what the raw bytes look like.

One thing that i'm still unclued about is why my attempted reinstallation of grub in the 11.04 disk failed.  Also, i don't know how to boot into an OS except through the grub menu at startup.  It seems like if i should be able, at any time, to boot a partition (provided that it has a kernel on it, etc).

But the boot_info_script is a big step into seeing what is going on.

Thanks all.

---

### Post by oldfred on 2011-08-05
BIOS based computers only boot from BIOS, to MBR, the MBR code is tiny and then loads code from somewhere else on hard drive to continue booting.

There are programs that will try to boot a system. Links to two of them:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

If you boot with grub you can go to grub's command line and manually enter the commands required to boot.  Usually you are just correcting a grub entry.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by danh-h on 2011-08-13
Thanks everybody for your help.

In this particular case i was able to run grub from the 10.10 disk, and then type "c" to grub to get into a grub shell, from which i could boot the chosen partition of the 11.04 disk (using the "linux" and "boot" commands).  This is what oldfred said, and per Herman could the reinstall grub from the 11.04.

(I did download and boot the rescatux, and it had a grub, but i kind of bumbled around with it.)

So this is now solved for me.

dan

---

