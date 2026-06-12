---
title: "Ubuntu 10.04 Lucid Lynx nvidia glx 185 error"
date: 2009-12-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mobee on 2009-12-16
I have been forced to move into early Lucid Lynx since I was experiencing very slow internal connection while developing in Drupal environment.
Lucid Lynx indeed is faster and better but now I am forced to work in low resolution since nvidia driver fails to load and Lucid Lynx falls back to command line which is not useful for web development ;-)
I was trying to configure xorg.conf by hand but it had no effect I still work with 800x600 instead of 1280x1024, the weired part is the 9.10 detected my screen manufacture and resolution with no problem.

I really like to stay with my Ubuntu system, please help an early adopter as me.

My lspci output:

00:00.0 Host bridge: nVidia Corporation MCP73 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.3 Co-processor: nVidia Corporation MCP73 Co-processor (rev a2)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
00:10.0 VGA compatible controller: nVidia Corporation C73 [GeForce 7100 / nForce 630i] (rev a2)
01:07.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)

---

### Post by mobee on 2009-12-18
Any one interested in help me solve Lynx & nvidia problem?

---

### Post by Ubuntaqua on 2009-12-18
> **mobee said:**
> Any one interested in help me solve Lynx & nvidia problem?

Maybe you should try to look at the 10.04 special forum.

---

### Post by oblivian516 on 2009-12-18
I'm typing this right now using 10.04 and having to use the 'nv' driver (resolution is way off here too) :( 185 is clearly not working atm. Perhaps by alpha 2.

~Dave

---

### Post by oblivian516 on 2009-12-19
Finally got the nvidia driver working. If you want the official ubuntu deb pkg you are going to have to wait. If not just download the 190.53 driver from nvidia and install using this tutorial: [http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

~Dave

---

### Post by faical117 on 2010-04-26
nvidia driver = :confused::confused::confused::confused:

---

