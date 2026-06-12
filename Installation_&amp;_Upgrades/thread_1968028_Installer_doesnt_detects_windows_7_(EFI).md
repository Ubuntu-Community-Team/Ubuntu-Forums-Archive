---
title: "Installer doesnt detects windows 7 (EFI)"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by Lancro on 2012-04-28
This is my partition table...

1.- EFI System partition 300 MB
2.- A partition called DELLUTILITY with 40MB fat32
3.- A partition called OS with Windows 7 and data file (This is where ubuntu should detect windows 7 and installs)
4.- A partition called RECOVERY with 750 MB

I want to install ubuntu alongside windows 7, I need an easy explanation, can anyone help me?.

Thanks.

---

### Post by darkod on 2012-04-28
Boot into live mode with the cd and in terminal post the output of:
sudo fdisk -l (small L)
sudo parted /dev/sda print

---

### Post by Lancro on 2012-04-28
[http://paste.org/48608](http://paste.org/48608)

There you are, and thanks.

---

### Post by darkod on 2012-04-28
I can't see anything wrong. Your win7 takes almost all of the hdd. You will have to open windows Disk Management first and shrink the partition for as much space as you want.

Then you have to be careful with EFI because there was a bug in ubuntu that was overwriting windows efi files on the EFI system partition. I don't think it's solved yet.

Just in case, copy the files from /dev/sda1 and keep them safe. Maybe you will need to copy them back if ubuntu deletes them.

Investigate dual booting with EFI because there are some issues. I don't use EFI and don't have all the details.

Look at post #10 here:
[http://ubuntuforums.org/showthread.php?t=1967058](http://ubuntuforums.org/showthread.php?t=1967058)

oldfred has more resources and links about EFI.

---

### Post by Lancro on 2012-04-28
Ok, I dont understand the link instrutions, I only want to dual boot, didnt know it was this hard, will wait for other answers or give up in installing ubuntu.

Thanks.

---

### Post by darkod on 2012-04-28
The combination of efi + gpt is a bit complicated for dual boot right now. And that is exactly the combination you have.

---

### Post by Lancro on 2012-04-29
Ok, I have created 2 partitions, one for / and another for swap, and I have instaled ubuntu on it, now I boot into ubuntu, but grub doesnt seem to detect my windows 7 partition, how can I do to configure grub to detect it?.

Thanks.

---

### Post by oldfred on 2012-04-30
With UEFI boot you primarily choose what to boot from the efi menu. It should be giving you the options of systems installed in the efi partition to boot.
You should have something like this which another user posted:

find /boot/efi -name "*efi"
/boot/efi
/boot/efi/EFI/ubuntu/grubx64.efi
/boot/efi/EFI/BOOT/bootx64.efi
/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
[http://ubuntuforums.org/showthread.php?t=1746194](http://ubuntuforums.org/showthread.php?t=1746194)


Do you have something like this, that another user posted, except you need to add Windows from /efi/Microsoft:
> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


Another way is to modify 40_custom.
[http://askubuntu.com/questions/125191/another-windows-7-entry-missing-from-grub2-question](http://askubuntu.com/questions/125191/another-windows-7-entry-missing-from-grub2-question)

---

