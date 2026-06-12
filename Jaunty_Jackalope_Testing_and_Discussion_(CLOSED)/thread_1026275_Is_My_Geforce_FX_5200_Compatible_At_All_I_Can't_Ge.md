---
title: "Is My Geforce FX 5200 Compatible At All? I Can't Get it Recognized."
date: 2008-12-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2008-12-30
My test box has a Geforce FX 5200, and I cannot get Ubuntu Jaunty (64-bit) to recognize it. When I run jockey-kde, it says that there are no proprietary drivers available. If I install the nvidia drivers manually, and then set it up in xorg.conf, I get a black screen. (Not even bulletproof X).

Here is the output of lspci:
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge        
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge        
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge        
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge        
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge        
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge          
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]                                                                              
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller  
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller  
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)                                                                           
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)                                                  
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)                                                                       
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] AddressMap
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M890CE/K8N890CE [Chrome 9] (rev 11)
04:04.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
04:05.0 Ethernet controller: Belkin Device 700f (rev 20)
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)

```

Is this video card supported?

---

### Post by jrusso2 on 2008-12-31
You will have better luck with 32 bit.  Or a video card that has 6s4 bit drivers.

---

### Post by jlacroix on 2008-12-31
> **jrusso2 said:**
> You will have better luck with 32 bit.  Or a video card that has 6s4 bit drivers.

Do you think that's the issue? It worked with Intrepid. I gave up 32-bit completely and I don't have any plans of downgrading...

I forgot to mention, I tried Envy and it ended up in a black screen.

---

### Post by Frak on 2008-12-31
You'll need to use this driver

[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

---

### Post by jrusso2 on 2008-12-31
Good Find Frak.

---

### Post by jlacroix on 2008-12-31
> **Frak said:**
> You'll need to use this driver

[http://www.nvidia.com/object/linux_display_amd64_173.14.12.html](http://www.nvidia.com/object/linux_display_amd64_173.14.12.html)

The 173 driver is in the repositories, and it wants to remove all of the xorg packages. :(

---

### Post by autocrosser on 2008-12-31
Take a look at the "xorg breakage" thread & follow dinxter's bit about "no ABI" in your xorg.conf & then hand-install the driver from nVidia. The only repository driver working right now (and that is via PPA), is the new 180.18...and it will not support your card. 

Right now, due to the Xorg update--many drivers are broken--ATI, Intel & nVidia--you could use the "nv" driver--it WILL work--if you can call it that :(

Sorry about the no joy, but that is the way alpha testing goes......Alberto is working on it, but I'll bet it's a couple of weeks before nVidia drivers are all up & running......

---

### Post by tepsipakki on 2009-01-01
alberto can't fix the drivers, since nvidia should need to publish new versions for xserver 1.6 first.

---

### Post by plun on 2009-01-01
> **tepsipakki said:**
> alberto can't fix the drivers, since nvidia should need to publish new versions for xserver 1.6 first.

Well... I am not going to argue about it but the beta drivers just works and there is also a ppa version for the 180 driver...

Driving users to Windows 7  :confused:


@jlacroix

**Please take a look at the driver situation here:**

[http://www.nvnews.net/vbulletin/showthread.php?t=122606](http://www.nvnews.net/vbulletin/showthread.php?t=122606)


As you can see there is a **beta driver** for 5XXX cards > **173.14.15**

You must install this driver in **recovery mode** because tty is also broken.


xorg.conf must also include a ignoreABI option

```
Section "ServerFlags"
          Option  "IgnoreABI" "True"
EndSection
```

---

