---
title: "Attempting to create bootable Flash Drive for general use"
date: 2020-08-27
forum: Installation &amp; Upgrades
---

### Post by drew2sea on 2020-08-27
Hello,

I have been off of the Ubuntu wagon for about 3 years and I have the goal in mind of creating a Live, Bootable USB drive that can be used with most computers.  

Where I live macs are more common than PCs (due to the density of software developers in my community).  I have an older Macbook Pro running macOS Catalina.  

I was able to successfully make a bootable installer flash drive, then the trouble starts.  I attempted to use this installer to install desktop Ubuntu 20.04 LTS onto another flash drive.  I set up the installer with custom settings to install the bootloader and the OS on the flash drive.

Disappointment settled in when I could not boot from the flash drive and I got a GRUB bootloader error attempting to describe searching for Ubuntu on the built in SSD (don't want to mess with macOS bc it can cause problems).  I noticed when booting my MacBook today that GRUB was now the default bootloader (I did not intend to use GRUB on my computer), so I typed "exit + 'return'" and was relieved to be greeted by an apple logo and avoid total corruption of my MacBook.

So my questions comes down to these:

1. How can I make a bootable Flash Drive with Ubuntu 20.04 LTS using my MacBook Pro and a handful of flash drives?
2. Can I easily remove GRUB from my MacBook Pro?
3. How can I avoid GRUB from installing itself on additional volumes without my permission?

Right now I'm frustrated and a little bit stuck.

Thank you for reading this

---

### Post by drew2sea on 2020-08-27
I quickly discovered the first issue was due to a boot flag on my main disk left by the pesky Ubuntu installed. I used Gparted to remove the boot flag from my main disk and add it to the flash drive. 

however the grub is still installed on my Mac, presumably using the pesky default behavior of overwriting the recovery partition and the flash drive is not visible to my efi boot loader.

---

### Post by sudodus on 2020-08-27
I think I can help you with item #1, if you are happy with an Ubuntu system without encryption.

You can download a compressed image of an installed Ubuntu system, extract it from compression and then clone the extracted image onto a flash drive. Afterwards you can use gparted to make the installed system use the whole drive.

See these links:

[If you need not encrypt the drive, there is an easy alternative](https://ubuntuforums.org/showthread.php?t=2447539&p=13974203#post13974203)

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Item #2: Sorry, I don't know Mac computers.

Maybe the following tip can help you with item #3: In UEFI mode the Ubuntu installer writes the bootloader (the EFI system partition in this case) to the first drive, which is usually the internal drive, even if you tell it to write the installer to some other drive. A solution is to unplug, disconnect or otherwise disable the internal drive. This is not so difficult in PC computers but I don't know if it is easy or difficult in Mac computers.

**Edit:** An alternative is a persistent live system. If this would be good enough for you, and you want help, please let me know.

---

### Post by dragonfly41 on 2020-08-27
I am not a Mac user (at least now I am on Dell, I was on an old Mac some years past).
Your environment is similar to mine in that I want as much separation as possible between my external USB 3.0 SSD's and internal Dell drive containing Windows 10. To achieve this I use Gparted on a Ubuntu LiveUSB to pre-partition each external USB drive, ensuring that each external drive is self contained with bootable EFI partition (500mbs) at /dev/sdx1 and remainder {/dev/sdx2) ext4 format for Ubuntu mounted at /. Boot flags in EFI .
The final touch is that in lieu of usual GRUB I install rEFInd into /dev/sdx (not the internal drive /dev/sda).  When installing rEFInd you specify where to install and I choose external drive (although it can be placed in the internal drive if you so choose - I gather you do not want it in there). I then go into Dell BIOS boot options and move rEFInd loader at the top of list. This should pickup all drives including Windows 10 or in your case Macbook Pro (in theory). I see every OS in my rEFInd boot GUI and you can customise the theme in refind.conf.

[P.S.] I searched and f[ound this blog referring to Mac and rEFInd]("https://www.ianmaddaus.com/portfolio/refind/"). There must be others.

---

### Post by C.S.Cameron on 2020-08-27
> **sudodus said:**
> I think I can help you with item #1, if you are happy with an Ubuntu system without encryption.

You can download a compressed image of an installed Ubuntu system, extract it from compression and then clone the extracted image onto a flash drive. Afterwards you can use gparted to make the installed system use the whole drive.

[https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz](https://phillw.net/isos/linux-tools/uefi-n-bios/dd_unb_ubuntu-20.04_15GB_2020-06-26.img.xz)

This is what I would try first, The download is only 2GB, But I also have never touched a Mac. My daughter owns one but she will not let me near it.

---

