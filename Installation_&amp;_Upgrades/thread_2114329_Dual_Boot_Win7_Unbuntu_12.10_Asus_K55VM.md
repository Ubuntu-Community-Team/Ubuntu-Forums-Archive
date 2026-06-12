---
title: "Dual Boot Win7 Unbuntu 12.10 Asus K55VM"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by ScottChak on 2013-02-09
Hello All,

Here is the situation :
 - was using mainly Ubuntu for a long time on my old PC (it was 5+ years old with Vista, so too slow and frustrating to use Vista),
 - changed PC in august 2012 (an Asus K55VM, if this relevant to up coming question),
 - tried installing Ubuntu in august, didn't know I had an Uefi system and ended up completely screwing up my bootloader,
 - after a send back to factory to get the PC reset, decided against going a second round until the issue of Uefi firmware was solved.

So here I am, trying to install a Ubuntu 12.10 dual-boot. Where I went wrong last time was running easyBCD in windows and trying to write an MBR over the actual bootloader. So not going to do that again ...

Read through this tutorial:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and "Installing Ubuntu Quickly and Easily via Trial and Error" section was applied, using Lili to make a USB key to boot.

Don't have secure boot, so that wasn't an issued.

Taken a bad photo off my boot options in the bios (can send by email if required). To sum up :
 - have the option to turn of or on the Uefi boot,
 - my usb key is uefi boot, with a [UEFI: ...] type boot option, and will only boot when Uefi boot is enabled in bios. So I assume that the installation was done with a UEFI boot,
 - two other options (from HDD) that are [P0: ...] and [P2: ...] in boot order. These will load when Uefi is disabled, so I assume these are Legacy Boot.

Ran bootrepair, twice, as recommended : 
 - [http://paste.ubuntu.com/1605674](http://paste.ubuntu.com/1605674)
 - [http://paste.ubuntu.com/1631073](http://paste.ubuntu.com/1631073)
and still boot straight into windows on startup when usb key is not plugged in to computer.

Judging from what I gathered from reading the above tutorial (see link), and the evidence of my computer's boot options, I think this isn't working because I have Ubuntu installed as Uefi, but since my windows is Legacy, i'm not getting any updated bootloader.

That's all the information that I have that seems relevant. I hope this will be enough to come up with a solution.

---

### Post by oldfred on 2013-02-10
Even if your system is UEFI/BIOS both Windows & Ubuntu are in BIOS mode.

But you still have the Windows boot loader in the MBR. Boot-Repair installed grub to the MBR and it returned no error,  code 0 is that it worked. But it looks like it did not work.

I might try manual install from liveCD.

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub
    
It is showing a sdb, it that another flash drive or small SSD that came with system. I might just unplug that when reinstalling or first boot. Sometimes extra hardware both flash or DVD can confuse booting.

---

### Post by ScottChak on 2013-02-10
Hello again,

Does "BIOS mode" mean the same thing as "Legacy" ? And by reading the boot-repair records, you have deduced that Ubuntu was installed in BIOS mode (just like my Win7)?

The sdb is the USB key that I made with LiLi USB creator to make to boot the installer. I have always installed Ubuntu this way, and I didn't have a problem during installation.

Right now, there is no way for me to boot into the the Ubuntu installed on my PC, all I can do is boot into the Ubuntu installed to my USB key. I will however try to update the bootloader of my usb key, this might allow me to boot the HDD Ubuntu through the boot loader on the USB.

---

### Post by oldfred on 2013-02-10
Some systems call it legacy, BIOS, CSM, AHCI and maybe others. It just is not UEFI mode then.

IF you have UEFI, you would have gpt partitioning not MBR(msdos) and one of the first partitions would be an efi partition.

You may be able to use Supergrub to bypass your grub install and just boot kernels. Install looks ok from BootInfo.  Then once in install you can do a full reinstall of grub2.

If you can boot into install you do not have to chroot. If "simple" mount & install commands posted above do not work we often have to use the chroot from a liveCD.
       chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Also once booted, you may want to run this:
       
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
    The basic Supergrub is a small download that just boots any system with a working kernel.

---

