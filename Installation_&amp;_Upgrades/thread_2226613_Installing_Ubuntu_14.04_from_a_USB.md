---
title: "Installing Ubuntu 14.04 from a USB"
date: 2014-05-28
forum: Installation &amp; Upgrades
---

### Post by Comet220 on 2014-05-28
When they say you can install Ubuntu from a USB drive, do you have to use one of those little USB sticks, or can you use a hard drive?

I'm on a course for my job so I don't have much stuff with me - no USBs, or blank CDs, or DVDs - and I'm dirt poor so I'd rather not get any if I don't have to. But I've been trying to install Ubuntu for days and nothings working. When I try and do the bootable USB thing with my hard drive it all seems to work fine until I have to reboot and Ubuntu doesn't come up at all. I've tried pressing f12 for booting up options or whatever that is but only Windows comes up. I also tried f2 for whatever all those options were, and changed USB to the first thing my laptop looks at but it still didn't work.

When I boot up with Windows and open the wubi.exe and choose the option for when rebooting isn't working it tries to install some sort of boot menu thing but it takes over 24h to install, and ended up failing because it was bigger than 290GB and my laptop doesn't have that much internal storage.

Does anyone know what I'm doing wrong because I swear it shouldn't be this difficult to install Ubuntu.

Also, I don't know anything about programming, or using command line but if you spell out every step of what I need to do I can follow along easily enough.

---

### Post by zemega on 2014-05-28
Are you trying to replace your Windows Installation? What is your Windows version?, 7, 8? What is your Harddisk size? You won't get even a cheap 4GB USB stick? No **external** hard drive either? How about borrowing one from other people? Installation should only take less than two hours. What model is your laptop?

From this discussion below it is possible to install 14.04 using WUBI. You won't have problem with 12.04 as well. Note that using WUBI is greatly discouraged now. The real question now is you harddisk space. Do you have enough space at all? Do remember filling up the harddisk more than 90% of its capacity can lead to hard disk breakdown.
[http://askubuntu.com/questions/449486/windows-installer-for-ubuntu-14-04-lts-onwards](http://askubuntu.com/questions/449486/windows-installer-for-ubuntu-14-04-lts-onwards)

---

### Post by Comet220 on 2014-05-28
I have a Dell Inspiron N5010 and Windows 7. My Hard Disk is 581GB with 290GB free. So it's about half full.

I want to install Ubuntu alongside Windows. If WUBI is discouraged, what is encouraged. I'm not really that against getting a USB or CD but I'm about 25 minutes from the nearest city and I don't have a car anyway.

---

### Post by zemega on 2014-05-28
This sounds like you have the ISO with you and you mount that ISO, then you run the WUBI program right? What you need to do is copy that wubi.exe into your harddrive. Then run the wubi program. this time you will see a diferenct interface. When you click install, the wubi will start downloading the necessary file.
[ATTACH=CONFIG]253536[/ATTACH]
After that click the reboot. It will reboot your laptop into Ubuntu installation. During installation it will download files over the Internet. It will reboot again by itself after that. You will see Windows Boot Manager page. Select Ubuntu. Select Ubuntu again at the purple GRUB page. And I have just installed Ubuntu 14.04 using WUBI.

Edit:
This is the steps for installing Ubuntu 14.04 using wubi. Which I still do not recommend.

---

### Post by LastDino on 2014-05-28
Support for Wubi has been pulled out and it is best to not rely on it with latest operating systems. IMO, buy one USB with 8-16 GB, you wont regret it as it's probably going to be pretty handy. Also, if you've card reader and MicroSD card of 4GB, you can use that as USB too. I do the same. I think your lappy has inbuilt card reader, doesn't it?

---

### Post by Comet220 on 2014-05-28
I don't know what it means to mount an ISO. All I've done is exactly what they say on [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop). I downloaded what they said to download and followed the instructions here [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) on how to make a bootable USB. From there, nothing happened when I restarted my computer so I went into my hard drive and opened wubi and it opened some thing where I could choose demo and full installation, so I did that and it did a bunch of stuff and then it said I needed to reboot, so I did but nothing happened and when I rebooted and pressed f12 for that boot menu thing, only Windows came up. Ubuntu wasn't even an option. So I uninstalled Ubuntu and then did the same thing again but when it said: reboot now, reboot manually, or help me to boot from CD, I chose the last one and that's when it took all night to try installing some boot menu option thing that failed because it filled up my entire C: disk.

Also, you guys keep saying that WUBI is not recommended, but I don't know any other ways of installing Ubuntu. If there's some other way that's easier and more reliable just let me know so I can stop messing around with WUBI because I don't like it either.

---

### Post by MoebusNet on 2014-05-28
Ok, maybe we can discuss a little terminology then get you started. WUBI is a way of running Ubuntu as a program under Windows, just like any other program. It is being phased out and is not what you wanted anyway, if I understand you correctly. What I think you want is what is referred to as a dual-boot system; when you start your computer you will be offered the choice of booting into either Windows or Ubuntu.

The next thing is that when you start your computer, it is booting into Windows on your hard drive first, before it looks for Ubuntu on your USB drive. That is why you are not able to install Ubuntu as you desire.

Quoting from: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
> Booting the Computer from USB

Remove all unneeded USB items, but keep the network cable attached.

Insert the bootable USB flash drive that you just created in your target computer and restart it. Most newer computers can boot from a USB flash drive. If your computer does not automatically do so, you might need to edit the BIOS settings.

Restart your computer, and watch for a message telling you which key to press to enter the BIOS setup. It will usually be one of F1, F2, DEL, ESC or F10. Press this key while your computer is booting to edit your BIOS settings. (On HP Mini Netbooks, they correct key is usually F9.)

Instead of editing BIOS settings, you can chose a boot device from the boot menu. Press the function key to enter the boot menu when your computer is booting. Typically, the boot screen displays which key you need to press. It maybe one of F12, F10. Note: with some motherboards you have to select 'hard disk/USB-HDD0' to choose the USB flash disk. It may work like this because the system sees the USB drive 'a mass storage device' as a hard disk drive, and it should be at the top of the boot order list.

So you need to edit the Boot Order. Depending on your computer, and how your USB key was formatted, you should see an entry for "removable drive" or "USB media". Move this to the top of the list to make the computer attempt to boot from the USB device before booting from the hard disk.

Once you are able to boot Ubuntu from USB, I recommend you try out Ubuntu without installing it to confirm hardware compatibility. Once you are satisfied that Ubuntu will work for you, you can install it by following the instructions at: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

IMPORTANT: Look for the install option that tells you "Install alongside Windows" to keep your Windows OS and your data, otherwise if you install Ubuntu only you will lose your Windows OS and all your data.

As always, back up any data you want to keep. There are only two kinds of people: those who back up their data, and those who wish they had.

---

### Post by Comet220 on 2014-05-29
Yeah I'd already done that. It's all good though, I got a flash drive and seems to be working fine with that. Must have been avn issue trying to use a hard drive.

---

