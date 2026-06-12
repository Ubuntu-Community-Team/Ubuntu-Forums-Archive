---
title: "Data drive crashed, boot drive no longer boots successfully"
date: 2022-10-16
forum: Installation &amp; Upgrades
---

### Post by peyre on 2022-10-16
I think my data drive crashed while I was performing a backup [COLOR="#40E0D0"]and it may have also munched the ext4 partition on my backup drive[/COLOR] (My mistake, it didn't - I lost data on the drive earlier because my backups weren't completing as they should).  In any case, now the boot drive won't boot (dangit boot drive, you had one job!).  I come to a blank screen with only

```
Ubuntu 22.04.1 LTS peyre tty1

peyre login:
```

at the top.  If I were seeing something like this this in Windows I might be able to do something, but I'm a little out of my depth here since I'm mostly a dumb end user of Linux.  What do I do with this thing?  I first shut down the computer, removed the data drive, and then rebooted and remmed out the lines to auto-mount that drive, but now I simply get to a CLI.  How do I fix this, anyone?  I don't even know where to start.[COLOR="#008080"][/COLOR]

---

### Post by peyre on 2022-10-16
Odd!  On a Windows machine with ext2 Volume Manager, I can open and read my ext4 partition on the backup drive--yet my Linux laptop doesn't seem to see it, *or* the Windows partition on it.

I was also able to connect my storage drive to a Windows machine and see it using ext2 Volume Manager, but it shows as empty.  That's rather distressing, as I don't have a recent backup of all my data. :(  Strange that Linux doesn't see either this or my backup drive at all though.  (The backup drive is a 4TB portable drive with an ext4 and an NTFS partition, for backing up both my computer and my wife's Windows machine.)

---

### Post by oldfred on 2022-10-16
Can you login?
Then it is some sort of gui issue.

You may need to reboot & use escape (if UEFI) or shift key (if BIOS) to get grub menu & boot recovery mode.
Then a minimum menu will offer several options.
Often a crash will require a fsck of any/all open ext4 partitions.
But reason for crash needs separate investigation.

If you cannot get to grub's recovery mode, boot your Ubuntu live installer in live mode & run fsck from it.
[https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by peyre on 2022-10-16
Yes, I can log in.  It's an old computer, so BIOS.  I can get into recovery mode, yes.  It says "Recovery Menu (filesystem state: read-only)" - not sure if that's important.

I told it to fsck all drives.  It said "Continuing will remount your / filesystem in read/write mode and mount any other filesystem defined in /etc/fstab.  I told it to continue, and it immediately said:

/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcS: No such file or directory
fsck from util-linu 2.37.2
Finished, please press ENTER

Then it brings me back to the recovery menu.  I selected fsck again, and its says:

The option you selected requires your filesystem to be in read-only mode. Unfortunately another option you selected earlier, made you exit this mode. The easiest way of getting back in read-only mode is to reboot your system.

If it helps, these are my options in the Recovery Menu:
Resume normal boot
Try to make free space
Repair broken package
Check all file systems
Update grub bootloader
Enable networking
Drop to root shell prompt
System summary

---

### Post by oldfred on 2022-10-16
I do not show a /etc/default/rcS file either.
Files do have to be unmounted for fsck. Often suggested to use live installer, but should work from recovery mode, if no other option selected to mount partition(s). 

I can only suggest trying to boot, sometimes it boots from recovery mode when it does not directly.

---

### Post by peyre on 2022-10-16
:(  Yeah, it just drops me to a command line.

---

### Post by oldfred on 2022-10-16
If that is Linux command line and not grub's, then you are booting and it is a gui issue.
What video card/chip do you have?
And then what driver is installed?

[FONT=monospace][COLOR=#000000]inxi -G

[/COLOR]
[/FONT]

---

### Post by peyre on 2022-10-17
Yes, it's the GUI that doesn't come up.  Linux itself does boot.  My video card is:

Yeston AMD Video Card Radeon RX550 4G D5 LP Gaming Graphics Card GPU, 4G/128bit/GDDR5 PCI-Express 3.0x8 DirectX 12,DVI+HDMI+VGA Desktop Graphics Card (HTPC ITX is compatible)
([https://www.newegg.com/yeston-rx550-4g-lp/p/27N-0042-00062?Item=9SIAZUEEV66160]("https://www.newegg.com/yeston-rx550-4g-lp/p/27N-0042-00062?Item=9SIAZUEEV66160"))

---

### Post by oldfred on 2022-10-17
I do not know AMD cards and what issues they have. I thought they just worked.

I used to have nVidia, but old nVidia card was a lot lower performance than new Intel CPU's video when I built new system.
I do not game, so did not need high performance video.

May need GRUB_GFXMODE in grub settings. From 2020
[https://www.phoronix.com/scan.php?page=article&item=ubuntu-2004-59mesa203&num=1](https://www.phoronix.com/scan.php?page=article&item=ubuntu-2004-59mesa203&num=1)

---

### Post by peyre on 2022-10-18
Hum!  Well, I've removed the video card entirely, and booted with just the onboard video.  That also comes up to a command line.  Maybe there's a permissions issue?  It says:

/usr/lib/ubuntu-release-upgrader/release-upgrade-motd: 31: cannot create /var/lib/ubuntu-release-upgrader/release-upgrade-available: Read-only file system
cat: /var/lib/update-notifier/fsck-at-reboot: 38: cannot create /var/lib/update-notifier/fsck-at-reboot: Read-only file system
run-parts: /etc/update-motd.d/98-fsck-at-reboot exited with return code: 1

/usr/lib is owned by root:

drwxr-xr-x 126 root root 4096 Sep 26 19:35 lib

**Here's the contents of fstab at the moment, with the contents of fstab.bak pasted in, with the one line that was in it this evening at the bottom.**  The contents of fstab.bak I think were from before I wiped the drive and reinstalled from scratch a few months ago.

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb3 during installation
UUID=526d1aaf-fab5-4dbf-9d57-8919cf91a3c2 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb2 during installation
UUID=3D1B-BAAB  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# mount sdc1 on /data
UUID="002e92c4-784a-4cb3-9d52-4171af4804c8"  /home/leon/Storage             ext4    defaults  0       2


# mount floppy disks

---

### Post by oldfred on 2022-10-18
Do you have  a floppy drive? Bit unusual to have that in fstab?

Are you booting to recovery mode? That defaults to read only, so you can run fsck.
But then you can try to other commands. Many need you to turn on networking first.

---

### Post by peyre on 2022-10-18
Yes, this is an old machine (with a Core 2 Duo processor!) and a built-in floppy drive.  I downgraded to the old computer I had in the garage so my 15yo son could have a machine he could game with.

The menu offered different options and I could have selected advanced options and gone into recovery mode, but I didn't this time - just straight Ubuntu.

---

### Post by oldfred on 2022-10-19
My old core2 duo laptop from 2006 would not even install Ubuntu.
I was able to install server and then fallback, a lightweight gui like old gnome2.
I use Kubuntu on my newer & now very new desktop and was surprised that Kubuntu would install on that old laptop. 
Typically old systems need one of the lightweight flavors.

---

### Post by peyre on 2022-10-19
Yep.  My poison is Xubuntu.  It's not as lightweight as Lubuntu or puppy, but much lighter than mainstream Ubuntu.  It runs nice and snappy, even fairly quick on this system if I don't tax it with something heavy like LOTRO or compiling software.

I'll try fscking the drive.  Anything else to suggest?

---

### Post by peyre on 2022-10-19
Ok, so fsck /dev/sda (this is the only drive attached) returns:
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem. If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
  e2fsck -b 8193 <device>
or
  e2fsck -b 32768 <device>

Found a gpt partition table in /dev/sda

So, there's something wrong with the superblock on the drive?  That's not a hardware issue is it?  What do I do about this?  Running either of the suggested commands (e2fsck -b 8193 /dev/sda or e2fsck -b 32768 /dev/sda) returns:

e2fsck 1.46.5 (30-Dec-2021)
/dev/sda is in use.
e2fsck: Cannot continue, aborting.

Umounting where /dev/sda is mounted (/media/xubuntu/526d1aaf-fab5-4dbf-9d57-8919cf91a3c2) and then running either of those commands returns the first message above about magic numbers in superblocks, and suggesting I run the commands I just ran(!)

---

### Post by oldfred on 2022-10-19
Is drive new enough to support Smart tools?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)

In Ubuntu is Disks and hamburger icon in upper right corner is Smart Status. 
AllI know is if drive passes or fails, but it can run many tests.

[https://ubuntuforums.org/showthread.php?t=2445397&page=2&p=13965854#post13965854](https://ubuntuforums.org/showthread.php?t=2445397&page=2&p=13965854#post13965854)

---

### Post by peyre on 2022-10-19
It is pretty new.  I've run an Extended Test.  It says Threshold not exceeded and Disk is OK.  All the Assessments in SMART Attributes show OK.

---

### Post by tea for one on 2022-10-20
> **peyre said:**
> Ok, so fsck /dev/sda (this is the only drive attached) returns:
fsck from util-linux 2.37.2
e2fsck 1.46.5 (30-Dec-2021)
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda
You do not run fsck on a drive/disk.
Using a live session, you check the filesystem on an unmounted partition.
Example:-
```
sudo fsck /dev/sda1 
```

---

### Post by peyre on 2022-10-20
Oh, on the partition!  (Yes, I'm in a live session, rather than recovery mode.)  Ok, I ran fsck /dev/sda1, but I got the same error. Bad magic number in super-block, etc.  Running the two e2fsck commands against /dev/sda1 gets the same error as before too.

If it helps, running dumpe2fs -h /dev/sda returns:
dumpe2fs 1.46.5 (30-Dec-2021)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.
Fount a gpt partition table in /dev/sda

---

### Post by tea for one on 2022-10-20
> **peyre said:**
> Oh, on the partition!  Ok, I ran fsck /dev/sda1, but I got the same error. Bad magic number in super-block, etc.  Running the two e2fsck commands against /dev/sda1 gets the same error as before too.

If it helps, running dumpe2fs -h /dev/sda returns:
dumpe2fs 1.46.5 (30-Dec-2021)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda
Couldn't find valid filesystem superblock.
Fount a gpt partition table in /dev/sda

I'm sure that you have to target a partition rather than the disk i.e. sda1 as opposed to sda.
From a live session, try this
```
dumpe2fs /dev/sda[COLOR="#0000FF"]1[/COLOR] | grep superblock
[COLOR="#0000FF"]Double check the partition number before proceeding[/COLOR]
```
More info [https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](https://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

---

### Post by peyre on 2022-10-20
Thanks.  That returns:

dumpe2fs 1.46.5 (30-Dec-2021)
dumpe2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem [COLOR="#FF0000"]superblock[/COLOR].

---

### Post by tea for one on 2022-10-20
> **peyre said:**
> Couldn't find valid filesystem [COLOR="#FF0000"]superblock[/COLOR].
Not a promising outcome,
If I can think of anything else, I'll revisit the thread

---

### Post by peyre on 2022-10-20
I appreciate it teaforone.  FWIW, this is the less serious of the two problems I'm having right now.  With this one, worst-case scenario is I have to reinstall from scratch, but I can copy my home folder over from a recent backup.  With my other one ([https://ubuntuforums.org/showthread.php?t=2480047&page=2&p=14116189#post14116189](https://ubuntuforums.org/showthread.php?t=2480047&page=2&p=14116189#post14116189)), my worst-case is that I've lost all my data on the drive, and can only restore from the offsite backup I took in March.

---

### Post by peyre on 2022-10-22
Well, it looks like my only option at this point is to wipe the drive and reinstall from scratch. At least I have backups of my boot drive so I can restore the Desktop, downloads, etc.

---

