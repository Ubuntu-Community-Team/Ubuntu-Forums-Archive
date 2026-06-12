---
title: "UEFI Motherboard dual boot/dual HDD"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by tdm on 2013-01-13
I have a UEFI motherboard (Gigabyte GA Z77MX-D3H) and a 120GB SSD and 2TB HDD.

_Here is my current config:_
**sda 120GB SSD**
 sda1 ntfs 100MB Windows boot partition
 sda2 ntfs 70GB Windows partition
 sda3 ext4 40GB Xubuntu / partition
**sdb 2TB HDD**
 sdb1 ntfs 1500GB Storage partition
 sdb2 swap 10GB Linux-swap
 sdb3 ext2 500MB Xubuntu /boot partition
 sdb4 ext4 300GB Xubuntu /home partition
Bootloader installed to **sdb** in Xubuntu installer

However, I cannot boot Xubuntu. Only the windows BCD bootloader ever appears. Even leaving default option and installing bootloader to **sda** doesn't work. Its always the Windows bootloader appearing.

I have tried booting from the 2TB HDD where I expect the MBR for GRUB2 will be installed from the installer but it just goes on to the Windows bootloader as if it couldn't find GRUB.

I have tried adding Xubuntu to the Windows BCD to chainload with EasyBCD but it just reverts straight to Grub4Dos prompt.

I think my motherboard being UEFI is relevant somewhere. I am unsure of what UEFI is in comparison to BIOS.



**What configuration do I take to get this dual-boot up and running? **I would prefer Xubuntu OS to be on the SSD and /home to be on the HDD.

Thanks

---

### Post by 101kitty on 2013-01-13
I don't know what UEFI is but, you should see look at your HHD and see if the one is set to master and the other one slave, or they could both be set to master, not sure if this is the problem but it would not hurt to see if this could be the problem.
If this is the problem check this it, it will tell you were to put the pins on your HHD

[http://en.wikipedia.org/wiki/Master/slave_(technology](http://en.wikipedia.org/wiki/Master/slave_(technology))

---

### Post by tdm on 2013-01-13
> **101kitty said:**
> I don't know what UEFI is but, you should see look at your HHD and see if the one is set to master and the other one slave, or they could both be set to master, not sure if this is the problem but it would not hurt to see if this could be the problem.
If this is the problem check this it, it will tell you were to put the pins on your HHD

[http://en.wikipedia.org/wiki/Master/slave_(technology](http://en.wikipedia.org/wiki/Master/slave_(technology))
With SATA hard disks there is no master/slave afaik.

UEFI is some new replacement for BIOS that released last year. It allows faster booting and Windows 8 requires it but it has booting complications.

---

### Post by james2b on 2013-01-13
UEFI has a feature known as "secure boot" which blocks out any other boot loaders or operating systems. So try to hit your F key to enter that EFI set up screen to find and disable secure boot if that is available as an option. Here are some UEFI web sites links here; [http://www.uefi.org/about/,and](http://www.uefi.org/about/,and) here; [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) , and this one too; [http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)

---

### Post by tdm on 2013-01-13
> **james2b said:**
> UEFI has a feature known as "secure boot" which blocks out any other boot loaders or operating systems. So try to hit your F key to enter that EFI set up screen to find and disable secure boot if that is available as an option. Here are some UEFI web sites links here; [http://www.uefi.org/about/,and](http://www.uefi.org/about/,and) here; [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) , and this one too; [http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)
My MB manual doesn't document anything like this. I did however find an more than 4 options under "CSM Support" that could be "Legacy only", "UEFI only", "UEFI and Legacy". One of those options called "Boot mode support". Is this relevant?

I set CSM Support to Never instead of Always as an experiment and the computer did long beep and no response. Had to reset CMOS. So that isn't the option obviously...


Now, do you have any answers to the OP's question?

---

### Post by james2b on 2013-01-13
Search that Gigabyte motherboard web site for more specific information such as CSM, this motherboard here may be yours; [http://www.gigabyte.us/products/product-page.aspx?pid=4145#ov](http://www.gigabyte.us/products/product-page.aspx?pid=4145#ov) , and here; [http://www.tomshardware.com/forum/347038-28-support](http://www.tomshardware.com/forum/347038-28-support) Did that computer come with Windows 8 originally, and what brand PC ?

---

### Post by tdm on 2013-01-13
> **james2b said:**
> Search that Gigabyte motherboard web site for more specific information such as CSM, this motherboard here may be yours; [http://www.gigabyte.us/products/product-page.aspx?pid=4145#ov](http://www.gigabyte.us/products/product-page.aspx?pid=4145#ov) , and here; [http://www.tomshardware.com/forum/347038-28-support](http://www.tomshardware.com/forum/347038-28-support) Did that computer come with Windows 8 originally, and what brand PC ?
Thanks for the help but if you read the OP you would see that I know what motherboard I have. Because I built the PC from new parts (i5 3570K, GTX 670 etc.). And there is nothing to do with Windows 8, this is for trying to get to Xubuntu's GRUB menu (I have Windows 7 btw).

Thanks

---

### Post by oldfred on 2013-01-13
I think CSM is another name for BIOS or legacy boot. But to see where everything is installed in detail.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by tdm on 2013-01-13
> **oldfred said:**
> I think CSM is another name for BIOS or legacy boot. But to see where everything is installed in detail.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)
Here is the boot-info I took in a Live-USB:

[http://paste.ubuntu.com/1529128/](http://paste.ubuntu.com/1529128/)

The thing is, I have even tried default options. (replacing windows bootloader on **sda** (via ubiquity) MBR and booting from **sda** and the Windows bootloader remains!

---

### Post by tdm on 2013-01-13
I have gotten further. I was able to boot further by using Grub4Dos command-line with EasyBCD's NeoGrub.

I typed:
set --root (hd1,1)
kernel (hd1,1)/linux-3.5.0-17-generic (or something similar [used "ls" to find its name])
initrd (hd1,1)/initrd.img-3.5.0-17-generic
boot

And it just stopped here after about 10 seconds of loading text on the screen:

[IMG]http://i47.tinypic.com/2zhp8j6.jpg[/IMG]


I also tried not using separate /boot partition on 2TB HDD. I just let it be in / like I usually would. Same situation as above happens.

NOTE:
Since the bootloader is installed to PARTITION and not DEVICE, I tried chainloading in GRUB like so:
set --root (hd0,3)
chainloader +1
boot

It notes the partition as ext2fs instead of ext4 (might be normal)
Then it says "Unsupported executable format..."

---

### Post by oldfred on 2013-01-13
I have no idea how EasyBCD manages to boot Ubuntu.

but if you have started to boot you may need nomodeset or other boot parameters. With grub you press e on grub menu and replace splash quiet with nomodeset.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ronparent on 2013-01-13
My inspection of your boot info script shows that your system seems to need only a simple BIOS boot. It shows the boot loader on sdc? You do not appear to understand how grub functions and may have over complicated your installation. You have already apparently spent considerable time trying to untangle your system. Consider it time well spent a a learning exercise.

I suggest the simplest approach is for you to abandon your prior efforts and simply reinstall! Just make sure you this time install grub to the MBR of either sda or sdb and make sure the chosen drive is selected to boot first in the bios. A dedicated boot partition is unnecessary and only complicates your setup. Also the uuid of the partition you install on should also be the location of your kernel (ie /vmlinuz-3.5.0-17-generic root=UUID=.....etc). I see no reason why your system should not dual boot if grub is installed properly. A simple installation should require less than 20 minutes a clean up all your problems. Do select 'do something else' on the third screen and then select sda4 to install / to and sda or sdb to install the grub MBR to. Let us know how you make out.

---

### Post by tdm on 2013-01-13
> **ronparent said:**
> My inspection of your boot info script shows that your system seems to need only a simple BIOS boot. It shows the boot loader on sdc? You do not appear to understand how grub functions and may have over complicated your installation. You have already apparently spent considerable time trying to untangle your system. Consider it time well spent a a learning exercise.

I suggest the simplest approach is for you to abandon your prior efforts and simply reinstall! Just make sure you this time install grub to the MBR of either sda or sdb and make sure the chosen drive is selected to boot first in the bios. A dedicated boot partition is unnecessary and only complicates your setup. Also the uuid of the partition you install on should also be the location of your kernel (ie /vmlinuz-3.5.0-17-generic root=UUID=.....etc). I see no reason why your system should not dual boot if grub is installed properly. A simple installation should require less than 20 minutes a clean up all your problems. Do select 'do something else' on the third screen and then select sda4 to install / to and sda or sdb to install the grub MBR to. Let us know how you make out.
Thanks for the help.
I have reinstalled many times and have tried all those steps you suggested. They were the first things I did.

The overcomplication is just me trying to make it work. I put /boot partition on sdb (2TB HDD) as I couldn't boot from sda but I still wanted the OS installed on sda (SSD) for speed. That didnt work.

Also, you should have noticed that sdc in the Boot-Info is the USB drive I used to generate the Boot-Info. you said "the boot loader on sdc" as if it was the only boot loader in the system. Is this true? Has the ubuntu installer not been putting bootloaders on the SSD or HDD?

---

### Post by dsv47 on 2013-01-14
Your problem is a known issue with booting to an SSD from a Gigabyte motherboard. Try changing the SATA ports to AHCI in the BIOS settings and then reboot. Also, if you are normally booting to the SSD, you would want the SSD to be placed before the other HDD in the BIOS menu for setting the device boot order.

---

### Post by tdm on 2013-01-14
> **dsv47 said:**
> Your problem is a known issue with booting to an SSD from a Gigabyte motherboard. Try changing the SATA ports to AHCI in the BIOS settings and then reboot. Also, if you are normally booting to the SSD, you would want the SSD to be placed before the other HDD in the BIOS menu for setting the device boot order.
It was at AHCI by default. And boot order is SSD first.

---

### Post by tdm on 2013-01-14
Here's some progress:

Fedora 17 boots fine with chainloader +1 from Grub4Dos.
Yet with Xubuntu it says "Unsupported executable format".

---

### Post by james2b on 2013-01-14
Okay I see then, and since you do not have Windows 8, and do dual boot with 7, then there is no need for the UEFI, you can try to set your system to that legacy standard BIOS with CSM enabled full at least it may be worth to try. Did you try to boot to a Ubuntu live CD or DVD to re-install grub2, such as; grub-install /dev/sda from terminal as sudo root ?

---

### Post by tdm on 2013-01-14
> **james2b said:**
> Okay I see then, and since you do not have Windows 8, and do dual boot with 7, then there is no need for the UEFI, you can try to set your system to that legacy standard BIOS with CSM enabled full at least it may be worth to try. Did you try to boot to a Ubuntu live CD or DVD to re-install grub2, such as; grub-install /dev/sda from terminal as sudo root ?
I will experiment with the BIOS options to see what one I should have enabled.
To install bootloader, I just reinstall ubuntu. Only takes 3 mins with good USB drive and SSD.

---

### Post by ronparent on 2013-01-14
I really understand your frustration. I myself also have a Gigabyte MB and have spent days trying to install 12.10 to a raid0 - with NO success whatsoever! I had to finally resort to simply copying a 12.10 (&13.04) from a system installed to a pen drive! But I digress.

Just to warn you that in playing with my own 'BIOS' CSM settings I have been left with a non-functioning 3 beep MB and have had to remove the battery to reset it (the board does have a BIOS reset switch which didn't fix it for me). Then you have to re-enter all of your Prior BIOS changes. What a pain! Otherwise it is a great MB and very robust.

I hope that you have success in finding something that works. In my opinion your kind of problem should not exist and should be fixed in the distro.

---

### Post by oldfred on 2013-01-14
I also suggest installing grub2's boot loader to the MBR. If you really do not want to remove Windows boot loader leave it and install grub to your other drive. But grub is designed to multi-boot where EasyBCD is modifying Windows boot loader and still using the Windows version of grub to boot.

Where did Fedora come in? That often installs to lvm and you have to install lvm2 driver and mount partition for grub to find lvm installs. Not sure grub4dos can do that.

---

