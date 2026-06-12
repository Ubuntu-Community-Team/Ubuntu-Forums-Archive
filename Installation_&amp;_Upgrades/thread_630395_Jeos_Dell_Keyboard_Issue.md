---
title: "Jeos Dell Keyboard Issue"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by fully on 2007-12-03
Hi,
  I am trying to install JeOS on a Dell E520 so that I can run it as a vm server.  Having a problem that I can't get the USB keyboard to work.  Works fine in the Dell bios util, but can't find any bios option talking about  native USB support.  Couldn't get it to go past the boot screen because the keyboard didn't work.  So I played with the install disk and added a default option and after starting the install process, the keyboard worked fine.  But after booting up the keyboard is again not working, it just sits at the logon prompt.

  Unfortunately the machine has  no plugs for ps2 and as I mentioned can't find any legacy support options in bios.  Anybody got any ideas?

  Thanks for any help you can offer.

---

### Post by dimebag_forever on 2007-12-04
I have no ideas, but I do have exactly the same problem with a DELL optiplex 745

---

### Post by fully on 2007-12-13
Hi,
  Sorry for delay, been otherwise engaged.  After even more web searching found this useful link: [Ubuntu on Dell Dimension n-Series Desktop]("https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellDimensionNSeries"), which suggested that there were some bios issues with the machine.  I reflashed the bios (which needed windows!! although I glimpsed some posts in my searching intimating people had worked out how to do it from linux) and this seemed to partially sort it all out.  The boot menu on the install DVD and install itself could see the keyboard without issue but by the time it got to the installed JeOS login prompt it could see the keyboard again.

  I assume that there is some driver issue with JeOS.  Anyway I downloaded a copy of Gutsey server and installed a blank version that instead, which works fine.  Then installed vmware from the commercial repository and it is all working great.

  Cheers

---

### Post by Profusion on 2007-12-15
I had this exact problem. Though I installed it on my Dell poweredge 1800 I found a fix for it.
Off the top of my head I changed a bios setting related to boot up bios support? or something like that? After I did that I got it to work. I cant really confirm this unless someone knows how to get into the bios without rebooting it. Its running as a webserver =P.

---

### Post by bradmkjr on 2008-05-05
Greetings,

As far as I know, there is no USB module in JeOS. JeOS is designed to be run inside a Virtual Machine, not as a Virtual Machine Host. I have a Dell SC440 server running VMware on Ubuntu 7.10 Server (full edition, not JeOS) and a USB keyboard without any issue.

VMware does a translation from USB to PS2 for the keyboard and mouse, and therefore doesn't require USB support in JeOS. Remember the whole idea of virtualization is take the most basic widely support hardware and virtualize it, therefor PS2 is much more logical then usb.

I would imagine there are other issues which physical storage devices, network cards and video adapters which are also not included in the base install of JeOS.

Here is some additional information for other Dell / Ubuntu issues: [https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellDimensionNSeries](https://wiki.ubuntu.com/HardwareSupportMachinesDesktopsDellDimensionNSeries)

Good Luck,
Bradford Knowlton
[http://x86Virtualization.com](http://x86Virtualization.com)

---

