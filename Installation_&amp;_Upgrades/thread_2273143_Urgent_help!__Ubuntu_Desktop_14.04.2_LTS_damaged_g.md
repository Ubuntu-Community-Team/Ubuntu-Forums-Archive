---
title: "Urgent help!  Ubuntu Desktop 14.04.2 LTS damaged graphics card??!!"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by Carolina_Cordero on 2015-04-10
Hi.

I'm posting in this forum because I need urgent help.

I'm new Ubuntu user coming from Windows environments.

I've decided to install Ubuntu Desktop 14.04.2 64-bit on my Dell Studio 1558 laptop, for having it available in dual boot with my existing Windows 7 installation.

The specs of my Dell Studio 1558 are:
[LIST]
[*]Intel Core i7 processor, 64bit
[*]8GB RAM
[*][COLOR=#333333][FONT=Helvetica]ATI Radeon HD 5470 Graphics card[/FONT][/COLOR]
[*][COLOR=#333333][FONT=Helvetica]500GB hard drive[/FONT][/COLOR]
[/LIST]
[COLOR=#333333][FONT=Helvetica]I must say I've never had any problems with this hardware.

[/FONT][/COLOR]I've installed Ubuntu 14.04.2 in dual boot, created three partitions: ext4 (/) primary partition, swap partition and ext4 (home) partition.

I've checked the two options: 1) [COLOR=#666666][FONT=Trebuchet MS]Download updates while installing, and 2) [/FONT][/COLOR][COLOR=#666666][FONT=Trebuchet MS]Install this third-party software now[/FONT][/COLOR]

The setup process completed perfectly fine, the dual boot menu was successfully updated, I've could log in Ubuntu and Windows, and I've started to work in my Ubuntu fresh installation:  I familiarized with the environment, opened a PDF book, a terminal window, Mozilla Firefox, looked some pictures, everything worked fine.

After about 20 minutes working with Ubuntu, I've received a notification for updates available, so I've choosen to download them and to install them.

The download and installation of this first update took about 30-45 minutes, after that Ubuntu ask me to reboot the computer.

The problems started here:  when I choose to reboot, the computer started to show screen flashes, with vertical colored stripes.  After that the system rebooted and continued to showing this vertical colored stripes.  I rebooted again and logged into Windows, where the problem persisted (it was not only in Ubuntu).

After that I rebooted again, but this time the laptop screen was completely dead:  I now can't see Dell logo, neither Ubuntu boot menu, nothing.  The screen is completely black.

I've connected the computer to an external monitor via VGA cable, also to a led tv via HDMI cable, and the video output is completely distorted, as you can see in this images:

HDMI Output:
[http://i.imgur.com/WFe4Xmx.jpg](http://i.imgur.com/WFe4Xmx.jpg)

VGA Output:
[http://i.imgur.com/F6nykl4.jpg](http://i.imgur.com/F6nykl4.jpg)

The laptop screen continues dead.


As you can see, I need urgent help, I wonder if it's possible that the first update on a fresh Ubuntu installation could have damaged the hardware, I must say I haven't installed any specific graphics/video driver, none, it's was a fresh Ubuntu installation.

I was wondering if there is some command to rollback the last update, I don't know if such command exists, any help is appreciated since I'm new to Ubuntu.

Thanks.

---

### Post by sandyd on 2015-04-10
The so called stripes on the screen are a sign of video card issues and/or overheating. I had the same issues on two other laptops,  (Dell 1737 with ATI 5450 Mobility which is a larger, earlier version of your laptop and another laptop) whose dedicated video cards stopped working. Laptop was made workable again through buying a motherboard through ebay. Now, I don't buy laptops with dedicated video cards anymore.

By default, Ubuntu uses the open source radeon graphics drivers.

---

### Post by Carolina_Cordero on 2015-04-10
Thanks.
As I mentioned in my previous post, my laptop never presented video card issues or overheating.  
This problem began just after installing the first update suggested by Ubuntu.

Thus my concern about this strange sympthom.

Any suggestion about things I could try?

[edit]

Is there a command to uninstall the last update?  Or to uninstall the graphics driver update?

---

