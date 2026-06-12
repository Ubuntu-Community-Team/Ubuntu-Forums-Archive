---
title: "Lubuntu Flash problem"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by michael35 on 2013-08-22
Hello, 
after installing the flash pluggin in the Lubuntu-Software center videos on youtube and other flash contents look like on the 
picture below.(i tried firefox and chromium)

I also tried Gnash but firefox don t even list it in the plugins after the installation.

Is there some way to get flash running on ubuntu without beeing an expert.

---

### Post by Frogs Hair on 2013-08-22
Hello and Welcome 

Please provide some information about your computer hardware. Flash will no longer work on some older CPU's . The following terminal command will indicate what processor you have.   ```
lspci
```

---

### Post by BazBear on 2013-08-22
Obviously do what Frog's Hair has asked; but I'm curious, is this a new install of Lubuntu, and hence it's first Flash player, or is it just the latest Flash update that screwed it up?

---

### Post by michael35 on 2013-08-24
thanks for your response,

lscpi:

> 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:03.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to CSA Bridge (rev 02)
00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
02:01.0 Ethernet controller: Intel Corporation 82547EI Gigabit Ethernet Controller


I don t know if this problem also accured with the preinstalled flash i can just remember that i installed the flashpackage from the lubuntu-software center one month ago and then i don t cared about the problem because the person for who i installed the pc told me that he doesn t need flash.

Flash is removed at the moment, i tried lightspark but at the place where the flash content should be shown I  only see an gray rectangle.

---

### Post by vasa1 on 2013-08-24
> **michael35 said:**
> Hello, 
after installing the flash pluggin in the Lubuntu-Software center videos on youtube and other flash contents look like on the 
picture below.(i tried firefox and chromium)
....
The image you posted is very similar to one posted here: [http://askubuntu.com/questions/335124/flash-player-a-big-bug](http://askubuntu.com/questions/335124/flash-player-a-big-bug)

It's possible the same solution may work for you.

BTW, I don't wish to sound negative but I'd forget about Gnash and lightspark, etc.

---

### Post by michael35 on 2013-08-24
problem solved :cool:, 

I had to install the intel graphics driver:

[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)


thanks for your help

---

### Post by abdulmajid on 2014-01-05
> **michael35 said:**
> problem solved :cool:, 

I had to install the intel graphics driver:

[https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2](https://01.org/linuxgraphics/downloads/2013/intelr-linux-graphics-installer-version-1.0.2)


thanks for your help

Which package did you install? I am getting some dependency error while isntalling. :(

> abdulmajid@abdulmajid-Ezeebee-MAX4781:~$ cd Downloads/abdulmajid@abdulmajid-Ezeebee-MAX4781:~/Downloads$ ls
intel-linux-graphics-installer_1.0.2-0intel3_i386.deb
abdulmajid@abdulmajid-Ezeebee-MAX4781:~/Downloads$ sudo dpkg -i intel-linux-graphics-installer_1.0.2-0intel3_i386.deb 
[sudo] password for abdulmajid: 
Selecting previously unselected package intel-linux-graphics-installer.
(Reading database ... 151026 files and directories currently installed.)
Unpacking intel-linux-graphics-installer (from intel-linux-graphics-installer_1.0.2-0intel3_i386.deb) ...
dpkg: dependency problems prevent configuration of intel-linux-graphics-installer:
 intel-linux-graphics-installer depends on libpackagekit-glib2-14; however:
  Package libpackagekit-glib2-14 is not installed.
 intel-linux-graphics-installer depends on ttf-ancient-fonts; however:
  Package ttf-ancient-fonts is not installed.


dpkg: error processing intel-linux-graphics-installer (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Errors were encountered while processing:
 intel-linux-graphics-installer
abdulmajid@abdulmajid-Ezeebee-MAX4781:~/Downloads$ 




---

### Post by mörgæs on 2014-01-05
Don't install the Intel drivers into a 13.10 system. Better to add an xorg.conf as described here:
[https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-November/006117.html)

---

### Post by abdulmajid on 2014-01-06
I have installed an older version of kernel which fixed the issue. Previously it was 3.11 something, but now with 3.2.1-030201-generic it is fixed.

---

