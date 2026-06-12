---
title: "BusyBox ALERT! device not found"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by wolfjuli on 2016-04-22
[SIZE=2]Hello Everyone,

**Intro**
i know, there are at least 1000 posts and questions and at least 12 bug reports at Ubuntu regarding nearly the same problem, but none of them are working (and to be honest are not 100% as my problem)

[B]Problem
[/B]I freshly installed ubuntu 16.04 via a live-usb stick. As expected, the usb starts smoothly. I run the setup as I always did (business as usual) and no problems happend. (Try to) Reboot to freshly installed ubuntu results in:

[/SIZE]```

Give up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - check rootdelay=(did the system wait long enought?)
  - check root=(did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=xxxx-xxx.... does not exist.[SIZE=2]
[/SIZE]
```
[SIZE=2]
first thing i checked was 

```

ls /dev

```

which resulted in no folder "/dev/disk" and no "/dev/sd*" at all.
[SIZE=2]```

cat /proc/modules

```
[/SIZE]
is empty

Nevertheless, i tried things like uncommenting
```

[FONT=Courier 10 Pitch]#GRUB_DISABLE_LINUX_UUID=&#8221;true&#8221;
[/FONT]
```[FONT=Courier 10 Pitch]
(and update-grub of course)

which resulted to 

[/FONT][/SIZE]```

Give up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - check rootdelay=(did the system wait long enought?)
  - check root=(did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda1 does not exist.[SIZE=2]
[/SIZE]
```
[SIZE=2][FONT=Courier 10 Pitch]Which was nearly expected...

removing and adding boot params like noapic nolapic nomodset etc.etc. didn't change anything (or maybe i missed one permutation of them?)

also, try the solution
[/FONT][/SIZE]```

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
update-initramfs -u
update-grub

```
[SIZE=2][FONT=Courier 10 Pitch]didn't work out.

Waiting for longer time also didn't change anything (so increasing the time out)

**My Setup**
Notebook Nexoc
EFI disabled - normal BIOS boot

/dev/sda: Samsung EVO 850 SSD 250GB
/dev/sdb: (IMHO not important here): a "default" 1 TB HDD
NO raid, NO encryption

**Important notes**
[LIST]
[*]Before Installation of Ubuntu, I had Mint 17.3 (kernel version 3.19), which booted as a charm but was not only able to init my wifi without ugly hacks and ran a bit unstable with mz hardware - This is the reason for the desired kernel update but upgrade the kernel of this distro killed it. 
[*]Alongside, on /dev/sda2, i have windows 10 - (still) boots like a charm 
[*]As Ubuntu 16.04 (kernel 4.4) didn't work, i freshly installed Ubuntu 15.10 (kernel 4.2) - same problem here, the devices are not found by the kernel - although by grub and the live usb 
[*]When writing manually into the grub console to show all messages, there is only one line which says "ACPI probe failed" - I googled and it is said, this is no problem at all.. 
[/LIST]

I'm out of ideas what to do. Any help would be appreciated. Thanks
[/FONT]

**Edit:**
Funny thing: I tried to enable UEFI and reinstall again - the installer crashes. Sent a bug-report and somebody has the same issue ([https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1571230](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1571230)) 

As long as I'm not able to install this version of linux-Kernel (i don't care which distro), I'm not switching back to Linux. Interesting point in time where we got here: Linux is less reliable the windows. Since today it has been the other way round for me...
[/SIZE]

---

### Post by nelsongarcia-info on 2016-04-22
I tried with Ubuntu 16.04 LTS and Ubuntu mate 16.0.4 LTS, with same results:

Give up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  - check rootdelay=(did the system wait long enought?)
  - check root=(did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=xxxx-xxx.... does not exist.
shell!

BusyBox v1.22.1 (Ubuntu 1:1.22.0-15ubuntu1) build-in shell (ash)
Enter 'help' for a list of build-in commands.

---

