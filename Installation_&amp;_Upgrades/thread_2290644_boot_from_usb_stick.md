---
title: "boot from usb stick"
date: 2015-08-14
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2015-08-14
Hi, I want to install the latest Ubu 15.04. I downloaded the 32 bit iso from this Ubu site, right clicked it, and went to 'open with disc image writer'. Wrote it to my usb stick. BIOS is set to boot from usb stick, that's how I installed 14.04. Checked with gparted, the boot flag is set. Nothing happens, it will not boot from this usb stick.

Anyone know why

---

### Post by sudodus on 2015-08-14
Please tell us more about your computer. That makes it easier for us to help. Otherwise we can only guess.

0. Please describe exactly what happens, when you try to boot from the pendrive with 15.04! What is written to the screen, sounds ... ?

1. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

2. Are you making the USB pendrive in a computer running Ubuntu 14.04 LTS?

3. Which tool are you using? I guess it is 'gnome-disks' alias 'Disks'? I'm asking, because I and other people able to help might use another desktop environment. We might not know what tool is linked to that right-click option. If you don't know, please make a screenshot and attach it to a reply (attach it via 'Manage Attachments' in the 'advanced editor'. Do not put it directly into the reply).

I think that 'gnome-disks' alias 'Disks' is a very reliable tool. So the problem is probably somewhere else (if you are using this tool).

4. What pendrive are you using?

- Can you boot another computer with it?
- Can you boot some computer with it, if you install another operating system in this pendrive.

See this link and links from it for more details,

[Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

- Can you boot your computer with another pendrive?

---

### Post by Pedroski55 on 2015-08-14
This is an old Asus X50GL which I use at home. Has dual Intel T1600 CPUs GeForce 8200 M, wifi don't know right now, Broadcom I think, 4GB RAM. 

Everything works fine. I downloaded the latest 15.04 Ubu, then started usbstick creator from Dash. This is Ubu 14.04, just thought I'd try the latest version.

Pendrive is an Innostar 14GB.

I tried the same pendrive in my newer laptop, also nothing happened. I actually used another pendrive to install Ubu on both laptops, so I know it works, but gave that one to someone. This pendrive has no problems, I can write to it ok, read from it ok.

On boot it ses the usb stick, but does not boot from it. Moves on to the grub boot screen.
Weird!

---

### Post by sudodus on 2015-08-14
You know what you are doing :-)

Anyway, you are using the 'Ubuntu Startup Disk Creator', which has some problems. It is not as reliable as 'Disks'. You might try another tool to make the USB pendrive bootable with Ubuntu. Several tools are described in this link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Some pendrives work well for storage (read and write), but they do not work for booting. The problem could be that the pendrive was not made quite according to some standard. There are cheap pendrives that are slow but reliable booters, for example Sandisk Cruzer Blade. It is enough with a small one, 4 GB, for this purpose (to install an operating system). Actually 2 GB is enough, but maybe hard to buy nowadays.

You can also try with another Ubuntu version (for example 14.04.3 LTS) in this pendrive. Who knows, it might work.

---

### Post by Pedroski55 on 2015-08-15
15.04 still does not work. I tried another, good usb stick. I tried it on my new laptop. Does not boot. I installed 14.04 from a usb stick on that computer.

So I made a dvd and installed from there. Installation went well. I installed alongside 14.04. However, after I get the log in screen, enter my password, I have a Ubu coloured screen, and the mouse pointer, nothing else. No system.

I can ctrl alt f2 into a virtual terminal, and I updated and upgraded, retarted, but still nothing works. Not very good 15.04!

---

### Post by oldfred on 2015-08-16
Newer systems should not use 32bit version.
Your old system may even support 64 bit and if 4GB of RAM 64 bit would be better.

Often video issue if nVidia chip or card.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

