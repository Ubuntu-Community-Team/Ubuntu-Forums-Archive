---
title: "Raid0"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by eportuguesas on 2013-01-05
Hi...

Hi have a pc with Win 8 Pro and 2 HDD with RAID0 and it seems like Ubuntu 12.04 and 12.10 dont recognize that...

Any soluction?

---

### Post by darkod on 2013-01-05
For fakeraid install you had to use the Alternate Install CD earlier, not the standard desktop live cd. For 12.04 there is an alternate image to create the cd, but for 12.10 there is no such image.

To make things even more complicated, most new win8 machines come preinstalled with Secure Boot and UEFI. If you use Secure Boot, only 12.10 64bit is compatible.

The live cd should still include the dmraid package that handles fakeraid so you might be able to install but it usually fails to install grub2. So you might need to chroot into the installation later and install grub.

UEFI dual boot with Secure Boot is complicated enough even without your raid0, so I think you have a lot to learn about the way new uefi systems work.
This might be a good starting point, but this is for standard install, not raid:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Make sure to be careful and boot the 12.10 cd/usb in uefi mode as specified there. Only in that case it will try to install in uefi mode.

You might need to go into Try Ubuntu first to activate the raid array. You can do that in terminal with:
sudo dmraid -ay

After that you should see some devices like /dev/mapper/.... You can check that with:
sudo parted -l (small L)

That's your raid array.

---

### Post by ronparent on 2013-01-05
Just to add to darkrod's comments. Ubuntu 12.10 would not install for me from the live cd. I had to install it on a usb memory key and copy that install to the RAID0. And there although simple gets complicated to the new user. The dmraid should be installed to the usb key prior to the copying, and, if, a simple copy command is used to transfer it, the /etc fstab file has to be edited to enter the uuid of the raid target partition it was copied to as well a a swap on that array. Once you update-grub on booted to the key you will have an option in the key installed grub to boot into the target. Once booted into the target you need to grub-install to create the grub on the target. The boot sector must be placed on /dev/dm-0 for it to boot. That said, good luck!

---

### Post by darkod on 2013-01-05
> **ronparent said:**
> Just to add to darkrod's comments. Ubuntu 12.10 would not install for me from the live cd. I had to install it on a usb memory key and copy that install to the RAID0. And there although simple gets complicated to the new user. The dmraid should be installed to the usb key prior to the copying, and, if, a simple copy command is used to transfer it, the /etc fstab file has to be edited to enter the uuid of the raid target partition it was copied to as well a a swap on that array. Once you update-grub on booted to the key you will have an option in the key installed grub to boot into the target. Once booted into the target you need to grub-install to create the grub on the target. The boot sector must be placed on /dev/md0 for it to boot. That said, good luck!

Are you sure you are not talking about software raid instead of fakeraid?

The /dev/mdX devices are part of software raid and controlled by mdadm.
The fakeraid devices have names like /dev/mapper/... and are controlled by the dmraid package.

mdadm is not included on the live cd so for any installation or managment of software raid you need to add the package first in the live session. It is included on the alternate cd which is why it should be used for raid or LVM installations.

dmraid is included on the live cd so you should be able to install on fakeraid without bigger problems except that it won't install grub2 correctly, so you have to add it manually later. But it should be able to see and manipulate fakeraid array.

---

### Post by ronparent on 2013-01-05
Darko - I am definitely talking about fakeRAID. The dm- devices are also setup on loading along with the /dev/mapper devices. The numbering sometime varies but /dev/dm-0 is always the RAID root. When I am able to confirm the order in which the devices loaded in the udev log I often like to use those references in preference to the corresponding /dev/mapper references. 

The problem is not with dmraid. The installation used to fail with the failure of grub to properly install, but that was fixable. With 12.10 something else is left uninitiated and the install is left in a state where it will only boot to the initramfs prompt. Rather than try to untangle the problem with the install script that the developer left us with I found it easier to just copy the contents of the usb key partition to the raid target partition (after installing dmraid to it). You can tell from the 12.10 notes that the developer knew that 12.10 would not install to a raid but left it at that!

Fortunately the distro is otherwise pretty robust and it doesn't absolutely require that the initramfs be compiled to the raid to make a completed install image. I doubt that a complete noob will be able to work this out however without a lot of detailed guidance.

Note: A bit of dyslexia - I actually meant dm- devices not md- devices. Big difference!

---

### Post by eportuguesas on 2013-01-05
Thanks to all for the replies ... I will try but is too difficult for a noob... :S

The ubuntu should suport this... I think :)

---

### Post by darkod on 2013-01-05
Unfortunately the new UEFI boot process and win8 with Secure Boot make it very difficult to dual boot. It's a new way to make people use only windows. On some machines it's almost impossible to create the dual boot.

I think you should go step by step. And get more data about your machine first.

1. Go into BIOS and check if there is option like Secure Boot and whether it's enabled. That is important.

2. Boot the ubuntu cd in live mode (12.04 or 12.10), open terminal and try to activate the raid and check if it's recognized correctly:
```
sudo dmraid -ay
sudo parted -l (small L)
```

The first command will try to activate the raid and the second will print the list of all disk devices and partitions. Post the output here so we can have a look if the raid is detected.

---

### Post by eportuguesas on 2013-01-07
> **darkod said:**
> Unfortunately the new UEFI boot process and win8 with Secure Boot make it very difficult to dual boot. It's a new way to make people use only windows. On some machines it's almost impossible to create the dual boot.

I think you should go step by step. And get more data about your machine first.

1. Go into BIOS and check if there is option like Secure Boot and whether it's enabled. That is important.

2. Boot the ubuntu cd in live mode (12.04 or 12.10), open terminal and try to activate the raid and check if it's recognized correctly:
```
sudo dmraid -ay
sudo parted -l (small L)
```

The first command will try to activate the raid and the second will print the list of all disk devices and partitions. Post the output here so we can have a look if the raid is detected.

Seems more simple... I will check that :)

---

