---
title: "Mis aligned partition"
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by Wray on 2014-02-24
I have cloned my new 1 terabyte drive for the second time now.  The first time  i got a warning message 
**"The partition is misligned by 1024 bytes. this may cause poor performance, re partitioning is suggested"**
The second time i got the same warning except now it is 512 bytes.

Anyone have an idea what is going on here?  I used    	 	 	 	   [B]dcfldd if=/dev/sda of=/dev/sdb statusinterval=10 bs=10m conv=notrunc

[/B]It seemed to run fine, took a little over 3hours.

I am running 12.04 with all the updates (I think)[IMG]http://ubuntuforums.org/images/icons/icon11.png[/IMG]

   	 	 	 	   [B]parted /dev/sda unit s print 

 [/B]   	 	 	 	   
[B]     Sector size (logical/physical): 512B/4096B 
[/B]
[B]     Partition Table: msdos 
[/B]
[B]     Number  Start        End          Size         Type      File system     Flags 
[/B]
[B]     1      2048s        1941014527s  1941012480s  primary   ext4            boot 
[/B]
[B]     2      1941016574s  1953523711s  12507138s    extended 
[/B]
**     5      1941016576s  1953523711s  12507136s    logical   linux-swap(v1)**

  Where should the partition  start

---

### Post by oldfred on 2014-02-25
If the error is on the extended partition it is not critical as the extended partition is not written into, but partitions inside the extended partition must be aligned.

I find if not using Windows it just is now better to use gpt. Ubuntu can boot from gpt with either BIOS or UEFI. And I now configure new drives with both an efi partition as first partition and bios_grub so I can boot now with BIOS, but then when I move drive to new UEFI system I do not have to totally reconfigure to use with UEFI.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

Also with these large hard drives, it is better to use a smaller / (root) partition and use rest of drive as /home or data partition(s). Then all boot files are closer together on drive and drive does not have to work so hard just to find system files.

---

### Post by Wray on 2014-02-25
Thanks old fred for your very informative response.  below is  the output of gparted
 
  	 	 	 	Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sdb: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start        End          Size         Type      File system     Flags
 1      2048s        1941014527s  1941012480s  primary   ext4            boot
 2      1941016574s  1953523711s  12507138s    extended
 5      1941016576s  1953523711s  12507136s    logical   linux-swap(v1)
Primary and logical  are multiples of 8 but ext is not.
So, that's still ok, correct?

Interestingly enough i just discovered that  my install ( on /dev/sda) of 12.04 created a FAT16 partition...a bit surprised at that.
What else do i have to do with this cloned disk (sdb) to make it uesable?  Mount? grub?
So many questions, so little knowledge:(
Again many thanks,  without the good folks here i would have no chance at this; even though i have been running  12.xx for , i guess, about 3 years now!

---

### Post by oldfred on 2014-02-25
If an exact clone you cannot use it when your original disk is installed as you have duplicate UUIDs which are not allowed.
I normally suggest a new install and copy /home and list of installed apps to recreate a working system. Often less detail work and easier for a newer user.

You have to change all the UUIDs, edit fstab with new UUIDs and reinstall grub. You may have to edit a few other settings that have saved UUIDs throughout system.

 # To clear cache and get new view of UUID:
sudo blkid -c /dev/null -o list

      
 Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid


 UUID in grub, fstab &
/etc/initramfs-tools/conf.d/resume
Install drive:
more /var/cache/debconf/config.dat  | grep /dev/disk
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

If using in a different computer then you should not have UUID issues but other issues.

 If different computer:
/etc/hostname and /etc/hosts,

---

### Post by Wray on 2014-02-25
I never intended for both drives to be even physically in the system at the same time.

What i wanted was a backup for the system currently in use, so that in the event of a crash
 i could remove the crashed drive and plug in the cloned one and be on my merry way with 
all my settings intact.
your comments seem to relate to having both systems in the system at the same time, which 
never contemplated.
I tried replacing the original, perfectly good drive (that's Why i want to clone it! :)), with the 
cloned one, and the system doesn't see it.    Not mounted?  I think it is mounted at (as) the UUID.

Can i mount it at root while the original drive is in the system?  Obviously, whatever i do i don't
 want to damage the original drive

---

### Post by oldfred on 2014-02-25
As long as it is not plugged in when you boot. 
Then it may randomly use either one or the other as it sees the first one that BIOS reports and that may vary.

---

### Post by Wray on 2014-02-26
[SIZE=4]Success![/SIZE]

Thanks oldfred You are my linux hero!
I find your suggestions are always spot on and your links are GOLD
With your help i was able to do this. Indeed I am posting from the cloned drive.

As i indicated earlier i first tried the dd  if=/dev/sda of=/dev/sdb  Which ran for ~12 hours and seemed to complete, but the system would not see the cloned drive.

Then I ran     	 	 	 	[B]dcfldd if=/dev/sda of=/dev/sdb statusinterval=10 bs=10m conv=notrunc
[/B]Which ran approximately 3, maybe 4hours and booted fine

I definately recommend dcfldd.  It runs much quicker and unlike dd gives an on screen progress report.


Incidentally, will dcfldd clone a windows drive?  In my mind it seems that it should since it creates an identical copy
.  But then, my "mind", in the linux world is gnat sized.
Again, thanks  you will hear more from me i'm sure

---

