---
title: "Running Ubuntu off a External USB Drive on Windows 8 Laptop."
date: 2014-06-16
forum: Installation &amp; Upgrades
---

### Post by irv on 2014-06-16
I put a video on youtube on how to run Ubuntu off a external drive 
[https://www.youtube.com/watch?v=uOrrN-JCcQE&feature=youtu.be]("https://www.youtube.com/watch?v=uOrrN-JCcQE&feature=youtu.be")

---

### Post by johnwe1977 on 2014-06-16
It's a great way:o

---

### Post by irv on 2014-06-16
Here is a quick look at the speed when running off the USB.
[https://www.youtube.com/watch?v=y0cMgUU3B2Q&feature=youtu.be]("https://www.youtube.com/watch?v=y0cMgUU3B2Q&feature=youtu.be")

---

### Post by oldfred on 2014-06-17
UEFI or BIOS install on external?

What external drive?

I assume USB3 port?

---

### Post by irv on 2014-06-19
Yes, a USB3 port.

---

### Post by sudodus on 2014-06-19
Nice demos :-)

Please tell us how you installed your Ubuntu system into the USB 3 drive!

- UEFI or BIOS (I guess UEFI)
- what drive (HDD or SSD)
- which version of Ubuntu
- some special tweaks

---

### Post by irv on 2014-06-19
The first thing you need to do is create an install USB stick and put it into one of the USB slot. Then make sure you plug in the external drive you want to install on into another USB slot. If you have a USB3 slot or slots use them. It will make the install go faster.

Just like in the video you restart Windows 8 or 8.1 by holding down the [Shift] key as it restarts. Choose boot for other devices. You should see install USB and maybe the external drive if it is formatted with something Windows can see. But that doesn't matter at this point, because you can format it when you do the install. You want to choose the Install USB. Select it and your system should boot into the install. If you don't see it, just boot back into Windows again and let Windows completely load and then restart holding down the [Shift]key again. (That's a Windows thing).

As you do the install, just make sure you pick the external drive to install Ubuntu on. Also you need to put the grub on the external drive. This way it will not even go to the grub unless you have the external drive plugged in when you do the restart [Shift] and select it.

This is how I did it.

---

### Post by monkeybrain20122 on 2014-06-19
If you install into an external hd I am not sure what difference it would make between usb2 and usb3 (with flash drive there may be a difference). 

I have installed Ubuntu and other Linux distros on external drives as portables to boot off different machines for a while (e.g at work, or when I visit my family, I just bring one of these and boot off my dad's machine instead of bringing my laptop) I have not noticed any difference in speed and performance between running in an external hd via a usb2 and installing internally. Installing into a flash drive and running with usb2 is significantly slower than internal install though, not sure about usb3.

All machines are BIOS rather than UEFI.

---

### Post by sudodus on 2014-06-19
Concerning speed with USB drives, see this link (USB 3 can be much faster than USB 2)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

Concerning BIOS and UEFI, see this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Portable_installed_system_booting_from_UEFI_and_BIOS](https://help.ubuntu.com/community/Installation/FromUSBStick#Portable_installed_system_booting_from_UEFI_and_BIOS)

---

### Post by monkeybrain20122 on 2014-06-19
> **sudodus said:**
> Concerning speed with USB drives, see this link (USB 3 can be much faster than USB 2)

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)



Faster for what? It seems that it talks about writing to and reading from **usb flash drives** and applies to things like transfering files. I am not sure if this has relevance to running an installation in an **external hard drive**. I can't see any difference  in performance running Ubuntu (or any Linux distro I have tried) from an external hard drive (usb2) and installing internally. I have been doing that a lot for a few years booting off a range of machines with diverse specs. Yeah with **usb flash drives** it is painfully slow.

I am writing from Ubuntu 14.04 installed in an external hd right now (13.10 in the internal drive). It is blazing fast and this machine doesn't have any usb3 port.

---

### Post by sudodus on 2014-06-19
Why do you think people want faster HDDs and SSDs?

***Edit***: And why should the same not count for the USB interface?

---

### Post by monkeybrain20122 on 2014-06-19
I don't know 'faster' in what context, all I am saying is empirically I can't see any difference in speed or performance in the present context (running Linux in an external hd) due to usb interface.

---

### Post by sudodus on 2014-06-20
*@monkeybrain20122,* we have different experiences, and I think it is good to discuss it :-)

My experience is that certain things, including booting (reading) and shutting off (flushing cached data) and copying files can be limited by the USB 2 transfer rate, which makes the system slow compared to running from internal drives, eSATA and USB 3 drives. A live system is reading its compressed file system into RAM, so it is quite responsive, while a persistent live system and an installed system are more depending on reading uncompressed data from the drive, which makes them slower when limited by slow flash memory but also by USB 2.

I certainly agree with you, that > with **usb flash drives** it is painfully slow except with some of the really fast USB 3 pendrives, where the flash hardware is much faster than standard flash memory hardware.

And I agree with both of you, *irv* and *monkeybrain20122*, that running installed systems from USB works quite well. This is a good alternative to messing with dual booting in the internal drive and the potential risk to damage an installed Windows system. Installed systems in USB drives are also good as ***portable*** operating systems (if you use no proprietary driver).

---

### Post by sudodus on 2014-06-20
[**[COLOR=#000000]zemega[/COLOR]**]("http://ubuntuforums.org/member.php?u=1772190") reports problems when booting a PAE system from a USB drive in a computer with a non-pae CPU. The post was moved to an own thread
[URL="http://ubuntuforums.org/showthread.php?t=2230598"]
booting from external drive with non-pae CPU[/URL]

---

### Post by irv on 2014-06-20
Just to mention that I don't use this installed OS on the external drive in any other computer. And maybe another reason it runs fast in the fact that I have a i7 processor and 8gig of RAM.
I have been thinking about getting an external SSD and installing Ubuntu on it. I would think with this and using it on USB3 would improve performance even more.

---

### Post by sudodus on 2014-06-20
I'm running this computer (that I'm typing from) from an SSD in eSATA right now. It is about the same speed as USB 3. It is not generally portable, because I have an nvidia proprietary driver, NVIDIA 304.88 for a GeForce GT 430 card. (But with the nouveau driver it is quite portable. I have tried.)

---

### Post by monkeybrain20122 on 2014-06-20
> **sudodus said:**
> I'm running this computer (that I'm typing from) from an SSD in eSATA right now. It is about the same speed as USB 3. It is not generally portable, because I have an nvidia proprietary driver, NVIDIA 304.88 for a GeForce GT 430 card. (But with the nouveau driver it is quite portable. I have tried.)

It would still work with nvidia proprietary driver, just have to rename xorg-config when you boot it off another machine that doesn't have a Nvidia card, in fact you may not even have to do that, I think the Nvidia driver will not load if it doesn't detect a Nvidia card (but I haven't tried it). Not sure about fglrx.

---

### Post by sudodus on 2014-06-20
I have another computer with an older nvidia chip. This driver does not work with that chip. Instead it wants the '173' proprietary driver.

---

### Post by monkeybrain20122 on 2014-06-20
> **sudodus said:**
> I have another computer with an older nvidia chip. This driver does not work with that chip. Instead it wants the '173' proprietary driver.

No, that wouldn't work. I only had one computer with Nvidia so I was booting off other computers with Intel or Amd.

---

### Post by monkeybrain20122 on 2014-06-20
> **sudodus said:**
> *@monkeybrain20122,* we have different experiences, and I think it is good to discuss it :-)

My experience is that certain things, including booting (reading) and shutting off (flushing cached data) and copying files can be limited by the USB 2 transfer rate, which makes the system slow compared to running from internal drives, eSATA and USB 3 drives. A live system is reading its compressed file system into RAM, so it is quite responsive, while a persistent live system and an installed system are more depending on reading uncompressed data from the drive, which makes them slower when limited by slow flash memory but also by USB 2.


Depending on where you copy from/to. If from another drive then you are probably right. But in the same drive I see no difference. Booting up and shutting off may be a bit slower, but in general I find the difference is quite small.Once up and running there is no difference from my experience.

---

### Post by monkeybrain20122 on 2014-06-20
> **sudodus said:**
> [**[COLOR=#000000]zemega[/COLOR]**]("http://ubuntuforums.org/member.php?u=1772190") reports problems when booting a PAE system from a USB drive in a computer with a non-pae CPU. The post was moved to an own thread
[URL="http://ubuntuforums.org/showthread.php?t=2230598"]
booting from external drive with non-pae CPU[/URL]

Yes, portability may be somewhat limited if you try to boot off a drastically different machine. For example, if you have Unity and boot it off another machine which doesn't support 3d desktop than not only does it not work, you may mess up your Unity-Compiz settings irreversibly, but I suppose 2d desktops like xfce would not have this issue.

---

### Post by sudodus on 2014-06-20
@monkeybrain20122,

zemega might appreciate if you post in their thread too.

---

### Post by zemega on 2014-06-21
> **sudodus said:**
> @monkeybrain20122,

zemega might appreciate if you post in their thread too.

I don't have any more non PAE capable CPU or machine, so I do not wish to pursue the discussion. Its just a head up so that people don't try booting Ubuntu (I tried with 12.04 32 bit) with kernel that needs PAE on a machine with CPU that don't support PAE. It breaks some part of Ubuntu installation/loading/booting and it persists  even when you boot it up on PAE capable machine after that.

---

### Post by irv on 2014-06-22
There is another way to run Ubuntu on a windows 8 machine without using an external drive or even installing it, but you need a machine running Ubuntu on your network.
You can do this by using a VNC viewer in windows by opening a VNC connection to the Ubuntu machine and run it in a window. I think you can do this over the Internet by opening a port, but I haven't done this. Someone said it has a security issue. But I do it all the time on my close network. Here is a couple of screen shots. By the way I use TightVNC Viewer in Windows to manage my server from my laptop or other machines on my network.
[ATTACH=CONFIG]254155[/ATTACH][ATTACH=CONFIG]254156[/ATTACH]

---

