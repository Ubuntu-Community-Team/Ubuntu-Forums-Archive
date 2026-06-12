---
title: "Wubi-Help"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by Carharttjimmy on 2010-12-07
So, I downloaded Wubi.exe and also the ubuntu-10.04.1-desktop-i386.iso file. 

I ran Wubi and then it did its work. Rebooted and selected Ubuntu. Then it went through the installation progress and after it hit 100% it rebooted (that may be the main error).

Then I was like hmmm, and selected Ubuntu to boot. And, it showed me where it was and I was like hmm again and hit that, then it brought me back to the boot screen again. Then, I decided to go into boot with an edit and grub came up and it began to hang on me.

Idk what to do....so yeah.

---

### Post by Carharttjimmy on 2010-12-07
I also reliezed I hit the wrong prefix. 

Thats what 3 days of being up all night does to ya.

---

### Post by bcbc on 2010-12-07
Did you install while connected to the net? There is an update out there that breaks a default 10.04.1 install so maybe it got installed automatically and broke wubi.

Since you just installed, I'd reinstall, and unplug your ethernet cable after the windows part. And then don't allow the update manager to update grub-pc or grub-common.

Or don't use Wubi.

Or if you feel adventurous you could fix it: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198) (problem #2 solution #1 followed by the permanent fix)

---

### Post by Carharttjimmy on 2010-12-07
I installed Wubi with no internet active. I mean I had all my wireless devices off and Ethernet unplugged.

---

### Post by Carharttjimmy on 2010-12-07
I might just install Ubuntu or Arch as I have both ISOs and I think a Debian CD somewhere. Probably Ubuntu as I have found it works better on laptops (at least those manufactured by Lenovo).

But, I am using Wubi to make my final decision as I have Arch on a main desktop that I use.

---

### Post by bcbc on 2010-12-07
OK maybe there is some other issue. It's absolutely normal for the Wubi install to run to completion and then restart the computer. The first part in Windows just sets up the boot mechanism and the unformatted virtual disk, the second part (first reboot) formats and installs to the virtual disks in an unattended installation. 

So... perhaps there is a hardware incompatibility. Brand...model...graphics card...?

---

### Post by Carharttjimmy on 2010-12-07
I have a 
Lenovo T500
Processor: Intel(R) Core(TM) 2 Duo CPU
32-bit op system
ATI Mobility Raedon HD 3650

---

### Post by bcbc on 2010-12-07
I can't find any issues with 10.04 and this model, but apparently if you can switch between the graphics card and the built-in graphics using the bios, this helps.
Here's a bug report that seems relevant...
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/542931](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/542931)

---

