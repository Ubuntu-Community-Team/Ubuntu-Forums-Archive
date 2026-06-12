---
title: "grub installation problem"
date: 2016-07-01
forum: Installation &amp; Upgrades
---

### Post by nanenaro on 2016-07-01
Hello.

I have Windows 10 in my new Acer E5-573G and I need to install Ubuntu in dual boot. I created USB stick using Rufus utility with mode "GPD for UEFI machines".
Installation started sucessfully, but when in came to installing grub2 this message appeared: Executing 'grub-install /dev/sda' failed. This is a fatal error

After that failure I tried to install Ubuntu on an external hard drive. I  selected it for grub, created ext4 "/" partition and swap partition on that hard drive and again started the installation. But the error was the same - installer was unable to install grub2 onto that hard drive too. 

After that I tried to enable\disable secure boot option in my UEFI, but nothing changed. I also marked \EFI\BOOT\grubx64.efi on the stick as "trusted" UEFI file, but this also did not solve the problem. Now the error message looks like "The grub-efi-amd64-signed package failed to install into /target/."

Then I booted again from USB stick and started "boot-repair" utility with selected option "recommended repair". The output was:
> An error occurred during the repair.
Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair].

But I already have suitable FAT32 partition, it is dev\sda2. Do I really need to create another one? 

Here is the output of BootRepair (partially) : [http://pastebin.com/XUQdbTWR](http://pastebin.com/XUQdbTWR) (sda is builtin hard drive, sdb is the external hard drive(samsung) and sdc is the usb stick(kingmax))

I will appreciate any help!

---

### Post by oldfred on 2016-07-01
With Acer it is after install that you have to set the files in the ESP as trusted.

Your issue seems to be that it will not add those files to the ESP on sda.

Usual issue is some sort of corruption on ESP. Often then chkdsk from Windows for fsck/dosfsck from Linux repairs it. Note -a option to clear dirty bit.
Some have had to fully back up ESP (which you should have already done anyway) and delete partition, recreate as FAT32 with boot flag with gparted and restore current Window boot files.

       sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sda2
man dosfsck 
OR:

 dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by nanenaro on 2016-07-02
Thanks.
I made fsck.vfat -t -a /dev/sda2  + BootRepair + install Ubuntu. This new installation was successful, no grub errors. BootRepair aslo reported success, no [COLOR=#000000]*Locked-ESP errors*[/COLOR].
But Ubuntu doesn't boot. I turn on the computer and Windows starts.

shimx64.efi is added as trusted: Select an UEFI file as trusted for executing ->HDD0 -><EFI> -><ubuntu> ->shimx64.efi

---

### Post by ubfan1 on 2016-07-02
Is the ubuntu shim entry first in the boot order?  Can you boot to Ubuntu through the EFI menu (some function key at power-up)?  If so, run efibootmgr -v to see the order, and then change it with the -o xxxx,yyyy,...etc. switch on efibootmgr.

---

### Post by nanenaro on 2016-07-02
> **ubfan1 said:**
> Is the ubuntu shim entry first in the boot order?  Can you boot to Ubuntu through the EFI menu (some function key at power-up)?  If so, run efibootmgr -v to see the order, and then change it with the -o xxxx,yyyy,...etc. switch on efibootmgr.
shim entry doesn't exist in the boot list at all (despite the fact that I added it).


But after that I added HDD0 -><EFI> -><ubuntu> ->grubx64.efi and it worked! This entry (grub.efi, I mean) appeared in the boot list, I tuned it's position and voila - ubuntu works!


thank you very much, oldfred, for mentioning fsck.vfat! It solved the problem.

---

