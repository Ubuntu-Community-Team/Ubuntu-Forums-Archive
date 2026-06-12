---
title: "Not boot from the second hd"
date: 2013-08-18
forum: Installation &amp; Upgrades
---

### Post by SteMMo on 2013-08-18
Hi all,
on my PC i have two physical HDs: 160 + 40 GB.
On the first hd i have ubuntu and it is running without problems (i'm using it..).
I installed a Debian distro on the second hd but i'm not able to boot with it.
With different grub configurations i received Error 21 (selecte4d disk does not exist) or Error 15 (File not found).
If i type fdisk -l I see two disks (sda and sdb).
The BIOS shows only one disk (i guess the first disk).

How can i boot on the second disk?

Thanks!

---

### Post by oldfred on 2013-08-18
Generally if BIOS does not see a drive, then no system can see the drive. Some systems have drives in CD slots as an option and those are often not bootable. 

The errors you are getting are from grub legacy which Ubuntu has not used as default since 9.04. New grub2 on error usually just gives a grub> or grub rescue>.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by SteMMo on 2013-08-18
Hi, i changed the BIOS settings and finally the second hd is in the list.
Now when i select the following:

title		Debian 7.1.0, kernel 3.2.0-4-686
uuid		67a2737d-5f71-4d98-9d23-4fbfae73af48
kernel	/boot/vmlinuz-3.2.0-4-686-pae root=UUID=67a2737d-5f71-4d98-9d23-4fbfae73af48 ro quiet
initrd		/boot/initrd.img-3.2.0-4-686-pae

i see the output:
boot from (hd1,0) ext4  67A2........
Error 15: File not found

Can i refer to the kernel or initrd file simply by /boot/... notation?

---

### Post by oldfred on 2013-08-18
Grub legacy with Ubuntu 9.04 or last version using grub legacy was updated by Ubuntu in its version to work with ext4. Error 15 is still from grub legacy and is usually the incompatibility of grub legacy and grub2.

Best to post link to BootInfo report so we can see details.

---

