---
title: "Gparted says: Can't have overlapping partitions."
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by mkellerman on 2013-05-31
When I boot my Dell Vostro 1400 I get a grub error. I suspect this happened since after it was powered off suddenly while being booted. I dual boot Ubuntu and Windows XP.

I booted from an Ubuntu USB drive and can see my partitions and files in the Ubuntu file explorer. The only unsual thing (not sure if it was like this before the computer wouldn't boot) is that there are two partitions that seem to be duplicates of each other: /media/MEDIADIRECT and /media/MEDIADIRECT_  The contents of these are Dell bloatware that allows you to boot into a slimmed down version of Windows that plays video and audio files--don't care if this bloatware is deleted, if those partitions are causing the problem. 

When I booted from the USB drive I ran the following command:

```
ubuntu@ubuntu:~$ sudo fdisk  -lu /dev/sda

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x92fc5002

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   307323513   312576704     2626596    c  W95 FAT32 (LBA)
/dev/sda2          160650    84068144    41953747+   7  HPFS/NTFS/exFAT
/dev/sda3        84068206   312576704   114254249+   f  W95 Ext'd (LBA)
/dev/sda5        84068208   267239423    91585608    7  HPFS/NTFS/exFAT
/dev/sda6       307323513   312576704     2626596    0  Empty
/dev/sda7       267241472   303353855    18056192   83  Linux
/dev/sda8       303355904   307320831     1982464   82  Linux swap / Solaris

Partition table entries are not in disk order


```
Any idea what I should do? Can fixparts fix this?

---

### Post by mkellerman on 2013-05-31
More info about the grub issue.

When I boot, the following is displayed. (I typed *ls* to get more info)
```
error: unknown filesystem
grub rescue> ls
(hd0) (hd0,msdos7) (hd0,msdos6) (hd0,msdos5) (hd0,msdos2) (hd0,msdos1)
grub rescue> 

```

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by mkellerman on 2013-05-31
OK, I installed gsmartcontrol, but my hard drive shows as "unknown model". I don;t see an attributes tab.
The command line output looks like this:
```
ubuntu@ubuntu:~$ gsmartcontrol &
[1] 6193
ubuntu@ubuntu:~$ <warn>  [hz] Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.
<warn>  [hz] Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.
<warn>  [hz] Warning: exit: Command line did not parse.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.
<warn>  [hz] Warning: exit: Device open failed, or device did not return an IDENTIFY DEVICE structure.
<warn>  [app] execute_smartctl(): Error while executing smartctl binary.
<warn>  [app] StorageDevice::execute_device_smartctl(): Error while executing smartctl binary.


```


Anyway, on to the next bit. I executed the code you suggested to fix grub as shown:

```
ubuntu@ubuntu:~$ umount /dev/sda7
umount: /dev/sda7 is not mounted (according to mtab)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# grub-install --recheck /dev/sda
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-25-generic
Found initrd image: /boot/initrd.img-3.5.0-25-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Embedded on /dev/sda1
Found Microsoft Windows XP Home Edition on /dev/sda2
Found Microsoft Windows XP Embedded on /dev/sda6
done


```

I'm going to reboot and see what happens...I'm wiritng this on the machine with the problem...


> **ahallubuntu said:**
> You don't have "duplicate partitions."  Partitions are mounted in /media by Nautilus.  It appears the Dell media partition was simply mounted twice for some reason.  The "not in disk order" message is not an error and is not unusual.

As I recall, those Dell media partitions (I had an old Dell laptop with one of those, too) can't actually be deleted.  Somehow they are "fixed" on the drive.  And the size isn't that large, anyway, as I recall.

You're really trying to fix the Grub error, right?  Your hard disk can't boot?  Go back to focusing on that.  First thing is to check the hard drive S.M.A.R.T. health.  Boot up your live USB again and install GSmartControl.  Start it up and find the Attributes tab.  Look for Attributes that are highlighted in pink or red - these are the ones that are possible problems.  (Pending Sectors for example where the raw value is greater than 0.)  If there are no Attributes highlighted, the drive is probably not failing.

You can re-install Grub from the live USB on to the hard drive.  I prefer the chroot method:

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

which in a simple system without RAID, without a separate /boot partition, with one hard drive, boils down to this:

(unmount /dev/sda7 if mounted somewhere else)

```
sudo mount /dev/sda7 /mnt
for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
sudo chroot /mnt
grub-install --recheck /dev/sda
update-grub
exit

```

and then reboot and see if it works.  But if your hard drive has S.M.A.R.T. issues, you may not be able to do much of this.

---

### Post by mkellerman on 2013-05-31
Doh...I realised that maybe gsmartcontrol has to be run as root. I did sudo smartcontrol and it worked.

In the attributes tab, all attributes were shown in black.  I got it to perform a short self-test which completed without error.

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by mkellerman on 2013-05-31
I rebooted and the problem is fixed. Thanks a lot!

Just one question, how can I change the default OS that is booted if I do not touch the keyboard when  the computer is booted?

---

### Post by ahallubuntu on 2013-05-31
~

---

### Post by mkellerman on 2013-06-01
Thanks, I'll try this. It seems you need to look at the boot menu as it boots up to see when the number after "GRUB_DEFAULT" should be. This issue can be considered SOLVED.

> **ahallubuntu said:**
> Edit the file /etc/default/grub (as sudo):

```
gksu gedit /etc/default/grub
```

and change the number after "GRUB_DEFAULT" to the menu position you want.

Save the file.  Then update Grub again:

```
sudo update-grub
```

It may take a little trial and error to pick a number that gets you the right menu position.

---

