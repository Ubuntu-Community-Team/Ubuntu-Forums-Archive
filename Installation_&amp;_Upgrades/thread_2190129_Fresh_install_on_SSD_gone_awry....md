---
title: "Fresh install on SSD gone awry..."
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by kim3 on 2013-11-25
I have installed windows 7 on my new 128gb SSD...then [COLOR=#000000][FONT=Verdana]I ran the ubuntu 12.04 LTS installer and altered the Windows partition to 85gb. Created a ext4 with mount as / of 35gb. a swap of 8gb, before following on with the install i was asked to make another partition, of at least 1mb, for bios loader or something along those lines. the install process ran through fine...until the completed screen when i had to reset manually, and when i restarted, i found no ubuntu, just straight into windows...

any ideas as to where I have gone wrong and how to get the grub installed to let me choose which OS to use when i boot?[/FONT][/COLOR]

---

### Post by oldfred on 2013-11-25
Windows only boots from gpt partitioned drives with UEFI. And Ubuntu will boot from gpt partitioned drives with UEFI and uses the same efi partition or boots with BIOS boot mode but needs a tiny 1MB unformatted bios_grub partition for grub to install correctly.
It sounds like you installed Ubuntu in BIOS boot mode but have Windows in UEFI boot mode.
You can dual boot but will have to go into UEFI/BIOS and turn on/off UEFI or BIOS/CSM/Legacy boot modes to match install. Not the easiest way to dual boot but can be done.

Boot-Repair can convert a BIOS Ubuntu install to UEFI boot by uninstalling grub-pc (BIOS) and installing grub-efi (UEFI).

From UEFI menu you do need to boot live installer in UEFI boot mode.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by kim3 on 2013-11-26
The first information bootrepair gave me was-
**EFI detected. Please check the options.**

I ran bootrepair and chose reccommended repair and it led me to a screen suggesting I add-
sudo chroot "/mnt/boot-sav/sda4" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda4" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda4" apt-get purge -y --force-yes grub*-common shim-signed
to the terminal and then choose YES to remove all GRUBS...

Next step was to copy 
sudo chroot "/mnt/boot-sav/sda4" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed
into the terminal

I chose not to do anything to the WINefi file...


Finally I reach here>

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/6477357/](http://paste.ubuntu.com/6477357/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!

Now when I hit the power, I boot to the GNU Grub screen with the following options-
Ubuntu Linuc xxxxxx
Ubuntu Recovery
UEFI bootmgfw.efi
Windows Boot UEFI loader
System setup

Windows Boot UEFI loader goes to the dogs. Tries to recover system, but cannot do so.
The UEFO bootmgfw.efi loads Windows perfectly.

Also...when I hit f12 to check boot options i get to the UEFI boot drive selection screen with the following options-
p4- DVDRW
p2 SANDISK 128gb
Windows Boot Manager p2
Ubuntu p2 - sandisk
Ubuntu p2 - sandisk

Seems I have some cleaning up to do, but how???

Perhaps it would be more simple wiping the lot and starting over?? I have no documents saved on either.

---

### Post by oldfred on 2013-11-26
If you get grub menu & Windows works, is it that Ubuntu still does not work?
You show you are booting with the i915 video driver. That usually does not need nomodeset but needs specific boot options but seems to depend on model. 

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

      
 Some other Intel boot options
acpi_osi=Linux  acpi_backlight=vendor
 i915.i915_enable_rc6=1

   Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

---

