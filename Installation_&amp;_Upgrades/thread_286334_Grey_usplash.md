---
title: "Grey usplash"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by phork on 2006-10-27
After upgrading to Edgy the usplash screen during the boot is a grey and black and the progress bar is segmented.  Has anyone else experienced this?

---

### Post by toxygen on 2006-10-28
yes.
I have the same problem.

Linux thermaltake 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

model name      : AMD Athlon(tm) 64 Processor 3500+

---

### Post by phork on 2006-10-28
Here are the details on my system:
Linux fame 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
04:08.0 Network controller: RaLink Unknown device 0302
04:0a.0 Communication controller: Agere Systems Unknown device 0620

AMD Athlon(tm) 64 X2 Dual Core Processor 4200+

Any ideas?

---

### Post by peter07 on 2006-10-28
I have the same problem. I can only see a black ubuntu logo and nothing else.

Any ideas?

---

### Post by Cosmic_Crusader on 2006-10-29
Yup me to, on an AMD64 platform with and ATI X700 video card.

If I boot up using hte 386 LiveCD I get color but it's a grainy..

---

### Post by hajk on 2006-10-29
Same here: grey splash on AMD64, coloured splash on i386 (the latter running in Parallels VM with "vga=792" boot option).

---

### Post by Marcelo Fernández on 2006-10-29
I have the same issue here, in an AMD64 - Nvidia 6600 card :-? 

Marcelo

---

### Post by wilberfan64 on 2006-10-29
I thought I should get in on this thread--same deal here.   I re-clean-installed Edgy last night--and even the Live CD splash was greyscale !

AMD 64x2

---

### Post by peter07 on 2006-10-30
Please look here:

[http://ubuntuos.com/2006/02/howto-change-the-default-usplash-colors](http://ubuntuos.com/2006/02/howto-change-the-default-usplash-colors)
It's a copy of:
[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)
which is the best HOWTO for ubuntu, but on ubuntuOS site we can find usplash.png:
[http://www.ubuntuforums.org/attachment.php?attachmentid=3197&stc=1&d=1130425734](http://www.ubuntuforums.org/attachment.php?attachmentid=3197&stc=1&d=1130425734)
I don't have time now, but maybe someone can try to make new usplash using one of these method?


You can also check this:

[http://ubuntuos.com/2006/02/searching-for-splash-image-none-found-skipping](http://ubuntuos.com/2006/02/searching-for-splash-image-none-found-skipping)

---

### Post by metalfreak666 on 2006-10-30
Hi ! I have an gray usplash since the RC ... AMD64

---

### Post by wilberfan on 2006-10-30
I wonder if we're dealing with a known bug here?

[https://wiki.ubuntu.com/EdgyEft/Beta](https://wiki.ubuntu.com/EdgyEft/Beta)

Look near the bottom of the page:

> On certain platforms with 64-bit CPUs and NVIDIA graphics, the graphical boot screen does not function and a blank screen is displayed. The solution is to wait patiently for the login screen to appear ([WWW] #56587).

---

### Post by prs on 2006-10-30
> **wilberfan said:**
> I wonder if we're dealing with a known bug here?

[https://wiki.ubuntu.com/EdgyEft/Beta](https://wiki.ubuntu.com/EdgyEft/Beta)

Look near the bottom of the page:

Not exactly - that bug report indicates that *nothing at all* is visible (and mostly with nvidia cards), but I use an ati graphics card and can at least see the grey ubuntu image. It would be nice to get some colors, however - it worked fine when I upgrade Xubuntu 6.06.1 to 6.10, funny that Ubuntu has this bug.

---

### Post by peter07 on 2006-10-30
Maybe we must report new bug?

---

### Post by teddy879 on 2006-10-30
Bug [#67545]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/67545") has already been reported... doesn't seem like there's a resolution yet.

---

### Post by Valehru on 2006-10-30
Same problem here, updated from dapper (spalsh was fine) went to Edgy (usplash is grey and flickering).  I also have the problem that when I leave gnome for a terminal Alt+Ctrl+F5 etc, the terminal is also flickering much the same as the usplash.  This is only a problem in Edgy.  Using the 64 bit image as well with nvidia drivers.  Gnome is fine by the way.

---

### Post by wilberfan on 2006-10-31
I loaded the Kubuntu desktop (AND the Xubuntu one, too!) over the weekend, and their usplash screens seem OK...

---

### Post by A_arthur_N on 2006-11-06
I am also getting the same problem, 64bit Edgy,

Sempron 3000+
Nvidia 6100

---

### Post by rko618 on 2006-11-20
I'll add myself to the list

Core 2 Duo e6400
64bit Edgy

I am shocked to find there is no known solution to this problem.

---

### Post by mod2422 on 2006-11-20
+1 with the same problem.
I'm very dissapointed that one month after final release such an annoying and reproducible bug isn't fixed...

Running edgy on an AMD64x2 3800+

Rgds
Mod2422

---

### Post by mithion on 2006-11-29
I'm also running Edgy 64bit with an AMD 64 3300 processor and a X700 ATI card.  I have the gray usplash at bootup.  So +1 with the problem.

---

### Post by 454redhawk on 2006-12-16
Same problem here.

AMD opteron 170 dual core.
ASUS EN7600GS graphics card.

---

### Post by Wall86 on 2006-12-16
i have had the same problem, but my computer never actually bots up to ubuntu, win xp is running fine, it is just ubuntu, i have flashed my bios and everything,

would there be any way to install the new Nvidia drivers without having to boot?

AMD Athlon 64 x2 3800
1GB RAM
BFG Geforce 7300 gs OC
foxconn 6100 m2ma board.

ubuntu 6.10 64 bit vrsn
just downloaded the i386. and the other versiosn of 6.06

---

