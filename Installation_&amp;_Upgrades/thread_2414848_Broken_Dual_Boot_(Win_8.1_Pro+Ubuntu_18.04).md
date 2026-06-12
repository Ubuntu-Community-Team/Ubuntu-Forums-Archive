---
title: "Broken Dual Boot (Win 8.1 Pro+Ubuntu 18.04)"
date: 2019-03-16
forum: Installation &amp; Upgrades
---

### Post by daniell2 on 2019-03-16
I've been running Win 8.1 Pro with Debian 9 in a dual boot configuration for some time. Recently changed Debian 9 to Ubuntu 18.04 and I was still able to dual boot with no issues. After a week or so the dual boot broke, perhaps due to some update. I am not aware what happened. Upon startup I received a "System Bootorder not found. Initializing defaults." error. 
It was very important I be able to access my Windows partition for work, so I removed my drive with encrypted Ubuntu 18.04, deleted all boot entries from my Windows partition and recreated just a Windows boot record using Windows repair disk.
I'm trying to get the dual boot up and running again. I started by just trying to get my disk with Ubuntu to boot. It seems there is some issue with the way grub is configured on that drive, and it boots straight to grub rescue. "error: file `/boot/grub/x86_64-efi/normal.mod' not found." Which isn't surprising but I thought it was worth seeing if I could boot to it that way.

I tried to repair everything using boot-repair, but it had no effect. Here is my pastebin output:

[http://paste.ubuntu.com/p/nqPmDyJjCn/](http://paste.ubuntu.com/p/nqPmDyJjCn/)

I don't understand the setup well enough to repair it myself. It would be nice if I could regain access to my Ubuntu install without having to start over again. The drive is encrypted, so I'm not sure how to access the files.

I appreciate your feedback.

---

### Post by oldfred on 2019-03-16
There used to be major issues with filling the UEFI memory with boot entries. Some systems when half full totally locked up and could only be reset by vendor. Originally blamed on Linux, but shown to also happen with Windows.

So you first need to houseclean all the duplicate UEFI entries.
See also:
man efibootmgr 

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B 

For Boot-Repair to update grub (or chroot to update grub) you have to mount & decrypt your install.
Then try Boot-Repair again.

All your UEFI boot entries are using the same GUID as Windows or expect the /EFI/ubuntu to be in ESP on sda2.
But you have an old Debian boot entry on ESP on sdb, but no Ubuntu entries on either ESP. Ubuntu's grub normally default installs to first ESP.

---

### Post by daniell2 on 2019-03-16
> **oldfred said:**
> There used to be major issues with filling the UEFI memory with boot entries. Some systems when half full totally locked up and could only be reset by vendor. Originally blamed on Linux, but shown to also happen with Windows.

So you first need to houseclean all the duplicate UEFI entries.
See also:
man efibootmgr 

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B 

For Boot-Repair to update grub (or chroot to update grub) you have to mount & decrypt your install.
Then try Boot-Repair again.

All your UEFI boot entries are using the same GUID as Windows or expect the /EFI/ubuntu to be in ESP on sda2.
But you have an old Debian boot entry on ESP on sdb, but no Ubuntu entries on either ESP. Ubuntu's grub normally default installs to first ESP.

Thank you for your response. I will try to implement your suggestions.

---

### Post by daniell2 on 2019-03-17
I've followed your instructions and removed duplicate entries.

```
                         ubuntu@ubuntu:~$ sudo efibootmgr -v
 BootCurrent: 0003
 Timeout: 0 seconds
 BootOrder: 0001,0002,0004,0003,2001,2002,2003
 Boot0001* Windows Boot Manager    HD(2,GPT,eac81798-a589-4662-bbaa-48ec8e3b4153,0x96800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
 Boot0002* Command Linpus lite    HD(1,GPT,fdb6f304-21b2-4130-8b79-af242fcd9c57,0x800,0x100000)/File(\EFI\Boot\bootx64.efi)RC
 Boot0003* Linpus lite    HD(1,MBR,0x31c7b6,0x800,0xe6858c)/File(\EFI\Boot\grubx64.efi)RC
 Boot0004* Command Linpus lite    HD(1,MBR,0x31c7b6,0x800,0xe6858c)/File(\EFI\Boot\bootx64.efi)RC
 Boot0007* ubuntu    HD(2,GPT,eac81798-a589-4662-bbaa-48ec8e3b4153,0x96800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
 Boot2001* EFI USB Device    RC
 Boot2002* EFI DVD/CDROM    RC
 Boot2003* EFI Network    RC
  
```

I mounted and decrypted my encrypted drive using the following commands:

```

udisksctl unlock -b /dev/sdb5
udisksctl mount -b /dev/mapper/ubuntu--vg-root
```

Then ran Boot-repair again. Boot-repair exited with an error. 

Pastebin output:

[https://paste.ubuntu.com/p/vdcSnGtyGS/](https://paste.ubuntu.com/p/vdcSnGtyGS/)

I then rebooted and my laptop booted straight to Windows as expected.

Under Windows I ran cmd.exe as administrator and executed the following command:

```

bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
  
```

This enables me to reboot into the GRUB2 menu. Now if I select 'Ubuntu' I see the following error:

```
Gave up waiting for root file system device. Common problems:...
...ALERT! /dev/mapper/ubuntu--vg-root does not exist. Dropping to a shell
```

If I press 'e' from the GRUB2 boot menu I can see 'set root='hd1_gpt2'. Perhaps that is relevant.

---

### Post by oldfred on 2019-03-17
Do not know why you get many of these from old UEFI entries.
Skipping unreadable variable "Boot0008": Input/output error

We have seen a lot of the /dev/mapper/ubuntu--vg-root error.

I do not know LVM, nor use encryption, but thought grub has add in commands insmod and needed a decrypt insmod since, your /boot is inside the LVM.
Old LVM installs used a /boot outside the LVM.

Other threads mention using different kernel but most of those are old threads.
or full chroot into LVM and update-initramfs like this.
[https://ubuntuforums.org/showthread.php?t=2264947](https://ubuntuforums.org/showthread.php?t=2264947)

[https://askubuntu.com/questions/567730/gave-up-waiting-for-root-device-ubuntu-vg-root-doesnt-exist](https://askubuntu.com/questions/567730/gave-up-waiting-for-root-device-ubuntu-vg-root-doesnt-exist)

perhaps this bug? has some steps to try to know issue, posts by TJ.
[https://bugs.launchpad.net/cryptsetup/+bug/1767527](https://bugs.launchpad.net/cryptsetup/+bug/1767527)

[https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
[https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)
refreshgrub script for use once chrooted into full drive encryption.
[https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b](https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b)

---

### Post by daniell2 on 2019-03-18
> **oldfred said:**
> Do not know why you get many of these from old UEFI entries.
Skipping unreadable variable "Boot0008": Input/output error

We have seen a lot of the /dev/mapper/ubuntu--vg-root error.

I do not know LVM, nor use encryption, but thought grub has add in commands insmod and needed a decrypt insmod since, your /boot is inside the LVM.
Old LVM installs used a /boot outside the LVM.

Other threads mention using different kernel but most of those are old threads.
or full chroot into LVM and update-initramfs like this.
[https://ubuntuforums.org/showthread.php?t=2264947](https://ubuntuforums.org/showthread.php?t=2264947)

[https://askubuntu.com/questions/567730/gave-up-waiting-for-root-device-ubuntu-vg-root-doesnt-exist](https://askubuntu.com/questions/567730/gave-up-waiting-for-root-device-ubuntu-vg-root-doesnt-exist)

perhaps this bug? has some steps to try to know issue, posts by TJ.
[https://bugs.launchpad.net/cryptsetup/+bug/1767527](https://bugs.launchpad.net/cryptsetup/+bug/1767527)

[https://help.ubuntu.com/community/ManualFullSystemEncryption/](https://help.ubuntu.com/community/ManualFullSystemEncryption/)
[https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)
refreshgrub script for use once chrooted into full drive encryption.
[https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b](https://gist.github.com/lovromazgon/7d0a5b6ac8f7557059a8b97e8442720b)

I've decided to go ahead and backup all of my data from my encrypted install using the Ubuntu live cd. I've reinstalled Ubuntu for now without encryption and lvm so as to minimize issues in my dual boot configuration.

I appreciate all of your help and hope the contents of this thread will be useful to others with similar issues. Thanks.

---

