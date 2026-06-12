---
title: "Ubuntu 11.1 - Kernel panic"
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by nhasan on 2011-12-08
Hi all,

My system is pretty much broken at this point and I cannot boot into ubuntu Please help. I have tried repairing using the Rescatux and Ubuntu secure remix (boot-repair) and no luck.This started after upgrading to Ubuntu 11.1. Previously, the system booted up and dropped me to a command prompt (some issue with the X-server)

[LIST=1]
[*]I am seeing a error: sparse file not allowed if I try and boot up normally
[*]If go to recovery mode then I get the following additional information
[/LIST]
> 
VFS: Cannot open root device "sda2" or unknown-block (0,0)
Please append a correct "root=" boot option: here are all the available partitions:
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
Pid: 1 comm: swapper Not tainted 3.0.0.12-generic #20 Ubuntu


I booted using the livecd and here is some of the info collected:
=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8c8fa5e8-e335-4313-91ee-1624a2c6be79 /               reiserfs notail          0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

Thanks for any help it is apprciated.

~nhasan

---

### Post by nhasan on 2011-12-08
Added information on the drive / partition. 

Additional note: This is a dual boot setup and Win XP is booting up fine. In my previous post I mentioned I upgraded to 11.1... I used the Ubuntu live CD remix to upgrade.

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   152,344,394   152,344,332   7 NTFS / exFAT / HPFS
/dev/sda2    *    152,344,395   233,440,514    81,096,120  83 Linux
/dev/sda3         233,440,576   234,436,544       995,969   f W95 Extended (LBA)
/dev/sda5         233,440,578   234,436,544       995,967  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63   112,454,999   112,454,937  83 Linux
/dev/sdb2         112,455,000   234,436,544   121,981,545   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        426822536822464F                       ntfs       
/dev/sda2        8c8fa5e8-e335-4313-91ee-1624a2c6be79   reiserfs   
/dev/sda5                                               swap       
/dev/sdb1        0f8f4bde-bc75-4c08-88fd-18fdc87bc75c   reiserfs   
/dev/sdb2        6EFC63CFFC63905F                       ntfs       VM

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/8c8fa5e8-e335-4313-91ee-1624a2c6be79 reiserfs   (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)

---

### Post by nhasan on 2011-12-09
This is a gentle bump - which I am told is allowed once every 24 hours and my previous post says it has been there for 1 day.

~nhasan

---

### Post by flyingfisch on 2011-12-09
A similar problem happened to me yesterday. I ended up reinstalling ubuntu. Like you I dual boot XP and Ubuntu 11.10 and like you, I could boot up XP just fine.

You will probably want to back up your home folder with the LiveCD before you reinstall.

---

### Post by MAFoElffen on 2011-12-09
> **nhasan said:**
> Hi all,

My system is pretty much broken at this point and I cannot boot into ubuntu Please help. I have tried repairing using the Rescatux and Ubuntu secure remix (boot-repair) and no luck.This started after upgrading to Ubuntu 11.1. Previously, the system booted up and dropped me to a command prompt (some issue with the X-server)

[LIST=1]
[*]I am seeing a error: sparse file not allowed if I try and boot up normally
[*]If go to recovery mode then I get the following additional information
[/LIST]


I booted using the livecd and here is some of the info collected:
```

=============================== sda2/etc/fstab:=================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=8c8fa5e8-e335-4313-91ee-1624a2c6be79 /               reiserfs notail          0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

```Thanks for any help it is apprciated.

~nhasan
Can you boot from a LiveCD?

You mentioned
> (some issue with the X-server)I am very curious what issue it mentioned.

So from a LiveCD, go to your installed disk and partition and post these 2 file:
/var/log/Xorg.0.log
/var/log/syslog
...BUT, Please post those files between the CODE tags from the "#" button of the posting toolbar. That will put them withing a text box with scrollbars. If not, those 2 long files will take 50 screens to read...instead of one screen while scrolling. 

I helped flyingfisch, but your's seems a little different ( at least so far).

---

### Post by adrian15 on 2011-12-09
> **nhasan said:**
> 
My system is pretty much broken at this point and I cannot boot into ubuntu Please help. I have tried repairing using the Rescatux and Ubuntu secure remix (boot-repair) and no luck.

How to solve this problem with [Rescatux](http://www.supergrubdisk.org/rescatux/) (I hope so):

First of all make sure that you select Live AMD64 at boot screen if you installed a 64bit version of Ubuntu.

First of all try the: **Grub. Update grub configuration** option.

If it fails you should use the **Filesystem Check (Fix forced)** option and choose your Linux root partition.

Once you have done this it might boot but I don't actually think so. Thus you will have to run:
**Grub. Update grub configuration** option.
**Restore Grub to the MBR** option too.

Probably the last one won't be needed. Not sure.

adrian15

---

### Post by MAFoElffen on 2011-12-09
> **adrian15 said:**
> How to solve this problem with [Rescatux]("http://www.supergrubdisk.org/rescatux/") (I hope so):

First of all make sure that you select Live AMD64 at boot screen if you installed a 64bit version of Ubuntu.

First of all try the: **Grub. Update grub configuration** option.

If it fails you should use the **Filesystem Check (Fix forced)** option and choose your Linux root partition.

Once you have done this it might boot but I don't actually think so. Thus you will have to run:
**Grub. Update grub configuration** option.
**Restore Grub to the MBR** option too.

Probably the last one won't be needed. Not sure.

adrian15
I think the keyword there would be 
> Not sure.With Grub2, If you get the Grub Menu, the MBR is good, has booted and has read the filesystem of /boot/grub/grub.cfg successfully... So reinstalling and configuring is not going to get this OP anywhere.

Although, if in that Grub Menu he selects one on the "Recovery" menu items, if he selects the "root" option. Then he can see to boots messages and see where it goes.  If it hangs, he can see where it the messages before it hung.  If it boots to a TTY Text console Root promt, then we can rule out the kernel itself.

If it hangs, he can try an earlier kernel and see if it boots.

If it boot to the root prompt- Then he could type "exit" and get back to the recovery menu. There is 2 options for filesystem- One option (remount) is to mount all filesystems. The other is fsck which would check the filsystems on the next boot.  The first option on the 11.10 Recovery menu is "resume" which uses the failsafe script and configuration to boot with 9 module scripts instead of 30 plus...with low-graphics mode.

If there was a problem with your just your fstab, even if messaging where turned of, you would be at the Plymouth Splash (Ubuntu with the red and white does) and you would get a message displaying an error in fstab and display that particular fstab line...

I really think we'll find your problem in your Xorg log, but if not, it will surely be in your syslog.

---

### Post by nhasan on 2011-12-09
> **MAFoElffen said:**
> Can you boot from a LiveCD?

You mentioned
I am very curious what issue it mentioned.

So from a LiveCD, go to your installed disk and partition and post these 2 file:
/var/log/Xorg.0.log
/var/log/syslog
...BUT, Please post those files between the CODE tags from the "#" button of the posting toolbar. That will put them withing a text box with scrollbars. If not, those 2 long files will take 50 screens to read...instead of one screen while scrolling. 

I helped flyingfisch, but your's seems a little different ( at least so far).

Hi and thank you for the advice and your time

I took a look in the directory and it doesn't seem to have the files mentioned. I have provided the current contents of the directory below along with a lengthier recap of the events leading up to this Kernel Panic

```
ubuntu@ubuntu:/media/8c8fa5e8-e335-4313-91ee-1624a2c6be79/var/log$ ls -atrl
total 1041
drwxr-xr-x  2 root              root     48 2011-05-21 09:12 ConsoleKit
drwx------  2 speech-dispatcher root     48 2011-06-06 02:29 speech-dispatcher
drwxr-xr-x  2 root              root     48 2011-07-19 14:51 unattended-upgrades
drwxr-xr-x  2 root              root     48 2011-09-27 13:16 cups
drwxr-xr-x  2 root              root     48 2011-09-30 19:09 samba
drwxr-xr-x  2 root              root     48 2011-10-07 12:41 lightdm
drwxr-xr-x  2 root              root     48 2011-10-10 12:05 dist-upgrade
-rw-rw-r--  1 root              utmp      0 2011-10-12 14:27 wtmp
-rw-rw----  1 root              utmp      0 2011-10-12 14:27 btmp
drwxr-xr-x  2 root              root    104 2011-10-12 14:27 fsck
-rw-r-----  1 root              adm      31 2011-10-12 14:27 dmesg
-rw-r-----  1 root              adm      31 2011-10-12 14:27 boot
-rw-r--r--  1 root              root  49092 2011-10-12 14:27 bootstrap.log
drwxr-xr-x 13 root              root    360 2011-10-12 14:31 ..
-rw-r--r--  1 root              root   2509 2011-10-12 14:31 fontconfig.log
drwxr-xr-x  2 root              root    104 2011-11-05 11:26 apt
-rw-rw-r--  1 root              utmp 292292 2011-12-05 03:08 lastlog
-rw-r--r--  1 root              root  24024 2011-12-05 03:08 faillog
-rw-r--r--  1 root              root  23043 2011-12-05 03:08 alternatives.log
drwxr-xr-x  4 root              root    104 2011-12-05 03:11 clean
drwxr-xr-x 12 root              root    600 2011-12-05 03:11 .
-rw-r--r--  1 root              root 929523 2011-12-08 10:12 dpkg.log
ubuntu@ubuntu:/media/8c8fa5e8-e335-4313-91ee-1624a2c6be79/var/log$ date
Fri Dec  9 23:50:09 UTC 2011

```

Here are the events which happened.
1. Ubuntu installed and chugging along fine
2. Changed graphics card and monitor and X dies [(roughly 3 years ago)]("http://ubuntuforums.org/showthread.php?t=944874") 
3. I get nowhere trying to fix it. Lose interest in the whole thing and shelve Ubuntu
4. Dec 5th this year I get inspired and try to revive the system
5. I think I booted into and got the command prompt for 6.06 LTS
6. I download the LiveCD remix of Ubuntu
7. I decided to upgrade Ubuntu in place to 11.1
8. Now system doesnt boot and I get a Kernel panic for 11.1
9. I try many different repair combinations using Rescatux and Ubuntu Live CD remix (Boot-repair - Grub re-installs, MBR restores etc)
10. None work... leading to my post on the forums...

Also note the following responses to various questions

1. I forced a check on the filesystem but that returned remarkably quickly and did not report errors
2. I see the Grub menu
    - selecting latest kernel result in the sparse files and system hang
    - selecting latest kernel in recovery mode results in sparse files and panic (see details in my original post
    - selecting any other previous kernels simply causes the system to reboot
3. I don't see a root option when i select the recovery kernel (just a sparse files message) and press enter to continue - leading up to the messages around the panic

Thanks for reading about my long sad story. Hope it helps in understanding what has happened how it could be solved.

~nhasan

---

### Post by adrian15 on 2011-12-09
> **MAFoElffen said:**
> I think the keyword there would be 
With Grub2, If you get the Grub Menu, the MBR is good, has booted and has read the filesystem of /boot/grub/grub.cfg successfully... So reinstalling and configuring is not going to get this OP anywhere.


Yes, you are probably right. There is not usually need to reinstall grub to the mbr. But the fsck command run from Rescatux might move the hard disk position of grub2 needed files, and that could lead to "Grub2 not finding its own files" error. To solve this problem you need to run the **Restore Grub to the MBR** option from Rescatux.

But his problem (I forgot to mention this little detail :) ) is:
```

VFS: Cannot open root device "sda2" or unknown-block (0,0)
Please append a correct "root=" boot option: here are all the available partitions:
Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
Pid: 1 comm: swapper Not tainted 3.0.0.12-generic #20 Ubuntu 

```
which usually means that either the grub.cfg is incorrect, which sometimes happens when you upgrade or that actually the system cannot mount the root fs.

If the system cannot mount the root fs I doubt that you can get to recovery screen but you might after all.

In the case that cannot mount the root fs you can fix that with the Rescatux **fsck** option I have mentioned. Might it be that the Ubuntu fsck option that you mentioned, the one that it is found on the recovery screen, has forced fix... but I am not quite sure about that. If it had the forced fix then you could use that instead of Rescatux fsck option.

If the problem is an incorrect grub then running the update-grub command is the way to go. From Rescatux is using the **Update grub configuration** option.

There could be a third possibility about drivers. I mean... Maybe the last system could mount read that hard disk ok but the current one (due to some faulty drivers) cannot read the same hard disk ok.

adrian15

---

### Post by adrian15 on 2011-12-09
> **nhasan said:**
> 
Here are the events which happened.
...
5. I think I booted into and got the command prompt for 6.06 LTS
...

Usually when going from 6.06 to 11.10 or any other big jumps (That's 5 years!) it is recommended to save your /home directory and make a clean install and restore your /home directory.

Depending on your needs you might want to save your installed packages list.

Please ask someone else if you are interested in this path.
> **nhasan said:**
> 
1. I forced a check on the filesystem but that returned remarkably quickly and did not report errors

If you mean that you forced it by the means of Rescatux (and that you selected the right partition) I would like to see its log. **Support. Share log on forum** option might assist you.

---

### Post by MAFoElffen on 2011-12-09
> **nhasan said:**
> Hi and thank you for the advice and your time

I took a look in the directory and it doesn't seem to have the files mentioned. I have provided the current contents of the directory below along with a lengthier recap of the events leading up to this Kernel Panic

]Here are the events which happened.
1. Ubuntu installed and chugging along fine
2. Changed graphics card and monitor and X dies [(roughly 3 years ago)]("http://ubuntuforums.org/showthread.php?t=944874") 
3. I get nowhere trying to fix it. Lose interest in the whole thing and shelve Ubuntu
4. Dec 5th this year I get inspired and try to revive the system
5. I think I booted into and got the command prompt for 6.06 LTS
6. I download the LiveCD remix of Ubuntu
7. I decided to upgrade Ubuntu in place to 11.1
8. Now system doesnt boot and I get a Kernel panic for 11.1
9. I try many different repair combinations using Rescatux and Ubuntu Live CD remix (Boot-repair - Grub re-installs, MBR restores etc)
10. None work... leading to my post on the forums...

Also note the following responses to various questions

1. I forced a check on the filesystem but that returned remarkably quickly and did not report errors
2. I see the Grub menu
    - selecting latest kernel result in the sparse files and system hang
    - selecting latest kernel in recovery mode results in sparse files and panic (see details in my original post
    - selecting any other previous kernels simply causes the system to reboot
3. I don't see a root option when i select the recovery kernel (just a sparse files message) and press enter to continue - leading up to the messages around the panic

Thanks for reading about my long sad story. Hope it helps in understanding what has happened how it could be solved.

~nhasan
So lets backup a bit.  There is NO current upgrade path from 6.xx to 11.10.  The online path for that to happen ended years ago.  You could have done it manually if you had all the alternate install CDs for each and went incremental for each version up to 10,04, then to 11.10. But if you tried to go all at once, then poof. Then even with the filesystems? Trying to convert Ext2 to a system that does Ext4... then theres your sign.

It would have to be a clean, fresh, new install of 11.10.  Even then, the one thing you need to know = The make and model of your video card. (Yes back to that). Because 11.10 does a lot more than just VGA graphics that was in 6.x.

If you boot on a LiveCD, go to a terminal session:
```

lspci -vnn | grep VGA

```If you can post the results of that, I give you instructions and which Video driver you need to install. In the meantime. you can use a LiveCD to bckup any data you want off it, taking into consideration that the drive need to be repartitioned and reformatted.  If you have that on a network, from the LiveCD you could mount a drive thru "network" to your other PC to temporarily store those file there (I use my fileservers).

---

### Post by nhasan on 2011-12-09
Hi.. and thank you again for bearing with me on this epic journey :)

I am using ReiserFS on both the systems. It looks like I can still mount the filesystem using the liveCD so it doesnt look like there is anything corrupt per se.

I ran the force check and it looks like it even though it reported it ran correctly on the GUI the log says it skipped the check...

I am thinking at this point to do fresh install... do I have kill off all my partitions or can i just install in parallel? I remember I setup some extra software way back when backuppc which has some backed up files on it do you think i can recover those?

This is a semi-automated message generated from [Rescatux live cd]("http://www.supergrubdisk.org").
My description of my system is:
Ubuntu 11.1 - kernel panic
My problem is:
system not booting after getting grub menu
I join the Rescatux output for fsck_log.txt :
```

+ set -v

# Forces a fsck of a partition
# 1 parametre = Selected partition
function rtux_Fsck_Forced () {
  local SELECTED_PARTITION=$1
  local EXIT_VALUE=1 # Error by default

  fsck -fy /dev/${SELECTED_PARTITION} \
  | tee >(zenity ${ZENITY_COMMON_OPTIONS} \
	--text "${RUNNING_STR}" \
	--progress \
	--pulsate \
	--auto-close) >> /dev/stdout
  EXIT_VALUE=$?
  return ${EXIT_VALUE}

} # rtux_Fsck_Forced ()

# fsck Main program

FSCK_FORCED_OK_STR="Filesystem check with automatic fix was OK! :)"
+ FSCK_FORCED_OK_STR='Filesystem check with automatic fix was OK! :)'
FSCK_FORCED_KO_STR="Filesystem check with automatic fix went wrong! :("
+ FSCK_FORCED_KO_STR='Filesystem check with automatic fix went wrong! :('

SELECTED_PARTITION=$(rtux_Choose_Partition)
rtux_Choose_Partition)
rtux_Choose_Partition
++ rtux_Choose_Partition
rtux_Get_System_Partitions)
rtux_Get_System_Partitions
+++ rtux_Get_System_Partitions
+++ awk '{ if ( ( NR>2 ) && ( $4 ~ "[0-9]$" ) ) {print $4} }' /proc/partitions
++ rtux_Abstract_Choose_Partition sda1 sda2 sda3 sda5 sdb1 sdb2 loop0
++ local n=0
++ local LIST_VALUES=
++ local DESC_VALUES=
++ local 'SBIN_GRUB_PARTITIONS=sda1 sda2 sda3 sda5 sdb1 sdb2 loop0'
++ for n_partition in '${SBIN_GRUB_PARTITIONS}'
rtux_Get_Etc_Issue_Content ${n_partition}
+++ rtux_Get_Etc_Issue_Content sda1
+++ local PARTITION_TO_MOUNT=sda1
+++ local n_partition=sda1
+++ local TMP_MNT_PARTITION=/mnt/rescatux/sda1
+++ local TMP_DEV_PARTITION=/dev/sda1
+++ mkdir --parents /mnt/rescatux/sda1
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null
++++ mount -t auto /dev/sda1 /mnt/rescatux/sda1
+++ [[ -e /mnt/rescatux/sda1/etc/issue ]]
+++ echo 'Not detected'
+++ umount /mnt/rescatux/sda1
++ local 'issue_value=Not detected'
echo $issue_value | sed 's/\ /\-/')
echo $issue_value | sed 's/\ /\-/'
+++ sed 's/\ /\-/'
+++ echo Not detected
++ issue_value=Not-detected
echo $issue_value | sed 's/ /\-/')
echo $issue_value | sed 's/ /\-/'
+++ sed 's/ /\-/'
+++ echo Not-detected
++ issue_value=Not-detected
++ [[ n -eq 0 ]]
++ LIST_VALUES='TRUE sda1 Not-detected'
++ let n=n+1
++ for n_partition in '${SBIN_GRUB_PARTITIONS}'
rtux_Get_Etc_Issue_Content ${n_partition}
+++ rtux_Get_Etc_Issue_Content sda2
+++ local PARTITION_TO_MOUNT=sda2
+++ local n_partition=sda2
+++ local TMP_MNT_PARTITION=/mnt/rescatux/sda2
+++ local TMP_DEV_PARTITION=/dev/sda2
+++ mkdir --parents /mnt/rescatux/sda2
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null
++++ mount -t auto /dev/sda2 /mnt/rescatux/sda2
+++ [[ -e /mnt/rescatux/sda2/etc/issue ]]
head -n 1 ${TMP_MNT_PARTITION}${ETC_ISSUE_PATH} |	sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' -e 's/\ /-/g' -e 's/\ \ /-/g' -e 's/\n/-/g')
head -n 1 ${TMP_MNT_PARTITION}${ETC_ISSUE_PATH} |	sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' -e 's/\ /-/g' -e 's/\ \ /-/g' -e 's/\n/-/g')
head -n 1 ${TMP_MNT_PARTITION}${ETC_ISSUE_PATH} |	sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' -e 's/\ /-/g' -e 's/\ \ /-/g' -e 's/\n/-/g'
++++ sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' -e 's/\ /-/g' -e 's/\ \ /-/g' -e 's/\n/-/g'
++++ head -n 1 /mnt/rescatux/sda2/etc/issue
+++ echo Ubuntu-11.10-
+++ umount /mnt/rescatux/sda2
++ local issue_value=Ubuntu-11.10-
echo $issue_value | sed 's/\ /\-/')
echo $issue_value | sed 's/\ /\-/'
+++ sed 's/\ /\-/'
+++ echo Ubuntu-11.10-
++ issue_value=Ubuntu-11.10-
echo $issue_value | sed 's/ /\-/')
echo $issue_value | sed 's/ /\-/'
+++ sed 's/ /\-/'
+++ echo Ubuntu-11.10-
++ issue_value=Ubuntu-11.10-
++ [[ n -eq 0 ]]
++ LIST_VALUES='TRUE sda1 Not-detected FALSE sda2 Ubuntu-11.10-'
++ let n=n+1
++ for n_partition in '${SBIN_GRUB_PARTITIONS}'
rtux_Get_Etc_Issue_Content ${n_partition}
+++ rtux_Get_Etc_Issue_Content sda3
+++ local PARTITION_TO_MOUNT=sda3
+++ local n_partition=sda3
+++ local TMP_MNT_PARTITION=/mnt/rescatux/sda3
+++ local TMP_DEV_PARTITION=/dev/sda3
+++ mkdir --parents /mnt/rescatux/sda3
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null
++++ mount -t auto /dev/sda3 /mnt/rescatux/sda3
+++ echo 'Cannot mount'
++ local 'issue_value=Cannot mount'
echo $issue_value | sed 's/\ /\-/')
echo $issue_value | sed 's/\ /\-/'
+++ sed 's/\ /\-/'
+++ echo Cannot mount
++ issue_value=Cannot-mount
echo $issue_value | sed 's/ /\-/')
echo $issue_value | sed 's/ /\-/'
+++ sed 's/ /\-/'
+++ echo Cannot-mount
++ issue_value=Cannot-mount
++ [[ n -eq 0 ]]
++ LIST_VALUES='TRUE sda1 Not-detected FALSE sda2 Ubuntu-11.10- FALSE sda3 Cannot-mount'
++ let n=n+1
++ for n_partition in '${SBIN_GRUB_PARTITIONS}'
rtux_Get_Etc_Issue_Content ${n_partition}
+++ rtux_Get_Etc_Issue_Content sda5
+++ local PARTITION_TO_MOUNT=sda5
+++ local n_partition=sda5
+++ local TMP_MNT_PARTITION=/mnt/rescatux/sda5
+++ local TMP_DEV_PARTITION=/dev/sda5
+++ mkdir --parents /mnt/rescatux/sda5
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null
++++ mount -t auto /dev/sda5 /mnt/rescatux/sda5
+++ echo 'Cannot mount'
++ local 'issue_value=Cannot mount'
echo $issue_value | sed 's/\ /\-/')
echo $issue_value | sed 's/\ /\-/'
+++ sed 's/\ /\-/'
+++ echo Cannot mount
++ issue_value=Cannot-mount
echo $issue_value | sed 's/ /\-/')
echo $issue_value | sed 's/ /\-/'
+++ sed 's/ /\-/'
+++ echo Cannot-mount
++ issue_value=Cannot-mount
++ [[ n -eq 0 ]]
++ LIST_VALUES='TRUE sda1 Not-detected FALSE sda2 Ubuntu-11.10- FALSE sda3 Cannot-mount FALSE sda5 Cannot-mount'
++ let n=n+1
++ for n_partition in '${SBIN_GRUB_PARTITIONS}'
rtux_Get_Etc_Issue_Content ${n_partition}
+++ rtux_Get_Etc_Issue_Content sdb1
+++ local PARTITION_TO_MOUNT=sdb1
+++ local n_partition=sdb1
+++ local TMP_MNT_PARTITION=/mnt/rescatux/sdb1
+++ local TMP_DEV_PARTITION=/dev/sdb1
+++ mkdir --parents /mnt/rescatux/sdb1
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null
++++ mount -t auto /dev/sdb1 /mnt/rescatux/sdb1
+++ [[ -e /mnt/rescatux/sdb1/etc/issue ]]
+++ echo 'Not detected'
+++ umount /mnt/rescatux/sdb1
++ local 'issue_value=Not detected'
echo $issue_value | sed 's/\ /\-/')
echo $issue_value | sed 's/\ /\-/'
+++ sed 's/\ /\-/'
+++ echo Not detected
++ issue_value=Not-detected
echo $issue_value | sed 's/ /\-/')
echo $issue_value | sed 's/ /\-/'
+++ sed 's/ /\-/'
+++ echo Not-detected
++ issue_value=Not-detected
++ [[ n -eq 0 ]]
++ LIST_VALUES='TRUE sda1 Not-detected FALSE sda2 Ubuntu-11.10- FALSE sda3 Cannot-mount FALSE sda5 Cannot-mount FALSE sdb1 Not-detected'
++ let n=n+1
++ for n_partition in '${SBIN_GRUB_PARTITIONS}'
rtux_Get_Etc_Issue_Content ${n_partition}
+++ rtux_Get_Etc_Issue_Content sdb2
+++ local PARTITION_TO_MOUNT=sdb2
+++ local n_partition=sdb2
+++ local TMP_MNT_PARTITION=/mnt/rescatux/sdb2
+++ local TMP_DEV_PARTITION=/dev/sdb2
+++ mkdir --parents /mnt/rescatux/sdb2
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null
++++ mount -t auto /dev/sdb2 /mnt/rescatux/sdb2
+++ [[ -e /mnt/rescatux/sdb2/etc/issue ]]
+++ echo 'Not detected'
+++ umount /mnt/rescatux/sdb2
++ local 'issue_value=Not detected'
echo $issue_value | sed 's/\ /\-/')
echo $issue_value | sed 's/\ /\-/'
+++ sed 's/\ /\-/'
+++ echo Not detected
++ issue_value=Not-detected
echo $issue_value | sed 's/ /\-/')
echo $issue_value | sed 's/ /\-/'
+++ sed 's/ /\-/'
+++ echo Not-detected
++ issue_value=Not-detected
++ [[ n -eq 0 ]]
++ LIST_VALUES='TRUE sda1 Not-detected FALSE sda2 Ubuntu-11.10- FALSE sda3 Cannot-mount FALSE sda5 Cannot-mount FALSE sdb1 Not-detected FALSE sdb2 Not-detected'
++ let n=n+1
++ for n_partition in '${SBIN_GRUB_PARTITIONS}'
rtux_Get_Etc_Issue_Content ${n_partition}
+++ rtux_Get_Etc_Issue_Content loop0
+++ local PARTITION_TO_MOUNT=loop0
+++ local n_partition=loop0
+++ local TMP_MNT_PARTITION=/mnt/rescatux/loop0
+++ local TMP_DEV_PARTITION=/dev/loop0
+++ mkdir --parents /mnt/rescatux/loop0
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null)
mount -t auto ${TMP_DEV_PARTITION} ${TMP_MNT_PARTITION} 2> /dev/null
++++ mount -t auto /dev/loop0 /mnt/rescatux/loop0
+++ [[ -e /mnt/rescatux/loop0/etc/issue ]]
head -n 1 ${TMP_MNT_PARTITION}${ETC_ISSUE_PATH} |	sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' -e 's/\ /-/g' -e 's/\ \ /-/g' -e 's/\n/-/g')
head -n 1 ${TMP_MNT_PARTITION}${ETC_ISSUE_PATH} |	sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' -e 's/\ /-/g' -e 's/\ \ /-/g' -e 's/\n/-/g')
head -n 1 ${TMP_MNT_PARTITION}${ETC_ISSUE_PATH} |	sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' -e 's/\ /-/g' -e 's/\ \ /-/g' -e 's/\n/-/g'
++++ sed -e 's/\\. //g' -e 's/\\.//g' -e 's/^[ \t]*//' -e 's/\ /-/g' -e 's/\ \ /-/g' -e 's/\n/-/g'
++++ head -n 1 /mnt/rescatux/loop0/etc/issue
+++ echo Debian-GNU/Linux-6.0-
+++ umount /mnt/rescatux/loop0
++ local issue_value=Debian-GNU/Linux-6.0-
echo $issue_value | sed 's/\ /\-/')
echo $issue_value | sed 's/\ /\-/'
+++ sed 's/\ /\-/'
+++ echo Debian-GNU/Linux-6.0-
++ issue_value=Debian-GNU/Linux-6.0-
echo $issue_value | sed 's/ /\-/')
echo $issue_value | sed 's/ /\-/'
+++ sed 's/ /\-/'
+++ echo Debian-GNU/Linux-6.0-
++ issue_value=Debian-GNU/Linux-6.0-
++ [[ n -eq 0 ]]
++ LIST_VALUES='TRUE sda1 Not-detected FALSE sda2 Ubuntu-11.10- FALSE sda3 Cannot-mount FALSE sda5 Cannot-mount FALSE sdb1 Not-detected FALSE sdb2 Not-detected FALSE loop0 Debian-GNU/Linux-6.0-'
++ let n=n+1
zenity ${ZENITY_COMMON_OPTIONS}  	--list  	--text "${WHICH_PARTITION_STR}" 	--radiolist  	--column "${SELECT_STR}" 	--column "${PARTITION_STR}" 	--column "${DESCRIPTION_STR}" ${LIST_VALUES})"
zenity ${ZENITY_COMMON_OPTIONS}  	--list  	--text "${WHICH_PARTITION_STR}" 	--radiolist  	--column "${SELECT_STR}" 	--column "${PARTITION_STR}" 	--column "${DESCRIPTION_STR}" ${LIST_VALUES})
zenity ${ZENITY_COMMON_OPTIONS}  	--list  	--text "${WHICH_PARTITION_STR}" 	--radiolist  	--column "${SELECT_STR}" 	--column "${PARTITION_STR}" 	--column "${DESCRIPTION_STR}" ${LIST_VALUES}
+++ zenity --width=600 --height=400 --list --text 'Which partition?' --radiolist --column Select --column Partition --column Description TRUE sda1 Not-detected FALSE sda2 Ubuntu-11.10- FALSE sda3 Cannot-mount FALSE sda5 Cannot-mount FALSE sdb1 Not-detected FALSE sdb2 Not-detected FALSE loop0 Debian-GNU/Linux-6.0-
++ echo sda2
+ SELECTED_PARTITION=sda2

if ( rtux_Fsck_Forced ${SELECTED_PARTITION} ) ; then
  rtux_Message_Success ${FSCK_FORCED_OK_STR}
else 
  rtux_Message_Failure ${FSCK_FORCED_KO_STR}
fi
+ rtux_Fsck_Forced sda2
+ local SELECTED_PARTITION=sda2
+ local EXIT_VALUE=1
zenity ${ZENITY_COMMON_OPTIONS} 	--text "${RUNNING_STR}" 	--progress 	--pulsate 	--auto-close)
+ tee /dev/fd/63
+ fsck -fy /dev/sda2
zenity ${ZENITY_COMMON_OPTIONS} 	--text "${RUNNING_STR}" 	--progress 	--pulsate 	--auto-close
++ zenity --width=600 --height=400 --text 'Running process... Please wait till finish message appears.' --progress --pulsate --auto-close
fsck: fsck.reiserfs: not found
fsck: Error 2 while executing fsck.reiserfs for /dev/sda2
+ EXIT_VALUE=0
+ return 0
+ rtux_Message_Success Filesystem check with automatic fix was 'OK!' ':)'
+ local 'text_to_show=Filesystem check with automatic fix was OK! :)'
+ zenity --width=600 --height=400 --info '--title=Success!' '--text=Filesystem check with automatic fix was OK! :)'

```
Thank you very much for your help!
~nhasan

PS: I booted into Rescatux to run the force file-check unfortunately it doesnt look like lspci is available there... i will run it and post back the results

---

### Post by MAFoElffen on 2011-12-09
> **nhasan said:**
> Hi.. and thank you again for bearing with me on this epic journey :)

I am using ReiserFS on both the systems. It looks like I can still mount the filesystem using the liveCD so it doesnt look like there is anything corrupt per se.

I ran the force check and it looks like it even though it reported it ran correctly on the GUI the log says it skipped the check...

I am thinking at this point to do fresh install... do I have kill off all my partitions or can i just install in parallel? I remember I setup some extra software way back when backuppc which has some backed up files on it do you think i can recover those?

This is a semi-automated message generated from [Rescatux live cd]("http://www.supergrubdisk.org").
My description of my system is:
Ubuntu 11.1 - kernel panic
My problem is:
system not booting after getting grub menu
I join the Rescatux output for fsck_log.txt :

Thank you very much for your help!
~nhasan

PS: I booted into Rescatux to run the force file-check unfortunately it doesnt look like lspci is available there... i will run it and post back the results

lspci is a command in the Linux CLI to list all the devices loaded on the PCI bus.  You would have to do that from a Linux terminal session. Filter like I posted will norrow it down to the video and display just the info you need. If you booted from a Ubuntu LiveCD or Debian LiveCD... etc. you could do it from a terminal session.  I'm not familiar with Rescutux, but you could probably get to a terminal session from there and also do it.

You should be able to install in the same partitions and it will format it accordingly. You will have to use other/manual, which will let you pick/change the partition > use, mount at "/", then format.  And if you were using a swap > select the old > done.

---

### Post by nhasan on 2011-12-09
Thanks.

Somehow the command was not available thru command line on Rescatux. I booted back on the Ubuntu secure remix LiveCD and ran the command. output is: 

```
ubuntu@ubuntu:~$ lspci -vnn | grep VGA
03:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7600 GT] [10de:02e0] (rev a2) (prog-if 00 [VGA controller])
ubuntu@ubuntu:~$ 

```

If it reformats partitions it sounds like all the data would be lost? Does it matter that the ReiserFS is installed there?

~nhasan

From the Ubuntu live CD i was able to run ReiserFS

```
ubuntu@ubuntu:~$ sudo fsck -fy /dev/sda2
fsck from util-linux 2.19.1
reiserfsck 3.6.21 (2009 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda2
Will put log info to 'stdout'
###########
reiserfsck --check started at Sat Dec 10 02:05:12 2011
###########
Replaying journal: Done.
Reiserfs journal '/dev/sda2' in blocks [18..8211]: 0 transactions replayed
Checking internal tree.. finished
Comparing bitmaps..finished
Checking Semantic tree:
finished
No corruptions found
There are on the filesystem:
	Leaves 10755
	Internal nodes 73
	Directories 21102
	Other files 146825
	Data block pointers 923500 (165 of them are zero)
	Safe links 0
###########
reiserfsck finished at Sat Dec 10 02:05:28 2011
###########
ubuntu@ubuntu:~$ 

```

---

### Post by MAFoElffen on 2011-12-09
> **nhasan said:**
> Thanks.

Somehow the command was not available thru command line on Rescatux. I booted back on the Ubuntu secure remix LiveCD and ran the command. output is: 

```
ubuntu@ubuntu:~$ lspci -vnn | grep VGA
03:00.0 VGA compatible controller [0300]: nVidia Corporation G73 [GeForce 7600 GT] [10de:02e0] (rev a2) (prog-if 00 [VGA controller])
ubuntu@ubuntu:~$ 

```If it reformats partitions it sounds like all the data would be lost? Does it matter that the ReiserFS is installed there?

~nhasan

From the Ubuntu live CD i was able to run ReiserFS

```
ubuntu@ubuntu:~$ sudo fsck -fy /dev/sda2
fsck from util-linux 2.19.1
reiserfsck 3.6.21 (2009 www.namesys.com)

*************************************************************
** If you are using the latest reiserfsprogs and  it fails **
** please  email bug reports to reiserfs-list@namesys.com, **
** providing  as  much  information  as  possible --  your **
** hardware,  kernel,  patches,  settings,  all reiserfsck **
** messages  (including version),  the reiserfsck logfile, **
** check  the  syslog file  for  any  related information. **
** If you would like advice on using this program, support **
** is available  for $25 at  www.namesys.com/support.html. **
*************************************************************

Will read-only check consistency of the filesystem on /dev/sda2
Will put log info to 'stdout'
###########
reiserfsck --check started at Sat Dec 10 02:05:12 2011
###########
Replaying journal: Done.
Reiserfs journal '/dev/sda2' in blocks [18..8211]: 0 transactions replayed
Checking internal tree.. finished
Comparing bitmaps..finished
Checking Semantic tree:
finished
No corruptions found
There are on the filesystem:
    Leaves 10755
    Internal nodes 73
    Directories 21102
    Other files 146825
    Data block pointers 923500 (165 of them are zero)
    Safe links 0
###########
reiserfsck finished at Sat Dec 10 02:05:28 2011
###########
ubuntu@ubuntu:~$ 

```
All I know about "ReiserFS," is that the smalll group supporting and developing that project disolved in early 2008, shortly after Hans Reiser, the developer, founder of NameSys, etc was found guilty of murdering his wife.  Not much has been mentioned of that project or file system in the 2 1/2 years since. Novell and Suse moved away from it, then everyone else followed suit.

You could just format the partitions in ReiserFS and in the partitioner, unselect format... If you wanted to hang on to that filesystem, you could.  Or you could select ext4, which is to default, is also a journaling filesystem and does have the reputation that ReiserFS had in data and tree corruption.

I fyou are worried about the Home or just data there- Boot from a LiveCD, mount your other PC's drive to copy over the data to a shared drive.  Use compression if you're worried about space.

---

### Post by nhasan on 2011-12-09
Wow, that is bad for the community (and for his family) from what i remember the fs was fast and becoming popular back then.

Thanks for all the advice guys. It is much appreciated. I am going to attempt to move all my data and so a fresh install. 

Wish me luck.

~nhasan

---

### Post by MAFoElffen on 2011-12-09
> **nhasan said:**
> Wow, that is bad for the community (and for his family) from what i remember the fs was fast and becoming popular back then.

Thanks for all the advice guys. It is much appreciated. I am going to attempt to move all my data and so a fresh install. 

Wish me luck.

~nhasan
Crossing fingers and wishing well...

---

### Post by nhasan on 2011-12-10
Yay!

Install done... thanks!!. I am finally able to login without using a liveCD. Before i try and recover my home files etc though. It looks like I am getting a horrible resolution on my X server for some reason. I have pasted the logs from the X server below

X.0.org.log
```
[    22.387] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    22.387] X Protocol Version 11, Revision 0
[    22.387] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    22.387] Current Operating System: Linux Mars 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686
[    22.387] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=d09cf86f-0393-4d57-9f63-5cf3b3ce7dbe ro vga=792 quiet splash vt.handoff=7
[    22.387] Build Date: 19 October 2011  05:09:41AM
[    22.387] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    22.387] Current version of pixman: 0.22.2
[    22.387] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.387] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.387] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  9 22:51:53 2011
[    22.397] (==) Using config file: "/etc/X11/xorg.conf"
[    22.398] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.398] (==) No Layout section.  Using the first Screen section.
[    22.398] (==) No screen section available. Using defaults.
[    22.398] (**) |-->Screen "Default Screen Section" (0)
[    22.398] (**) |   |-->Monitor "<default monitor>"
[    22.398] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    22.398] (**) |   |-->Device "Default Device"
[    22.398] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.398] (==) Automatically adding devices
[    22.398] (==) Automatically enabling devices
[    22.399] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.399] 	Entry deleted from font path.
[    22.399] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.399] 	Entry deleted from font path.
[    22.399] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.399] 	Entry deleted from font path.
[    22.399] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.399] 	Entry deleted from font path.
[    22.399] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.399] 	Entry deleted from font path.
[    22.399] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.399] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.399] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.399] (II) Loader magic: 0x823ada0
[    22.399] (II) Module ABI versions:
[    22.399] 	X.Org ANSI C Emulation: 0.4
[    22.399] 	X.Org Video Driver: 10.0
[    22.399] 	X.Org XInput driver : 12.3
[    22.399] 	X.Org Server Extension : 5.0
[    22.403] (--) PCI:*(0:3:0:0) 10de:02e0:3842:a559 rev 162, Mem @ 0xe5000000/16777216, 0xd0000000/268435456, 0xe6000000/16777216, BIOS @ 0x????????/131072
[    22.405] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.405] (II) LoadModule: "extmod"
[    22.406] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.406] (II) Module extmod: vendor="X.Org Foundation"
[    22.406] 	compiled for 1.10.4, module version = 1.0.0
[    22.406] 	Module class: X.Org Server Extension
[    22.406] 	ABI class: X.Org Server Extension, version 5.0
[    22.406] (II) Loading extension MIT-SCREEN-SAVER
[    22.406] (II) Loading extension XFree86-VidModeExtension
[    22.406] (II) Loading extension XFree86-DGA
[    22.406] (II) Loading extension DPMS
[    22.406] (II) Loading extension XVideo
[    22.406] (II) Loading extension XVideo-MotionCompensation
[    22.406] (II) Loading extension X-Resource
[    22.406] (II) LoadModule: "dbe"
[    22.406] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.406] (II) Module dbe: vendor="X.Org Foundation"
[    22.406] 	compiled for 1.10.4, module version = 1.0.0
[    22.406] 	Module class: X.Org Server Extension
[    22.406] 	ABI class: X.Org Server Extension, version 5.0
[    22.406] (II) Loading extension DOUBLE-BUFFER
[    22.406] (II) LoadModule: "glx"
[    22.406] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    22.530] (II) Module glx: vendor="NVIDIA Corporation"
[    22.530] 	compiled for 4.0.2, module version = 1.0.0
[    22.530] 	Module class: X.Org Server Extension
[    22.530] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[    22.530] (II) Loading extension GLX
[    22.530] (II) LoadModule: "record"
[    22.531] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.531] (II) Module record: vendor="X.Org Foundation"
[    22.531] 	compiled for 1.10.4, module version = 1.13.0
[    22.531] 	Module class: X.Org Server Extension
[    22.531] 	ABI class: X.Org Server Extension, version 5.0
[    22.531] (II) Loading extension RECORD
[    22.531] (II) LoadModule: "dri"
[    22.531] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.531] (II) Module dri: vendor="X.Org Foundation"
[    22.531] 	compiled for 1.10.4, module version = 1.0.0
[    22.531] 	ABI class: X.Org Server Extension, version 5.0
[    22.531] (II) Loading extension XFree86-DRI
[    22.531] (II) LoadModule: "dri2"
[    22.544] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.544] (II) Module dri2: vendor="X.Org Foundation"
[    22.544] 	compiled for 1.10.4, module version = 1.2.0
[    22.544] 	ABI class: X.Org Server Extension, version 5.0
[    22.544] (II) Loading extension DRI2
[    22.544] (==) Matched nvidia as autoconfigured driver 0
[    22.544] (==) Matched nouveau as autoconfigured driver 1
[    22.544] (==) Matched nv as autoconfigured driver 2
[    22.544] (==) Matched vesa as autoconfigured driver 3
[    22.544] (==) Matched fbdev as autoconfigured driver 4
[    22.544] (==) Assigned the driver to the xf86ConfigLayout
[    22.544] (II) LoadModule: "nvidia"
[    22.544] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.546] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.546] 	compiled for 4.0.2, module version = 1.0.0
[    22.546] 	Module class: X.Org Video Driver
[    22.546] (II) LoadModule: "nouveau"
[    22.556] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.557] (II) Module nouveau: vendor="X.Org Foundation"
[    22.557] 	compiled for 1.10.1, module version = 0.0.16
[    22.557] 	Module class: X.Org Video Driver
[    22.557] 	ABI class: X.Org Video Driver, version 10.0
[    22.557] (II) LoadModule: "nv"
[    22.558] (WW) Warning, couldn't open module nv
[    22.558] (II) UnloadModule: "nv"
[    22.558] (II) Unloading nv
[    22.558] (EE) Failed to load module "nv" (module does not exist, 0)
[    22.558] (II) LoadModule: "vesa"
[    22.558] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.558] (II) Module vesa: vendor="X.Org Foundation"
[    22.558] 	compiled for 1.10.2, module version = 2.3.0
[    22.558] 	Module class: X.Org Video Driver
[    22.558] 	ABI class: X.Org Video Driver, version 10.0
[    22.558] (II) LoadModule: "fbdev"
[    22.559] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.559] (II) Module fbdev: vendor="X.Org Foundation"
[    22.559] 	compiled for 1.10.0, module version = 0.4.2
[    22.559] 	ABI class: X.Org Video Driver, version 10.0
[    22.559] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[    22.559] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    22.559] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    22.559] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.559] 	RIVA TNT        (NV04)
[    22.559] 	RIVA TNT2       (NV05)
[    22.559] 	GeForce 256     (NV10)
[    22.559] 	GeForce 2       (NV11, NV15)
[    22.559] 	GeForce 4MX     (NV17, NV18)
[    22.559] 	GeForce 3       (NV20)
[    22.559] 	GeForce 4Ti     (NV25, NV28)
[    22.559] 	GeForce FX      (NV3x)
[    22.559] 	GeForce 6       (NV4x)
[    22.559] 	GeForce 7       (G7x)
[    22.559] 	GeForce 8       (G8x)
[    22.559] 	GeForce GTX 200 (NVA0)
[    22.559] 	GeForce GTX 400 (NVC0)
[    22.559] (II) VESA: driver for VESA chipsets: vesa
[    22.559] (II) FBDEV: driver for framebuffer: fbdev
[    22.560] (++) using VT number 7

[    22.560] (II) Loading sub module "fb"
[    22.560] (II) LoadModule: "fb"
[    22.560] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.560] (II) Module fb: vendor="X.Org Foundation"
[    22.560] 	compiled for 1.10.4, module version = 1.0.0
[    22.560] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.560] (II) Loading sub module "wfb"
[    22.560] (II) LoadModule: "wfb"
[    22.561] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.561] (II) Module wfb: vendor="X.Org Foundation"
[    22.561] 	compiled for 1.10.4, module version = 1.0.0
[    22.561] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.561] (II) Loading sub module "ramdac"
[    22.561] (II) LoadModule: "ramdac"
[    22.561] (II) Module "ramdac" already built-in
[    22.561] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.561] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.561] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.561] (WW) Falling back to old probe method for vesa
[    22.561] (WW) Falling back to old probe method for fbdev
[    22.561] (II) Loading sub module "fbdevhw"
[    22.561] (II) LoadModule: "fbdevhw"
[    22.561] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.562] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.562] 	compiled for 1.10.4, module version = 0.0.2
[    22.562] 	ABI class: X.Org Video Driver, version 10.0
[    22.562] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.562] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    22.562] (==) NVIDIA(0): RGB weight 888
[    22.562] (==) NVIDIA(0): Default visual is TrueColor
[    22.562] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.562] (**) NVIDIA(0): Option "NoLogo" "True"
[    22.562] (**) NVIDIA(0): Enabling RENDER acceleration
[    22.562] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    22.562] (II) NVIDIA(0):     enabled.
[    23.341] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    23.341] (II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:3:0:0 (GPU-0)
[    23.341] (--) NVIDIA(0): Memory: 524288 kBytes
[    23.341] (--) NVIDIA(0): VideoBIOS: 05.73.22.71.69
[    23.341] (II) NVIDIA(0): Detected AGP rate: 8X
[    23.341] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    23.341] (--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:3:0:0:
[    23.341] (--) NVIDIA(0):     CRT-0
[    23.341] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    23.342] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    23.342] (==) NVIDIA(0): 
[    23.342] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    23.342] (==) NVIDIA(0):     will be used as the requested mode.
[    23.342] (==) NVIDIA(0): 
[    23.342] (II) NVIDIA(0): Validated modes:
[    23.342] (II) NVIDIA(0):     "nvidia-auto-select"
[    23.342] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    23.342] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    23.342] (WW) NVIDIA(0):     from CRT-0's EDID.
[    23.342] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    23.342] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    23.342] (II) UnloadModule: "nouveau"
[    23.342] (II) Unloading nouveau
[    23.342] (II) UnloadModule: "vesa"
[    23.342] (II) Unloading vesa
[    23.342] (II) UnloadModule: "fbdev"
[    23.342] (II) Unloading fbdev
[    23.342] (II) UnloadModule: "fbdevhw"
[    23.342] (II) Unloading fbdevhw
[    23.342] (--) Depth 24 pixmap format is 32 bpp
[    23.347] (II) NVIDIA(0): Initialized AGP GART.
[    23.356] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    23.456] (II) Loading extension NV-GLX
[    23.475] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    23.476] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    23.476] (==) NVIDIA(0): Backing store disabled
[    23.476] (==) NVIDIA(0): Silken mouse enabled
[    23.476] (==) NVIDIA(0): DPMS enabled
[    23.476] (II) Loading extension NV-CONTROL
[    23.477] (==) RandR enabled
[    23.477] (II) Initializing built-in extension Generic Event Extension
[    23.477] (II) Initializing built-in extension SHAPE
[    23.477] (II) Initializing built-in extension MIT-SHM
[    23.477] (II) Initializing built-in extension XInputExtension
[    23.477] (II) Initializing built-in extension XTEST
[    23.477] (II) Initializing built-in extension BIG-REQUESTS
[    23.477] (II) Initializing built-in extension SYNC
[    23.477] (II) Initializing built-in extension XKEYBOARD
[    23.477] (II) Initializing built-in extension XC-MISC
[    23.477] (II) Initializing built-in extension SECURITY
[    23.477] (II) Initializing built-in extension XINERAMA
[    23.477] (II) Initializing built-in extension XFIXES
[    23.477] (II) Initializing built-in extension RENDER
[    23.477] (II) Initializing built-in extension RANDR
[    23.477] (II) Initializing built-in extension COMPOSITE
[    23.477] (II) Initializing built-in extension DAMAGE
[    23.477] (II) Initializing built-in extension GESTURE
[    23.481] (II) Initializing extension GLX
[    23.541] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.568] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.568] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.568] (II) LoadModule: "evdev"
[    23.569] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.570] (II) Module evdev: vendor="X.Org Foundation"
[    23.570] 	compiled for 1.10.2, module version = 2.6.0
[    23.570] 	Module class: X.Org XInput Driver
[    23.570] 	ABI class: X.Org XInput driver, version 12.3
[    23.570] (II) Using input driver 'evdev' for 'Power Button'
[    23.570] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.570] (**) Power Button: always reports core events
[    23.570] (**) Power Button: Device: "/dev/input/event1"
[    23.570] (--) Power Button: Found keys
[    23.570] (II) Power Button: Configuring as keyboard
[    23.570] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.570] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.570] (**) Option "xkb_rules" "evdev"
[    23.571] (**) Option "xkb_model" "pc105"
[    23.571] (**) Option "xkb_layout" "us"
[    23.583] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.583] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.583] (II) Using input driver 'evdev' for 'Power Button'
[    23.583] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.585] (**) Power Button: always reports core events
[    23.588] (**) Power Button: Device: "/dev/input/event0"
[    23.588] (--) Power Button: Found keys
[    23.588] (II) Power Button: Configuring as keyboard
[    23.588] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    23.588] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.588] (**) Option "xkb_rules" "evdev"
[    23.588] (**) Option "xkb_model" "pc105"
[    23.588] (**) Option "xkb_layout" "us"
[    23.591] (II) config/udev: Adding input device Microsoft Microsoft Wheel Mouse Optical® (/dev/input/event3)
[    23.591] (**) Microsoft Microsoft Wheel Mouse Optical®: Applying InputClass "evdev pointer catchall"
[    23.591] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wheel Mouse Optical®'
[    23.591] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.591] (**) Microsoft Microsoft Wheel Mouse Optical®: always reports core events
[    23.591] (**) Microsoft Microsoft Wheel Mouse Optical®: Device: "/dev/input/event3"
[    23.591] (--) Microsoft Microsoft Wheel Mouse Optical®: Found 3 mouse buttons
[    23.591] (--) Microsoft Microsoft Wheel Mouse Optical®: Found scroll wheel(s)
[    23.591] (--) Microsoft Microsoft Wheel Mouse Optical®: Found relative axes
[    23.591] (--) Microsoft Microsoft Wheel Mouse Optical®: Found x and y relative axes
[    23.591] (II) Microsoft Microsoft Wheel Mouse Optical®: Configuring as mouse
[    23.591] (II) Microsoft Microsoft Wheel Mouse Optical®: Adding scrollwheel support
[    23.591] (**) Microsoft Microsoft Wheel Mouse Optical®: YAxisMapping: buttons 4 and 5
[    23.591] (**) Microsoft Microsoft Wheel Mouse Optical®: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.591] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3/event3"
[    23.591] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wheel Mouse Optical®" (type: MOUSE)
[    23.591] (II) Microsoft Microsoft Wheel Mouse Optical®: initialized for relative axes.
[    23.592] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) keeping acceleration scheme 1
[    23.592] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration profile 0
[    23.592] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration factor: 2.000
[    23.592] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration threshold: 4
[    23.592] (II) config/udev: Adding input device Microsoft Microsoft Wheel Mouse Optical® (/dev/input/mouse0)
[    23.592] (II) No input driver/identifier specified (ignoring)
[    23.600] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    23.600] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.600] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.600] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.600] (**) AT Translated Set 2 keyboard: always reports core events
[    23.600] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    23.601] (--) AT Translated Set 2 keyboard: Found keys
[    23.601] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    23.601] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    23.601] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    23.601] (**) Option "xkb_rules" "evdev"
[    23.601] (**) Option "xkb_model" "pc105"
[    23.601] (**) Option "xkb_layout" "us"
[    25.206] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    32.677] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    36.612] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[   450.525] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[   451.458] (II) Power Button: Close
[   451.458] (II) UnloadModule: "evdev"
[   451.458] (II) Unloading evdev
[   451.458] (II) Power Button: Close
[   451.458] (II) UnloadModule: "evdev"
[   451.458] (II) Unloading evdev
[   451.473] (II) Microsoft Microsoft Wheel Mouse Optical®: Close
[   451.473] (II) UnloadModule: "evdev"
[   451.473] (II) Unloading evdev
[   451.474] (II) AT Translated Set 2 keyboard: Close
[   451.474] (II) UnloadModule: "evdev"
[   451.474] (II) Unloading evdev
[   451.917]  ddxSigGiveUp: Closing log
```


X.org.log
```
[    22.589] 
X.Org X Server 1.10.4
Release Date: 2011-08-19
[    22.589] X Protocol Version 11, Revision 0
[    22.589] Build Operating System: Linux 2.6.24-29-server i686 Ubuntu
[    22.589] Current Operating System: Linux Mars 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686
[    22.589] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=d09cf86f-0393-4d57-9f63-5cf3b3ce7dbe ro vga=795 quiet splash vt.handoff=7
[    22.590] Build Date: 19 October 2011  05:09:41AM
[    22.590] xorg-server 2:1.10.4-1ubuntu4.2 (For technical support please see http://www.ubuntu.com/support) 
[    22.590] Current version of pixman: 0.22.2
[    22.590] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[    22.590] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    22.590] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Dec  9 23:00:10 2011
[    22.590] (==) Using config file: "/etc/X11/xorg.conf"
[    22.590] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    22.590] (==) No Layout section.  Using the first Screen section.
[    22.590] (==) No screen section available. Using defaults.
[    22.590] (**) |-->Screen "Default Screen Section" (0)
[    22.590] (**) |   |-->Monitor "<default monitor>"
[    22.591] (==) No device specified for screen "Default Screen Section".
	Using the first device section listed.
[    22.591] (**) |   |-->Device "Default Device"
[    22.591] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[    22.591] (==) Automatically adding devices
[    22.591] (==) Automatically enabling devices
[    22.591] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    22.591] 	Entry deleted from font path.
[    22.591] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    22.591] 	Entry deleted from font path.
[    22.591] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    22.591] 	Entry deleted from font path.
[    22.591] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    22.591] 	Entry deleted from font path.
[    22.591] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    22.591] 	Entry deleted from font path.
[    22.591] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/Type1,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[    22.591] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    22.591] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[    22.591] (II) Loader magic: 0x823ada0
[    22.591] (II) Module ABI versions:
[    22.591] 	X.Org ANSI C Emulation: 0.4
[    22.591] 	X.Org Video Driver: 10.0
[    22.591] 	X.Org XInput driver : 12.3
[    22.591] 	X.Org Server Extension : 5.0
[    22.592] (--) PCI:*(0:3:0:0) 10de:02e0:3842:a559 rev 162, Mem @ 0xe5000000/16777216, 0xd0000000/268435456, 0xe6000000/16777216, BIOS @ 0x????????/131072
[    22.593] (II) Open ACPI successful (/var/run/acpid.socket)
[    22.593] (II) LoadModule: "extmod"
[    22.593] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[    22.594] (II) Module extmod: vendor="X.Org Foundation"
[    22.594] 	compiled for 1.10.4, module version = 1.0.0
[    22.594] 	Module class: X.Org Server Extension
[    22.594] 	ABI class: X.Org Server Extension, version 5.0
[    22.594] (II) Loading extension MIT-SCREEN-SAVER
[    22.594] (II) Loading extension XFree86-VidModeExtension
[    22.594] (II) Loading extension XFree86-DGA
[    22.594] (II) Loading extension DPMS
[    22.594] (II) Loading extension XVideo
[    22.594] (II) Loading extension XVideo-MotionCompensation
[    22.594] (II) Loading extension X-Resource
[    22.594] (II) LoadModule: "dbe"
[    22.594] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[    22.594] (II) Module dbe: vendor="X.Org Foundation"
[    22.594] 	compiled for 1.10.4, module version = 1.0.0
[    22.594] 	Module class: X.Org Server Extension
[    22.594] 	ABI class: X.Org Server Extension, version 5.0
[    22.594] (II) Loading extension DOUBLE-BUFFER
[    22.594] (II) LoadModule: "glx"
[    22.594] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    22.657] (II) Module glx: vendor="NVIDIA Corporation"
[    22.657] 	compiled for 4.0.2, module version = 1.0.0
[    22.657] 	Module class: X.Org Server Extension
[    22.657] (II) NVIDIA GLX Module  173.14.30  Thu Apr 14 09:20:02 PDT 2011
[    22.657] (II) Loading extension GLX
[    22.657] (II) LoadModule: "record"
[    22.657] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[    22.657] (II) Module record: vendor="X.Org Foundation"
[    22.657] 	compiled for 1.10.4, module version = 1.13.0
[    22.657] 	Module class: X.Org Server Extension
[    22.657] 	ABI class: X.Org Server Extension, version 5.0
[    22.657] (II) Loading extension RECORD
[    22.657] (II) LoadModule: "dri"
[    22.658] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[    22.658] (II) Module dri: vendor="X.Org Foundation"
[    22.658] 	compiled for 1.10.4, module version = 1.0.0
[    22.658] 	ABI class: X.Org Server Extension, version 5.0
[    22.658] (II) Loading extension XFree86-DRI
[    22.658] (II) LoadModule: "dri2"
[    22.658] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[    22.658] (II) Module dri2: vendor="X.Org Foundation"
[    22.658] 	compiled for 1.10.4, module version = 1.2.0
[    22.658] 	ABI class: X.Org Server Extension, version 5.0
[    22.658] (II) Loading extension DRI2
[    22.658] (==) Matched nvidia as autoconfigured driver 0
[    22.658] (==) Matched nouveau as autoconfigured driver 1
[    22.658] (==) Matched nv as autoconfigured driver 2
[    22.658] (==) Matched vesa as autoconfigured driver 3
[    22.658] (==) Matched fbdev as autoconfigured driver 4
[    22.658] (==) Assigned the driver to the xf86ConfigLayout
[    22.658] (II) LoadModule: "nvidia"
[    22.659] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.660] (II) Module nvidia: vendor="NVIDIA Corporation"
[    22.660] 	compiled for 4.0.2, module version = 1.0.0
[    22.660] 	Module class: X.Org Video Driver
[    22.660] (II) LoadModule: "nouveau"
[    22.676] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    22.677] (II) Module nouveau: vendor="X.Org Foundation"
[    22.677] 	compiled for 1.10.1, module version = 0.0.16
[    22.677] 	Module class: X.Org Video Driver
[    22.677] 	ABI class: X.Org Video Driver, version 10.0
[    22.677] (II) LoadModule: "nv"
[    22.678] (WW) Warning, couldn't open module nv
[    22.678] (II) UnloadModule: "nv"
[    22.678] (II) Unloading nv
[    22.678] (EE) Failed to load module "nv" (module does not exist, 0)
[    22.678] (II) LoadModule: "vesa"
[    22.678] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    22.678] (II) Module vesa: vendor="X.Org Foundation"
[    22.678] 	compiled for 1.10.2, module version = 2.3.0
[    22.678] 	Module class: X.Org Video Driver
[    22.678] 	ABI class: X.Org Video Driver, version 10.0
[    22.678] (II) LoadModule: "fbdev"
[    22.679] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    22.679] (II) Module fbdev: vendor="X.Org Foundation"
[    22.679] 	compiled for 1.10.0, module version = 0.4.2
[    22.679] 	ABI class: X.Org Video Driver, version 10.0
[    22.679] (II) NVIDIA dlloader X Driver  173.14.30  Thu Apr 14 08:56:42 PDT 2011
[    22.679] (II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
[    22.679] (II) NOUVEAU driver Date:   Thu Mar 24 02:13:12 2011 +1000
[    22.679] (II) NOUVEAU driver for NVIDIA chipset families :
[    22.679] 	RIVA TNT        (NV04)
[    22.679] 	RIVA TNT2       (NV05)
[    22.679] 	GeForce 256     (NV10)
[    22.679] 	GeForce 2       (NV11, NV15)
[    22.679] 	GeForce 4MX     (NV17, NV18)
[    22.679] 	GeForce 3       (NV20)
[    22.679] 	GeForce 4Ti     (NV25, NV28)
[    22.679] 	GeForce FX      (NV3x)
[    22.679] 	GeForce 6       (NV4x)
[    22.679] 	GeForce 7       (G7x)
[    22.679] 	GeForce 8       (G8x)
[    22.679] 	GeForce GTX 200 (NVA0)
[    22.679] 	GeForce GTX 400 (NVC0)
[    22.679] (II) VESA: driver for VESA chipsets: vesa
[    22.679] (II) FBDEV: driver for framebuffer: fbdev
[    22.679] (++) using VT number 7

[    22.680] (II) Loading sub module "fb"
[    22.680] (II) LoadModule: "fb"
[    22.680] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.680] (II) Module fb: vendor="X.Org Foundation"
[    22.680] 	compiled for 1.10.4, module version = 1.0.0
[    22.680] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.680] (II) Loading sub module "wfb"
[    22.680] (II) LoadModule: "wfb"
[    22.681] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.681] (II) Module wfb: vendor="X.Org Foundation"
[    22.681] 	compiled for 1.10.4, module version = 1.0.0
[    22.681] 	ABI class: X.Org ANSI C Emulation, version 0.4
[    22.681] (II) Loading sub module "ramdac"
[    22.681] (II) LoadModule: "ramdac"
[    22.681] (II) Module "ramdac" already built-in
[    22.681] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/nvidia_drv.so
[    22.681] (II) Loading /usr/lib/xorg/modules/libwfb.so
[    22.681] (II) Loading /usr/lib/xorg/modules/libfb.so
[    22.681] (WW) Falling back to old probe method for vesa
[    22.681] (WW) Falling back to old probe method for fbdev
[    22.681] (II) Loading sub module "fbdevhw"
[    22.681] (II) LoadModule: "fbdevhw"
[    22.681] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    22.682] (II) Module fbdevhw: vendor="X.Org Foundation"
[    22.682] 	compiled for 1.10.4, module version = 0.0.2
[    22.682] 	ABI class: X.Org Video Driver, version 10.0
[    22.682] (II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[    22.682] (==) NVIDIA(0): Depth 24, (==) framebuffer bpp 32
[    22.682] (==) NVIDIA(0): RGB weight 888
[    22.682] (==) NVIDIA(0): Default visual is TrueColor
[    22.682] (==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
[    22.682] (**) NVIDIA(0): Option "NoLogo" "True"
[    22.682] (**) NVIDIA(0): Enabling RENDER acceleration
[    22.682] (II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
[    22.682] (II) NVIDIA(0):     enabled.
[    23.448] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
[    23.448] (II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:3:0:0 (GPU-0)
[    23.448] (--) NVIDIA(0): Memory: 524288 kBytes
[    23.448] (--) NVIDIA(0): VideoBIOS: 05.73.22.71.69
[    23.448] (II) NVIDIA(0): Detected AGP rate: 8X
[    23.448] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    23.448] (--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:3:0:0:
[    23.448] (--) NVIDIA(0):     CRT-0
[    23.448] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    23.449] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    23.449] (==) NVIDIA(0): 
[    23.449] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    23.449] (==) NVIDIA(0):     will be used as the requested mode.
[    23.449] (==) NVIDIA(0): 
[    23.449] (II) NVIDIA(0): Validated modes:
[    23.449] (II) NVIDIA(0):     "nvidia-auto-select"
[    23.449] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    23.449] (WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
[    23.449] (WW) NVIDIA(0):     from CRT-0's EDID.
[    23.449] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
[    23.449] (==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
[    23.449] (II) UnloadModule: "nouveau"
[    23.449] (II) Unloading nouveau
[    23.449] (II) UnloadModule: "vesa"
[    23.449] (II) Unloading vesa
[    23.449] (II) UnloadModule: "fbdev"
[    23.449] (II) Unloading fbdev
[    23.449] (II) UnloadModule: "fbdevhw"
[    23.449] (II) Unloading fbdevhw
[    23.449] (--) Depth 24 pixmap format is 32 bpp
[    23.453] (II) NVIDIA(0): Initialized AGP GART.
[    23.463] (II) NVIDIA(0): Setting mode "nvidia-auto-select"
[    23.560] (II) Loading extension NV-GLX
[    23.619] (II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
[    23.620] (II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
[    23.620] (==) NVIDIA(0): Backing store disabled
[    23.620] (==) NVIDIA(0): Silken mouse enabled
[    23.620] (==) NVIDIA(0): DPMS enabled
[    23.620] (II) Loading extension NV-CONTROL
[    23.621] (==) RandR enabled
[    23.621] (II) Initializing built-in extension Generic Event Extension
[    23.621] (II) Initializing built-in extension SHAPE
[    23.621] (II) Initializing built-in extension MIT-SHM
[    23.621] (II) Initializing built-in extension XInputExtension
[    23.621] (II) Initializing built-in extension XTEST
[    23.621] (II) Initializing built-in extension BIG-REQUESTS
[    23.621] (II) Initializing built-in extension SYNC
[    23.621] (II) Initializing built-in extension XKEYBOARD
[    23.621] (II) Initializing built-in extension XC-MISC
[    23.621] (II) Initializing built-in extension SECURITY
[    23.621] (II) Initializing built-in extension XINERAMA
[    23.621] (II) Initializing built-in extension XFIXES
[    23.621] (II) Initializing built-in extension RENDER
[    23.621] (II) Initializing built-in extension RANDR
[    23.621] (II) Initializing built-in extension COMPOSITE
[    23.621] (II) Initializing built-in extension DAMAGE
[    23.621] (II) Initializing built-in extension GESTURE
[    23.625] (II) Initializing extension GLX
[    23.654] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    23.667] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    23.667] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.667] (II) LoadModule: "evdev"
[    23.667] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.669] (II) Module evdev: vendor="X.Org Foundation"
[    23.669] 	compiled for 1.10.2, module version = 2.6.0
[    23.669] 	Module class: X.Org XInput Driver
[    23.669] 	ABI class: X.Org XInput driver, version 12.3
[    23.669] (II) Using input driver 'evdev' for 'Power Button'
[    23.669] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.669] (**) Power Button: always reports core events
[    23.669] (**) Power Button: Device: "/dev/input/event1"
[    23.669] (--) Power Button: Found keys
[    23.669] (II) Power Button: Configuring as keyboard
[    23.670] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[    23.670] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.670] (**) Option "xkb_rules" "evdev"
[    23.670] (**) Option "xkb_model" "pc105"
[    23.670] (**) Option "xkb_layout" "us"
[    23.675] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    23.675] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    23.675] (II) Using input driver 'evdev' for 'Power Button'
[    23.675] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.675] (**) Power Button: always reports core events
[    23.675] (**) Power Button: Device: "/dev/input/event0"
[    23.676] (--) Power Button: Found keys
[    23.676] (II) Power Button: Configuring as keyboard
[    23.676] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[    23.676] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
[    23.676] (**) Option "xkb_rules" "evdev"
[    23.676] (**) Option "xkb_model" "pc105"
[    23.676] (**) Option "xkb_layout" "us"
[    23.678] (II) config/udev: Adding input device Microsoft Microsoft Wheel Mouse Optical® (/dev/input/event3)
[    23.678] (**) Microsoft Microsoft Wheel Mouse Optical®: Applying InputClass "evdev pointer catchall"
[    23.678] (II) Using input driver 'evdev' for 'Microsoft Microsoft Wheel Mouse Optical®'
[    23.678] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.678] (**) Microsoft Microsoft Wheel Mouse Optical®: always reports core events
[    23.678] (**) Microsoft Microsoft Wheel Mouse Optical®: Device: "/dev/input/event3"
[    23.678] (--) Microsoft Microsoft Wheel Mouse Optical®: Found 3 mouse buttons
[    23.678] (--) Microsoft Microsoft Wheel Mouse Optical®: Found scroll wheel(s)
[    23.678] (--) Microsoft Microsoft Wheel Mouse Optical®: Found relative axes
[    23.678] (--) Microsoft Microsoft Wheel Mouse Optical®: Found x and y relative axes
[    23.678] (II) Microsoft Microsoft Wheel Mouse Optical®: Configuring as mouse
[    23.678] (II) Microsoft Microsoft Wheel Mouse Optical®: Adding scrollwheel support
[    23.678] (**) Microsoft Microsoft Wheel Mouse Optical®: YAxisMapping: buttons 4 and 5
[    23.678] (**) Microsoft Microsoft Wheel Mouse Optical®: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    23.679] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:02.0/usb2/2-1/2-1:1.0/input/input3/event3"
[    23.679] (II) XINPUT: Adding extended input device "Microsoft Microsoft Wheel Mouse Optical®" (type: MOUSE)
[    23.679] (II) Microsoft Microsoft Wheel Mouse Optical®: initialized for relative axes.
[    23.679] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) keeping acceleration scheme 1
[    23.679] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration profile 0
[    23.679] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration factor: 2.000
[    23.679] (**) Microsoft Microsoft Wheel Mouse Optical®: (accel) acceleration threshold: 4
[    23.679] (II) config/udev: Adding input device Microsoft Microsoft Wheel Mouse Optical® (/dev/input/mouse0)
[    23.679] (II) No input driver/identifier specified (ignoring)
[    23.687] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[    23.687] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    23.687] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    23.687] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    23.687] (**) AT Translated Set 2 keyboard: always reports core events
[    23.688] (**) AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[    23.688] (--) AT Translated Set 2 keyboard: Found keys
[    23.688] (II) AT Translated Set 2 keyboard: Configuring as keyboard
[    23.688] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[    23.688] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
[    23.688] (**) Option "xkb_rules" "evdev"
[    23.688] (**) Option "xkb_model" "pc105"
[    23.688] (**) Option "xkb_layout" "us"
[    25.175] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    33.298] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    37.445] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
[    55.322] Warning: Xalloc: requesting unpleasantly large amount of memory: 0 bytes.
[    76.297] (II) XKB: reuse xkmfile /var/lib/xkb/server-A77BBE312A49C9FE89948D38B2A8CB84C3CBB410.xkm
```

Ok, installed startupmanager and mucked with to make the startup screen better. Installed "current version" on nvidia driver and the resolution went up to 1024x768. which is kinda bearable. Any ideas on getting it beyond that number?

~nhasan

---

### Post by MAFoElffen on 2011-12-10
> **nhasan said:**
> Yay!

Install done... thanks!!. I am finally able to login without using a liveCD. Before i try and recover my home files etc though. It looks like I am getting a horrible resolution on my X server for some reason. I have pasted the logs from the X server below

X.0.org.log
```
[    22.387] 
[    23.341] (WW) NVIDIA(GPU-0): [COLOR=Red]Unable to read EDID for display device CRT-0[/COLOR]
[    23.341] (II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:3:0:0 (GPU-0)
[    23.341] (--) NVIDIA(0): Memory: 524288 kBytes
[    23.341] (--) NVIDIA(0): VideoBIOS: 05.73.22.71.69
[    23.341] (II) NVIDIA(0): Detected AGP rate: 8X
[    23.341] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    23.341] (--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:3:0:0:
[    23.341] (--) NVIDIA(0):     CRT-0
[    23.341] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    23.342] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    23.342] (==) NVIDIA(0): 
[    23.342] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    23.342] (==) NVIDIA(0):     will be used as the requested mode.

[    23.342] (WW) NVIDIA(0): [COLOR=Red]Unable to get display device CRT-0's EDID; cannot compute DPI[/COLOR]
[    23.342] (WW) NVIDIA(0):     [COLOR=Red]from CRT-0's EDID.[/COLOR]

```X.org.log
```
[    23.448] (WW) NVIDIA(GPU-0): [COLOR=Red]Unable to read EDID for display device CRT-0[/COLOR]
[    23.448] (II) NVIDIA(0): NVIDIA GPU GeForce 7600 GT (G73) at PCI:3:0:0 (GPU-0)
[    23.448] (--) NVIDIA(0): Memory: 524288 kBytes
[    23.448] (--) NVIDIA(0): VideoBIOS: 05.73.22.71.69
[    23.448] (II) NVIDIA(0): Detected AGP rate: 8X
[    23.448] (--) NVIDIA(0): Interlaced video modes are supported on this GPU
[    23.448] (--) NVIDIA(0): Connected display device(s) on GeForce 7600 GT at PCI:3:0:0:
[    23.448] (--) NVIDIA(0):     CRT-0
[    23.448] (--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
[    23.449] (II) NVIDIA(0): Assigned Display Device: CRT-0
[    23.449] (==) NVIDIA(0): 
[    23.449] (==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"
[    23.449] (==) NVIDIA(0):     will be used as the requested mode.
[    23.449] (II) NVIDIA(0): Virtual screen size determined to be 640 x 480
[    23.449] (WW) NVIDIA(0): [COLOR=Red]Unable to get display device CRT-0's EDID; cannot compute DPI[/COLOR]
[    23.449] (WW) NVIDIA(0):    [COLOR=Red] from CRT-0's EDID.[/COLOR]
[    23.449] (==) NVIDIA(0): DPI set to (75, 75); computed from built-in default

```
What is the make and model of your monitor?

If you look above you'll see the error.  That your monitor is not returning any EDID data.  We can get your resolutions back via adding those modes back in manually.

Please post your /etc/X11/xorg.conf file.

Please install hwinfo
```

sudo apt-get install hwinfo

```And post the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
xrandr -q

```Then I'll go through that data, compute the modeline data for you and put that into your xorg.conf file.

---

### Post by adrian15 on 2011-12-10
> **nhasan said:**
> 
I am using ReiserFS on both the systems.
I join the Rescatux output for fsck_log.txt :
```

fsck: fsck.reiserfs: not found
fsck: Error 2 while executing fsck.reiserfs for /dev/sda2

```

It seems that [Rescatux does not support reiserfs](https://forja.cenatic.es/tracker/index.php?func=detail&aid=1369&group_id=205&atid=931). I will have to fix that.
> **nhasan said:**
> 
it doesnt look like lspci is available there... i will run it and post back the results
It is not a bad a idea for having a [hardware information option](https://forja.cenatic.es/tracker/index.php?func=detail&aid=1371&group_id=205&atid=934).

Thank you again for the log!

Good luck with your new installation.

---

### Post by nhasan on 2011-12-10
> **MAFoElffen said:**
> What is the make and model of your monitor?

If you look above you'll see the error.  That your monitor is not returning any EDID data.  We can get your resolutions back via adding those modes back in manually.

Please post your /etc/X11/xorg.conf file.

Please install hwinfo
```

sudo apt-get install hwinfo

```And post the results of 
```

sudo hwinfo --framebuffer
sudo hwinfo --monitor
xrandr -q

```Then I'll go through that data, compute the modeline data for you and put that into your xorg.conf file.

Did I mention thank you and you are the best already :)? Thanks again! . 

You too adrian15... thank a lot trying to help me out and creating the bug reports. One comment on Rescatux would be if the reiserfs check failed I would have expected the GUI just to let me know it failed rather than letting me think that the fs check was ok... just my 2 cents.

Make and model of the Monitor is ```
ViewSonic Optiquest Q2162wb
```
Here is a link to Manufacturers site (it is in their archives section by now) [http://www.viewsonic.com/products/archive/q2162wb.htm]("http://www.viewsonic.com/products/archive/q2162wb.htm") 


Here is the output of the various commands ```
toast@Mars:~$ sudo hwinfo --framebuffer
> hal.1: read hal dataprocess 3242: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.7T2wQEGWvaB
  Hardware Class: framebuffer
  Model: "NVIDIA G73 Board - p508h5b "
  Vendor: "NVIDIA Corporation"
  Device: "G73 Board - p508h5b "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 256 MB
  Memory Range: 0xd0000000-0xdfffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
toast@Mars:~$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 3248: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
33: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 1024x768@76Hz
  Driver Info #0:
    Max. Resolution: 1024x768
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-61 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
toast@Mars:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  
toast@Mars:~$ 

```

Here is the xorg.conf
```
toast@Mars:/etc/X11$ more xorg.conf

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

and I have attached an updated X.0.log (from after the Nvidia driver update) just in case (still has the CRT error reported)

Thanks again.

~nhasan

---

### Post by nhasan on 2011-12-11
A gentle bump - as I am allowed one every 24 hours I hear :)

~nhasan

---

### Post by MAFoElffen on 2011-12-11
> **nhasan said:**
> Did I mention thank you and you are the best already :)? Thanks again! . 

You too adrian15... thank a lot trying to help me out and creating the bug reports. One comment on Rescatux would be if the reiserfs check failed I would have expected the GUI just to let me know it failed rather than letting me think that the fs check was ok... just my 2 cents.

Make and model of the Monitor is ```
ViewSonic Optiquest Q2162wb
```Here is a link to Manufacturers site (it is in their archives section by now) [http://www.viewsonic.com/products/archive/q2162wb.htm](http://www.viewsonic.com/products/archive/q2162wb.htm) 


Here is the output of the various commands ```
toast@Mars:~$ sudo hwinfo --framebuffer
> hal.1: read hal dataprocess 3242: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.7T2wQEGWvaB
  Hardware Class: framebuffer
  Model: "NVIDIA G73 Board - p508h5b "
  Vendor: "NVIDIA Corporation"
  Device: "G73 Board - p508h5b "
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 256 MB
  Memory Range: 0xd0000000-0xdfffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
toast@Mars:~$ sudo hwinfo --monitor
> hal.1: read hal dataprocess 3248: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 280.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
33: None 00.0: 10000 Monitor                                    
  [Created at fb.71]
  Unique ID: rdCR.EY_qmtb9YY0
  Hardware Class: monitor
  Model: "Generic Monitor"
  Vendor: "Generic"
  Device: "Monitor"
  Resolution: 1024x768@76Hz
  Driver Info #0:
    Max. Resolution: 1024x768
    Vert. Sync Range: 50-90 Hz
    Hor. Sync Range: 31-61 kHz
  Config Status: cfg=new, avail=yes, need=no, active=unknown
toast@Mars:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  
toast@Mars:~$ 

```Here is the xorg.conf
```
toast@Mars:/etc/X11$ more xorg.conf

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```and I have attached an updated X.0.log (from after the Nvidia driver update) just in case (still has the CRT error reported)

Thanks again.

~nhasan
Your monitor is still not giving it's edid data... But also, your nvidia driver is there, but not configured.  

While I am creating the modelines for you, could you go to a terminal. run this command, then post the new /etc/X11/xorg.conf file?
```

sudo nvidia-xconfig

```

---

### Post by MAFoElffen on 2011-12-11
Nevermind-- Here's your new xorg.conf file. I posted it and added as an attachment. It includes all the data your card needs for that monitor.  Please keep a backup somewhere:
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# Revised As Of: 2011.12.11.MAFoElffen
# nvidia-xconfig:  version 2890.10
# 



Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # Preset timing VESA® 1680 x 1050 @ 60 Hz
    Identifier     "Monitor0"
    VendorName     "Optiquest"
    ModelName      "Viewsonic Q2162wb"
    DisplaySize     494.94 290.59 
    HorizSync       38.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
    Modeline "1600x1200 60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245 -hsync +vsync
    Modeline "1680x1050 60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
    Modeline "1440x900 75.00"   136.75  1440 1536 1688 1936   900  903  909  942 -hsync +vsync
    Modeline "1440x900 60.00"   106.50  1440 1528 1672 1904   900  903  909  934 -hsync +vsync
    Modeline "1256x1024 75.00"  135.50  1256 1344 1472 1688  1024 1027 1037 1072 -hsync +vsync
    Modeline "1256x1024 60.00"  106.50  1256 1336 1464 1672  1024 1027 1037 1063 -hsync +vsync
    Modeline "1256x800 75.00"   105.00  1256 1336 1464 1672   800  803  813  838 -hsync +vsync 
    Modeline "1256x800 60.00"    81.50  1256 1320 1448 1640   800  803  813  831 -hsync +vsync 
    Modeline "1024x768 75.00"    82.00  1024 1088 1192 1360   768  771  775  805 -hsync +vsync 
    Modeline "1024x768 70.00"    75.25  1024 1080 1184 1344   768  771  775  802 -hsync +vsync 
    Modeline "1024x768 60.00"    63.50  1024 1072 1176 1328   768  771  775  798 -hsync +vsync 
    Modeline "800x600 75.00"     49.00   800  840  920 1040   600  603  607  629 -hsync +vsync 
    Modeline "800x600 60.00"     38.25   800  832  912 1024   600  603  607  624 -hsync +vsync 
    Modeline "800x600 56.00"     35.00   800  832  904 1008   600  603  607  623 -hsync +vsync 
    Modeline "720x400 70.00"     26.25   720  744  808  896   400  403  413  420 -hsync +vsync 
    Modeline "640x480 75.00"     30.75   640  664  728  816   480  483  487  504 -hsync +vsync 
    Modeline "640x480 72.00"     29.50   640  664  728  816   480  483  487  503 -hsync +vsync 
    Modeline "640x480 60.00"     23.75   640  664  720  800   480  483  487  500 -hsync +vsync 
    Option "PreferredMode"   "1600x1200 60.00"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName "NVIDIA GeForce 6xxx series and newer"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes     "1600x1200" "1440x900" "1280x1024" "1024x768" "800x600"
    EndSubSection
EndSection


```
I set your preferred mode to the prefer mode of your monitor.

To install it, do something like this:
```

sudo /path_to_the_copy_of/xorg.conf.nhason.txt /etc/X11/xorg.conf

```

---

### Post by nhasan on 2011-12-11
Great thanks MAFoElffen!!

I tried the copy over when I booted up I see the display but some reason the white lines are going through a portion of it (both in the login screen and post login) and if i move my mouse in that area it looks like there are two mouse pointers (one where it actually is and the other a few inches away only showing the stuff from the white lines)

So I went the System -> display and changed the setting to the 1400 x 1050 (4:3) even though this is a wide screen and things look good now - after logging in pre-login i still get the white lines.

I am pretty good with this resolution... but just not sure if there is anything else going wrong which I should be looking for.

Thanks again.

~nhasan

PS: I wasn't sure if you wanted me to run nvidia-config so i havent done so it :)

---

### Post by MAFoElffen on 2011-12-12
> **nhasan said:**
> Great thanks MAFoElffen!!

I tried the copy over when I booted up I see the display but some reason the white lines are going through a portion of it (both in the login screen and post login) and if i move my mouse in that area it looks like there are two mouse pointers (one where it actually is and the other a few inches away only showing the stuff from the white lines)

So I went the System -> display and changed the setting to the 1400 x 1050 (4:3) even though this is a wide screen and things look good now - after logging in pre-login i still get the white lines.

I am pretty good with this resolution... but just not sure if there is anything else going wrong which I should be looking for.

Thanks again.

~nhasan

PS: I wasn't sure if you wanted me to run nvidia-config so i havent done so it :)
Are you setting the resolution via nvidia-settings (Nvidia XServer Settings) and not via Monitors right?

---

### Post by nhasan on 2011-12-12
hmmm... probably doing it using the Monitors way (I actually clicked on the top right corner (the gear like option) and selected the displays from there.

When I am at home I will try using nvidia-settings.

thanks again!! :)

~nhasan

---

### Post by nhasan on 2011-12-12
Hi MAFoElffen,

Thank for the suggestion!

I tried the nvidia-settings and it looks like (perhaps) it does like the format of the preferred mode? The application loads despite the error but the configuration page displays the same error (and nothing else)

~nhasan

```
toast@Mars:~$ nvidia-settings

(nvidia-settings:11412): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(nvidia-settings:11412): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(nvidia-settings:11412): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(nvidia-settings:11412): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

ERROR: Failed to parse mode '1600x1200 60.00 @1600x1200 +0+0'
       on screen 0 (on GPU-0)
       from metamode:
       'CRT-0: 1600x1200 60.00 @1600x1200 +0+0'

```

---

### Post by MAFoElffen on 2011-12-12
> **nhasan said:**
> Hi MAFoElffen,

Thank for the suggestion!

I tried the nvidia-settings and it looks like (perhaps) it does like the format of the preferred mode? The application loads despite the error but the configuration page displays the same error (and nothing else)

~nhasan

```
toast@Mars:~$ nvidia-settings

(nvidia-settings:11412): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(nvidia-settings:11412): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(nvidia-settings:11412): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(nvidia-settings:11412): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

ERROR: Failed to parse mode '1600x1200 60.00 @1600x1200 +0+0'
       on screen 0 (on GPU-0)
       from metamode:
       'CRT-0: 1600x1200 60.00 @1600x1200 +0+0'

```
Let me re-look at that mode... Wait one.

---

### Post by MAFoElffen on 2011-12-12
Okay, first try this- Deltee or comment out the "Mode" line in the Screen Section of Screen0. 
```
[FONT=monospace]
[/FONT] Section "Screen"     
    Identifier     "Screen0"     
    Device         "Device0"     
    Monitor        "Monitor0"     
    DefaultDepth    24     
    SubSection     "Display"         
        Depth       24         
        # [COLOR=Red]Modes     "1600x1200" "1440x900" "1280x1024" "1024x768" "800x600"[COLOR=Black]
    [/COLOR][/COLOR]EndSubSection 
EndSection

```Save and try.

Then if it still has the white lines in mode 1600x1200 60.00 then comment out the modeline for it in the "Monitor" Section and add this one to replace it...
```

Modeline "1600x1200 60.00"  160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync

```I calculated all the modelines using the cvt utility. This one above is calculated using the gft utility. If that works, then test the other resolutions and see if they need to be recalc'ed.

On nvidia-settings itself: If you're not starting it from the menu or app launcher, then use 
```

gksudo nvidia-settings

```Unless you are already as root. 

With Nvidia, forget the Monitor applet is  there and make your adjustments there.  Even people 9w/ nvidia) who don't have any graphics troubles- if they change res via the Monitor applet, then the graphics get really slow and it acts if your computer is bogged down.

---

### Post by nhasan on 2011-12-13
Thanks MAFoElffen.

After removing the line I am getting a 1024x768 display. When I startup the nvidia-settings I see the following message (both in the Xserver config and on the command line):

```
Unable to load X Server Display Configuration page:

Failed to parse mode '1024x768 75.00 @1024x768 +0+0'
on screen 0 (on GPU-0)
from metamode:

'CRT-0: 1024x768 75.00 @1024x768 +0+0'
```

I tried to add the following line into the xorg.conf

```
Modes      "1440x900" "1280x1024" "1024x768" "800x600"
```

I still got an error similar to the one above (but now about 1440x900) - it did give options to set the higher resolutions thru the monitor applet. I commented it out and rebooted and now I am back to the 1024x768 error.

Not sure what to do... please help. 

~nhasan

---

### Post by MAFoElffen on 2011-12-13
> **nhasan said:**
> Thanks MAFoElffen.

After removing the line I am getting a 1024x768 display. When I startup the nvidia-settings I see the following message (both in the Xserver config and on the command line):

```
Unable to load X Server Display Configuration page:

Failed to parse mode '1024x768 75.00 @1024x768 +0+0'
on screen 0 (on GPU-0)
from metamode:

'CRT-0: 1024x768 75.00 @1024x768 +0+0'
```I tried to add the following line into the xorg.conf

```
Modes      "1440x900" "1280x1024" "1024x768" "800x600"
```I still got an error similar to the one above (but now about 1440x900) - it did give options to set the higher resolutions thru the monitor applet. I commented it out and rebooted and now I am back to the 1024x768 error.

Not sure what to do... please help. 

~nhasan
Okay... I recalculated everything 3 different ways and put it into your (now) new xorg.conf file:
```

# nvidia-xconfig: X configuration file generated by MAFoElffen (custom)
# Revised As Of: 2011.12.13
# Not generated by nvidia-xconfig:
# 



Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # Preset timing VESA® 1680 x 1050 @ 60 Hz
    Identifier     "Monitor0"
    VendorName     "Optiquest"
    ModelName      "Viewsonic Q2162wb"
    DisplaySize     494.94 290.59 
    HorizSync       38.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
[COLOR=Green]    ## Notes and Instructions on setting UseModes "[COLOR=DarkOrange]modesection-id[/COLOR]" and Option "[COLOR=Green]PreferredMode[/COLOR]" 
    #  "[COLOR=Blue]mode_name[/COLOR]". Which means, select a modes section to test and change to it by changing 
    #  the Usemode [COLOR=DarkOrange]value[/COLOR] to the Identifier value of the modes section you want... Then change 
    #  the PreferredMode value to the [COLOR=Blue]name[/COLOR] of the modeline for that resolution.
[/COLOR]    #
    UseMode        "[COLOR=DarkOrange]NV_Calc[/COLOR]"
    Option "PreferredMode"   "[COLOR=Blue]1680x1050[/COLOR]"
    ##
    ## Recommended and supported resolutions
    ##
    # 1600 x 1200 @ 60 Hz
    # 1680 x 1050 @ 60 Hz
    # 1440 x 900 @ 60, 75 Hz
    # 1280 x 1024 @ 60, 75 Hz
    # 1280 x 800 @ 60, 75 Hz
    # 1024 x 768 @ 60, 70, 75 Hz
    # 800 x 600 @ 56, 60, 75 Hz
    # 640 x 480 @ 60, 72, 75 Hz
    # 720 x 400 @ 70 Hz
EndSection

Section "Modes"
    Identifier    "CVT_Calc"
    # Thes were calcculated using the linux cvt utility.
    Modeline "1600x1200 60.00"  161.00  1600 1712 1880 2160  1200 1203 1207 1245  -hsync +vsync
    Modeline "1680x1050 60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089  -hsync +vsync
    Modeline "1440x900 60.00"   106.50  1440 1528 1672 1904   900  903  909  934  -hsync +vsync
    Modeline "1280x1024 60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063  -hsync +vsync
    Modeline "1280x800 60.00"    83.50  1280 1352 1480 1680   800  803  809  831  -hsync +vsync
    Modeline "1024x768 60.00"    63.50  1024 1072 1176 1328   768  771  775  798  -hsync +vsync
    Modeline "800x600 60.00"     38.25   800  832  912 1024   600  603  607  624  -hsync +vsync
    Modeline "640x480 60.00"     23.75   640  664  720  800   480  483  487  500  -hsync +vsync
EndSection

Section "Modes"
    Identifier    "GTF_Calc"
    #These were calculated using the Linux gft utility.
    Modeline "1600x1200_60.00"  160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync
    Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
    Modeline "1440x900_60.00"   106.47  1440 1520 1672 1904   900  901  904  932  -HSync +Vsync
    Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Modeline "1280x800_60.00"    83.46  1280 1344 1480 1680   800  801  804  828  -HSync +Vsync
    Modeline "1024x768_60.00"    64.11  1024 1080 1184 1344   768  769  772  795  -HSync +Vsync
    Modeline "800x600_60.00"     38.22   800  832  912 1024   600  601  604  622  -HSync +Vsync
    Modeline "640x480_60.00"     23.86   640  656  720  800   480  481  484  497  -HSync +Vsync
EndSection 

Section "Modes"
    Identifier    "[COLOR=DarkOrange]NV_Calc[/COLOR]"
    ## Nvida Recognized Internal Modes. The NVidia Techs say that some of their cards 
    # ignore add modes except for the internal modes in their card. These modelines are 
    # from NVidia, saying they will recognize these...
    ModeLine "[COLOR=Blue]1680x1050[/COLOR]"        147.14  1680 1784 1968 2256  1050 1051 1054 1087  +HSync +VSync
    ModeLine "1600x1200"        162.00  1600 1664 1856 2160  1200 1201 1204 1250  +HSync +VSync
    ModeLine "1440x900"         108.84  1440 1472 1880 1912   900  918  927  946  +HSync +VSync
    ModeLine "1280x1024"        108.00  1280 1328 1440 1688  1024 1025 1028 1066  +HSync +VSync
    ModeLine "1280x800"          83.46  1280 1344 1480 1680   800  801  804  828  +HSync +VSync
    ModeLine "1024x768"          65.00  1024 1048 1184 1344   768  771  777  806  -HSync -VSync
    ModeLine "800x600"           40.00   800  840  968 1056   600  601  605  628  +HSync +VSync
    ModeLine "640x480"           31.50   640  656  720  840   480  481  484  500  -HSync -VSync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName "NVIDIA GeForce 6xxx series and newer"
    Option "UseEDID" "FALSE"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
EndSection

```I documented this config file on how to use it and what to change.  I figure since the Monitor, is not giving the EDID data to the Xserver, then Xserver was erroring out on parsing a modeline... but not telling us why(?) I just gave both of us something to test and hopefully work.

For now, since there is both different modelines for the same reslutions, as there are different refresh rates, I tried to slim it down, while still giving us some flexibility.  Read through the comments in the above posted file. I color coded the code in the post so that You might follow it easier-...

If you wanted to change your resolution or if we need to test to a different modeline for a particularr resolution, you are going to need to edit this file, rather than let one of the automated applets.  This is a work-around to solve a problem and those applets aren't geared for that.

Rather than cut-and-pasting the file... If you could download the attached file (same file), it might be better, as sometimes posting vs. is different in the formatting. I want you to have all chances at success with this... I least I'm hoping for that.

If you get "any" error, post your /var/log/Xorg.0.log file, on parsing errors, it usually shows what line number or some kind of clue...  Without that, I have to look and guess.

---

### Post by nhasan on 2011-12-13
Great thanks MAFoElffen... 

Now it looks I am stuck again. Here are the steps

1. The xorg.conf file was using UseMode I tried several different resolutions but they all failed 
[LIST]
[*]Would see the splash screen
[*]Ubuntu would freeze
[*]Ctrl-Alt-Del to restart and edit grub to boot kernel as "text"
[*]get the ttyl and edit the xorg.conf for next resolution
[/LIST]
2. I looked at X.org.log and saw the error related to the modes
3. looked at man xorg.conf and saw it should be UseModes
4. Changed the settings in xorg.conf and it looks like it is complaining in the X.org.log that I am not setting a Preferred mode?

With the UseModes change I *can not* <-- (meant to say can) boot into X and get 1024x768 resolution for now ;)

I am attaching the modified xorg.conf and a couple of Xorg.0.log files which show the results of setting with the NV option vs CV option

Please take a look :)

~nhasan

---

### Post by MAFoElffen on 2011-12-14
> **nhasan said:**
> Great thanks MAFoElffen... 

Now it looks I am stuck again. Here are the steps

1. The xorg.conf file was using UseMode I tried several different resolutions but they all failed 
[LIST]
[*]Would see the splash screen
[*]Ubuntu would freeze
[*]Ctrl-Alt-Del to restart and edit grub to boot kernel as "text"
[*]get the ttyl and edit the xorg.conf for next resolution
[/LIST]
2. I looked at X.org.log and saw the error related to the modes
3. looked at man xorg.conf and saw it should be UseModes
4. Changed the settings in xorg.conf and it looks like it is complaining in the X.org.log that I am not setting a Preferred mode?

With the UseModes change I *can not* <-- (meant to say can) boot into X and get 1024x768 resolution for now ;)

I am attaching the modified xorg.conf and a couple of Xorg.0.log files which show the results of setting with the NV option vs CV option

Please take a look :)

~nhasan
Sorry on the typo... Yes, frustratingly it's ignoring the "PreferredMode" and then using  autoselect.  

Just for a test, I added a few more pointers to 1440x900 and slimmed it down to just that resolution.  
```

# X configuration file generated by MAFoElffen (custom)
# Revised As Of: 2011.12.14
# Not generated by nvidia-xconfig:
# 

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Optiquest"
    ModelName      "Viewsonic Q2162wb"
    DisplaySize     494.94 290.59 
    HorizSync       38.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
    ## Valid UseModes values = CVT_Calc, GTF_Calc & NV_Calc
    UseModes        "NV_Calc"
    Option "PreferredMode"   "1440x900"
EndSection

Section "Modes"
    Identifier    "CVT_Calc"
    Modeline "1440x900"    106.50  1440 1528 1672 1904   900  903  909  934  -hsync +vsync
EndSection

Section "Modes"
    Identifier    "GTF_Calc"
    Modeline "1440x900"    106.47  1440 1520 1672 1904   900  901  904  932  -HSync +Vsync
EndSection 

Section "Modes"
    Identifier    "NV_Calc"
    ModeLine "1440x900"    108.84  1440 1472 1880 1912   900  918  927  946  +HSync +VSync
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName "NVIDIA GeForce 6xxx series and newer"
    Option "UseEDID" "false"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection      "Display"
        Depth       24
        Modes       "1440x900"
    EndSubSection
EndSection

```

---

### Post by nhasan on 2011-12-14
You are the man!!

:guitar::biggrin::biggrin::biggrin::biggrin:

I tried out the config (minor edit on the fasle --> false and then the nv_config didnot give the best results (the screen was off to one side). Tried the cvt_config and perfection!!

The screen before booting is higher resolution and once logged in it was lower resolution so I chose the 1440x900 using the Monitor applet and voila a beautiful screen :)

Thanks a lot MAFoElffen for taking the time and effort to help me out. It is much appreciated.

Thanks a lot and I wish you the best.

~nhasan

---

### Post by MAFoElffen on 2011-12-15
> **nhasan said:**
> You are the man!!

:guitar::biggrin::biggrin::biggrin::biggrin:

I tried out the config (minor edit on the fasle --> false and then the nv_config didnot give the best results (the screen was off to one side). Tried the cvt_config and perfection!!

The screen before booting is higher resolution and once logged in it was lower resolution so I chose the 1440x900 using the Monitor applet and voila a beautiful screen :)

Thanks a lot MAFoElffen for taking the time and effort to help me out. It is much appreciated.

Thanks a lot and I wish you the best.

~nhasan
You're very welcome. Please use the Thread tools link at the top of this page to mark this thread as solved.

---

