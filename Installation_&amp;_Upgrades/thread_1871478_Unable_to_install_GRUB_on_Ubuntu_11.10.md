---
title: "Unable to install GRUB on Ubuntu 11.10"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by L0ngsh0t on 2011-10-29
Hi, I got a new netbook a few days ago, and I thought I'd install Ubuntu on it. I've never touched any Linux OS before. I put the installation files on a USB disk with UNetbootin. This is a fresh install, so there aren't any other OSes or partitions on the hard disk. 
I've set the BIOS to boot from the USB disk, and the UNetbootin menu starts. I choose 'Install' on the UNetbootin menu, and the "purple" Ubuntu installer starts fine. Then I choose to install the OS on the whole hard disk, without partitioning. The installer connects to my wireless network and downloads (?) the necessary files from the Ubuntu server. When it comes to the "Install the GRUB boot loader on a hard disk" stage, it detects that it is the only OS on the disk, and asks to install GRUB to the MBR. I hit 'Yes', and the installer gives me an error message:
 
"Unable to install GRUB in (hd0)
Executing 'grub-install (hd0)' failed.
 
This is a fatal error."
 
If I choose not to install to the MBR, it gives me the option to install GRUB to another drive.
 
On the main menu, there are the options to install the LILO boot loader (I haven't got a clue what that is) or to continue without the boot loader. I don't know what the consequences of choosing these are, so I've decided to leave it for now.
 
Should I continue without GRUB for now, and fix it later? Should I install GRUB to my USB disk (how do I do that)? Have I done something wrong in the install process?
 
I've probably left some info out, so let me know what you need. TIA for any help.

---

### Post by oldfred on 2011-10-29
Do you have a BIOS with a locked MBR. Some do that and you have to change BIOS settings to allow a new boot loader to be installed.

BIOS & disable "Boot Sector Virus Protection"
Other BIOS settings - Security or locked down Boot sector, Bitlocker
core unlocker feature on asus m4a87td usb3 was causing the problem
Disable Quickboot in BIOS

---

### Post by L0ngsh0t on 2011-10-29
Thanks for the reply. I'm on an HP Pavilion dm1 notebook, running a BIOS called InsydeH20 (BIOS Version F.01, Rev. 3.5), which looks lighter than any BIOS I've yet seen. The only security options that are listed are the administrator password and the power-on password. About the most complex thing this BIOS allows me to do is to change my boot order. I don't see any option to enable advanced BIOS configuration.
 
My BIOS is not giving me the ability to fiddle with the MBR. Is there something about this BIOS I'm not getting? Is there a way to enable more advanced options?
 
Any ideas?? :confused:
 
Thanks again for the help.

---

### Post by oldfred on 2011-10-30
Many portables seem to have a minimal BIOS. But new systems are changing to UEFI which has more capability, but is a lot different.

this is a video issue that is reported as a bug on your machine.  Not sure if same configuration as yours. Is BIOS up to date?

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/853315](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/853315)

---

### Post by unisubzero on 2011-10-31
Maybe you could also try to give the installation path for GRUB manually ?
  Something like **/dev/sda** for example.

---

### Post by raja.genupula on 2011-10-31
> **L0ngsh0t said:**
> Hi, I got a new netbook a few days ago, and I thought I'd install Ubuntu on it. I've never touched any Linux OS before. I put the installation files on a USB disk with UNetbootin. This is a fresh install, so there aren't any other OSes or partitions on the hard disk. 
I've set the BIOS to boot from the USB disk, and the UNetbootin menu starts. I choose 'Install' on the UNetbootin menu, and the "purple" Ubuntu installer starts fine. Then I choose to install the OS on the whole hard disk, without partitioning. The installer connects to my wireless network and downloads (?) the necessary files from the Ubuntu server. When it comes to the "Install the GRUB boot loader on a hard disk" stage, it detects that it is the only OS on the disk, and asks to install GRUB to the MBR. I hit 'Yes', and the installer gives me an error message:
 
"Unable to install GRUB in (hd0)
Executing 'grub-install (hd0)' failed.
 
This is a fatal error."
 
If I choose not to install to the MBR, it gives me the option to install GRUB to another drive.
 
On the main menu, there are the options to install the LILO boot loader (I haven't got a clue what that is) or to continue without the boot loader. I don't know what the consequences of choosing these are, so I've decided to leave it for now.
 
Should I continue without GRUB for now, and fix it later? Should I install GRUB to my USB disk (how do I do that)? Have I done something wrong in the install process?
 
I've probably left some info out, so let me know what you need. TIA for any help.

you can install the grub to your usb by using this command

```
sudo dpkg-reconfigure grub-pc
```

then install the grub to your USB in the process ....

all the best.

---

### Post by L0ngsh0t on 2011-11-01
> **raja.genupula said:**
> you can install the grub to your usb by using this command
 
```
sudo dpkg-reconfigure grub-pc
```
 
then install the grub to your USB in the process ....
 
all the best.
 
It worked! Thanks a bunch for your help everyone. :D

---

### Post by raja.genupula on 2011-11-01
> **L0ngsh0t said:**
> It worked! Thanks a bunch for your help everyone. :D

Hi man
      Its really good news that you have solved your issue.Please mark the thread as solved from thread tools.

---

