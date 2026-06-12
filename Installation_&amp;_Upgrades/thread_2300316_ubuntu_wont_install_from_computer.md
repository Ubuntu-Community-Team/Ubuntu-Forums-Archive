---
title: "ubuntu wont install from computer"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by dellboy56 on 2015-10-25
hi guys my computer is a HP pavilion 15 right I am choosing to remove windows 8.1 this was preinstalled OS because its slow on my computer I have decided to migrate to Ubuntu problem is that I need help because I do stuff with the bios and uefi I don't now how it works for my computer but I got my cd in and I boot it with cd etc and it doesn't say anything about your computer has currently windows 8.1 it only shows this computer has windows boot manger inside of it and I don't want to do that so I would love if you guys could help me with this problem of mine cause I wanna use Ubuntu im ran it in virtualbox im happy with it and I think im upto now wanting to installing it on my laptop NO DUAL BOOT just Ubuntu on it and that's it so yeah once again im tried from some bios thing and uefi idk what steps you need to do for my computer to get it running and installing please reply because I want to install as soon as possible!

---

### Post by hansmc2 on 2015-10-25
What version of ubuntu are you trying to install? [http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop) has pictures of the installation process for 14.04. Did you see the "Welcome" screen where you can choose to 'try' or 'install' Ubuntu? Did you get to the "installation type" screen like is seen in step four of this example? If so you should be able to choose to replace windows with Ubuntu.

**Back up any files in windows that you want to save! Installing Ubuntu over the top of windows will erase all your files!**

---

### Post by dellboy56 on 2015-10-25
I'm trying to install Ubuntu 14.04 when I get to the installation it says it has Windows boot manger it doesn't have options to replace or remove Windows 8.1 it has none of that so what am I doing wrong

---

### Post by hansmc2 on 2015-10-25
Since your computer has windows 8.1 you will need to disable Secure Boot and enable Legacy boot support. You will also need to set your computer to boot from the CD drive. All my computers are older so I do not have to turn off the secure boot, but [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD) has one example of how to do it. If you got all these steps done correctly you should see a screen like this after starting up your computer (and waiting a little).
[IMG]http://assets.ubuntu.com/sites/ubuntu/1546/u/img/download/desktop/install-ubuntu-desktop/image-installdesktoplongtermsupport-1.jpg[/IMG]

Googled this "HP pavilion 15 turn off secure boot" and found this maybe helpful link:
[http://support.hp.com/us-en/document/c03736054](http://support.hp.com/us-en/document/c03736054)

---

### Post by Bucky Ball on 2015-10-25
You will also need to boot into Windows and switch off hibernation. If you don't do this, the installer can not access the drive.

Are you sure you have created the install media correctly? When you boot from the disk, you should be getting a list of options like 'Try Ubuntu' 'Install Ubuntu' etc. If you are not, something is a amiss and we should start there (as it sees nothing bootable in the machine apart from the Windows disk if it will not boot from the disk you have created and you have the BIOS set to boot from it).

Here's a few links that may help. The first couple show how to create an install USB, the next two how to install and burn a DVD. Just out of curiousity, where are you downloading the Ubuntu ISO from?

UNetbootin:
[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Universal USB Installer:
[www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Install Ubuntu 14.04.3
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Burn DVD:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by dellboy56 on 2015-10-25
I have created the cd with desktop burning gadget I can see try Ubuntu and install Ubuntu etc problems is I click install etc and it doesn't detect Windows 8.1 is installed and the 4 options it displays Windows boot manger would you like to replace etc but no Windows 8.1

Ok so my computer still isn't coping with what you guys said it still tells me it has Windows boot manager on it but I'm tried that page that told me to set my bios to the right settings which I'm done but still I am given the this computer currently has Windows boot manger

---

### Post by Bucky Ball on 2015-10-25
If it's not seeing Windows then you probably haven't booted into Windows and switched off hibernation and fast startup (called something like that) then shutdown Windows completely (not hibernated it). Therefore, when you close Windows, you don't actually unmount and shut the partitions, therefore the Ubuntu installer doesn't see the Win partition and you don't see Windows. 

Two things. A regular Ubuntu ISO installer doesn't fit on a CD, so do you mean DVD? Secondly, boot from the CD/DVD, 'Try Ubuntu', when you're at a desktop launch Gparted. Does that show the Windows partitions and everything else on there as they should be? Does the Win partition have a lock symbol or anything else next to it?

---

### Post by dellboy56 on 2015-10-25
Hibernation was already switched off I made my bios/uefi to boot from the disk when I boot my computer up I am presented with the gnu grub loader and lists the 4 things not sure about fast boot is that in the Windows power options or something?

I just booted into Ubuntu again no desktop and it says It still has Windows boot manager want would you like to do with it I'll send u photos

See attached pics.

My bios setup

---

### Post by Bucky Ball on 2015-10-25
Please attach large pics using 'Adv Reply' and the paperclip icon. Thanks.

---

### Post by dellboy56 on 2015-10-25
That's largest I can go

Surely I'm doing something wrong right? :(

---

### Post by Bucky Ball on 2015-10-25
Doesn't look like it. You have two choices as you don't need a dual-boot. Choose 'Erase disk and install Ubuntu' or choose 'Something Else', wipe the drive and setup Ubuntu to install how you like. 

You'll find some help with the Something Else install [here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352").

Are you trying to install the newly released Wily 15.10 by any chance? Be aware interim releases need to be upgraded every six months. 14.04 LTS is the current support long-term support release and is support until April 2019. It can be upgraded to the next LTS, 16.04 LTS directly via Software Updater next April. That will be supported until 2021.

---

### Post by dellboy56 on 2015-10-25
So if that comes up with the Windows boot manager does that mean that including Windows 8.1 is all gone then so I can safely assure my computer just installs Ubuntu and doesn't corrupt

---

### Post by Bucky Ball on 2015-10-25
The install should wipe that. Please re-read my last post as I have edited, but if in doubt, wipe all partitions from the drive using Gparted in 'Try Ubuntu' or in Something Else window. 

Are you intending to install in UEFI or regular BIOS mode? This could be some MS/manufacturer UEFI magic that is causing issues, but I'd just wipe the drive and see how you go. Let Ubuntu 'Erase disk and install Ubuntu' as a test and see what happens. 

Goes without saying, but I'll say it: make sure to back up anything you don't want to lose prior to doing this. :)

Good luck.

---

### Post by dellboy56 on 2015-10-25
Well idk I'm not sure if my bios can support both I might go uefi because that is what latest computers now come equip with I suppose

---

### Post by Bucky Ball on 2015-10-25
You're too fast for me. :)

You probably didn't get all of my last post #18 either. :)

Yep, UEFI, fine. If you let Ubuntu wipe and install automagically it should take care of that. If you choose the 'Something Else' option there are a few tricks to creating the UEFI partition. Just create a partition around 500mb and make it FAT32 filesystem. The install will pick that up as the EFI partition and use it accordingly ... theoretically.

---

### Post by dellboy56 on 2015-10-25
Ok so if I click on my f9 boot device options it gives me a option right I boot into it this one says no operating system on it the other one says Windows boot manager on it in Uefi

I'm double checking this because my internal hard drive picks up no operating system while the uefi one picks up a boot manager for some reason so I'm really stuck what to do

Bucky I clicked on the that had the Windows boot manager I'm installing it now hopefully it doesn't stuff up or anything cause my laptop has no warranty and I did what you wanted me to is that I install from the Windows boot manager I clicked Earle I didn't click the one with no operating system I clicked the one with the boot manager

---

### Post by yancek on 2015-10-25
> I'm double checking this because my internal hard drive picks up no  operating system while the uefi one picks up a boot manager for some  reason so I'm really stuck what to do


You still have windows installed which is why it still picks up the windows boot manager.  Until you install and erase everything you are going to see that on boot.  You do know that this will overwrite any data on your windows partitions.  I don't know what you're trying to say in the last paragraph.  You need to boot from the DVD or flash drive with Ubuntu on it.  You should see an option to use EFI or CSM/Legacy boot.

---

