---
title: "kernel pan Target filesystem doesn't have requested /sbin/init even after Boot Repair"
date: 2024-10-08
forum: Installation &amp; Upgrades
---

### Post by robbiethek on 2024-10-08
Here is a link to the [Pastebin]("https://paste.ubuntu.com/p/5VzdWszzFQ/") showing the repair log. Here are the drive configs:

[[IMG]https://i.postimg.cc/DS18qt63/Image-20241003-120300-798.jpg[/IMG]]("https://postimg.cc/DS18qt63")


[[IMG]https://i.postimg.cc/cKZ6TXkg/Image-20241003-120641-002.jpg[/IMG]]("https://postimg.cc/cKZ6TXkg")


[[IMG]https://i.postimg.cc/KKNjWBC9/Image-20241003-120702-950.jpg[/IMG]]("https://postimg.cc/KKNjWBC9")

Here's the last error: [IMG]https://postimg.cc/7f0xcS2g[/IMG]


[FONT=courier new]can't execute lisbin/init': No such file or directory 
Target filesystem doesn't have requested /shin/init. 
run-init: can't execute lisbin/inits: No such file or directory 
run-init: can't execute lietc/init': Permission denied 
Kernel panic - not syncing: Attempted to kill initl exitcode=0x00000100 
CPU: 0 PID: 1 Comm: run-init Not tainted 5.15.0-72-generic479-Ubuntu [/FONT]

---

### Post by yancek on 2024-10-08
Which of the drives shown in your images is the problem drive?  Your images shows 4 drives?
Were you ever able to boot Ubuntu?  Were there any changes made just prior to the problem and if so, what?
Boot repair is not going to do anything to repair the missing file referred to, it changes/modifies or repairs boot files, Grub specifically
Some details on how this problems came about would probably help someone to help you. .

Your second image shows attempt to run fsck on drives, you need to make sure the partition is NOT mounted and then run it on the filesystem of the partition, sda1, sdb2, etcx.  I don't believe it will work on just a drive such as sda unless you have no partition on it.

---

### Post by robbiethek on 2024-10-09
> **yancek said:**
> Which of the drives shown in your images is the problem drive?  Your images shows 4 drives?


It's in the pastebin, /dev/nvme0n1p4:

> **yancek said:**
> Were you ever able to boot Ubuntu?

No both kernels and all grub options failed with the same kernel panic.
 
> **yancek said:**
> 
 Were there any changes made just prior to the problem and if so, what?


No was running Cryosparc, rebooted and this happened.

> **yancek said:**
> Boot repair is not going to do anything to repair the missing file referred to, it changes/modifies or repairs boot files, Grub specifically

OK any suggestions on how to fix the partition? I believe that's where initd is supposed to be.


> **yancek said:**
> Your second image shows attempt to run fsck on drives, you need to make sure the partition is NOT mounted and then run it on the filesystem of the partition, sda1, sdb2, etcx.  I don't believe it will work on just a drive such as sda unless you have no partition on it.

Thanks I unmounted and tried, to no avail. No problems found. Any other suggestions?

Edit: would you recommend any of solutions suggested in [this other AU thread]("https://askubuntu.com/questions/92946/cannot-boot-because-kernel-panic-not-syncing-attempted-to-kill-init")? such as below:

Booted from live usb and run these commands


[FONT=courier new]sudo mount /dev/sda1 /mnt[/FONT]
[FONT=courier new]sudo mv /mnt/usr/lib/x86_64-linux-gnu /mnt/usr/lib/x86_64-linux-gnu-copy[/FONT]
[FONT=courier new]sudo mkdir /mnt/usr/lib/x86_64-linux-gnu[/FONT]
[FONT=courier new]sudo cp -r /usr/lib/x86_64-linux-gnu/* /mnt/usr/lib/x86_64-linux-gnu

[FONT=arial]Would I need to use the same version of Ubuntu Live USB that is on the system?[/FONT]
[/FONT]

---

### Post by yancek on 2024-10-09
I'm not sure why you ran the commands you posted on sda.  If you look at line 44 you will see:  sfdisk: /dev/sda: does not contain a recognized partition table

Your Ubuntu is installed on nvme0n1p4.  There are no  grub files showing there but they do show on nvme0n1p2 so it would seem this is a separate /boot partition and  nvme0n1p4 is the / filesystem partition.

If you look at line 352 you will see that the grub.cfg file on the EFI partition is pointing to nvme0n1p4 which does not have any grub files showing but they do show on nvme0n1p2 so that line in the grub.cfg file in the EFI partition should probably be changed to point to  nvme0n1p2.

I don't know what Cryosparc is or what it is supposed to do.  Was your Ubuntu running well before this problem?  It appears to be an EFI install but the errors shown on line 108 EFI variables are not supported on this system as well as the error on line 110  Warning: NVram is locked (Ubuntu not found in efibootmgr) need to be corrected.  The nvram locked has a number of threads here at the forums but there is no single solution to it.  I'm not sure why you get the other error about EFI variables not supported if you had an EFI install and  it worked.

I don't use RAID or a separate boot partition so investigating the errors above is all I can suggest.

---

### Post by robbiethek on 2024-10-09
> **yancek said:**
> If you look at line 352 you will see that the grub.cfg file on the EFI partition is pointing to nvme0n1p4 which does not have any grub files showing but they do show on nvme0n1p2 so that line in the grub.cfg file in the EFI partition should probably be changed to point to  nvme0n1p2.

Would that be done in the Boot Repair GUI? Can you provide some instructions?

> **yancek said:**
> Was your Ubuntu running well before this problem?
Yes

> **yancek said:**
> 
 It appears to be an EFI install but the errors shown on line 108 EFI variables are not supported on this system as well as the error on line 110  Warning: NVram is locked (Ubuntu not found in efibootmgr) need to be corrected.  The nvram locked has a number of threads here at the forums but there is no single solution to it.  I'm not sure why you get the other error about EFI variables not supported if you had an EFI install and  it worked.

Which nvram locked solutions should I start with?

I also tried the secure boot option checked and I believe I found a bug:
[COLOR=#000000][FONT=Menlo]Traceback (most recent call last):[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "/usr/bin/glade2script-python3", line 2319, in set_widget[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    exec( arg )[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]  File "<string>", line 1[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]    self._label9.set_text('''sudo chroot "/mnt/boot-sav/nvme0n1p4" dpkg --configure -a\nsudo chroot "/mnt/boot-sav/nvme0n1p4" apt-get install -fy\nsudo chroot "/mnt/boot-sav/nvme0n1p4" apt-get install -y mdadm\nsudo chroot "/mnt/boot-sav/nvme0n1p4" mdadm --assemble --scan\nsudo chroot "/mnt/boot-sav/nvme0n1p4" apt-get install -y dmraid\nsudo chroot "/mnt/boot-sav/nvme0n1p4" dmraid -ay\nsudo chroot "/mnt/boot-sav/nvme0n1p4" apt-get install -y grub-efi-amd64-signed shim-signed linux-headers-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]                          ^[/FONT][/COLOR]
[COLOR=#000000][FONT=Menlo]SyntaxError: unterminated triple-quoted string literal (detected at line 1)

[FONT=arial]Also is there a tutorial to reinstall in place on the same version of Ubuntu? I was thinking of forcing an upgrade to the Live USB version oof 24 but from what I'm [reading]("https://ubuntuforums.org/showthread.php?t=2497447") that is not recommended.

 Edit: I see [this tutorial]("https://operavps.com/docs/reinstall-ubuntu/") that mentions reinstalling in place.[/FONT][/FONT][/COLOR]

---

### Post by robbiethek on 2024-10-10
Here are the options I chose in Boot Repair:

[[IMG]https://i.postimg.cc/R6dPqZDx/20241008-163203.jpg[/IMG]]("https://postimg.cc/R6dPqZDx")


[[IMG]https://i.postimg.cc/5Yb7xCpm/20241010-101150.jpg[/IMG]]("https://postimg.cc/5Yb7xCpm")


[[IMG]https://i.postimg.cc/qtfD5Y3S/20241010-101441.jpg[/IMG]]("https://postimg.cc/qtfD5Y3S")


[[IMG]https://i.postimg.cc/3ygf5BjR/20241010-101506.jpg[/IMG]]("https://postimg.cc/3ygf5BjR")

Edit: I saw a [FONT=courier new]/boot not found[/FONT] message scroll by when trying to go into UEFI settings.

---

### Post by yancek on 2024-10-10
> If you look at line 352 you will see that the grub.cfg file on the EFI  partition is pointing to nvme0n1p4 which does not have any grub files  showing but they do show on nvme0n1p2  

The comment above is from my earlier post and is not correct, my mistake as the grub.cfg file on the EFI partition is pointing to the boot partition, nvme0n1p2 so ignore that.

What is Cryosparc and what were you doing  with it?  Anything relating to booting or boot files?

If this is a fairly new install, it might be simpler to just reinstall.  Back up any personal data first.  If you are using RAID and want a separate boot partition just do the install using partition 1 as EFI, partition 2 as boot, partition 3 as swap and partition for as the / (root) filesystem partition.  The requirement is you do this is that you select NOT to format the partitions.  You don't really need a swap partition as Ubuntu creates a swap file but it would be simpler to keep the same partitions.  I did this with another Linux system and it repaired the entire system which had been unbootable and also retained personal files/data.  If you have made changes to system configuration files, they won't be saved. 

The link you posted for reinstalling Ubuntu should work and appears to be the same as my description above.  I haven't seen that option in the installs I have done but I haven't done a new install since 20.04. You should be able to use the Something Else option to do it but it may be simpler for you to use the Reinstall option if you don't have much experience.

---

### Post by robbiethek on 2024-10-17
Well this was a nightmare. Ubuntu 22 kept crashing during a reinstall. Even with a format. See attached crash log.

I tried Ubuntu 24 and formatted the 4 partitions. I also had to set the kernel parameter (pressing 'e' during boot when the grub menu appears) and adding acpi=off as suggested [by this user.]("https://askubuntu.com/a/1440765") Then it installed.

---

