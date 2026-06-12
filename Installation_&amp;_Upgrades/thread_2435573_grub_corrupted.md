---
title: "grub corrupted"
date: 2020-01-22
forum: Installation &amp; Upgrades
---

### Post by hongg on 2020-01-22
I had a dual boot machine with Windows and Ubuntu 18.04.  The latest Ubuntu update introduced an issue with gnome due to my nvidia GT 730 video card - Ubuntu would hang on start up on the gnome display manager.  I decided to install Mint to work around this.  The install failed while it was trying to update grub.  Now grub won't start except for the grub prompt.  I tried to use boot-repair on the mint boot disk to fix.  No luck.  I tried to restore the MBR using boot-repair.  No luck.  Can someone help me?  

[http://paste.ubuntu.com/p/DydWwFrKyT/](http://paste.ubuntu.com/p/DydWwFrKyT/)

[http://paste.ubuntu.com/p/YQRk2hNxfZ/](http://paste.ubuntu.com/p/YQRk2hNxfZ/)

thx.

---

### Post by oldfred on 2020-01-22
You have mixed BIOS & UEFI which on one drive cannot be done.

Windows requires BIOS boot on MBR partitioned drives.
Windows requires UEFI boot on gpt partitioned drives.
Ubuntu does let you install in UEFI boot mode to MBR(msdos) partitioned drives, but probably should not.

You can only have one boot flag per drive.
And with BIOS boot Windows has to have boot flag on its boot partition, your sda1.
But UEFI requires boot flag on the ESP - efi system partition, and you have that as as sda6.
Use gparted to move boot flag back to sda1. Since you have syslinux in MBR, Windows should then boot.  If Windows 10, make sure Windows fast start up is off.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Then you need to convert last install to BIOS boot. You can use Boot-Repair's advanced mode to choose install and drive to install grub into.

How did you install nVidia driver? If you installed directly from nVidia, you have to reinstall on every kernel update. Always better to install driver from Ubuntu repository. And you may be able to boot from recovery mode and older kernel, if nVidia driver was boot issue.

If you now want Mint, I will move this thread to the MINT subforum.

---

### Post by hongg on 2020-01-22
Thanks so much for your reply!  (I'm still digesting it.)  My understanding is that the drivers packaged with Ubuntu are quite inferior for my Nvidia card, so I was using proprietary drivers.  I was only installing Mint as a workaround.  I'll see if I can't get the Windows and Ubuntu to work again, following your advice.  thx again.

---

### Post by oldfred on 2020-01-22
The Ubuntu drivers are the official nVidia proprietary drivers, just compiled to work easier with Ubuntu.
And older installation ISO may have somewhat older versions. Now newest version installs nVidia driver automatically if you select to install restricted extras.

And ppa has the very newest drivers if you have a very new nVidia card/chip.
Ubuntu Launches Its "Fresh" Proprietary Driver PPA - August 2015
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa

---

### Post by hongg on 2020-01-23
thx again!  Linuxbabe says this about ubuntu drivers for nvidia:  Ubuntu comes with the open source nouveau driver which is included in  the Linux kernel for Nvidia cards.  However, this driver lacks 3D  acceleration support. If you are a gamer or need to work with 3D  graphics, then you will benefit from the better performance of the  proprietary Nvidia driver.  

I guess you're saying that this is no longer true.

---

### Post by hongg on 2020-01-23
Ok... sda1 had boot flag still, but i removed esp flag from sda6.  Now I  can boot into Windows (which I know see is Windows 7, so no  fastboot/hibernation issue).  

Can you detail the following for me?  "Then you need to convert last install to BIOS boot. You can use  Boot-Repair's advanced mode to choose install and drive to install grub  into."  Meantime, I'll dig into it some more myself.  Much appreciated.  thx.

---

### Post by hongg on 2020-01-23
Ok... i think i found how to do it:  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[h=2]Converting Ubuntu into Legacy mode[/h] **Note:**  Use this procedure only to convert an UEFI-mode Linux installation to  boot in BIOS/CSM/legacy mode. Such a conversion may be necessary if some  hardware doesn't work correctly under UEFI mode. (Video cards are a  common source of problems.) Converting to boot in BIOS/CSM/legacy mode  while Windows boots in UEFI mode can make the boot process more awkward  -- you'll need to use the computer's built-in boot manager to switch  between OSes, and some computer's have such poor boot managers that this  may be impossible. 

[LIST]
[*]If Ubuntu is installed on a GPT disk (you can check it via the 'sudo parted -l' command), use [Gparted]("https://help.ubuntu.com/community/Gparted") to create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag) at the start of its disk. 

[*]Start [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"), click on "Advanced options", go to the "GRUB location" tab. 

[*]Untick the "Separate /boot/efi partition" option 
[*]Click the "Apply" button. 
[*]Set up your BIOS so that it boots the HDD in Legacy mode (see the ""[Set up the BIOS in UEFI or Legacy mode]("https://help.ubuntu.com/community/UEFI#Setup_the_BIOS_in_EFI_or_Legacy_mode")" paragraph above). 

[/LIST]

---

### Post by oldfred on 2020-01-23
If you are a gamer, you will want the nVidia drivers, its just you install from Ubuntu repository using system settings, or command line.

Similar threads on installing, some may have a detail others do not.
If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351)

Shows Boot-Repair's advanced mode screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You need to always have an Ubuntu live installer flash drive and a Windows repair/recovery flash drive. With Windows 10 it likes to change settings and then you have to make repairs. Windows 10 can be installed in old BIOS/MBR configuration, but dual boot works better if both Windows & Ubuntu are UEFI on gpt partitioned drive(s).

---

### Post by hongg on 2020-01-23
I've got the three different OS's booting now.  On the first boot-repair, only Mint was in the Grub menu.  I did a 2nd boot-repair on Ubuntu, and everything is now in the Grub menu.  

I can get Ubuntu to get past the gnome display manager issue (some incompatibility with Nvidia proprietary drivers) with the old kernel, as you said.  Is there a clean way to make the old kernel the default rather than have to select it off the Ubuntu advanced options?  Something I read said that removing the latest kernel might remove the previous kernel as well.  thx!

---

### Post by oldfred on 2020-01-23
Never removed kernels.

#What is installed
dkms status

I am not a gamer and could not tell any difference with nVidia and Nouveau with my older GT620 card. And it turns out the Intel Haswell chip was faster on most things than the nVidia card, so unplugged it.

---

### Post by hongg on 2020-01-24
Ok.  

Yes, I'm starting to realize that the graphics chip that  comes with these old business desktops that i use might be good enough.   

Since it's installed and boots up now, I'll give Mint a try.  

thx.

---

