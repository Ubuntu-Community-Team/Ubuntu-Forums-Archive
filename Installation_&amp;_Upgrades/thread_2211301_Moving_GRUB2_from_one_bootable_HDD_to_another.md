---
title: "Moving GRUB2 from one bootable HDD to another"
date: 2014-03-15
forum: Installation &amp; Upgrades
---

### Post by SageOfSmeg on 2014-03-15
Two physically hard disks, each 4.3GB (yes, old hardware, PC100 motherboard)
First HDD (HDD#0, bootable) = Windows 98
Second HDD (HDD#1, bootable) = Lubuntu 12.04.3
 
Windows 98 installed on HDD#0 but then HDD#0 disconnected and BIOS detection disabled/removed, so effectively HDD#0 was not present as far as the machine was concerned.
 
Lubuntu then installed on HDD#1 (for trial purposes) with GRUB2 bootloader but obviously without detection of Windows.
 
Now that I am happy with the Lubuntu setup and have ensured that it can run okay on this old machine, I want to reconnect HDD#0 and enable dual booting via GRUB2.
 
I assume that I will need to somehow disable GRUB2 on the MBR of HDD#1 and/or copy selected GRUB2 files from HDD#1 to HDD#0, or alternatively uninstall GRUB2 completely from HDD#1 and then install GRUB2 on HDD#0 and then manually edit the new /etc/default/grub on HDD#0 to include both operating systems as menuentry items.
 
Question: what would be the best approach? I really don’t want to wipe HDD#1 and reinstall Lubuntu just to get GRUB2 set up on HDD#0.

Question: how do I install GRUB2 independently – is there a live CD or floppy install?
 
Footnote: I have no knowledge of MBR editing.

---

### Post by Herman on 2014-03-15
After plugging your first hard drive in again you should be able to boot Windows 98 normally and you won't be able to boot Lubuntu unless you go about it a different way.

You should be able to boot your HDD#1 hard disk with Lubuntu in it by the BIOS boot menu.
If you press a key during the early stages of booting when the BIOS screens are still visible you should be able to get the BIOS boot menu and choose which hard disk you would like the BIOS to boot for you. Commonly the F12 key or maybe the F8 key or less commonly some other key like F2 or Esc or some other might be the BIOS Boot Menu key for your computer. If you watch carefully during boot-up there is most likely some text which flashes up briefly during boot-up which will tell you which key to press for the BIOS boot menu. It should be mentioned in your computer's  motherboard manual if you have one, or you could just find it by trial and error.

When you have Lubuntu up and running if you issue the command 'sudo update-grub' (no inverted commas), your Lubuntu's GRUB should detect Windows 98 and add it to your GRUB Boot Menu.
```
sudo update-grub
```

If you want you can issue the command 'sudo grub-install /dev/sda', to install GRUB to MBR in your first hard drive.
```
sudo grub-install /dev/sda
```
GRUB comes in three parts. One part is installed in the MBR and the second part is in unused sectors in the first track of the hard disk. It won't hurt  Windows 98 because Windows 98 starts with its 'boot sector' at the beginning  of the second track of the hard disk.
The MBR code points to the GRUB code in the second track which is larger and more capable, and that points to the GRUB files in your second hard disk's Lubuntu installation's /boot/grub folder, where the real work of booting the computer is done.
From there you will be able to choose to boot either Lubuntu or Windows 98.

After you install GRUB to your first hard disk's MBR you will need to boot via the second hard disk's GRUB from then on. If the second hard disk is removed from the computer for some reason, your computer won't be able to boot Windows 98 by itself again. (Or at least not without an emergency boot disk of some kind). You can return your first hard disk's MBR back to it's original condition again, only capable of booting Windows 98, by using a Windows 98 boot floppy disk. If you don't still have one the files for making one may still be avialable for free download from [bootdisk.com]("http://www.bootdisk.com/bootdisk.htm") .

---

### Post by Herman on 2014-03-15
There are lots of other ways you can install and use GRUB from various other kinds of media.

If  you can spare the cash for a USB flash memory stick of 8GB or larger  capacity, you can install Ubuntu or Lubuntu into the flash memory as an  auxilliary Ubuntu or Lubuntu installation. It will have its own GRUB in  it and if your computer's internal operating systems aren't already in  its boot menu you can run 'sudo update-grub' in your USB installation to  update its boot menu and boot operating systems in any computer. It's  convenient at times to have an auxillary Ubuntu or Lubuntu installation  rather than just use a Live CD for working on your regular hard-disk  Ubuntu or Lubuntu installation.

If you want to save money and you  have a spare USB lying around for file storage, you don't need to use  an entire flash memory stick if you only want a GRUB boot disk. You can  install GRUB in it and use it as a GRUB boot disk. You will need to  install a GRUB folder in it for the boot loader files. They won't take  up much room or harm your existing files in your USB. You'll need to run  a special GRUB command to make the GRUB boot memu file for it. 

You can make a GRUB Rescue CD or a floppy disk using the grub-mkrescue command.
You could use a partition editor and shrink Windows 98 a little and make a dedicated GRUB partition in the first hard disk.
You  could lave the Windows 98 partition as it is and install GRUB inside  Windows 98, but do not install it to the partition boot sector. By using  the approriate commands it is possible to have a GRUB folder inside  Windows 98 and boot both Windows 98 and Ubuntu from it.

---

### Post by SageOfSmeg on 2014-03-16
Thanks for the replies. I shall experiment. The option of 'sudo grub-install /dev/sda' seems a good way to go for the time being.

Lubuntu is my preferred OS on this machine and I use it to monitor my network. To be honest, I only ever use Win98 in an emergency if my other WinXP machine is playing up (some backed up data files copied to backup discs). I just want to avoid having to reinstall either OS because this old machine is slow and installs can take hours, if not all day.

---

### Post by SageOfSmeg on 2014-03-24
I have now had the time to try out the above suggestions and the installation of grub on HDD#0 worked perfectly and the machine now dual-boots just as intended. I have even managed to shrink the Win98 partition to free up a small area on the original HDD#0 disk for use as an extra ext4 partition for Lubuntu.
 
This is why I love Ubuntu because when great advice is received it makes everything is so much simpler than Windoze. Thanks guys.

---

