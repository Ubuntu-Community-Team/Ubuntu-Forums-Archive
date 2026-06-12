---
title: "I can't boot!"
date: 2022-08-08
forum: Installation &amp; Upgrades
---

### Post by alkerjt on 2022-08-08
Hi there,
 
After a power failure, I cannot get Ubuntu server 18 to boot. 

The boot went to initramfs and i got an error "/dev/mapper/ubuntu--vg-ubuntu-lv does not exist"

I tried boot repair ([https://pastebin.ubuntu.com/p/tZnD5nJYQd/](https://pastebin.ubuntu.com/p/tZnD5nJYQd/)). The output is pasted below.

I am a rookie, any tips appreciated.

Cheers

<pasted output removed>

---

### Post by QIII on 2022-08-08
There is no need to duplicate the output of boot repair in a post here.  That is the point of the paste bin.

---

### Post by oldfred on 2022-08-08
You have Ubuntu installed in the old BIOS boot mode on newer gpt partitioned drive. You also have NTFS partitions, but no bootable Windows.
Best to only have NTFS if using Windows as you cannot run chkdsk from Linux.

But booted live installer in UEFI boot mode. Since install is BIOS, better to reboot in BIOS mode & run Boot-Repair from BIOS boot.
How you boot USB flash drive UEFI or BIOS is then how it installs or repairs a system. You just need to always be consistent.
(But with newer systems, usually better to use UEFI.)

After hard shutdown, you may need fsck on ext4 partition(s)s and chkdsk (from Windows) on NTFS partitions.

Do not know LVM, but you often need to manually mount LVM to run fsck on the ext4 in the volume(s). 
And if encrypted, you have to decrypt it first.

If manually mounting & then run fsck or e2fsck.
Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

---

