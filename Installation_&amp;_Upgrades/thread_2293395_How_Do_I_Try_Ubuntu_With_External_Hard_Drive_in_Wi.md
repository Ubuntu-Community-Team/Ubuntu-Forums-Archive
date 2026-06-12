---
title: "How Do I Try Ubuntu With External Hard Drive in Win 8.1?"
date: 2015-09-04
forum: Installation &amp; Upgrades
---

### Post by taurusx5 on 2015-09-04
I got Windows 8.1 (64 bit) and would like to try Ubuntu before I install it. Keep in mind that I DO NOT want to install it just yet. I just want to try it out first. 

So far, I got an external hard drive and downloaded the ISO for Ubuntu (64 bit). How do I boot Ubuntu at boot using an external hard drive?

---

### Post by yancek on 2015-09-04
If your operating system is windows, you would need image burning software and use the burn as image  option to put it on a DVD.  You could also use software to create a bootable flash drive, examples are unetbootin which has a windows version and pendrivelinux which works on windows.  They will be Live CDs which you can then boot and run it to test.  You won't be able to boot an Ubuntu iso from the windows bootloader, at least I know of no way to do that.

---

### Post by Petro Dawg on 2015-09-04
Do you have a high speed connection such as USB3.0 for your external drive?   If not, then you are better off running the live version as explained in the previous post.  If you do have a high speed connection to the external HD you can install the OS directly to it from the install CD or USB.  When I've done that in the past I physically removed the internal HD so that it could not get messed up during installation and then install Ubuntu from the CD or USB with the external drive plugged in.  

After the install, reconnect the original HD.  To boot Ubuntu you may need to change the boot order of devices in your BIOS to check for external drives first.  Of course when the external drive is not present the computer will default to the next device in the boot order list and start up as usual.

---

### Post by taurusx5 on 2015-09-08
> **Petro Dawg said:**
>  To boot Ubuntu you may need to change the boot order of devices in your BIOS to check for external drives first.  Of course when the external drive is not present the computer will default to the next device in the boot order list and start up as usual.

I installed Ubuntu using pendrivelinux on my external hard drive. I also changed the boot order of devices in Windows 8.1 to boot from the external hard drive first. But when I restart my laptop with the external hard drive connected via USB, it boots straight to the desktop instead. Do I need a USB pen drive? What am I doing wrong?

---

### Post by Bucky Ball on 2015-09-08
You don't need to install it to try it at all. Simply boot from the USB/disk and when you get to the options choose 'Try Ubuntu'. You're now trying it running from the USB/disk. :)

This applies for all Ubuntu flavours and other spins and distros.

This post was in the wrong place and I was about to move, but now you have installed and want support with that, I'll leave here and hopefully you can get some help.

First up, boot to Ubuntu and open a terminal. Type, or copy/paste:

```
sudo update-grub
```

Reboot. Do you get a menu of operating systems, Win included? If not, reboot and this time hit the shift key just after the manufacturer splash screen. That should get you to the menu. What is on it? Report back on your progress. You need both drives plugged in.

PS: Please use code tags if posting terminal output. See the last link in my signature for how.

PPS: If you have Ubuntu installed, no, you don't need a USB. USB/disk, makes no difference. What is on them is identical.

---

### Post by yancek on 2015-09-08
The pendrivelinux software is used to create a bootable Linux Live CD on a flash drive which you can use to test and which will include the installer should you choose to do that.  What do you mean by "it boots to Desktop"?  Does it boot to windows?  If it boots to the Ubuntu Desktop, that's what you said you wanted.  You need to explore the options in the BIOS setup to make sure you have the correct device set to first boot priority.  On my machine, there are multiple entries for usb but only one actually boots from usb.

---

### Post by oldfred on 2015-09-08
What brand/model system?
Was Windows pre-installed? Then it is UEFI boot.
Did you install Ubuntu in UEFI mode on external drive or legacy/BIOS/CSM mode?

May be best to see details. You can run from live installer:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by taurusx5 on 2015-09-09
> **yancek said:**
> The pendrivelinux software is used to create a bootable Linux Live CD on a flash drive which you can use to test and which will include the installer should you choose to do that. 

Ok, I'm confused. Is pendrivelinux used to install Ubuntu/linux on a pen drive, or an external disk drive? FYI, I installed it on my external HD, which isnt flash. 

>  What do you mean by "it boots to Desktop"?  Does it boot to windows? 

Yes it boots to Win 8.1 Desktop. 

> You need to explore the options in the BIOS setup to make sure you have the correct device set to first boot priority.

When i go to the BIOS, it states the boot order of devices. I made sure to make external devices to boot up as first priority then HD second. But it doesnt boot to Ubuntu from the external HD. Instead it goes straight to the Win 8.1 Desktop as I said. 

> **oldfred said:**
> 
Did you install Ubuntu in UEFI mode on external drive or legacy/BIOS/CSM mode?

I dont understand your question. But am I supposed to press a button as Win 8.1 boots up while my external HD is connected via USB to my laptop? Why is something so easy becoming so <snip> hard to do?

---

### Post by Bucky Ball on 2015-09-09
Go to your BIOS. It will tell you somewhere whether you are using UEFI or legacy mode. Boot from the install disk, Try Ubuntu, launch gparted at a desktop. See a small 500Mb partition with the boot flag on it?

---

### Post by yancek on 2015-09-09
> Ok, I'm confused. Is pendrivelinux used to install Ubuntu/linux on a pen  drive, or an external disk drive? FYI, I installed it on my external  HD, which isnt flash. 

Yes it is but it should work on an external also.  You will have to create partitions yourself on the external drive to be able to use it for other data.

When you go to the BIOS setup, you will need to check the various options to boot from another drive.  Some computers have multiple entries for usb, some will work to boot and others won't.  When you are in the BIOS setup you need to check the various options to see if there is any mention of UEFI or CSM.  If you have windows 8 pre-installed, it is most likely UEFI.

---

### Post by oldfred on 2015-09-09
I do not know for sure about external hard drives.

My second drive sdb with another install of Ubuntu in UEFI mode overwrote my working installs /EFI/Ubuntu in sda first drive and booted new install by default.

My install to a flash drive sdc did the same, but flash drives only boot from /EFI/Boot/bootx64.efi. So I copied /EFI/ubuntu on sda to /EFI/ubuntu on flash drive & then copied it to /EFI/Boot and renamed grubx64.efi to bootx64.efi. You have to also have the /EFI/ubuntu folder as the version in sda is hard coded to look for /EFI/ubuntu/grub.cfg (maybe other files also?) which is just a tiny configfile to link to the real grub.cfg in your install.

---

### Post by taurusx5 on 2015-09-09
> **Bucky Ball said:**
> Go to your BIOS. It will tell you somewhere whether you are using UEFI or legacy mode. 

Its set at UEFI. But it also gives me the option for Legacy.

> Boot from the install disk, Try Ubuntu, launch gparted at a desktop. 

I cant boot from the disk because I dont have a DVD or CD rom. I got an ultrabook which doesnt have one.

> **yancek said:**
> 
When you go to the BIOS setup, you will need to check the various options to boot from another drive.  Some computers have multiple entries for usb, some will work to boot and others won't.  When you are in the BIOS setup you need to check the various options to see if there is any mention of UEFI or CSM.  If you have windows 8 pre-installed, it is most likely UEFI.

It only gives me 3 entries: Internal Hard Disk, External Devices and Network. There are no sub-headers to these entries. And as I've said in the above post, I got UEFI and it gives me the option to choose Legacy. So what do you think? Should I choose Legacy?

---

### Post by oldfred on 2015-09-09
If you have Secure boot on, you may also have to change a setting in UEFI to allow boot of external devices. 

Best not to use Legacy, but if you do then you have to go into UEFI and turn on/off mode to match your install. Or to boot Windows turn on UEFI, and to boot external turn on Legacy. Best if all installs are UEFI or all installs are BIOS. And if Windows is UEFI then Ubuntu should be UEFI.

If you do not have /EFI/Boot/bootx64.efi, then it will not see the external device for booting.

---

### Post by taurusx5 on 2015-09-14
I got 3 questions:

1) In the BIOS I changed the setting from UEFI to Legacy. Ubuntu was able to boot from the external hard drive. A menu came up for 10 secs. I didn't select anything from it. Then a new screen came up and at the bottom it said the following (attached is a pic showing this):
**"UFS: Unable to mount root fs on unknown-block(2,0)"**

2) My external hard drive is NTFS, not FAT. Could this be why I'm unable to boot Ubuntu from it? 

3) You made this comment:
**"And if Windows is UEFI then Ubuntu should be UEFI."**

I don't understand, how can I make Ubuntu UEFI?

---

### Post by Bucky Ball on 2015-09-14
1. Sounds like you have Ubuntu installed on the external in legacy?
2. You should have free space to install Ubuntu to on the external drive, not full of partitions. If there are no EXT partitions on the external drive, you don't have Ubuntu on it.
3. See 1. What it says. If you have Win in EFI then Ubuntu should be in EFI also. Looks like it is in legacy.

---

### Post by oldfred on 2015-09-14
Ubuntu does not run from NTFS, except with the obsolete wubi. If you tried to install with wubi then it will not work. Last supported wubi was 12.04, but wubi does not work with gpt partitions which are required for UEFI boot.

How you boot installer, UEFI or BIOS is then how it installs. 
But with external drives or second drives you have to use Something Else which requires a bit more work and understanding of partitions. Default install is / (root) and swap. But that goes back years when drives were a lot smaller and dual boot with Windows made a default root relatively small. Now with TB size drives you get to too large root with some default installs. Better then to have / as ext4 with 25GB and /home and/or data partition for rest of space (and some swap). 

Often easier to partition in advance and you should use gpt partitioning as then you can boot Ubuntu in either UEFI or BIOS mode. But UEFI needs the ESP - efi system partition as first partition, and BIOS needs a 1 or 2MB unformatted partition with bios_grub flag. Easier to do with gparted to create partitions, but you still use Something Else to choose which partition is /, /home. Swap automatically found if created in advance.

Post this:
sudo parted -l

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

[       ]("https://help.ubuntu.com/community/UEFI")
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)

    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by taurusx5 on 2015-09-16
> **oldfred said:**
> Ubuntu does not run from NTFS, except with the obsolete wubi. If you tried to install with wubi then it will not work. Last supported wubi was 12.04, but wubi does not work with gpt partitions which are required for UEFI boot. 

I didnt install with Wubi. So youre saying  I got to either install Wubi or convert my external hard drive to a FAT drive? 

No offense but I cant get technical with Ubuntu installs. All I want to do is just try it out. Why is it so extremely difficult to try out Ubuntu?

---

### Post by monkeybrain20122 on 2015-09-16
> **taurusx5 said:**
> I didnt install with Wubi. So youre saying  I got to either install Wubi or convert my external hard drive to a FAT drive? 

No offense but I cant get technical with Ubuntu installs. All I want to do is just try it out. Why is it so extremely difficult to try out Ubuntu?

No, Wubi is dead. If you want to install Ubuntu on an external hd you need to format it to ext4. You can try Ubuntu with a live usb. In that case you need a flash drive formatted to FAT and copy the ISO to it using whatever software to create Linux live usb in Windows e.g unetbootin or [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) This is not a real installation, but good enough for demo and doing simple things like web browsing.

---

### Post by Bucky Ball on 2015-09-16
As I said very early on, you don't need to install Ubuntu to try it. Simply create install media, boot from it, choose the 'Try Ubuntu' option. This will start a 'live' session running from install media, USB or DVD, not the hard drive.

---

