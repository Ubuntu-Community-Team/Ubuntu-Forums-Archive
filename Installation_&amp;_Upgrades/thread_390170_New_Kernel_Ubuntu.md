---
title: "New Kernel Ubuntu"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by RLovelett on 2007-03-21
I am extremely new to linux.  I've noticed that there are newer versions of the linux kernel out there.  Currently, I'm running...2.6.17-10-generic in Ubuntu 6.10.  My question is: Is there any sense in upgrading to the newest kernel?  If so how do I do so.

The only real reason I ask is that I am trying to set up my Hauppauge PVR-500MCE and reading on-line has lead me to believe that I should have at least 2.6.18 running for the best results.

Any help would be greatly appreciated.

Thanks,
Ryan

---

### Post by mikewhatever on 2007-03-21
The kernel was indeed upgraded about a month ago. Here are the reasons [http://www.linuxcompatible.org/USN-416-1_Linux_kernel_vulnerabilities_s81279.html](http://www.linuxcompatible.org/USN-416-1_Linux_kernel_vulnerabilities_s81279.html)
If you only just installed, the upgrade will probably be offered in no time through auto updates.

---

### Post by RLovelett on 2007-03-21
[http://ivtvdriver.org/index.php/Main_Page](http://ivtvdriver.org/index.php/Main_Page)

The IVTV website says that 2-17-2007 that the 2.6.18 kernel is the one that everyone should have and that any version prior to such will no longer be supported.  So to me that means that to make the switch to Ubuntu I need to have this kernel.  Because I need to have my PVR working in order for me to make the switch.

Is there any good tutorial for how to upgrade my linux kernel in ubuntu?

::EDIT::
I am going to try this:
[Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158")

---

### Post by RLovelett on 2007-03-23
I have compiled the kernel. And everything seems to be going fine. I have tried booting Ubuntu 6.10 with kernel 2.6.20.3. But when I do it boots until you see the Ubuntu logo. The bar shows up but it hangs and never actually boots.

I tried getting it to boot with the debug going and here is where it hangs:
[ 7.055411] drivers/usb/input/hid-core.c v2.6: USB HID core driver

I don't know what that is, and I don't know where to even go with this. I did a search and some of the launchpad errors near this refer to a wireless card. Should I try removing the wireless card and boot again?

---

### Post by laklare on 2007-03-27
I'm having the same problem with USB/HID hanging at boot time with 2.6.20

---

