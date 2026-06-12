---
title: "Unable to create bootable usb hdd with 16.04 server"
date: 2016-10-08
forum: Installation &amp; Upgrades
---

### Post by pcla56 on 2016-10-08
Hi Team, I have successfully created a usb stick with the iso on it and my PC detects the stick ok and boots into the install dialogs.

I plug in my (quite old) 120GB WD portable usb hdd and ask the partitioner to install the server on the entire disk with LVM (old IBM habits!).

I then ask it to NOT touch my exisiting MBR but to install the grub boot-loader onto the same usb hdd. It seems to complete successfully but so far I cannot get it to boot, even though the usb hdd appears on the boot options menu. It simply hangs with an underscore flashing cursor at the top of the screen.

One further bit of the puzzle is when I look at the new usb disk partitions none of them have a boot flag.

I'm not sure whether I am being stupid, not understanding the process enough, or have tripped over a bug!

Any help or suggestions welcome. My aim is to try and have a server installation I can use on multiple machines.

Thanks, Paul

---

### Post by Bucky Ball on 2016-10-08
Welcome. Can you boot to Ubuntu on the other drive or a Ubuntu live session from install media, launch Gparted (in the repos if not already installed), set a boot flag on the appropriate partition on the USB install drive, reboot and give that a try?

You may also try booting to the internal Ubuntu install, if you have one, and 

```
sudo update-grub
```

... in a terminal, reboot and see if it is picked up then.

It would help if we knew what you have on the internal drive and why LVM? Unless you need it for a specific reason, try and shake that habit unless you are completely au fait with it. It can cause headaches down the line and be rather inflexible. This is derived from observation of the support threads here, not personal experience ...

---

### Post by sudodus on 2016-10-08
Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Some computers can be tricky to boot into installed systems via USB, for example some HP computers, but there are work-arounds ...

Did you test if you can boot another computer from this USB boot HDD drive?

-o-

You can also try to start from a compressed image file with a portable installed mini system according to these links, and links from them

64-bit: [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

32-bit: [OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

---

### Post by yancek on 2016-10-08
> [COLOR=#000000]I then ask it to NOT touch my exisiting MBR but to install the grub boot-loader onto the same usb hdd. I[/COLOR]

You would have needed to use the manual (Something Else) option to do that and you would have had to select Device for bootloader installation as /dev/sdb, /dev/sdc depending upon how many drives you have attached.

I'm assuming since you haven't indicated, that you are installing some version of Ubuntu since you are posting here.  Which one?

Linux systems generally do not have to have a partition marked with a boot flag.

---

### Post by oldfred on 2016-10-09
If you know & understand LVM that is ok, it just is we get many brand new users that choose LVM and do not understand that standard partitions tools do not work & you have to use LVM tools. And extra commands are required to mount and use the LVM partitions to repair them.

Boot flag is not used by grub, but some BIOS do need to see a boot flag, so we usually suggest that you have one. WiIndows boot loaders, syslinux, lilo and new UEFI systems require a boot flag. But with UEFI it is not the same boot flag as  BIOS. UEFI boot flag using parted tools really is just used to assign the correct GUID, so UEFI knows it is the FAT32 partition with efi boot files.

---

