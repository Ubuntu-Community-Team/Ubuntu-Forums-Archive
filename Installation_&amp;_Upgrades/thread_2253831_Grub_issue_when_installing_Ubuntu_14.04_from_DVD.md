---
title: "Grub issue when installing Ubuntu 14.04 from DVD"
date: 2014-11-22
forum: Installation &amp; Upgrades
---

### Post by networker2 on 2014-11-22
I’m trying to install Ubuntu 14.04 from a DVD (that I bought)  to replace Red Hat Enterprise Linux 6.  Skills = newbie to Linux and totally new to Ubuntu.  I did the following:  1.   Inserted the DVD and restarted system  2.  Got a background image on the screen displaying the words Ubuntu 14.04, but over that is a menu titled:  “XBOOT DVD” with 3 choices:   Boot from Hard Drive (note: this launches Red Hat).......Ubuntu 14.04 32-bit......Ubuntu 14.04 64-bit
 
When I select the Ubuntu 14.04 64-bit version I get the following messages:
Loading  /boot/syslinux/grub.exe..
Launching GRUB…
Begin pxe scan…                          Starting cmain() …_
grub>  
 
What to do?........some grub command? Like ‘kernel’?  If so, what is the path? …. Do I edit /boot/grub/grub.conf ?  If so, how?  ……Something else?

I'm new to the forum, Thanks!

---

### Post by oldfred on 2014-11-22
The pxe is a network boot, usually you have that last on BIOS list so it tries booting everything else first, hard drive(s), flash drive(s), DVD/CD, floppy etc first.

Not sure how DVD is configured. It may be using grub4dos as you do not have an exe file for grub. 
If booting in BIOS mode it uses syslinux and if in UEFI mode it directly uses grub2.
Only the now obsolete wubi has an exe file for installing inside your Windows.

What brand/ model, video card system is this?

UEFI or BIOS only?

You do not normally purchase Ubuntu. Just download from Ubuntu or a local mirror and install the installer to a flash drive or DVD.
       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

            Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by networker2 on 2014-12-02
Hi and Thanks, oldfred              I did download and burn the install image onto a DVD and installed.   This is an old Dell Precision M65 that used to run RedHat.  It's got dual processors.  I upgraded the RAM to 4GB (2 x 2GB).  Now the install seems to work but the OS and Applications don't work.  I'm not sure if Ubuntu has not loaded properly or what the issue is.  The log in for my username comes up, and my password seems to work.  However, I end up with a blank 'desktop'.  I see "Ubuntu 14.04 LTS" at the bottom left, but nothing else.  I frequently get the following messages:  .......GPU lockup - switching to software fbcon;  ......failed to idle channel 0xcccc0001........failed to idle channel  0xcccc0000.....   Thanks for any suggestions, networker2

---

### Post by ubfan1 on 2014-12-02
What video card do you have in the system?  You might need a proprietary driver.  Can you switch to a virtual terminal (function keys F2 - F6) with the command
Ctrl-Alt-F2
Login, and please post the output of
sudo lshw -C video
It might help to edit the grub commands to add the "nomodeset" word to the "linux" line -- then you might be able to run the gui enough to add the video driver from "Additional Drivers" from the Dash (top of launcher).

---

### Post by networker2 on 2014-12-02
Thanks ubfan1,

the output of sudo lshw -C video was

PCI (sysfs)
  *-display
    description: VGA compatible controller
    product:  G72GLM [Quadro FX 350M]
    vendor:  NVIDIA Corporation
    physical id: 0
    bus info:  pci@0000:01:00.0
    version:  a1
    width:  64 bits
    clock: 33MHz
    capabilities:  pm msi pciexpress vga_controller bus_master cap_list rom
    configuration:  driver=nouveau latency=0
    resources: irq:45 memory:ed000000-edffffff  memory:d0000000-dffffff  memory:ee000000-eeffffff  memory:ef000000-ef01ffff

Thanks,  networker2

---

### Post by oldfred on 2014-12-02
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
That shows the 304.x legacy driver for your nVidia chip.

       Updated driver search by nVidia model
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Try the nomodeset option to see if you can boot into low level graphics and install nVidia driver from Ubuntu repository using System Settings or from command line.
Best not to install directly from nVidia unless your card/chip is so new that is the only option. And then usually better to use PPA, not nVidia direct download.

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by networker2 on 2014-12-03
Thanks oldfred and ubfan1,

I tried something easy.  I installed Ubuntu 13.04 and everything works fine.  The desktop looks normal, and I can see the installed apps and they work.

---

### Post by oldfred on 2014-12-03
You really should not use a version that is not supported anymore.

13.04 end of life Jan 2014
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

