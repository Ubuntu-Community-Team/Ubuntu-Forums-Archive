---
title: "Can't boot on ubuntu installation on Surface pro 3"
date: 2014-10-25
forum: Installation &amp; Upgrades
---

### Post by dominik95-8 on 2014-10-25
Hi all,

after some trials and errors, I succeeded in installing  ubuntu 14.10 on my surface 3 (windows 8.1 up to date). I was having  trouble with grub errors that I get solved running few times "fsck -a  /dev/sda2" on the EFI partition.

Now that the installation process went to the end, I am trying to boot ubuntu without success.

1)  When booting the first time in windows -> option de recuperation  -> restart -> boot usb,... -> selecting the ubuntu tab : ubuntu  does not boot, windows fire up instead.
When trying another time to get to boot ubuntu, the ubuntu choice has disappeared, there is only "boot usb".

2)  I had run boot-repair a few times from the ubuntu live cd (adding the  ppa, updating, installing) while "Secure Boot" option off in the bios.

3) Trying to have another EFI partition is not an option because I can't shrink the windows partition below the 100GB limit.

Here are two boot repair log I got : [http://paste.ubuntu.com/8669720/](http://paste.ubuntu.com/8669720/) and [http://paste.ubuntu.com/8670551/](http://paste.ubuntu.com/8670551/) .

What was done on the windows side : 
- bitlocker and encryption are disabled
- hibernate is disabled

Am I missing something in order to get the multi-boot to work ? 
Can anyone points me to the right direction to solve my problem (without having to repartition the sdd as I want to keep windows ) ?

In case re-partitioning is mandatory, is there a way to partition the sdd the way I want and get windows installed after that ?
4) Tried bcdedit stuff from windows :
when running bcdedit without args, 
- the bootmgr is set to \EFI\ubuntu\grubx64.efi (or shimx64.efi tried both)
- the current is set to \windows\system32\winload.efi
the system boots windows in both grub and shim case
5) Tried 
sudo -i
mount /dev/sda3 /mnt
mount /dev/sda1 /mnt/boot/efi
mount --bind /dev /mnt/dev 
mount --bind /dev/pts /mnt/dev/pts
mount --bind /proc /mnt/proc
mount --bind /sys /mnt/sys
modprobe efivars
chroot /mnt
apt-get install --reinstall grub-efi-amd64
update-grub
umount /mnt/boot/efi
umount /mnt
reboot 
the ubuntu choice shows up next to usb boot in the "options de recuperation"->restart, but windows boot and the ubuntu choice is no longer available.

6) Following Andrea Lazzarotto comment on [http://askubuntu.com/questions/524059/how-can-i-get-grub-to-work-after-restoring-deleted-efi-partition](http://askubuntu.com/questions/524059/how-can-i-get-grub-to-work-after-restoring-deleted-efi-partition) , I tried to switch the boot 
sequence from network->usb->ssd to ssd, and SURPRISE, grub is showing up :-) That is a good news !!!! 
The (bad) news is that the windows entry is missing ... I'm looking at adding the windows entry ...

7) Added the windows 8 entry in the /etc/grub.d/40-custom file, windows boots, restarting allow me to boot in ubuntu again :-)


Regards,
  Dominique

---

