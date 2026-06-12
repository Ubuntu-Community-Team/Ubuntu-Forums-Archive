---
title: "Boot to ubuntu only when specific hard drive is selected"
date: 2015-08-30
forum: Installation &amp; Upgrades
---

### Post by souledge121 on 2015-08-30
Let me start off by saying thank you for any advice given

I have two hard drives in my pc, a 500GB SSD which only has windows 10 on it, and a 1TB hardrive that I use for other storage. What I want to do is format the 1TB and partition and install ubuntu on it.
My question is though, when I boot my pc, I want it to boot to windows 10, completely ignoring ubuntu and the grub loader as if I had never installed it on the 2nd hard drive. I only want to boot into ubuntu when I select that
2nd hard drive to boot to from the BIOS, again as if I physically removed the ssd from my pc. Is this possible?

Feel free to ask for clarification if needed.

And I have an MSI z87 G45 motherboard in case that helps

---

### Post by dino99 on 2015-08-30
the boot loader list & show you the possible installed OSs to boot with, then you can choose what you want to boot with.
but when you says 'i want to always boot w10, except when i decide something else: i would say, its either one or the other. But you are the boss onboard and there no pretty geny to know what you thing before booting.

[http://superuser.com/questions/958316/is-it-easier-to-install-ubuntu-on-a-windows-10-machine-or-windows-10-on-a-laptop](http://superuser.com/questions/958316/is-it-easier-to-install-ubuntu-on-a-windows-10-machine-or-windows-10-on-a-laptop)

---

### Post by grahammechanical on 2015-08-30
The answer is, yes.

I have two hard disks with different versions of Ubuntu installed. I also have a USB stick (sdc) with an experimental version of Ubuntu Personal on it. I use the BIOS settings to select which drive to load from. Hard disk sdb is my preferred choice but I can change to sda or sdc.

When you install Ubuntu onto that 1TB (sdb?) disk make sure that the installer does not install the Grub boot loader to the 500GB disk (sda?) or that will over-write the Windows boot loader. 

With Ubuntu installed on the 1TB disk and the BIOS set to load from the 1TB disk you will get a boot menu with options to load Ubuntu or Windows.

With the BIOS set to load from the 500GB disk you will get no option to load Ubuntu but will load straight into Windows.

Regards.

---

### Post by oldfred on 2015-08-30
It is preferred if Windows is booting in UEFI mode that you install Ubuntu in UEFI mode.
Or if Windows is booting in BIOS mode that you install Ubuntu in BIOS boot mode.

You do not absolutely have to have same boot modes, but then can only use UEFI to boot and may have to go into UEFI and turn on/off UEFI/CSM settings.
If same mode you can use one time boot key like f10 or f12, see motherboard manual for correct boot key.

Part of issue may be that UEFI needs gpt partitioning and BIOS needs MBR(msdos) partitioning. 
How are drives partitioned? Are both MBR or both gpt?
Post this:
sudo parted -l

How you boot installer for both Windows & Ubuntu is how it installs. Or if you boot in UEFI mode it installs in UEFI mode. 
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

