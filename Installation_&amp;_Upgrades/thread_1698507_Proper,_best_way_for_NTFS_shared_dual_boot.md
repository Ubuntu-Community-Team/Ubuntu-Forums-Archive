---
title: "Proper, best way for NTFS shared dual boot"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by volkswagner on 2011-03-02
Greetings, 

I installed 10.04 dual boot with XP.

I used advanced partition scheme and added partitions for /, /home, /swap, and and NTFS partition mounted at /home/username/Desktop/DATA.

Unfortunately the NTFS partition was created as a "Linux (0x83)" partition and therefore is not recognized inside Windows. I did not even realize there was such a thing as Linux only (Non MS) NTFS partition. :(  I don't even recall the details when selecting the partition type.

I tried using disk Ubuntu utility to change the type to "HPFS/NTFS (0x07)".  While mounted I get error after long delay (hang) high CPU usage error "Message did not receive a reply (timeout by message bus)"

If I try the same change with DU after unmounting the volume, I get the same error.

I'm in the process of moving/backingup all data on the volume.  I'll most likely reformat.  Question is, shall I format with Gparted or within Windows Disk Manager?  I seem to recall some odd permission problems in the past with mounted NTFS volumes.

---

### Post by Morbius1 on 2011-03-02
> I used advanced partition scheme and added partitions for /, /home,  /swap, and and NTFS partition mounted at /home/username/Desktop/DATA.

Unfortunately the NTFS partition was created as a "Linux (0x83)"  partition and therefore is not recognized inside Windows. I did not even  realize there was such a thing as Linux only (Non MS) NTFS partition.None of that makes any sense so it's best to post some facts so people here can help you.

Please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```

---

### Post by volkswagner on 2011-03-02
> **Morbius1 said:**
> None of that makes any sense so it's best to post some facts so people here can help you.

Well I guess that makes two of us.... why would Ubuntu installer set NTFS partition type to Linux.

Please realize the issue here is When using MS Windows, the partition DATA is listed as unknown, healthy but not browsable.

Here is comparison shots of Windows Created NTFS, vs. Ubuntu created NTFS.  Take note of different "partition type".

Windows:
[IMG]http://volkswagner.com/gate/DU-1.png[/IMG]


Ubuntu:
[IMG]http://volkswagner.com/gate/DU-2.png[/IMG]
 
> **Morbius1 said:**
> 
Please post the output of the following commands:


sudo blkid -c /dev/null

```

/dev/sda1: UUID="C8F029D1F029C692" TYPE="ntfs" 
/dev/sda2: LABEL="DATA" UUID="2585E0EB55D6A7ED" TYPE="ntfs" 
/dev/sda3: UUID="ce36a54c-bd0c-4532-9abb-4f6198d0f522" TYPE="swap" 
/dev/sda5: UUID="695195ed-ab55-4c24-a05a-53c181814c63" TYPE="ext4" 
/dev/sda6: UUID="4ec0aab7-4e14-4895-adc6-a23706bde706" TYPE="ext4" 
```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=695195ed-ab55-4c24-a05a-53c181814c63	/	ext4	errors=remount-ro	0	1
#Entry for /dev/sda6 :
UUID=4ec0aab7-4e14-4895-adc6-a23706bde706	/home	ext4	defaults	0	2
#Entry for /dev/sda2 :
UUID=2585E0EB55D6A7ED	/home/eric/Desktop/DATA	ntfs-3g	defaults	0	0
#Entry for /dev/sdb1 :
#this may have been added due to installing smartmontools and having usb mounted so I commented out
#UUID=0E84E2B384E29C89	/media/0E84E2B384E29C89	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077	0	0
#Entry for /dev/sda3 :
UUID=ce36a54c-bd0c-4532-9abb-4f6198d0f522	none	swap	sw	0	0

```


mount
```

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/eric/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=eric)
/dev/sda2 on /home/eric/Desktop/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

```

---

### Post by Morbius1 on 2011-03-02
Yikes,  I didn't even think that was possible. There may be a way to change the "partition type (0x86)" without reformatting but I sure don't know how. 

If you're reformatting it anyway I would use Windows. Even though Linux seems to be OK with the inconsistency of a Linux partition type for an NTFS formatted partition, Windows most certainly is not. Make Windows happy first then alter the fstab entry since the UUID number will change with every reformat.

BTW, If it were me I wouldn't mount it to the Desktop. I would mount it to:
/home/username/Data. 

It will have the same affect in that a mount icon will be produced on the Desktop.

Sorry, this is a new one to me.

---

### Post by volkswagner on 2011-03-02
Yeah, I was really hoping to understand why Ubuntu installer would mark the partition as Linux.

Anyone know which is best practice, add NTFS partition to share on dual boot, after, before, or during install of Ubuntu.

What really sucks, is I thought I was advancing and implementing what I had learned.  I though to get rid of quirky permission issues, would be to format and mount the NTFS partition using the Ubuntu installer.  Guess I was wrong!

---

### Post by Hakunka-Matata on 2011-03-02
[LIST=1]
[*]Boot into Ubuntu
[*]Click on "Places"
[*]you should see your NTFS drive there, listed as XXGB
[/LIST]

like this Thumbnail shows.  You don't have to do anything else.  

See the 52GB Filesystem?, that's a WindowsXP NTFS partition.

---

### Post by Morbius1 on 2011-03-03
> **Hakunka-Matata said:**
> 
[LIST=1]
[*]Boot into Ubuntu
[*]Click on "Places"
[*]you should see your NTFS drive there, listed as XXGB
[/LIST]
like this Thumbnail shows.  You don't have to do anything else.  
The problem as I understand it is not on the Linux end of things. Even though the partition type is labled as Linux ( 0x83 ) it is in fact formatted in NTFS.

blkid confirms that it is NTFS:
>  /dev/sda2: LABEL="DATA" UUID="2585E0EB55D6A7ED" TYPE="ntfs"Although I wouldn't personally put the mountpoint at that location he has the correct fstab entry:
>  UUID=2585E0EB55D6A7ED    /home/eric/Desktop/DATA    ntfs-3g    defaults    0    0And the output of "mount" confirms that it is in fact being mounted as NTFS (fuseblk ) :
>  /dev/sda2 on /home/eric/Desktop/DATA type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)The problem is with Windows. Windows doesn't recognize the NTFS partition as an NTFS partition.

I've never even read about this type of thing happening before. Perhaps someone with experience in this sort of thing has a more elegant solution than reformatting the partition. I for one do not have that knowledge.
>  Anyone know which is best practice, add NTFS partition to share on dual boot, after, before, or during install of Ubuntu.I have done it after and before but never during the install. If I need to create a new NTFS partition ( or even a new Linux partition ) I do so before I install Linix and I generally use Parted Magic ( [http://partedmagic.com/doku.php](http://partedmagic.com/doku.php) ). It always has a more up to date gparted.

---

### Post by volkswagner on 2011-03-06
Well I guess nobody has answered my question, because it is to easy to figure out.  Why would the Ubuntu Installer create the NTFS as Linux?  I guess the real question is why would it create it any other way... it IS Linux after all!

I was able to solve the issue without reformatting.  Although Disk Utility, and cfdisk did not work, fdisk did.

The fix:
```
sudo fdisk /dev/sda
```

The above gets fdisk command prompt.  From there commands like p (p)rint out the partition table like fdisk -l would. Then t opens prompt to change (t)ype, fdisk asks which partition to change, then asks to what type.  Then reboot after making changes, all is well!

I'm a new fan of fdisk.  I though it was just used to extract info.... I did not know it was such a powerful tool!

I was able to get the help I needed from my local LUG mailing list.  It think the Ubuntu forums are getting overwhelmed by users needing help, with not enough experienced users being able to offer help.

---

### Post by Morbius1 on 2011-03-06
> Why would the Ubuntu Installer create the NTFS as Linux?  I guess the  real question is why would it create it any other way... it IS Linux  after all!Here is the output of a partition created by Parted Magic (  a Linux distro - using gparted ):
>    Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFSIt has no problem creating an ntfs partition type for an ntfs formatted partition. If the installer is doing this to you and you can reliably reproduce it you might consider submitting a bug report.

---

### Post by Dissident Penguin on 2011-05-13
Well, thanks to your problem I could solve mine. I am a Linux newbie and  had been looking for the best way to mount an NTFS volume at boot time  with read and write support so I could have access to my windows  thunderbird mailbox, and after looking in many forums and set-up guides  with very scarce info on how to add entries to fstab, managed to do it  (using a somewhat baroque method creating an ntfs group and adding my  user to it), but for some reason thunderbird couldn't write to some of  my mailbox's folders.

Reading your fstab entries gave me the  answer. Using partition's UUID instead of /dev/sd(whatever), and using  ntfs-3d to mount the volume made it work seamlessly.

Tanks guys!!
DP

---

