---
title: "Video Resolution During Installation"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by Ciaraldi on 2016-04-25
I have been using Ubuntu and other Linux distros for many years, but I ran into a new problem while trying to install Ubuntu 16.04 LTS on my new PC.
This is a Powerspec with an Asrock motherboard with Z170 chipset, Intel i7-6700 processor, 16 GB RAM, 256 GB SSD, and 2 TB HDD. The videocard is from MSI and contains an nVidia 970 GPU chip. It is currently running Windows 10 Pro, and I opened up a 100 GB free space on the HDD for Ubuntu.

This computer and several others are connected to my keyboard, mouse, and monitor through a Linkskey 7308 KVM switch. This works fine under Windows and has worked with Linux on other machines in the past. The only problem is that none of the computers are able to query the EDID of the monitor in order to automatically set the video resolution, so I usually have to set this manually after installation.

My new PC actually has several places to attach a video monitor. Right on the motherboard there are HDMI and DVI-D ports. The videocard has HDMI, DVI-D, and DVI-I ports. Since my KVM switch wants VGA input, I plugged a passive DVI-I to VGA adapter (which came with the machine) into the DVI-I port, and plugged the KVM switch into that. This works with Windows. The monitor is from Samsung and has a native resolution of 1680x1050.

When I boot up the Ubuntu 16.04 installation DVD and ask it to run Ubuntu without installing, the screen turns blue and says Ubuntu in the middle, with the dots underneath it that travel from left to right. So far so good; if the video stayed that way I would be happy. Then after about a minute the screen goes blank except for a message from the monitor itself that it cannot display the resolution which the computer is putting out. So I need to tell Ubuntu to use a valid resolution during installation.

I did some searching online and tried setting to 640x480 by pressing F6 to display the boot options, then replacing quiet and splash with vga=771. This actually works, but the background has a weird dithered color which makes it almost impossible to read anything. So I was hoping someone could tell me how to set to a better resolution during installation. Thanks.

---

