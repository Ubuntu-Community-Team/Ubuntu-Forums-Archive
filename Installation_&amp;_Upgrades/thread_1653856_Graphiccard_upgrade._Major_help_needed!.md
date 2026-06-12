---
title: "Graphiccard upgrade. Major help needed!"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by Englischdude on 2010-12-27
Hi All,

have just built an arcade cabinet for MAME Emulator which is based on Xubuntu. Unil now I was using an on-board graphics card, but with only a maximum of 32mb memory I have upgraded a little. I have acquired a cheap Geforce2 Nvidia MX400 which I cant seem to get working. This is what I have done so far:

- started using the on board intel card and installed the 96 drivers for this card.
- when trying to then boot with the new card the system hangs at startup with a variety of errors
- when trying nvidia-xconfig it says command not found
- xorg.conf file is completely empty
- nouveau is blacklisted
- when trying modprobe nvidia I get a fatal error nvidia module not found.

Am using Xubuntu 10.10

Please help!  But bear in mind that I am a newbie so please make any explanations clear, and directions with the required terminal commands.

Many thanks to all of you in advance.
Martin

---

### Post by Englischdude on 2010-12-27
Some more info which may help........


mame@mame:~$ sudo lspci | grep -i vga
[sudo] password for mame: 
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
mame@mame:~$ grep -i driver /etc/X11/xorg.conf
mame@mame:~$

---

### Post by Englischdude on 2010-12-27
and some more info..........

mame@mame:~$ sudo lshw -C display; dpkg -l | grep nvidia
  *-display               
       description: Display controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:f0000000-f7ffffff memory:fe780000-fe7fffff ioport:ec00(size=8)
  *-display UNCLAIMED
       description: VGA compatible controller
       product: NV11 [GeForce2 MX/MX 400]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: b2
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller cap_list
       configuration: latency=32 maxlatency=1 mingnt=5
       resources: memory:fd000000-fdffffff memory:e0000000-e7ffffff memory:fe5f0000-fe5fffff
ii  nvidia-96                             96.43.18-0ubuntu1                                 NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-current                        260.19.06-0ubuntu1                                NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-glx-96                         96.43.18-0ubuntu1                                 Transitional package for nvidia-glx-96
ii  nvidia-settings                       260.19.06-0ubuntu1                                Tool of configuring the NVIDIA graphics driver

---

### Post by Englischdude on 2010-12-28
thought about a fresh install. if worst comes to worst I will install back to ).04 where [I] can then use ENVY to setup the driver. Have tried installing ENVY on this system but cant ge it going on 10.10.

Have tried starting from a live cd of Xubuntu 10.10 from the new graphics card, but still errors at bootup!

Anyone?? Please??

---

### Post by cascade9 on 2010-12-28
I'l guess that you've installed the 96.xx drivers from the repos. Which doesnt work with 10.10. 

I dont know why there are still  non-working 96.xx drivers in the repos, or why the 96.xx have never been fixed on 10.10, and its been an issue for ages- 

[http://www.omgubuntu.co.uk/2010/10/nvidia-96-driver-ubuntu-10-10-fix/](http://www.omgubuntu.co.uk/2010/10/nvidia-96-driver-ubuntu-10-10-fix/)

I'd try manually installing the 96.xx drivers.

[http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

Yeah, that page is for 10.04, but AFAIK it works on 10.10 as well.

---

### Post by Englischdude on 2010-12-28
thanks for the tip. I am trying to install the drivers from the terminal, but it comes up with an error saying there is an xsession running which I should stop. How do I stop the "xsession" and how and when do I restart it again?

Thanks
Martin

---

### Post by dino99 on 2010-12-28
reboot into recovery mode, then:

sudo rm /etc/X11/xorg.conf

then reboot and add video=vesa on the boot line (before "quiet splash") (hold "shift" key down at end of bios process if you dont see grub menu)

---

### Post by Englischdude on 2010-12-28
> **dino99 said:**
> reboot into recovery mode, then:

sudo rm /etc/X11/xorg.conf

then reboot and add video=vesa on the boot line (before "quiet splash") (hold "shift" key down at end of bios process if you dont see grub menu)


Hello Dino99,

many thanks for your post and support. can you please ellaborate a little:

removing the xorg file does what exactly?
video=vesa should be entered where? what is the boot line? and what is quiet splash?  I did state in my first post that I am a newbie so clear explanations are greatly appreciated and avoid confusion (and stress)

Many thanks
martin

---

