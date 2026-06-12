---
title: "Can't install grub.  OS not bootable."
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by wagoner on 2012-12-28
I recently decided to install lubuntu on an old desktop PC.  It's 3GHz P4 with a half meg of ram.  I had openSUSE 11.4 on there, but KDE seemed to be too much for it.  The install went fine, but it wouldn't boot.

No problem, I thought. I have a Kubuntu 11.4 liveCD laying around, so I booted with that and attempted a rescue.  (I installed lubuntu with netboot, so I don't happen to have that on CD or USB).

Boot-Repair wouldn't install onto the system.  I tried adding the PPA and such as it is described in the community documents, but it returned an error saying that it was unable to find the package boot-repair.

So now onto plan C, reinstall grub via the command line without the benefit of boot repair.  For the most part, I followed the instructions that I found [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/Grub2/Installing")  Installing Grub with chroot.

When the system boots, it says grub loading stage 1.5, and then returns error 15 and hangs.  I guess this computer has legacy grub on there from the last system.

So here is my attempt to reinstall grub.

I'll start with a list of my partitions.  Here are the results of parted and blkid
```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST340014A (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  40.0GB  40.0GB  primary  ntfs         boot


Model: ATA Maxtor 4D040H2 (scsi)
Disk /dev/sdb: 41.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  107MB   106MB   primary   ext4
 2      107MB   13.0GB  12.9GB  primary   ext4
 3      13.0GB  41.0GB  28.0GB  extended                  lba
 5      13.0GB  39.4GB  26.4GB  logical   ext4
 6      39.4GB  41.0GB  1611MB  logical   linux-swap(v1)


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label         

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="9618C90E18C8EDF5" TYPE="ntfs" 
/dev/sdb1: UUID="caabcd3e-c343-4526-9e6c-e33243233943" TYPE="ext4" 
/dev/sdb2: UUID="7ffad25c-ddc1-4627-91da-ca7d2dd3e644" TYPE="ext4" 
/dev/sdb5: LABEL="beershelf folder" UUID="43c4066b-edf2-42af-9ca9-2663b18b7c62" TYPE="ext4" 
/dev/sdb6: UUID="27788ab1-7394-410b-a0af-504aed8308c3" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

```

/dev/sda1 is Windows XP and lubuntu is on /dev/hdb

/dev/sdb1 is the /boot partition
/dev/sdb2 is the / partition
/dev/sdb5 is the /home partion
/dev/sdb6 is swap

So, mount my lubuntu on /mnt
Please have a look and let me know if I made any errors.

```
ubuntu@ubuntu:~$ sudo mount /dev/sdb2 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /mnt/boot
ubuntu@ubuntu:~$ sudo mount /dev/sdb5 /mnt/home
ubuntu@ubuntu:~$ sudo mount -o bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount -v -o bind /dev /mnt/dev
/dev on /mnt/dev type none (rw,bind)
ubuntu@ubuntu:~$ sudo mount -v -o bind /sys /mnt/sys
/sys on /mnt/sys type none (rw,bind)
ubuntu@ubuntu:~$ sudo mount -v -o bind /dev/pts /mnt/dev/pts
/dev/pts on /mnt/dev/pts type none (rw,bind)
ubuntu@ubuntu:~$ sudo mount -v -o bind /run /mnt/run
mount: special device /run does not exist
```

I guess there is no directory /run.  There was one in the example.

Now everything is ready.  chroot into mount and install grub.

```
root@ubuntu:/# grub-install --boot-directory=/mnt/boot /dev/sda
/usr/sbin/grub-bios-setup: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.
root@ubuntu:/# grub-install --boot-directory=/mnt/boot --recheck /dev/sda
/usr/sbin/grub-bios-setup: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-21-generic
Found initrd image: /boot/initrd.img-3.5.0-21-generic
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
```

Everything looks good.  But when I reboot, I'm right back where I started.  It says loading grub stage 1.5, and then grub error 15.

What is the problem?

---

### Post by oldfred on 2012-12-28
With the new versions of grub2, you really need to repair with the same version. The full chroot should have worked.

The sector 32 in use, is usually flexnet DRM software. New version of grub2 have a work around. Flexnet is used by very proprietary software in Windows that want DRM so you cannot copy it.

Are you booting from sda, not sdb? I usually prefer to keep Windows boot loader on the Windows drive so it can boot directly & then install grub2 to the Ubuntu drive and set that as boot in BIOS as it will chain load back to Windows.

Error 15 is usually mixed grub legacy & grub2. Often from the chroot you need to do a full uninstall of grub & grub2 & the /boot/grub folder and totally reinstall grub2.

       # HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

    HowTo: Revert from grub2 to Legacy Grub or grub to grub2 
[https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy](https://help.ubuntu.com/community/Grub2/Upgrading#Reverting_to_GRUB_Legacy)
Older threads kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

Were you tring to install the correct version of Boot-Repair. I think it does not have a version for 11.04 as that is now obsolete. But you can download a full ISO to use as a repair install. If older system you may need 32 bit version?
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by wagoner on 2012-12-29
Thanks oldfred.  I burned the lubuntu desktop CD so that I had something that was up to date and started again.  I followed the directions from the > # HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
but I couldn't seem to access the repositories and I got an error about unable to resolve host names or something.  I copied the resolv.conf like the HOWTO said, and that seemed to help, but there were still some errors.

I went back to boot-repair and I was able to install that this time.  It worked.  Grub seems to be installed on /dev/sdb, which is ok, but I was really trying to install it to /dev/sda.  /dev/sda still has legacy grub on there and after a couple of days of trying to remove it, I'm starting to think it isn't going to leave.  

Now every time I boot I have to go into my bios and select the primary slave to boot from.  There doesn't seem to be any way to set this permanently.

/dev/sda is Windows XP.  My last install on this computer was openSUSE 11.4 on /dev/sdb, and I installed grub legacy to the MBR on /dev/sda at that time.  It seemed to work well, so I figured just install grub there again.

Incidentally, Windows XP isn't working now.  I don't think it's any fault of boot loader, since it starts but hangs part way through the boot process.  I tried to reinstall Windows XP today, but it returned an error while formatting the Windows partition /dev/sda1.  Maybe there is a problem with the primary master hard drive.

Nevertheless, it doesn't take much to write grub2 to the MBR of /dev/sda1.  Why doesn't this work?  Why is legacy grub still on there?

---

### Post by oldfred on 2012-12-29
Did you use sda1 to write grub? That would be why Windows would stop working. All NTFS partitions (whether bootable or not) have to have a NTFS boot signature. If you installed grub to sda1 you overwrote the XP boot in the partition. NTFS does have a backup PBR & testdisk can repair it. But if you have reinstalled I am not sure where you are at.

Post link to BootInfo report from Boot-Repair.

You should be able to directly install grub2's boot loader to sda. If booted, just run this.

       #reinstall from working (not live-CD/DVD/USB) system - first find Ubuntu drive (example is drive sda but use your drive not partitions):
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
#If that returns any errors run:
sudo grub-install --recheck /dev/sda
sudo update-grub


Must be an older IDE system. Newer one's with cable select have BIOS that let you boot either drive and remembered that if set as default in BIOS. Older systems only booted from sda or primary master set with jumpers on drive and BIOS was very limited.

---

### Post by darkod on 2012-12-29
Concerning the chroot process you tried earlier, you mixed it up a little. You use the --root-directory or --boot-directory option in grub-install only when doing it from live mode WITHOUT chroot (because you can do it that way too).

Once you are inside the chroot, it knows where / and /boot is, so you use only:
grub-install /dev/sda

for example.

Also, for chroot you don't need to mount the /home partition, leave it alone. You only need to mount / and /boot if you have it. A more precise chroot procedure you can find in one of my older posts:
[http://ubuntuforums.org/showpost.php?p=11858371&postcount=29](http://ubuntuforums.org/showpost.php?p=11858371&postcount=29)

In the first commnd where / is mounted you will have to adjust for your situation, and mount the /boot too if it exists. Also the grub-install command needs to be adjusted depending where you want to install grub2.

Also, you can install it on both /dev/sda and /dev/sdb and that way it will not make a difference from which disk you boot. As oldfred said, in cases it's better to keep the windows bootloader on /dev/sda but only in case your computer bios allows you to boot from /dev/sdb. If you can boot only from /dev/sda then you will have to have grub2 on it.

Again, as oldfred mentioned, you will need to check whether the XP stopped booting because you put grub2 on /dev/sda1.

---

### Post by wagoner on 2012-12-29
I tried some more things, but grub legacy is still on the MBR.  I booted the windows install disks, and got into the recovery screen and typed fixboot and fixmbr.  The messaged returned successful, but when I rebooted, still got grub error 15.

Next I attempted to overwrite the MBR with dd, and then reinstall grub.  Here it is.```
fred@beershelf:~/Computer$ sudo dd if=/dev/zero of=/dev/sda bs=446 count=1
1+0 records in
1+0 records out
446 bytes (446 B) copied, 0.0342275 s, 13.0 kB/s
fred@beershelf:~/Computer$ sudo grub-install /dev/sda
/usr/sbin/grub-bios-setup: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

```

Here is the boot script from boot-repair. [[COLOR="Red"]http://paste.ubuntu.com/1477729/[/COLOR]]("http://paste.ubuntu.com/1477729/")  This is after executing all of the commands above.

---

### Post by oldfred on 2012-12-29
It is still showing grub legacy in sda?

Your dd should have overwritten it??

Your grub install should have installed grub2, unless you really are booting with grub legacy. But all your files are grub2???

Grub error 15 is usually grub legacy and grub2 incompatibilities. Or error is from grub legacy as grub2 does not have error numbers.

Did you try Boot-Repair on installing grub2.

Grub2 also has an option to totally uninstall grub & grub2 and reinstall grub2.

You must have some DRM software in Windows that uses flexnet for the DRM. Grub2 has to write work arounds for sector 32 as its core.img is larger than grub legacy's stage 1.5.

---

### Post by darkod on 2012-12-30
I don't know if it uses sector 32 but sometimes there is also an option in BIOS to "protect" the MBR from writing. Make sure you don't have some option like that enabled or some software inside windows preventing you touching the bootloader. Although I don't see how a software in windows can prevent grub being overwritten when you are working with linux tools outside windows.

---

### Post by wagoner on 2012-12-30
Thanks for the help oldfred.  There seems to be a lot of posts about Flexnet on Sector 32 and grub.  Everyone seems to fix it easily enough with dd.  Doesn't seem to work here.  Take a look.

```
fred@beershelf:~$ sudo dd if=/dev/zero of=/dev/sda bs=512 count=62 seek=1
62+0 records in
62+0 records out
31744 bytes (32 kB) copied, 0.0275476 s, 1.2 MB/s
fred@beershelf:~$ sudo grub-install /dev/sda
/usr/sbin/grub-bios-setup: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

```

Any other ideas?

---

### Post by wagoner on 2012-12-30
Oh nevermind.  I'm pretty sure that the hdd on /dev/sda is bad.  I just tried to install windows XP on it, again, only to have it say it couldn't be installed for one reason or another.  Then I tried to install lubuntu on it and it said that there was a problem with the drive.

---

### Post by darkod on 2012-12-30
Remove Flexnet?

The message says the software stores something there and grub is avoiding it. My guess is overwriting doesn't work as long as Flexnet is not removed too. There is not much point in security protection that you can easily overwrite.

Try removing Flexnet, then reinstalling grub2.

---

### Post by wagoner on 2012-12-30
darknod, if the bios is protecting the MBR somehow, that might explain the problem.  I spent some time in the bios screen trying to change the boot order to /dev/sdb, but I didn't see anything about protecting the MBR.  Also, I attempted to remove flexnet with dd, and that didn't work. 

I opened up the box and switched the hard drives around, so that the slave is now the master.  /dev/sdb is now /dev/sda.  I didn't reinstall anything, but lubuntu boots and runs fine.  Is this ok?

Also, I performed the hard drive self diagnostics using smartmontools.  Can anyone interpret these results for me?  

[COLOR="Blue"]Is this drive bad? Keep in mind that this was /dev/sda in my previous posts, but it is now /dev/sdb because it has been switched.
[/COLOR]```
fred@beershelf:~$ sudo smartctl --attributes --log=selftest /dev/sdb
[sudo] password for fred: 
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.5.0-21-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   055   051   006    Pre-fail  Always       -       87704485
  3 Spin_Up_Time            0x0003   098   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       17
  7 Seek_Error_Rate         0x000f   089   060   030    Pre-fail  Always       -       889151690
  9 Power_On_Hours          0x0032   053   053   000    Old_age   Always       -       41674
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       190
194 Temperature_Celsius     0x0022   034   040   000    Old_age   Always       -       34
195 Hardware_ECC_Recovered  0x001a   055   051   000    Old_age   Always       -       87704485
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       11
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       11
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
200 Multi_Zone_Error_Rate   0x0000   100   253   000    Old_age   Offline      -       0
202 Data_Address_Mark_Errs  0x0032   100   253   000    Old_age   Always       -       0

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%         1         -

```

[COLOR="Blue"]:arrow:The raw read errors rate is pretty high, so I assume that is bad.

And here is the other drive with lubuntu installed and working.  It says read failure on the extended offline test.:confused:  What do you think?
[/COLOR]```
fred@beershelf:~$ sudo smartctl --attributes --log=selftest /dev/sda
smartctl 5.43 2012-06-30 r3573 [i686-linux-3.5.0-21-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, http://smartmontools.sourceforge.net

=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  3 Spin_Up_Time            0x0027   234   234   063    Pre-fail  Always       -       5836
  4 Start_Stop_Count        0x0032   253   253   000    Old_age   Always       -       225
  5 Reallocated_Sector_Ct   0x0033   242   242   063    Pre-fail  Always       -       29
  6 Read_Channel_Margin     0x0001   253   253   100    Pre-fail  Offline      -       0
  7 Seek_Error_Rate         0x000a   253   252   000    Old_age   Always       -       0
  8 Seek_Time_Performance   0x0027   249   228   187    Pre-fail  Always       -       32938
  9 Power_On_Minutes        0x0032   253   253   000    Old_age   Always       -       232h+01m
 10 Spin_Retry_Count        0x002b   253   252   157    Pre-fail  Always       -       0
 11 Calibration_Retry_Count 0x002b   253   252   223    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   250   250   000    Old_age   Always       -       1338
192 Power-Off_Retract_Count 0x0032   253   253   000    Old_age   Always       -       0
193 Load_Cycle_Count        0x0032   253   253   000    Old_age   Always       -       0
194 Unknown_Attribute       0x0032   253   253   000    Old_age   Always       -       0
195 Hardware_ECC_Recovered  0x000a   253   252   000    Old_age   Always       -       54
196 Reallocated_Event_Count 0x0008   252   252   000    Old_age   Offline      -       1
197 Current_Pending_Sector  0x0008   252   252   000    Old_age   Offline      -       1
198 Offline_Uncorrectable   0x0008   252   252   000    Old_age   Offline      -       1
199 UDMA_CRC_Error_Count    0x0008   199   199   000    Old_age   Offline      -       0
200 Multi_Zone_Error_Rate   0x000a   253   252   000    Old_age   Always       -       0
201 Soft_Read_Error_Rate    0x000a   253   252   000    Old_age   Always       -       2
202 Data_Address_Mark_Errs  0x000a   253   252   000    Old_age   Always       -       0
203 Run_Out_Cancel          0x000b   253   252   180    Pre-fail  Always       -       0
204 Soft_ECC_Correction     0x000a   253   252   000    Old_age   Always       -       0
205 Thermal_Asperity_Rate   0x000a   253   252   000    Old_age   Always       -       0
207 Spin_High_Current       0x002a   253   252   000    Old_age   Always       -       0
208 Spin_Buzz               0x002a   253   252   000    Old_age   Always       -       0
209 Offline_Seek_Performnce 0x0024   253   253   000    Old_age   Offline      -       0
 99 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
100 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0
101 Unknown_Attribute       0x0004   253   253   000    Old_age   Offline      -       0

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       40%       217         8253448
# 2  Extended offline    Completed: read failure       40%       217         8253448
# 3  Short offline       Completed without error       00%         1         -

```

Please have a look at the smartmontools results.

---

### Post by oldfred on 2012-12-30
I do not know details of tests, but just look at what it reports as the overall. Or green is good and anything else is time for a new drive.

---

