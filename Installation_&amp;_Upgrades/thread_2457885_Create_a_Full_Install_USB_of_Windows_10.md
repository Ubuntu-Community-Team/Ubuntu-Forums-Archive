---
title: "Create a Full Install USB of Windows 10?"
date: 2021-02-11
forum: Installation &amp; Upgrades
---

### Post by username2758 on 2021-02-11
Hey,

So I have just successfully created a full install USB of Ubuntu using mkusb software.

Now is it possible to do the same with Windows 10?

Thanks!

---

### Post by CelticWarrior on 2021-02-11
If a full Windows 10 installation has been imaged to a file that then is used the same way you just did then yes, it's possible. The licensing aspect of it is an entirely different issue though. A OEM licensed Windows can only be used in the same machine it was bundled with, it makes no difference whether it is a image recovery or a new installation; a retails license OTOH can be used in a different machine provided that only one machine is using the same license at the same time.

---

### Post by grahammechanical on 2021-02-11
I was able to obtain officially both a Windows 8 and a Windows 10 preview ISO image. I never got around to installing the Windows 10 edition but If I remember correctly with Windows 8 we first need a Windows type partition. We use Windows in a live session to create that.

In the past Windows had to be the first OS on the drive. I guess that might still be the standard procedure. If we have two drives then disconnect the Ubuntu drive. It will prevent the Windows installer from messing up the Ubuntu boot menu.

Regards

---

### Post by yancek on 2021-02-11
If you want to put the windows install iso on a usb, there are a number of sites which explain it such as the 2 links below:

[https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)

[https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu](https://www.linuxbabe.com/ubuntu/easily-create-windows-10-bootable-usb-ubuntu)

---

### Post by crip720 on 2021-02-11
Think you can only make a bootable Windows USB from Linux with either mkusb or woeusb, do not think any other ways will work for windows.  If computer came with Win 10, can replace with same version.  Can also goolge for getting Win 10 for legally for free.

---

### Post by C.S.Cameron on 2021-02-12
Do you want to create a USB that will run the Windows 10 operating system from USB?
Or do you want to create a USB that can be used to install Windows to an internal drive?

If you want to run Windows from USB you will need to create a **Windows-to-Go** drive.

The only way I know to do this from within Linux is to clone an existing Windows-to-Go drive.

From within Windows a WTG drive can be created using either Rufus or Universal USB Installer.

See attached picture for settings, Use Partition Scheme to select BIOS or UEFI install mode.

If you want to create a USB from inside Linux, that can be used to install Windows to an internal drive, you can boot the Windows ISO's contents using GRUB2, or make an installer USB using mkusb-plug, mkusb-dus, Ventoy or woeusb. I have not managed to get WoeUSB working for a few years now.

For the first time user I would recommend **mkusb-plug**. It has a number of fail-safes to prevent making any errors. 

mkusb-plug comes bundled in the mkusb suite, which you already have.

Edit: I should mention that the WTG creation process can be very slow, plan on it running overnight. The Target USB type can also make a big difference in how fast Windows will operate. I think it should run okay on an SSD.

I have managed to create a dual boot USB flash drive making a Full install of Ubuntu after installing Windows-to-Go. Ubuntu's GRUB will boot WTG as long as Ubuntu and WTG are installed in the same BIOS/UEFI mode.

---

### Post by chrischang2021 on 2021-02-12
It's possible to build up Microsoft operation system booting from USB . But run slowly. Suggest you use USB 3.0 or up

---

### Post by CelticWarrior on 2021-02-12
> **chrischang2021 said:**
> It's possible to build up Microsoft operation system booting from USB . 
No, it isn't, unless using the Windows-to-Go feature. Not available for Home edition.

---

### Post by C.S.Cameron on 2021-02-12
> **CelticWarrior said:**
> No, it isn't, unless using the Windows-to-Go feature. Not available for Home edition.

WTG works with Windows 10 Enterprise and Windows 10 Education versions.

---

### Post by username2758 on 2021-02-12
Okay guys, I have many questions now.

**@CelticWarrior**

Yes, this computer comes with an OEM license of Windows 10 Pro, and I plan to try and run some Windows version completely from USB on this very computer.

How do I create an image of Windows? Can I use Microsoft's backup tool to create such image to be used with Rufus?

In other words, do I need to create an image of my working Windows 10 Pro or download an image of Windows somewhere?

**@C.S.Cameron**

Yes, I want to run Windows completely from USB.

I didn't know about "Windows To Go" existence, I still don't know what it is exactly.

Upon quick search on Google I read it only supports Windows versions 8.1, 8.1 Enterprise, 10 Education and 10 Enterprise.

I have an OEM license of Windows 10 Pro with this computer, so I don't think it will work?

Also I've found an article that says this procedure only works with "Windows To Go Certified USB stick". True? ([https://www.onmsft.com/how-to/create-windows-go-usb-drive-running-windows-10](https://www.onmsft.com/how-to/create-windows-go-usb-drive-running-windows-10))

My main goal is to run Windows 10 Pro off of USB for testing purposes (avoid having to format Windows because of viruses and reduce wear-level on my primary M.2. SSD), meaning I'd also want to install some games on it eventually, if possible. Can Windows 10 Enterprise install games too? I hope it's not very different from Windows 10 Pro which I am more familiar with. I don't expect Windows To Go to have excellent performance, just be able to install applications and see if they are working or not - if it is virus or not.

---

### Post by yancek on 2021-02-12
> Yes, I want to run Windows completely from USB.
 

Windows is designed by microsoft not to install to a USB and the windows installer will give you an error message if you try and inform you that it will not proceed.   An OEM license for windows is tied specifically to the hardware. I'd suggest reading some of the links posted regarding windows to go before trying it.  Getting a working windows on a USB is not going to be a simple task as microsoft has done whatever it could to prevent this for obvious reasons.

---

### Post by chrischang2021 on 2021-02-12
CelticWarrior and C.S.Cameron thanks your corrected . I can't remember what kind of version I tried and run it by USB . I just did for   funny and feasible . Because it can't as faster as HD or inside store. &#128514;

---

### Post by C.S.Cameron on 2021-02-12
> **yancek said:**
> Windows is designed by microsoft not to install to a USB and the windows installer will give you an error message if you try and inform you that it will not proceed.   An OEM license for windows is tied specifically to the hardware. I'd suggest reading some of the links posted regarding windows to go before trying it.  Getting a working windows on a USB is not going to be a simple task as microsoft has done whatever it could to prevent this for obvious reasons.

yancek: 

Your information is obsolete.

See:

[https://docs.microsoft.com/en-us/windows/deployment/planning/windows-to-go-overview](https://docs.microsoft.com/en-us/windows/deployment/planning/windows-to-go-overview)

I know for a fact that it works.

---

### Post by C.S.Cameron on 2021-02-12
> **username2758 said:**
> 

**@C.S.Cameron**

Yes, I want to run Windows completely from USB.

I didn't know about "Windows To Go" existence, I still don't know what it is exactly.

Upon quick search on Google I read it only supports Windows versions 8.1, 8.1 Enterprise, 10 Education and 10 Enterprise.

I have an OEM license of Windows 10 Pro with this computer, so I don't think it will work?

Also I've found an article that says this procedure only works with "Windows To Go Certified USB stick". True? ([https://www.onmsft.com/how-to/create-windows-go-usb-drive-running-windows-10](https://www.onmsft.com/how-to/create-windows-go-usb-drive-running-windows-10))

My main goal is to run Windows 10 Pro off of USB for testing purposes (avoid having to format Windows because of viruses and reduce wear-level on my primary M.2. SSD), meaning I'd also want to install some games on it eventually, if possible. Can Windows 10 Enterprise install games too? I hope it's not very different from Windows 10 Pro which I am more familiar with. I don't expect Windows To Go to have excellent performance, just be able to install applications and see if they are working or not - if it is virus or not.

I have installed WTG half a dozen times to prove to myself that it works.
I used Windows 10 1909 ISO that I downloaded from the Microsoft site.
I installed it using Rufus with Enterprise version selected. (The computer has Windows 10 Pro registered).
First install was to a Kingston USB3 flash drive. It booted, but was too slow to be useful.
Next it was installed to a Lexar S25 64GB USB 3.0, (All plastic). The install worked well and it was quite usable. I managed to install and run Autocad.
Eventually I tried changing the wallpaper and I got a notice that I would need to register the OS to do so, but it continued to run with a permanent notice in the lower right corner of the screen.
I made an image file, (.img), of the drive using Gnome-Disks and have flashed the image to multiple disks as proof of concept. It seems to boot on anything USB3, even in USB2 ports, but speed is a factor on some devices.
I do not have a spare external SSD or HDD with me to try it on. Flashing it overwrites everything on the drive.
If the OS will run Autocad, it should run games. You will likely not notice a difference between Pro and Enterprise.
As I mentioned before I was able to dual boot the drive after installing Ubuntu on it. WTG needs to be installed before Ubuntu.
If you give it a try, please let us know how it works for you.

Microsoft says that WTG was removed from the May 2020 release of Windows 10, but it is hard to trust Microsoft.

---

### Post by username2758 on 2021-02-13
> **C.S.Cameron said:**
> I have installed WTG half a dozen times to prove to myself that it works.
I used Windows 10 1909 ISO that I downloaded from the Microsoft site.
I installed it using Rufus with Enterprise version selected. (The computer has Windows 10 Pro registered).
First install was to a Kingston USB3 flash drive. It booted, but was too slow to be useful.
Next it was installed to a Lexar S25 64GB USB 3.0, (All plastic). The install worked well and it was quite usable. I managed to install and run Autocad.
Eventually I tried changing the wallpaper and I got a notice that I would need to register the OS to do so, but it continued to run with a permanent notice in the lower right corner of the screen.
I made an image file, (.img), of the drive using Gnome-Disks and have flashed the image to multiple disks as proof of concept. It seems to boot on anything USB3, even in USB2 ports, but speed is a factor on some devices.
I do not have a spare external SSD or HDD with me to try it on. Flashing it overwrites everything on the drive.
If the OS will run Autocad, it should run games. You will likely not notice a difference between Pro and Enterprise.
As I mentioned before I was able to dual boot the drive after installing Ubuntu on it. WTG needs to be installed before Ubuntu.
If you give it a try, please let us know how it works for you.

Microsoft says that WTG was removed from the May 2020 release of Windows 10, but it is hard to trust Microsoft.
Thanks again!

I have finally found an available link for download of Windows 10 1909.iso because the official Microsoft website will force me to download the latest iteration no matter what. ([https://www.itechtics.com/windows-10-1909/](https://www.itechtics.com/windows-10-1909/))

So far so good!

I will give it a try later on today and give feedback!

(If it works with version 1909, then I will have a try again with an updated version of Windows afterwards too).

---

### Post by yancek on 2021-02-13
>  Your information is obsolete.

No, it isn't.  My post stated spedifically that "the windows installer will give you an error message if you try and inform you that it will not proceed".  You go on to talk about windows to go which is secondary software and NOT related to the windows installer.  We're comparing apples and oranges here.  Also, installing and using multiple versions of windows would violate the licensing agreement users agree to when they install and use windows so you would need multiple licenses to have windows on multiple drives.

---

### Post by C.S.Cameron on 2021-02-13
> **yancek said:**
> No, it isn't.  My post stated spedifically that "the windows installer will give you an error message if you try and inform you that it will not proceed".  You go on to talk about windows to go which is secondary software and NOT related to the windows installer.  We're comparing apples and oranges here.  Also, installing and using multiple versions of windows would violate the licensing agreement users agree to when they install and use windows so you would need multiple licenses to have windows on multiple drives.

As far as I can see Windows-to-Go is Windows and it works on USB and it is authorized by Microsoft.

---

### Post by username2758 on 2021-02-13
Hey guys!

So I am trying it out at this very moment, and I have got some questions!

Rufus is currently flashing the "Win10_1909_English_x64.iso" image at this moment as we speak, but it did not give me the option to select Windows 10 Enterprise version. After clicking "Start" in Rufus, a list of Windows versions was shown to me, including Windows 10 Pro which is the one I am trying out right now since I have a license for. Do you think it will work? I made sure to select "Windows To Go" in Rufus, and it still gave me the option to flash the Windows 10 Pro version.

Also, just out of curiosity, the first time I opened Rufus it did not list my 120GB USB SSD drive. After fiddling a little bit, I checked the box that says "List USB Hard Drives" and my 120GB SSD finally showed up. But the description of such options says "USE AT YOUR OWN RISK". Why would that be? Is this procedure risky by any means? If so, then why?

---

### Post by username2758 on 2021-02-13
Heeey, it works! I can't believe it! (:

I was just finishing up the installation process, which went very quickly by the way!

So I managed to install Windows 10 Pro on a USB 120GB SSD (SATA-3) that's more than 5 years old attached to a simple Orico docking station, and on USB3.0 the performance is pretty decent, at least much better than a 1TB 2.5" 7200RPM HDD (see attachment). All AMD drivers for this mini-pc are working fine, and the best part is it recognized the OEM license automatically too! Windows is activated! :D

Now this is going to be my primary testing device, I kind of missed Windows. I sure am going to format this one like hell lol!

I wonder if USB3.0 pendrives will have decent performance running Windows 10 Pro too? I mean if it can generate almost the same read and write speeds as a conventional 3.5" 7200RPM HDD, I will start buying those! But is it likely though? Do USB3.0 pendrives also have cache? I'm thinking about buying high-speed pendrives for Ubuntu as well!

---

### Post by kurt18947 on 2021-02-13
There are some pretty fast USB flash drives out, Sandisk Extreme is one I remember though that's been several years ago. they won't be the cheapest things going though.

---

### Post by C.S.Cameron on 2021-02-13
> **username2758 said:**
> Hey guys!

So I am trying it out at this very moment, and I have got some questions!

It sounds like you have already answered your own questions, congratulations.
It is great news that it worked well with a USB SSD, I figured that it would. 

It also sounds like it is much faster installing to SSD than it was to my flash drives.

The facts about not needing special Microsoft flash drives and it working with Pro version, just go to show that you still can't trust Microsoft. I would not be surprised if WTG also works on the current release of Win 10.

Please keep us informed about your experiments with fast pendrives. So far I see widely varying operating speeds using different pendrives.

> **username2758 said:**
> Is this procedure risky by any means? If so, then why?

For example I used the Rufus hard drive option once and forgot to turn it off afterward. I ended up overwriting my 4TB external drive that contained a copy of almost every Black and White Public Domain movie ever made, with an install of Kubuntu.

---

### Post by username2758 on 2021-02-14
> **kurt18947 said:**
> There are some pretty fast USB flash drives out, Sandisk Extreme is one I remember though that's been several years ago. they won't be the cheapest things going though.
Thanks for the recommendation!

Do you know if Sandisk Extreme has an internal cache? Also, are there any other models of pendrives you'd recommend?

> **C.S.Cameron said:**
> It sounds like you have already answered your own questions, congratulations.
It is great news that it worked well with a USB SSD, I figured that it would. 

It also sounds like it is much faster installing to SSD than it was to my flash drives.

The facts about not needing special Microsoft flash drives and it  working with Pro version, just go to show that you still can't trust  Microsoft. I would not be surprised if WTG also works on the current  release of Win 10.

Please keep us informed about your experiments with fast pendrives. So  far I see widely varying operating speeds using different  pendrives.
I will try, but first I need to figure out which  pendrives currently available in the market have internal cache (if at  all). Does anybody know?

Also, I have a question regarding drivers and Windows 10 on USB. I see that all the drivers for my hardware was installed. Due to the portable nature of Windows To Go, what happens if I connect this USB SSD to a different motherboard? Will it run Windows 10 Pro ok? Should I delete proprietary drivers if I am going to run this USB SSD on different machines as well? I remember you recommending not to install proprietary drivers on Ubuntu for this reason.

---

### Post by C.S.Cameron on 2021-02-14
I have only had a chance to try my WTG drive on three different machines and did not need proprietary drivers for any of them. One of the machines has a Nvidia Quadro card, but that machine works okay with Ubuntu USB installs also. Nowadays are not the best of times to drop by someones house and ask if it is okay to experiment on their computer.

This is the flash drive that so far has worked best for me. It is cheap all plastic design: [https://www.amazon.sg/Lexar-JumpDrive-64GB-Flash-Drive/dp/B00S5V63H0](https://www.amazon.sg/Lexar-JumpDrive-64GB-Flash-Drive/dp/B00S5V63H0)

---

### Post by username2758 on 2021-02-15
> **C.S.Cameron said:**
> I have only had a chance to try my WTG drive on three different machines and did not need proprietary drivers for any of them. One of the machines has a Nvidia Quadro card, but that machine works okay with Ubuntu USB installs also. Nowadays are not the best of times to drop by someones house and ask if it is okay to experiment on their computer.

This is the flash drive that so far has worked best for me. It is cheap all plastic design: [https://www.amazon.sg/Lexar-JumpDrive-64GB-Flash-Drive/dp/B00S5V63H0](https://www.amazon.sg/Lexar-JumpDrive-64GB-Flash-Drive/dp/B00S5V63H0)
Yes, Windows started updating and installing proprietary drivers automatically upon first boot. It didn't even give me the choice not to install the drivers.

 But even if proprietary drivers are installed, will this USB SSD boot properly if connected to a different motherboard? Or should I uninstall proprietary drivers first before trying it on different mobos?

And thank you for the pendrive suggestion. Sandisk Extreme and Lexar S25 are on my list.

---

### Post by C.S.Cameron on 2021-02-15
Perhaps wait and see if WTG grabs new drivers automatically when plugged into a new computer. See if it swaps new drivers for the old.

Thank you for sharing your findings.

---

