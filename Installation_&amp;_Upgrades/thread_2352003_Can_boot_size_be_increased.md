---
title: "Can /boot size be increased?"
date: 2017-02-08
forum: Installation &amp; Upgrades
---

### Post by ian78 on 2017-02-08
I have had the dreaded "gzip: stdout: No space left on device" error a number of times when applying updates over the past couple of years. One of them was during the upgrade from 14.xx to 16.xx and that took quite a lot of messing around to sort out. Given that i have a 3TB physical boot drive in the system with currently 2.5TB of free space, it seems silly to have a boot partition that is struggling for space so i would like to resize it to something like 2GB so i dont have to worry about space anymore.

I have just applied the latest set of updates and /boot has gone from having some free space to zero free space. Webmin reports /boot as having **Size** 236.29 MB **Free** 0 bytes

Is it possible to resize /boot and still have a working system afterwards?

---

### Post by #&amp;thj^% on 2017-02-08
What dose this report from the terminal:
```
sudo apt autoremove
```
And one more:
```
df -h
```
> Is it possible to resize /boot and still have a working system afterwards?
Never have i tried this..so no help from me on this.

---

### Post by ubfan1 on 2017-02-08
Do you even need a /boot partition?  Encrypted/LVM and your machine BIOS unable to address the full multi T disk may be reasons for having a /boot partition.  If you don't need one, it should be easy to unmount the /boot partition, remount it say at /mnt or /tmp/boot for instance, and recursively copy everything from the /boot partition to the root's /boot directory (assuming you have lots of room in /).  Then comment out the /etc/fstab mount of /boot, and see if you can reboot.

---

### Post by ajgreeny on 2017-02-08
The only good reason for having a /boot partition is if you have an encrypted or LVM system, in which case it is created at installation time.  You can not move the files or folders from that to another partition within your LVM or encrypted root partition as it will not work from an encrypted filesystem and you will be unable to boot at all.

Give us the output of command ```
dpkg -l | grep linux-image*
```followed by ```
ls /boot | grep vmlinuz
```so we can get some idea of the kernels installed on your system and we can then set about removing some properly.

**Do not attempt to remove anything at this stage simply by using the file manager or any rm commands** as that may cause a different problem which we will have to solve.

---

### Post by ian78 on 2017-02-08
df -h gave this (executed before the autoremove)

```
nasadmin@homenas:/$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                          48G     0   48G   0% /dev
tmpfs                        9.5G   10M  9.5G   1% /run
/dev/mapper/ubuntu--vg-root  2.7T  9.2G  2.6T   1% /
tmpfs                         48G  352K   48G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                         48G     0   48G   0% /sys/fs/cgroup
/dev/md0                      22T  4.9T   17T  23% /raid
/dev/sdi2                    237M  236M     0 100% /boot
/dev/sdi1                    511M  3.6M  508M   1% /boot/efi
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        9.5G   24K  9.5G   1% /run/user/112
tmpfs                        9.5G   12K  9.5G   1% /run/user/1000

```


apt autoremove had to be run twice before it completed without errors

first run

```
nasadmin@homenas:/$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-headers-4.4.0-53 linux-headers-4.4.0-53-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-image-4.4.0-53-generic
  linux-image-4.4.0-57-generic linux-image-extra-4.4.0-53-generic
  linux-image-extra-4.4.0-57-generic linux-signed-image-4.4.0-53-generic
  linux-signed-image-4.4.0-57-generic
0 to upgrade, 0 to newly install, 10 to remove and 4 not to upgrade.
6 not fully installed or removed.
After this operation, 593 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 338598 files and directories currently installed.)
Removing linux-headers-4.4.0-53-generic (4.4.0-53.74) ...
Removing linux-headers-4.4.0-53 (4.4.0-53.74) ...
Removing linux-headers-4.4.0-57-generic (4.4.0-57.78) ...
Removing linux-headers-4.4.0-57 (4.4.0-57.78) ...
Removing linux-signed-image-4.4.0-53-generic (4.4.0-53.74) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-53-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-53-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-53-generic (4.4.0-53.74) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-signed-image-4.4.0-57-generic (4.4.0-57.78) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-extra-4.4.0-57-generic (4.4.0-57.78) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Found linux image: /boot/vmlinuz-4.4.0-57-generic
Found initrd image: /boot/initrd.img-4.4.0-57-generic
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-4.4.0-57-generic (4.4.0-57.78) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-57-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-57-generic /boot/vmlinuz-4.4.0-57-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Adding boot menu entry for EFI firmware configuration
done
Errors were encountered while processing:
 linux-image-extra-4.4.0-53-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

second run

```
nasadmin@homenas:/$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-image-extra-4.4.0-53-generic
0 to upgrade, 0 to newly install, 1 to remove and 4 not to upgrade.
7 not fully installed or removed.
After this operation, 161 MB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 274059 files and directories currently installed.)
Removing linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-53-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
depmod: WARNING: could not open /lib/modules/4.4.0-53-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/4.4.0-53-generic/modules.builtin: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_2xW2St/lib/modules/4.4.0-53-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_2xW2St/lib/modules/4.4.0-53-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found linux image: /boot/vmlinuz-4.4.0-59-generic
Found initrd image: /boot/initrd.img-4.4.0-59-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-generic (4.4.0.62.65) ...
Setting up linux-generic (4.4.0.62.65) ...
Setting up linux-signed-image-generic (4.4.0.62.65) ...
Setting up linux-signed-generic (4.4.0.62.65) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic

```

Having now run the autoremove the boot partition now contains

```

nasadmin@homenas:/$ ls /boot | grep vmlinuz
vmlinuz-4.4.0-59-generic
vmlinuz-4.4.0-59-generic.efi.signed
vmlinuz-4.4.0-62-generic
vmlinuz-4.4.0-62-generic.efi.signed

```

and df now reports /boot as

```

/dev/sdi2                    237M  134M   91M  60% /boot

```


I have no idea if its possible to run without /boot or not. I'm sure the system boots from UEFI so is the BIOS actually still involved?
I dont know if a large raid 6 array in this system makes any difference or not to what/how it boots.

I've been using Windows (and before that MSDos) systems for the last 30 years but what i know about Linux systems could be written on the back of a small postage stamp. My preference would have been to stay inside my comfort zone and use a Windows Server but after testing Windows RAID and Linux RAID on ubuntu as well as reading extremely useful sources of information such as these forums it seemed that Linux raid was generally regarded as being better and more able than Windows raid.

---

### Post by #&amp;thj^% on 2017-02-08
> **ian78 said:**
> 
_**I dont know if a large raid 6 array in this system makes any difference or not to what/how it boots**_.
  
And with this bit of information added....I will have to hand off to a more knowledgeable person here.:D
I will add we have some sharp one's here.
Best of luck.;)

---

### Post by ubfan1 on 2017-02-08
I don't know much about RAID or logical volumes, but you probably do need the /boot partition.  Do you have any free space on the 3T disk? If so maybe you can just make a bigger partition for /boot.  Maybe you can shrink the /boot/efi a bit and add it to /boot, they look adjacent.  Do that cautiously since both are involved in booting.  Another possibly easy fix is to boot off a USB device,  which runs root off the disk.  i.e put the boot partition on a USB stick.

---

### Post by #&amp;thj^% on 2017-02-08
Just found this: [https://raid.wiki.kernel.org/index.php/Growing](https://raid.wiki.kernel.org/index.php/Growing)

---

### Post by yancek on 2017-02-08
The two options that would be most reasonable are to on a regular basis, run the 'autoremove' since that significantly reduced the used size of the boot partition.
Second option would be to shrink the EFI partition which is 500Mb and uses less than 4MB.  The problem with this is that you will be moving the data in the partition and I would not try this without having a backup of the entire boot partition as there is a high risk of the machine being unbootable if it fails.

---

### Post by r.stiltskin on 2017-02-08
Why risk resizing the partition at all?  The real problem here is just the accumulation of old superseded kernel images and there's no reason to keep them.  When have you ever had to revert back farther than the 2nd prior kernel version?  You should simply run autoremove after each kernel upgrade -- takes maybe a minute and /boot will never run out of space.

---

### Post by geeksmith on 2017-02-08
It looks to me like you could combine the sdi1 and sdi2 partitions to give yourself a little more headroom. This would require saving the contents of both partitions somewhere else, deleting both partitions, creating sdi1 using the space previously used by both partitions, formatting it, then moving your saved files back. Then you'd edit /etc/fstab to reflect these changes.

But in the end, I agree that simply cleaning up old kernels would be prudent, regardless of whatever else you decide to do.

---

### Post by ajgreeny on 2017-02-09
I will also have to bow out here as my knowledge of raid is zero, as is it for LVM and encryption.

However, the /boot partition is something you should definitely not mess with; any changes to it may mean you can not boot the machine at all.
Use the autoremove command whenever a new kernel appears and you will not see this problem again, so as suggested it is the quickest and safest way to proceed.

Playing around with partitions always carries a risk; doing so with a /boot partition probably has a greater risk than many other partition operations.

---

### Post by ian78 on 2017-02-10
> **ajgreeny said:**
> Use the autoremove command whenever a new kernel appears and you will not see this problem again, so as suggested it is the quickest and safest way to proceed.

Based on what i've read here i would have to agree that sticking with the current boot partition and managing the old kernels is the most sensible option, so a big thanks to everyone who ventured an opinion or offered advice.

My last question is with regard to the autoremove command suggested above. Is there any way to automatically trigger it to run when a new kernel is installed?

I was thinking maybe a cron job on boot-up since a new kernel is often the main reason for a reboot. Thats probably the way i will go unless there is a better way as i already have a cron job on bootup that sends a test notification email from the raid management software so adding another boot command should be fairly easy.

---

### Post by ajgreeny on 2017-02-11
I think that if you leave **unattended-upgrades** enabled the excess kernels are removed by the system automatically, but I am not totally sure about that as I have unattended-upgrades disabled; I prefer to have full control of timings and of what is being upgraded, so I still check manually after every boot.

---

### Post by howefield on 2017-02-11
> **ajgreeny said:**
> I think that if you leave **unattended-upgrades** enabled the excess kernels are removed by the system automatically...

I believe that you have to tell unattended-upgrades to remove unused dependencies, default is not to remove.

```
grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
```

---

### Post by ian-weisser on 2017-02-11
> **howefield said:**
> I believe that you have to tell unattended-upgrades to remove unused dependencies, default is not to remove.

```
grep Remove-Unused /etc/apt/apt.conf.d/50unattended-upgrades
//Unattended-Upgrade::Remove-Unused-Dependencies "false";
```

Correct in 14.04 and older. A new feature was added in 16.04 specifically to address the out-of-space-in-/boot reports by encryption users.
It's not a terribly clever feature, but seems effective for most users until 17.04 introduces the ability to boot from LVM partitions.

---

### Post by howefield on 2017-02-12
> **ian-weisser said:**
> Correct in 14.04 and older. A new feature was added in 16.04 specifically to address the out-of-space-in-/boot reports by encryption users.
It's not a terribly clever feature, but seems effective for most users until 17.04 introduces the ability to boot from LVM partitions.

Thanks for the clarification, ian-weisser.

---

### Post by ian78 on 2017-02-13
> **ian-weisser said:**
> ...until 17.04 introduces the ability to boot from LVM partitions.

Does this mean it will be possible to boot directly from the raid array? If so then i am liking that idea because as it stands the single unraided boot disk is a weakpoint in the server design.

Will there be any migration option from my current non-LVM partition to an LVM boot partition?

---

### Post by ian-weisser on 2017-02-14
You can already boot from a RAID array, which is different from an LVM partition...though there is much overlap in what the two provide.

I have seen no plan for a 'migration option'. A normal Ubuntu release-upgrade is simply a new set of sources and packages, not a repartitioning. Enough people haywire their systems enough ways that I wouldn't want to build an automated re-partition script either. If any community member wants to take a swing at such a script, do feel free.

---

