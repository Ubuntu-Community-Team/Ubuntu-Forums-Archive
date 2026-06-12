---
title: "Failing to install Ubuntu 14.04.3 64bit from USB"
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by UniqueActive on 2015-10-22
After verifying the hash and mounting the ISO with Universal USB Installer, I restarted my computer and booted from my USB. 
I have tried running it from USB and installing it normally, both options turned out the same: It showed me a couple of errors, the nice looking Ubuntu logo with the loading dots showed up and after that I arrived at this screen: 
  [ATTACH=CONFIG]265108[/ATTACH]
I'm guessing it's a problem with 32/64bit because of all the 64s and 32s I am seeing, can't tell though because two hours ago is the first time I got in touch with Ubuntu or Linux in general and I am not very familiar with analyzing errors, since I am a total noob (which I am trying to change). Help would be greatly appreciated!

---

### Post by ubfan1 on 2015-10-22
The problem might be the USB3.  Try the USB stick in a USB2 port if you have one.   Did you use the amd64 iso?  Is this a UEFI machine?

---

### Post by UniqueActive on 2015-10-23
I downloaded the 64bit ISO from the website. The stick is connected to USB2 but the stick itself is USB3. My mobo has an UEFI dual bios, I don't know if that might be causing problems. I can look for an option to disable the dual bios and use UEFI only, don't know if that could work.

---

### Post by sudodus on 2015-10-23
Welcome to the Ubuntu Forums :-)

There may or may not be a problem with the system in the pendrive. If you are creating the USB boot drive from Windows, you could try some other tools, ***Unetbootin*** or ***Win32 Disk Imager***.

See this link [Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)


There may be a problem with a driver for the graphics or the wifi. In this case you may need a ***boot option***, and later on install a ***proprietary driver***. The following links can help you with boot options.

[Is the computer running in UEFI mode or in classical BIOS mode?](http://ubuntuforums.org/showthread.php?t=2230389&p=13370798#post13370798)
[Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)


***Please specify your computer***

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Knowing more about your computer makes it easier to help :-)

---

### Post by UniqueActive on 2015-10-23
Thank you, after my previous post I tried using Win32 Disk Imager; I also went into my BIOS and disabled all Legacy options and made it do everything over UEFI, both attempts without success. Previously I also had the problem that it didn't register my Keyboard, which was plugged in over USB with an adapter, after I plugged it into the PS/2 port it worked without any issues.

My Computer is self-built, here are the specs:
CPU: AMD FX-6300
RAM: 8gb (2x4gb sticks) of Crucial Ballistix Sport
GPU: Sapphire Radeon 270X (DualX cooler with factory OC)
Mainboard: GA-970A-UD3P 				(rev. 1.0) 				 					 				(I might have to update the BIOS, looking that up right now)
LAN Chip: Realtek[SUP]®[/SUP] GbE LAN chip (10/100/1000 Mbit)

---

### Post by UniqueActive on 2015-10-23
Should I try installing a different version like for example 15.10 or maybe switch between 64 and 32 bit? I could also try running it on a virtual machine, I just don't know what to do since I can't seem to find the problem.

---

### Post by sudodus on 2015-10-23
It seems that the problem is not with the booting, but later in the startup process. (Win32 Disk Imager is very reliable.)

I know intel and nvidia graphics better than AMD/ATI/Radeon, but there are many people at the Ubuntu Forums who use Radeon graphics. I think and hope that you can get good advice about it. My advice would be to boot with the *boot option* **nomodeset** according to the links in my previous post, and to hope that there is a good proprietary driver for it.

-o-

Yes, it is worth trying another version like for example 15.10, which is released now. I would recommend a 64-bit version of standard Ubuntu or any flavour of Ubuntu. The computer has 'horsepower' and RAM enough for all of them, Kubuntu, Lubuntu, ..., Xubuntu.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by UniqueActive on 2015-10-23
Didn't have the problem with 15.10, didn't even get to try the boot options, although I might try that aswell. I'm going to mark this as solved, thanks for your help!

---

### Post by UniqueActive on 2015-10-24
After trying to find the mistake for another two hours I tried a different USB stick and even 14.04.3 works perfectly now.

---

### Post by sudodus on 2015-10-24
Congratulations :KS

and thanks for sharing your solution.

---

