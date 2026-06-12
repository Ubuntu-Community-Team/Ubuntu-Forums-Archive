---
title: "Grub2 not working on Raid5"
date: 2013-05-05
forum: Installation &amp; Upgrades
---

### Post by litmux on 2013-05-05
Ever since Ubuntu started probably using Grub2, I cant intsall Ubuntu on my Desktop. If I run the Ubuntu 11.04 or 11.10 or 12.04 or 12.10 or 13.04 install CD(or usb) and click install after the config screens, I get the error   Executing 'grub-install /dev/sda' failed. This is a fatal error, and it says "Failed to install the bootloader". I have raid5, and I dont wanna stop using Raid. Im desprate its not working:roll:

---

### Post by oldfred on 2013-05-05
I do not really know RAID, but have an example of grub reinstall. You have to change to your device. Note that your mount VOLUME_0p1 but install grub to VOLUME_0.
Not sure if your RAID5 is different.

 if RAID
For RAID reinstall from live-CD/DVD/USB
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

RAID is not common on Desktops. So it was always in the server and alternative installer versions. But they now have eliminated the alternative version and are planning on adding the RAID install capability to the Desktop version, but have not yet.

---

### Post by darkod on 2013-05-05
1. If you are using fakeraid (bios raid) the standard live cd usually doesn't install grub2 successfully. You need to add it later yourself from live mode.

2. If you are using mdadm software raid, this can still happen if your disks have gpt table but you didn't make a small partition with no filesystem and with the bios_grub flag. Grub2 needs this to install on gpt disks.

From live mode, can you post the output of:
```
sudo parted -l
```

If you first need to activate/aasemble the array, do it so that the parted command shows the array too.

---

### Post by litmux on 2013-05-06
> **oldfred said:**
> 
RAID is not common on Desktops. So it was always in the server and alternative installer versions. But they now have eliminated the alternative version and are planning on adding the RAID install capability to the Desktop version, but have not yet.

No Unbuntu Desktop supported raid long time ago. Raid5 was working pretty well on Ubuntu 10.10. 

> **darkod said:**
> 1. If you are using fakeraid (bios raid) the  standard live cd usually doesn't install grub2 successfully. You need to  add it later yourself from live mode.

2. If you are using mdadm software raid, this can still happen if your  disks have gpt table but you didn't make a small partition with no  filesystem and with the bios_grub flag. Grub2 needs this to install on  gpt disks.

From live mode, can you post the output of:
```
sudo parted -l
```

If you first need to activate/aasemble the array, do it so that the parted command shows the array too.

Im not using fake raid. When should I use the "sudo parted -l". can you please guide me step by step, im not really good at this :icon_frown:

---

### Post by darkod on 2013-05-06
OK, if you are using mdadm software raid, use the ubuntu cd to boot into live mode, add the mdadm package (because it's not included), assemble the arrays and then run that command. So, open terminal and execute one by one:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
sudo parted -l
```

Note: When installing mdadm it might ask you to install postfix too (the mail transport agent). If a window shows up to configure postfix, simply select No Configuration. You won't use it anyway.

---

### Post by litmux on 2013-05-06
Sorry Fake raid im guessing :grin: nforce630i controller. fake raid right?... now what?

---

### Post by darkod on 2013-05-06
As oldfred posted you can use thos commands. But if you need the exact command to the letter, boot into live mode in terminal and post the output of:
```
sudo dmraid -ay
sudo parted -l
```

---

### Post by litmux on 2013-05-06
okay what am I doing wrong?

I installed ubuntu 13.04. while installing grub fatal error showed up so I pressed ok. Then it said fail to install bootloader, so I clicked countinue without bootloader. Then I booted from a usb, clicked try ubuntu, opened teminal:

> ubuntu@ubuntu:~$ sudo dmraid -ay
ERROR: ddf1: seeking device "/dev/dm-2" to 18446744073709421056
ERROR: hpt37x: seeking device "/dev/dm-2" to 4608
ERROR: hpt45x: seeking device "/dev/dm-2" to 18446744073709547008
ERROR: isw: seeking device "/dev/dm-2" to 18446744073708469760
ERROR: sil: seeking device "/dev/dm-2" to 18446744073709289984
RAID set "nvidia_fcabdedh" already active
RAID set "nvidia_fcabdedh1" already active
RAID set "nvidia_fcabdedh5" already active


> ubuntu@ubuntu:~$ sudo mount /dev/mapper/nvidia_fcabdedh /mnt
mount: /dev/mapper/nvidia_fcabdedh already mounted or /mnt busy


> ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/mapper/nvidia_fcabdedh
Path `/mnt/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.


everything seemed messed up!

---

### Post by litmux on 2013-05-07
okay so I mounted also nvidia_fcabdedh1 or nvidia_fcabdedh5 dont remember and then installed grub on nvidia_fcabdedh and it worked!
Grub worked, but it wont get into ubuntu it only shows the startup screen.

---

### Post by oldfred on 2013-05-07
Which of these is your install? or do you have a separate /boot as you have to also mount it.
Your mount command left off the 1 or 5, so then the install could not find the grub folder to use for the reinstall of grub.

Your RAID is a bit different than the example in post2, but logic should still be same. From post #2
Note that your mount VOLUME_0p1 but install grub to VOLUME_0.

Just as in standard installs you mount a partition, example was p1, yours would be nvidia_fcabdedh1    or ....h5 and install to the root or nvidia_fcabdedh.

---

### Post by darkod on 2013-05-07
Also, the fakeraid looks weird or maybe that's how ubuntu interprets the nvidia controller. On top of the /dev/mapper/... devices you have some /dev/dm-2 device which I don't think it's normal.

Also, since I notice you have only two partitions, 1 and 5, which is how usually ubuntu installs as sole OS. root is 1, swap is 5 (logical partition). So I assume you have only ubuntu.

If you are not using a dual boot, it's usually best to use mdadm software raid instead of fakeraid. Much more flexible, better, etc. You would only use fakeraid if you need to dual boot since windows won't work on linux software raid.

But it's too late to do that unless you wipe everything off and start over.

I would investigate whether that /dev/dm-2 is normal with nvidia fakeraid, I'm not sure, but I don't use fakeraid myself.

---

