---
title: "[SOLVED] cannot install Ubuntu 8.04 on Dell E521 or run livecd"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by jagman on 2008-08-21
Hi all,

This is my PC:
Dell Dimension E521
AMD 64 X2 3800+ (2 Ghz)
4 GB DDR2 RAM (from Crucial)
40 GB SATA harddrive
SATA DVD/RW
ATI X1300 Pro 256MB
Broadcom 440x 10/100 Integrated Controller
Sigmatel STAC 92XX c-Major HD Audio
with the latest BIOS 1.1.11
VGA 20" monitor supports lots of resolutions (1024 x 768 and higher)

Problem:
I cannot install Ubuntu or even run the Live CD.  I have tried Ubuntu 8.04 32-bit and 64-bit.  There is no other OS.

What happens:
Originally I was getting the busybox/initramfs error, but using kernel boot options busybox no longer appears.  Now what happens is the machine keeps booting/installing from the CD and all looks ok, but then it takes me to the following prompt
ubuntu@ubuntu~$

What I've tried:
kernel boot options (i've tried some/all of these): all_generic_ide floppy=off irqpoll no apic nolapic pci=nomis acpi=off
I've also removed quiet splash

I've run out of things to try?!?

Questions:
1. what is "ubuntu@ubuntu~$"
2. according to guides I've seen the ubuntu install should take me to a gui where I partition the hardisk, create user/password etc
3. I've tried to run "startx" from the "prompt" and the screen flickers and then says fail

regards

Jag

---

### Post by coffeecat on 2008-08-21
I'm sorry that after three hours, no one has been able to respond to a newcomer to the forum. Welcome, by the way.

The busybox shell usually mean that the Ubuntu disc was having problems with one or more aspects of your hardware, so congratulations for getting past that. The problem you now have is that it can't configure the xserver for your graphics card. Is...

> **jagman said:**
> ATI X1300 Pro 256MB

... the graphics card?

> **jagman said:**
> 1. what is "ubuntu@ubuntu~$"

That's the prompt of a Linux virtual console (or a terminal if you had a GUI) - sort of, vaguely, not quite, :wink: analagous to the old MS-DOS prompt. It takes the form username@computername (in this case they are the same), followed by ~ = you are in the home directory, and $ = you have ordinary, not administrator rights. But you can get adminstrator rights in Ubuntu with 'sudo' - more on that in a minute. You are getting a virtual console because the xserver has failed, but all the OS is there - just not the GUI.

Try this:

```
sudo nano -w /etc/X11/xorg.conf
```Be precise with capitals and lower-case. Linux is case-sensitive. Scroll down to the Device section. Is there a Driver line? What does is say? Edit it, or if it's not there add it, so that you have:

```
Section "Device"
    Identifier   "Whatever you have there already"
    Driver       "vesa"
    Option       "Whatever you have there already"
EndSection
```Now ctrl-O to save and ctrl-X to exit. Now try 'startx"

That may get you a GUI in the live environment, but Heaven only knows how it will cope with an install to HD.

A couple more suggestions. Search the forum for your video card. It might be a problem one. You may find something useful. Also, have you tried any other live distros? Ubuntu is usually the best of all for hardware detection, but sometimes another will succeed where Ubuntu doesn't. Look out for Mandriva 2008 Spring, SimplyMepis 7 and openSUSE 11.0. The first two combine live and install CDs like Ubuntu. I'm not sure whether you can install from the live Suse disc.

---

### Post by jagman on 2008-08-21
Thanks for your reply coffeecat.  

I will try out what you have suggested and post back.

Also, I have done a bit of research on my graphics card (ATI X1300 Pro 256MB) and it seems to me this is the culprit

[http://ubuntuforums.org/showthread.php?t=849372&highlight=Radeon+X1300](http://ubuntuforums.org/showthread.php?t=849372&highlight=Radeon+X1300)

I have some options:
1. try the method described by coffeecat
2. take out the card for now and just use the built-in VGA to get Ubuntu installed and updated
3. I think I have another similar spec graphics card but its nVidia, which I understand is better supported.  If that is the case I may do a swap and try the install

If I try method 2 can I add a dedicated graphics card later, how much of a pain could this turn out to be?

Thanks

Jag

---

### Post by coffeecat on 2008-08-21
According to a quick Google, the built-in graphics adaptor in your computer is a nVidia GeForce 7300 LE. At the moment, nvidia is usually an easier option than ATI - although ATI should get better in the future as ATI works with the Linux community. So, as far as your options are concerned:

> **jagman said:**
> 1. try the method described by coffeecat

No, don't do that. :p Now I realise you've got nvidia graphics to hand, don't bother with the vesa driver. That's a resort of final desperation.

> **jagman said:**
>  2. take out the card for now and just use the built-in VGA to get Ubuntu installed and updated

Yes, absolutely. You've got oodles of RAM there and a pretty decent CPU, so you may find the onboard nvidia graphics works perfectly OK. You'll probably get* compiz and 3d effects if you use the proprietary nvidia driver, which is more than could be said for Vista. :roll: :wink:

> **jagman said:**
> 3. I think I have another similar spec graphics card but its nVidia, which I understand is better supported. If that is the case I may do a swap and try the install

Try both. If you're lucky, the graphics card may use the same proprietary nvidia driver (there's more than one version, depending on card) as the onboard video. By the way, when you first install, you'll get the open source 'nv' driver, which is perfectly adequate for 2d stuff, but lacks 3d acceleration. The easiest way of installing the proprietary 'nvidia' driver is to go to System > Administration > Hardware Drivers. Don't bother in the live environment. Save that till after you have installed. 
 
> **jagman said:**
> If I try method 2 can I add a dedicated graphics card later, how much of a pain could this turn out to be?

Depends. If they're both nvidia, you'll probably be OK. If you start with nvidia and add an ATI card, you'll end up with a crashed xserver. But even if that happens, there's ways of reconfiguring the xserver, and plenty of advice to be had here.

* **Edit:** Let me re-phrase that. You **will** get...

The machine I'm posting from has onboard nVidia GeForce 7025 graphics, but I fitted a PCIe nVidia GeForce 7200 SE card and I get perfectly good 3d acceleration, etc, with a similar graphics chipset to your onboard video. Of course, I have the advantage of the GPU, but what is your nVidia card? Is it a later/better chipset than the onboard one?

---

### Post by jagman on 2008-08-21
Thanks Coffeecat

Since removing the ATi graphics card and using the internal vga I can run the livecd successfully.

Over the weekend I will plugin a PNY GeForce 8500 GT 512MB PCI-E graphics card.  From my research this is nVidia chipsets and I've read people say they have had this working under 8.04 using envy drivers.  With this plugged in i'll go for the install to harddisk

thanks for your help.  I'll post back my results

Jag

---

### Post by coffeecat on 2008-08-22
> **jagman said:**
> Since removing the ATi graphics card and using the internal vga I can run the livecd successfully.

That's good news. Apart from getting a GUI, does that mean you are now not getting all the busybox nonsense and having to acpi=off, etc?

Good luck with the better-specced PCIe card. Envy seems to be a good choice, or you could try the inbuilt nvidia installer under System > Adminstration > Hardware Drivers. Being a simple sort of soul I've always gone for the latter (two clicks and it's done) but a lot of people seem happy with Envy. I think there's a difference in the version of the driver installed, but I can't remember the details.

---

### Post by jagman on 2008-08-22
> **coffeecat said:**
> That's good news. Apart from getting a GUI, does that mean you are now not getting all the busybox nonsense and having to acpi=off, etc?

No, I still get busybox if I don't add the boot kernel commands floppy=off all_generic_ide=off irqpoll etc.  I am investigating (trial/error) how many/which of the commands I need to have the fastest **working** bootup.  (I remove -quiet splash from the command options so I can see it stalling/waiting)

My setup is a little different from what I first posted.  I originally used a 160GB IDE harddisk with a _SATAtoIDE_ adapter.  *The E521 Motherboard only has SATA ports no IDE*.  When I ran into install problems, I thought to simplify, i'd replace it with a 40GB SATA drive I have spare. As you are aware the problem was the graphics card!!  My actual goal is to get the 160GB IDE working with Ubuntu.  I am adding this info because this 160GB drive might be the reason for me having to add all_generic_ide to avoid busybox.

Also I've had a change of heart I won't add the dedicated graphics card yet ... I can't get it from my brother -lol.  BTW my internal VGA card is a "nVidia GForce 6150" (from the dell website) so I think that means I actually have a NVIDIA GeForce 6150 LE.  Anyway, it works on LiveCD and over the bank holiday weekend, I'll do a full install and tweaking to get the best drivers + performance from the internal card.

I already have WinXP on the 160GB harddrive (35GB partition) the rest is empty.  _Will post back when I'm all done_.  Hope this long post makes sense & thanks for reading

Jag

---

### Post by jagman on 2008-08-26
I'm glad to say that I have got a dual-boot WinXP/Ubuntu system up & running on my Dell E521.

I had to swap my 160 GB IDE drive for a SATA harddisk - and now everything is running even with my PCI-E ATI Radeon X1300 Pro.  For clarity the system is now:
Dell Dimension E521
AMD 64 X2 3800+ (2 Ghz)
4 GB DDR2 RAM (from Crucial)
_160 GB SATA harddrive_
SATA DVD/RW
ATI X1300 Pro 256MB
Broadcom 440x 10/100 Integrated Controller
Sigmatel STAC 92XX c-Major HD Audio
with the latest BIOS 1.1.11
32" Techwood LCD TV, connected via DVI to HDMI - the windows XP partition runs Media Portal and the PC is also my HTPC.

To get Ubuntu 8.04 working for my setup:
-temporarily removed the PCI-E ATI card
-installed Ubuntu using the built in nVidia graphics card and using a VGA monitor
-did all the updates - sudo apt-get updates
-installed the Envy graphics drivers - sudo apt-get install envyng-gtk
-shutdown the PC.  Plugged in the PCI-E ATI card and plugged in the VGA monitor
-on reboot went to System > Administration > HardwareDrivers.  enabled 3rd party drivers for the ATI Radeon card.
-shutdown the PC.  Unplugged the VGA and plugged in the LCD via DVI to HDMI
-rebooted, Ubuntu is happy.  Am running at 1280 x 720 can push the resolution up to 1920 x 1080
NB: the only boot options I use now are floppy=off irqpoll (delete the quiet splash)

Thank you for your help coffeecat

Now I can get on with using Ubuntu for GNS-3 (Cisco Emulation tool, hence the 4GB RAM).

---

