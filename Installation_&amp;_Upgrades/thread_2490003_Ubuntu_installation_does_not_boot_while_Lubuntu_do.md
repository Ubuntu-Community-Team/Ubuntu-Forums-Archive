---
title: "Ubuntu installation does not boot while Lubuntu does"
date: 2023-08-18
forum: Installation &amp; Upgrades
---

### Post by srope01 on 2023-08-18
I have Ubuntu 22.04 running on a HP ProBook 4540s. Originally I started it way back on 18.04 and upgraded it twice (to 20.04 then to 22.04)


I got a new hard drive and I decided to start from scratch by installing 22.04.03 using the iso and a bootable usb. The live USB worked and then I got it to install. But on booting from the new hard drive, I got an error (BootDevice not found). Using gparted on the live usb, I can see the installation on the new hard drive as /dev/sda1 grub2core.img 1 MB, /dev sda2 EFI system partition, and /dev/sda3 is ubuntu 22.04. This isn't what I expected though as I thought the install was simply on /dev/sda1.


Strange thing is when I installed Lubuntu 22.04.03 instead using the live usb, Lubuntu booted properly and was installed on /dev/sda1 as expected.


I would rather be using Ubuntu than Lubuntu. Could anyone help me on how to get Ubuntu 22.04.03 to boot?

---

### Post by tea for one on 2023-08-18
The installer created three partitions because you booted/installed in Legacy mode.
If your PC is UEFI compatible, I would install only in UEFI mode with GPT.

In your HP UEFI settings, can you disable Legacy boot?

---

### Post by srope01 on 2023-08-18
> **tea for one said:**
> In your HP UEFI settings, can you disable Legacy boot?

I believe I can but you reminded me of a problem I had when I first installed 18.04. I looked in some old notes and it seems that back then, the 18.04 live usb would not even boot under HP's implementation of UEFI. So I enabled Legacy Boot and only then did I managed to install 18.04. It was a rather painful process though because I had to go back and forth in the UEFI menus and at one point, the laptop would not even boot at all (black screen only)! It seems HP has a bad implementation of UEFI. I would rather not like to go through that again and potentially get stuck with a brick laptop. Is there a way to get the Ubuntu installer to work with Legacy boot? Otherwise, I guess I have to switch to Lubuntu.

---

### Post by tea for one on 2023-08-18
> **srope01 said:**
>  It seems HP has a bad implementation of UEFI.
Yes, this is mentioned often in these forums.
> **srope01 said:**
> I would rather not like to go through that again and potentially get stuck with a brick laptop. Is there a way to get the Ubuntu installer to work with Legacy boot? 
Yes, I think so.

Boot the installer in Legacy mode
Check your boot mode via terminal with
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Open Gparted and create _one_ partition ext4
Close Gparted
Start the installer and install to the previous created partition.
The installer may ask to create an ESP - ignore it as long as you have booted in Legacy mode. 

i tested this some time ago - more info here (post 4) [https://ubuntuforums.org/showthread.php?t=2476625](https://ubuntuforums.org/showthread.php?t=2476625)

---

### Post by oldfred on 2023-08-18
If the drive is gpt partitioned (which I recommend) you will need a 1MB unformatted partition with the bios_grub flag (if using gparted). 
I have used gpt with my 2006 BIOS only laptop and a desktop from from about then also. I started converting drives to gpt in 2010.

I also suggest having the ESP, so perhaps in future you can convert to UEFI boot. The only real difference is UEFI settings on default boot and version of grub, grub-pc for BIOS or grub-efi-amd64 for UEFI.

We have seen many posts of HP with UEFI boot issues. Most eventually are able to boot. A few do give up and just boot with BIOS which does work ok. 

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[gpt Advantages]([http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)) & 
[https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR](https://wiki.archlinux.org/title/Partitioning#Choosing_between_GPT_and_MBR)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by srope01 on 2023-08-19
> **tea for one said:**
> 
Start the installer and install to the previous created partition.
The installer may ask to create an ESP - ignore it as long as you have booted in Legacy mode. 



Ok, I ran the test in terminal and I am sure I am in Legacy mode. I  created a partition for the whole drive. When I tried to install Ubuntu,  I got only one choice, "Erase disk and install Ubuntu". It then  installed the three partition Ubuntu which then does not boot. I went  back to the installer and tried it again, hoping to install in the  partition /dev/sda3. I get 3 choices, Erase and reinstall, Install side  by side, Erase disk and install.

How did you manage to install to the previous created partition?

---

### Post by tea for one on 2023-08-19
In the window "Installation Type", do you not see "Something else"?

Anyway, let's tweak the installation and see what happens:

Boot the 22.04 installer in Legacy mode
Double check with the terminal command
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Open Gparted > Device > Create Partition Table > msdos
Also create one ext4 partition but using only 50% of the target disk
Close Gparted
Start the installation
Choose Something else at Installation type
Select your pre-prepared partion
Format to ext4 and mount point = /
Boot loader to same disk (not to the partition) e.g. sda _not_ sda1
Ignore the warning about ESP
Continue the installation

Any joy?

---

### Post by yancek on 2023-08-19
>  the 18.04 live usb would not even boot under HP's implementation of UEFI.

I installed 18.04 on an HP in UEFI mode several years ago without problems.  I had an option in the BIOS boot options to select UEFI or Legacy boot.  Do you see that.  My newer HP laptop does not have an option to boot in Legacy mode and I expect that will be the case in the near future for other manufacturers as well.

>  /dev/sda1 grub2core.img 1 MB, /dev sda2 EFI system partition, and /dev/sda3 is ubuntu 22.04. 

An MBR install will put boot code in the MBR of the drive and need only 1 partition.  If you are using a GPT drive and install in Legacy mode, you need the BIOS-boot partition for the grub core.img file.  If it is an EFI install on GPT, you don't need the BIOS_boot partition only the EFI partition which in your case shows as sda2.  It would seem that your Lubuntu install is/was a Legacy isntall rather than EFI and Ubuntu is/was EFI.  Disable Legacy/csm boot in the BIOS and test boot.  It is usually simpler if you install all OS's in the same mode.

If you want a Legacy install and have that option in the BIOS, I would expect the recommendations posted by Tea For One to do the job.

---

### Post by Impavidus on 2023-08-19
I've got an HP of about the same age as yours and indeed, those are difficult to work with in UEFI mode. I just use Xubuntu in legacy mode.

Your Ubuntu creates an EFI partition, a BIOS_grub partition and a root partition. On legacy systems, the EFI partition isn't needed and isn't used, it's just created automatically. The BIOS_grub partition is needed to install Ubuntu in legacy mode on a GPT partitioned drive. Your Lubuntu live disk instead installs on an MBR partitioned drive, where you only need a root partition. It's considered old-fashioned; the option may have been removed from Ubuntu's installer, but retained on Lubuntu's installer. Lubuntu takes more care to work on older computers.

---

### Post by srope01 on 2023-08-19
> **tea for one said:**
> In the window "Installation Type", do you not see "Something else"?

Anyway, let's tweak the installation and see what happens:

Boot the 22.04 installer in Legacy mode
Double check with the terminal command
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Open Gparted > Device > Create Partition Table > msdos
Also create one ext4 partition but using only 50% of the target disk
Close Gparted
Start the installation
Choose Something else at Installation type
Select your pre-prepared partion
Format to ext4 and mount point = /
Boot loader to same disk (not to the partition) e.g. sda _not_ sda1
Ignore the warning about ESP
Continue the installation

Any joy?

When I chose Something else, I can see /dev/sda1 is the whole drive and there are three buttons Quit, Back, and Install Now. But the Install Now button is greyed out.

Following your tweaked instructions, it worked but there was one additional step. When I get to the point of selecting the prepared partition, I had to click on Change. I get a menu in which the default was "Do not use this partition". I changed it to ext4 and mount point /. The Install Now button is no longer grey. I am installing now. I will post again after rebooting.

---

### Post by srope01 on 2023-08-19
I have installed Ubuntu 22.04 under Legacy mode. Many thanks Tea For One! 

As for putting the HP back into UEFI mode, I am reluctant about that because their implementation is so bad. So for the rest of the life of this laptop, I will keep it in Legacy mode. I assume new laptops will have better implementations so it will be a lot easier to install to Ubuntu.

Many thanks to the others for the explanations of the advantages of UEFI mode, GPT vs MBR, and the difference between the Ubuntu and Lubuntu installers.

I will set this thread as solved.

---

