---
title: "something killed my ubuntu efi files"
date: 2015-02-10
forum: Installation &amp; Upgrades
---

### Post by Konrad_Brunner on 2015-02-10
Installed two days ago ubuntu 14.04.1 dual boot beside win 8.1 on a new notebook. All was running well:
- uefi boot
- secure boot
- grub was working well allowing me to choose
- was able to start to ubuntu
- was able to start to windows

Yesterday I installed OEM updates including a bios update. After that these updates grub is gone. No menu option any more. only boot to windows works. With boot options I'm able to boot /EFI/ubuntu/shim64.efi may anyway windows starts. I also tried to move the EFI ubuntu entry on the first place in BIOS. No way. I've started with LiveCD, mounted the partition with the EFI staff on it and tried to copy the entire file system to a different disk as reference and backup. Copy worked for all files except:
- /EFI/ubuntu/shimx64.efi
- /EFI/ubuntu/grubx64.efi

Both files can't be copied, or better to say only 4K of them. Then the copy process ends with a error message (don't remember, sorry).
So for me it looks like that something has corrupted my two ubuntu efi files!

Does someone has an idea, how to fix those?

---

### Post by oldfred on 2015-02-10
From Boot-Repair try the full uninstall/reinstall.

I thought UEFI updates saved most settings as it has its own NVRAM. Back with BIOS updates, it reset everything to defaults and you had to totally reset it. I took pictures just to document my changes.

What brand/model computer?
Many vendors are modifying UEFI to only boot Windows entry by text description.

If still issues post link to Summary report:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Konrad_Brunner on 2015-02-10
Boot-repair states sucess. Still only booting Windows. No grub.
[http://paste.ubuntu.com/10164416/](http://paste.ubuntu.com/10164416/)

---

### Post by oldfred on 2015-02-10
HP's were one of the first to modify UEFI to only Boot Windows using the description. That is not per UEFI standard.

But we have many work arounds. Most common with dual booting is to copy grub or shim to the /EFI/Boot folder and rename it to bootx64.efi. That is a hard drive boot entry that still works.

       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

General instructions, yours is sda2 and you already have the /EFI/Boot folder with bootx64.efi. Best to fully back up all of efi partition first. And Windows should be fully backed up.

 From live installer mount the efi partition on hard drive, lines with # are comments only:
#Mount efi partition. check which partition is FAT32 with boot flag. Often sda1 or sda2 but varies.
sudo mount /dev/sda1 /mnt
#only if not already existing, 
sudo mkdir /mnt/EFI/Boot
sudo cp /mnt/EFI/ubuntu/* /mnt/EFI/Boot
# If new folder created, the bootx64.efi will not exist, skip this command
sudo mv /mnt/EFI/Boot/bootx64.efi /mnt/EFI/Boot/bootx64.efi.backup
# make grub be hard drive boot entry in UEFI. If not existing, may have to update UEFI also with efibootmgr.
sudo mv /mnt/EFI/Boot/grubx64.efi /mnt/EFI/Boot/bootx64.efi 

[URL="http://ubuntuforums.org/showthread.php?t=2234019"]
[/URL]

---

### Post by Konrad_Brunner on 2015-02-11
As already stated in mz first post, the efi files from ubuntu are corrupt. Not able to copy them anywhere!

root@ubuntu:~# mount /dev/sda2 /mnt
root@ubuntu:~# ls /mnt
boot  boot-sav  EFI
root@ubuntu:~# cp /mnt/EFI/ubuntu/shimx64.efi /tmp
cp: error reading ‘/mnt/EFI/ubuntu/shimx64.efi’: Input/output error
cp: failed to extend ‘/tmp/shimx64.efi’: Input/output error

---

### Post by oldfred on 2015-02-11
Have you run the full un-install/reinstall of grub? 
And are you un-encrypting your encrypted partition while using live installer?

If shim & grub are corrupted which is very unusual, then they need to be rebuilt. Easiest way is a full reinstall of grub.

Have you tried booting with Supergrub, to get into system. That often makes it easier to repair than using live installer.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by ubfan1 on 2015-02-11
Looks like your input/output error is related to bug 1090829.  Repeated runs of 
sudo dosfsck -r /dev/sda2
Removing things as offered, then the entire /EFI/ubuntu directory may be removed and
grub reinstalled (successfully).

---

### Post by Konrad_Brunner on 2015-02-11
Solved with the following procedure:

booted to livecd with secure boot on and working as root
***dosfsck -w -r -l -a -v -t /dev/sda2***
-> sized corrupt files to 0 bytes and fixed some bad blocks
opened the encrypted logical volume lvg1
[B]mount /dev/mapper/lvg1-lv1 /mnt
mount /dev/sda6 /mnt/boot
mount /dev/sda2 /mnt/boot/efi
for i in dev dev/pts proc sys sys/firmware; do mount --bind /$i /mnt/$i; done
chroot /mnt
update-grub
grub-install --uefi-secure-boot[/B]

And my dual secure boot went back into normal state!

Many thanks to all who helped.

---

