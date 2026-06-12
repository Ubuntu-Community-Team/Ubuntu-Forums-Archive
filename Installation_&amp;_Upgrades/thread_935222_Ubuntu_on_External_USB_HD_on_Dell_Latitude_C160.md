---
title: "Ubuntu on External USB HD on Dell Latitude C160"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by ZeroVerteX on 2008-10-01
I have a Dell Latitude C160. It's an older laptop that does not have built-in support for booting to USB devices. I have an internal hard drive with Windows XP. I would like to load Ubuntu on the external HD for casual use but I have to have XP for daily work tasks. If I install it this way, (a) will GRUB see that USB drive and sucessfully boot to the drive without the BIOS support for booting to USB and (b) will I still be able to boot to the internal HD *without* the USB drive hooked up?

---

### Post by Piraja on 2008-10-01
I hope some Ubuntero corrects me if I'm making a mistake, but I think the answers to your questions are pretty simple, even for an inexperienced non-technical user like me. 

(a) Unfortunately you cannot boot to an external USB device if your BIOS does not support USB boot. (See the link below* for a way to use Ubuntu from within Windows even in machines that do not have the USB boot option: Virtual Machine Emulation.)

(b) That said, let us presume that you will some day try the external USB HDD install with some other machine. The answer to your second question is that since you should install Grub on your external drive's MBR, it will not affect the Windows' MBR (Master Boot Record) on the internal drive when the USB drive is unplugged. Windows knows nothing of the external drive's Grub when you boot without the USB drive. When you re-plug the USB device (assuming your BIOS allows for USB boot and is set so that USB boot precedes the internal HDD in the boot order) you should see the Grub menu again and be able to choose whether to boot Linux or Windows.**

* It might be worth your while to check out [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) and especially [Virtual Machine Emulation Category]("http://www.pendrivelinux.com/category/virtual-machine/"). Haven't tried it myself yet, but sooner or later will.

** **Edit**: I re-read your post and I'm no longer sure I understood your questions correctly. You ask (a) whether "GRUB [will] see that USB drive and sucessfully boot to the drive without the BIOS support for booting to USB", but Grub must be installed on the USB drive, not the internal drive's MBR. I think this is very important when you want to install Ubuntu on your external device and not build a dual-boot system on a single hard disk drive. This already implies the answer to the second question (b), but unfortunately the lack of USB boot option in the BIOS will prevent you from using the external device as a boot device.

---

### Post by govee on 2008-10-02
I am going through this right now on an older Compaq that does not have a boot from USB option as well and I think what needs to be clarified is that you are not using a USB flash, but a USB hard drive. 
I recently was given a couple of Zunes that were dead and I harvested the HDDs from them. Nice littler 1.5" 30 GB hard drives. I bought some cases of ebay and started to try to load ubuntu. I found that in my Bios the USB HDD shows up in the boot menu as a second HDD, not a removeable device. I loaded the memtest that also sets up the HDD as bootable. I went into the Bios and moved the USB HDD up in the order of available HDDs (actual internal is now second) and rebooted. The USB HDD then was used and booted and ran the memtest sucessfully. I rebooted again and removed the USB HDD and a normal boot of the Internal HDD executed.

What might work for you is boot from the Ubnuntu CD with both HDD's installed (I kept getting a no OS failure if I removed the internal HDD)and install Ubuntu to the USB Drive. During the install you will be asked where to install the OS. Mine showed the Internal as HD0 (or A, can't remember) and the USB HDD as SDA. I selected the SDA and proceeded. On the last setup screen there is an "advanced" button. Press that and change the location where the "MBR" is going to be stored as mine was defaulted to the Intenal and I beleive you want that on your USB HDD. If it goes on your internal I think you might have problems if your USB is not also installed during start up.

I can't tell you it worked for sure because I hang up during the loading. I believe that it is due to it being USB 1.1 and it is just too slow for this. I am going to get a USB-PCMCIA card to see if I can get the speed of USB 2.0 to see if I am right.

Good Luck

---

### Post by Piraja on 2008-10-02
> **govee said:**
> I think what needs to be clarified is that you are not using a USB flash, but a USB hard drive.
I realized that. But I think at least I had to enable USB booting in my Compaq Evo D510 in order to be able to use my external HDD as a booting device. I think the same applies also to my laptop, Acer Travelmate 2354. No matter whether it's a flash pendrive or an external HDD, in these two PCs you must enable USB boot and set the boot order so that the USB device precedes the internal HDD &#8212; I think. It's interesting to hear that this might not be the case in some other machines.

---

### Post by Piraja on 2008-10-02
> **govee said:**
> I found that in my Bios the USB HDD shows up in the boot menu as a second HDD, not a removeable device.
Oh, I'd like to add that this is not the case in my PCs, I think. I wish you both the best of luck! Please report your success, too.

---

### Post by Piraja on 2008-10-02
Just one more thing... At least when you have older hardware, you may have to edit two files in your /etc/initramfs-tools folder. See [this thread]("http://ubuntuforums.org/showthread.php?t=921291") and the links there for more information.

As was already pointed out, you MUST NOT install the bootloader (Grub) on your internal drive's MBR. And hey... Let's be careful out there!

---

### Post by govee on 2008-10-02
I should have chosen my words better. I just meant to say that it is significant on my machine that it is a USB HDD and not a FLASH drive. My laptop does not have the option to boot from USB in the removable devices, so it seems it is not impossible if I want to boot from USB, but what kind of usb device may determine if it is possible. 
Piraja,
I didnt mean to imply that your information was incorrect, but that small seemlingly insignicant difference (at least it was to me)has made a difference. Sorry about that.:)

I have been tethinking my hangup problem and I think it might be a power vice speed problem. I am using a usb hdd that only draws power from the usb connection and I bet during the long write cycles the power required might be too much. I will use a usb drive that has an external power source to see if it makes a difference.

---

### Post by Piraja on 2008-10-03
> **govee said:**
> Sorry about that.:)
No problem! I did not mind, just wanted to clarify a bit. Please tell us if you had better luck using the drive with an external power source.

---

### Post by au_vagabond on 2008-10-03
Have you tried updating the bios? I know this seems a bit obvious, but compaq may have released a new version of the bios with usb booting support.

Give it a go.

---

### Post by maddaemon on 2009-08-25
There is a solution in order to boot from USB when your BIOS doesn't support it.
Download wake2pup [http://www.murga-linux.com/puppy/viewtopic.php?mode=attach&id=1685&sid=dc9e51a26cb2c5ed6be617466e76d90d](http://www.murga-linux.com/puppy/viewtopic.php?mode=attach&id=1685&sid=dc9e51a26cb2c5ed6be617466e76d90d) and mount the img to have the files in it, copy them in a wake2pup directory.
Make a small partition with Gparted from a live linux CD, make it active
Boot from FREEDOS live CD install FREEDOS from the freedos live CD to drive C: make sure it is not your Windows partition (fdisk) if you have one.Choose base install.
Reboot from Linux and copy autoexec.bat, DRIVERS, config.sys (maybe gotta rename it), kernel.sys and linld.com from wake2pup directory.
Edit config.sys to replace every A:\ by C:\
Copy the file FLASHUSB to your USB stick
in autoexec.bat edit the line LINLD.COM image=%drv%\vmlinuz initrd=%drv%\initrd.gz "cl=%append%" to meet your requirements.
If you want a multi-boot, install GRUB
I used this for puppy but the idea is good: load drivers from a minimal freedos then uses LINDL to boot linux.

I'm sorry for my english. I wish my explanations are clear enough, and they'll help.
If something is not clear, feel free to post. Beware of knowing what you're doing with your system. Make shure you understood how it works before.

Bye and a big hourray for linux and all the community

---

