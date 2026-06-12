---
title: "Install 14.04 on external hard drive, to work in any PC or MAC."
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by RubberSoul on 2014-06-12
Hi, i wanna install the LTS 14.04 on a external HD, to work on any computer that i use.

Is that possible? Some help here??? Thankz.

---

### Post by Bucky Ball on 2014-06-12
You will probably need to install grub to the external hard drive with the OS install, but then you should be able to plug the hard drive into another machine, go to the BIOS to set it to boot from the external drive, and it should work. There is the issue of hardware drivers for each machine, which your external install may or may not have. May work faultlessly on some machines while others might be missing wireless or graphics drivers or something else less common.  

Give it a try and good luck.

---

### Post by RubberSoul on 2014-06-12
I wanna know if any of you guys know a step by step guide, cause I don't know how to start that... =(
I've made several searches on google, but none of them helped much... So... =(

---

### Post by Bucky Ball on 2014-06-12
Step by step guide to installing Ubuntu? Just follow the install and when you get to the partitioning section choose 'Something Else' to partition manually. Select to install to the external drive (which will probably be sdb).

You will need something like:

/ = where the OS goes, 20Gb plenty;
/home = where you personal data and settings go, large as you like;
/swap = 2Gb fine.

And that's it. All those mountpoints you will find as defaults and you want / and /home to be EXT4 filesystem and /swap to be swap space, also defaults you can select during the 'Something Else' manual partitioning.

Other than that, there are a million how-tos online dealing with installing Ubuntu.

---

### Post by oldfred on 2014-06-12
New UEFI or older BIOS, basic install is essentially the same, but settings in BIOS/UEFI or others may make a difference.

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

If you want both new UEFI and older BIOS, you can follow this. It is for a flash drive but same procedure for any drive.
      
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Best not to install any proprietary drivers, but you may need to add nomodeset to boot if one has nVidia.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by sudodus on 2014-06-12
If you avoid proprietary drivers, you can install a system that will work in many computers, but not all.

1. You might need some boot option to run in some computers. Simple.

2. You might need a proprietary driver for graphics or wifi. More complicated, and needs uninstalling afterwards, but possible.

3a. You can run 32-bit code with 32-bit and 64-bit CPUs and BIOS, but only 64-bit code works with UEFI.

3b. You can run 64-bit code with BIOS and UEFI, but not with 32-bit CPUs.

4. But the same code will ***not*** work in PCs (intel/amd) and PowerPCs (old MACs)

-o-

Simplified (for PCs):

A. You can run 32-bit code in most old and middle-aged computers, but not new ones with Windows 8, unless you enter the BIOS/UEFI menus and switch into BIOS alias CSM mode. If you want to extend it to really old computers, you should install Lubuntu into the external drive. This is rather straight-forward and can be done in many ways, including an installed system, multiboot systems and a persistent live system.

B. You can run 64-bit code in most new and middle-aged computers, but not old ones with 32-bit CPUs. I made an installed system for that purpose:
[URL="http://ubuntuforums.org/showthread.php?t=2213631"]
Portable installed system that boots in UEFI as well as in BIOS mode[/URL]

but you can also make a persistent live system from the Ubuntu desktop 64-bit iso file

---

