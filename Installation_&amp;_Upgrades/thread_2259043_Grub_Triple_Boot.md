---
title: "Grub Triple Boot"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by chazdg24 on 2015-01-01
I have been reading this thread [http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742).

I have a UEFI triple boot setup with Windows 8.1, Ubuntu and Opensuse.  Rather than install Grub into the efi partition, I created a separate mount partition and installed Grub there when I got my new computer. It has served me well as I like to distro hop.  This setup lets the Ubuntu installation control Grub.  I just would not install Grub in Arch and Opensuse.  I would just reboot into Ubuntu and update Grub which picked up all three OS's.

Not happy with Opensuse, I wanted to give Kubuntu a spin.  I deleted Opensuse and began the installation of Kubuntu.  The installer does not give me the option of not installing Grub.  I want Ubuntu to continue to control Grub, not Kubuntu.  

Is this possible?  The installer wants to install Grub somewhere but I'm not sure how to proceed with this without Kubuntu taking over Grub.  Any guidance is appreciated as I have been reading numerous websites without getting a clear idea if this is possible.

Thanks.

---

### Post by Dennis N on 2015-01-01
> **chazdg24 said:**
> I have been reading this thread [http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742).

The installer does not give me the option of not installing Grub.  I want Ubuntu to continue to control Grub, not Kubuntu.  

Is this possible?  The installer wants to install Grub somewhere but I'm not sure how to proceed with this without Kubuntu taking over Grub.  Any guidance is appreciated as I have been reading numerous websites without getting a clear idea if this is possible.

Thanks.

You are installing in UEFI mode. You cannot control where grub is installed - it can only be installed to the EFI system partition (shared with other OSes which are installed). All installs* done with Ubuntu's ubiquity installer put a folder named "Ubuntu" in the EFI system partition. If the folder already exists from a previous install, it is overwritten and you end up booting into grub on the new OS. To continue to boot to the previous OS, copy the Ubuntu folder (or its contents) to a safe place before installing the new OS. After it's done, copy the original folder (or contents) back to the EFI partition, replacing the newer one. This worked for me.

* true for all Ubuntu flavors I have tried - Ubuntu, Lubuntu, Xubuntu, Ubuntu-Mate. Kubuntu is one I have not installed, but I assume this it true for it too.

---

### Post by ajgreeny on 2015-01-01
Are you sure you can not control where grub is put?
If you use the "Something Else" option for the installation there is a dropdown box for where to install the bootloader, and you can there choose to put it in the Kubuntu root partition meaning it will not take over from the existing grub.

I have never needed to use that option on an UEFI machine, but it is certainly there if using that "Something Else" option and I assume it still works that way.

---

### Post by chazdg24 on 2015-01-01
> **ajgreeny said:**
> Are you sure you can not control where grub is put?
If you use the "Something Else" option for the installation there is a dropdown box for where to install the bootloader, and you can there choose to put it in the Kubuntu root partition meaning it will not take over from the existing grub.

I have never needed to use that option on an UEFI machine, but it is certainly there if using that "Something Else" option and I assume it still works that way.
That is what I thought.  So as you say, if I install Grub into the root partition, my existing grub remains intact, which is what I want.  On this Dell XPS, installing grub to the efi partition hosed my system (twice).  I found the alternative method of creating a separate /mount partition (ext4 - 500 mb in size) and installing Grub there worked perfectly for me. I found that solution after much digging.  Arch installed and so did Opensuse, keeping my existing Ubuntu Grub unscathed.

I preserved my efi partition in case something went wrong.  In six weeks nothing has gone wrong with a spin of Arch and Opensuse - my existing Grub remained intact.

I will give it a try with Kubuntu.

I'll let you know if it works out or if Kubuntu takes over...

---

### Post by Dennis N on 2015-01-01
> **ajgreeny said:**
> Are you sure you can not control where grub is put?

I'm positive. If you select the root partition, that will be ignored. It will only use an EFI system partition for grub install location. Furthermore, if you have two disks each with its own EFI system partition, only the EFI system partition on the first disk (sda) is used, even if you specify the second disk. That was my experience after several OS installs (multiboot) on my UEFI system (which has 2 disk drives). 

Also, the installer messages as to what it is doing even say it is installing to sdb, and it actually installed to sda.

---

### Post by LostFarmer on 2015-01-01
If you boot into EFI mode, the user seems to have no controll where grub-efi is installed, it will be installed in the boot drive's efi partition.  Not sure if there are 2 internal hdds with EFI partitons or if there are 2 efi partiton on one hdd  (See Dennis N post above).  But it will not install to a usb stick with an efi partition, even if it is selected as the efi install location and the internal hdd efi partition is marked Do Not Use.


{*  true for all Ubuntu flavors I have tried - Ubuntu, Lubuntu, Xubuntu,  Ubuntu-Mate. Kubuntu is one I have not installed, but I assume this it  true for it too.                                                                                              }
Same with Mint,Pinguy -based off of Ubuntu and uses it's installer.

---

### Post by Dennis N on 2015-01-01
> Arch installed and so did Opensuse, keeping my existing Ubuntu Grub unscathed.
If you are using these, they won't erase your Ubuntu EFI folder. They would make additional folders with other names (Arch and OpenSuse?), leaving Ubuntu alone. So no special precautions need be taken.

---

### Post by chazdg24 on 2015-01-01
And that is what happened.  After installing each, I had my existing Grub intact and just did a sudo update-grub to pick up the new OS.  It seems the jury is split on whether that will happen with a flavor of Ubuntu or Mint.  I still haven't installed Kubuntu to find out.

If Kubuntu does take over Grub, would it be possible to go into Ubuntu and restore the original Grub with the new OS (Kubuntu)?

Existing Grub is not installed in the efi partition.  I created a separate partition and left the efi partition alone.

---

### Post by Dennis N on 2015-01-02
> **chazdg24 said:**
> And that is what happened.  After installing each, I had my existing Grub intact and just did a sudo update-grub to pick up the new OS.  It seems the jury is split on whether that will happen with a flavor of Ubuntu or Mint.  I still haven't installed Kubuntu to find out.

If Kubuntu does take over Grub, would it be possible to go into Ubuntu and restore the original Grub with the new OS (Kubuntu)?

Existing Grub is not installed in the efi partition.  I created a separate partition and left the efi partition alone.

If you install a flavor of Ubuntu or Mint, after restarting you will boot into the grub menu on the new OS. Grub finds the previous Ubuntus or Mints and they will be boot options on grub menu. That's how my UEFI system works.

If you want to restore the original grub, you can do what I suggested in post #2:

> To continue to boot to the previous OS grub, copy the Ubuntu folder (or its contents) from the EFI partition to a safe place before installing the new OS. After it's done, copy the original folder (or contents) back to the EFI partition, replacing the newer one. Reboot and the previous version of grub will return.

I've done exactly this on my UEFI system. 

(I'm confused about the separate partition you mention, and do see how how you can install grub anywhere with ubiquity except for the EFI partition. I have read you can do this with some non-Ubuntu distros (Open Suse? or Fedora?), where the installer (not ubiquity) allows a different EFI patition to be used, or makes its own EFI partition.)

---

### Post by chazdg24 on 2015-01-02
> **Dennis N said:**
> (I'm confused about the separate partition you mention, and do see how how you can install grub anywhere with ubiquity except for the EFI partition. I have read you can do this with some non-Ubuntu distros (Open Suse? or Fedora?), where the installer (not ubiquity) allows a different EFI patition to be used, or makes its own EFI partition.)

This is what I did as using the efi did not work (twice).  My computer would not boot and rebuilding the Windows BCD did not work.  I was about to give up when I found this solution.  Only difference is I do not have a SSD hard drive.  It comes from the comment left by brightdawn. [http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/comment-page-1/#comments](http://www.linuxbsdos.com/2014/06/11/how-to-dual-boot-linux-mint-17-and-windows-8-on-a-pc-with-uefi-firmware/comment-page-1/#comments)

[COLOR=#333333][FONT=Arial]1. Install Win 8.1 first with Secure Boot turned on (after installing ASUS automatically created a EFI Boot Partion of about 105 MB)[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]2. Disable Fast Boot in Win 8.1 & Secure Boot in BIOS setting[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]3. Use the Live DVD to install Linux Mint 17[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]4. Partition the rest of the SSD as follow (after leaving 7-10% for Over Provisioning):[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]* 500 MB for boot partition (file system: ext4, mount point: /boot)[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]* 30 GB for root partition (file system: xfs, mount point: /)[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]* 50 GB for home partition (file system: xfs, mount point: /home)[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]5. Specify the boot loader to the /boot partition reserved for Linux Mint (very important step)[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]6. Continue installing & restart upon completion[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]7. Go into BIOS settings: enable Fast Boot & Secure Boot again[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]8. Enjoy dual boot system (the boot order can be changed easily with grub-customizer)[/FONT][/COLOR]

---

### Post by LostFarmer on 2015-01-02
The reason that 'brightdawn' needed a boot partition is grub will not read a xfs file system so could not boot.  The needed grubx64.efi file would still be in the efi partition efi/ubuntu folder to start the boot process and read the rest of grub needed files to boot in the '/boot' partition along with initrd and vmlinuz files, normally the files would be in the '/' partition under boot folder.

If you are useing a normal linux file system for '/'  , you should not need a '/boot' partition.  There might be a few other cases when a separate '/boot' partition is needed {raid (?), encreped '/' (?)}.

---

### Post by Dennis N on 2015-01-02
After looking over the article he links, this is just a confusion of terms - when he says "boot partition reserved for Mint", I believe he is referring to the EFI system partition (sda2 in the article). This is where grub is being installed in the article's tutorial. That EFI system partition is in turn mounted by the OS (Mint in the article) at /boot/efi/ within the root partition in the tutorial, but apparently in the separate (500mB) boot partition in #post 10.

---

### Post by LostFarmer on 2015-01-02
Dennis N-- one has to go all most to bottom of page and find the feedback by "			brightdawn"  dated Sep 25 2014 , to help understand what  the OP is saying. 'brightdawn' has '/' and '/home' formated as xfs so a '/boot' partition, ext4 is used.  You are correct that the EFI partition would still start the boot process.

---

### Post by Dennis N on 2015-01-02
A nice screenshot of the final partition table would be helpful to any reader of this thread.

---

