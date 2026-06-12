---
title: "How do I reconfigure the external monitor to ubuntu 11"
date: 2011-06-24
forum: Installation &amp; Upgrades
---

### Post by jmlynn on 2011-06-24
Hi,

I just upgraded my Ubuntu V10.4 LTS to Ubuntu 11.  After that, I lost my external monitor and I cannot find those usual "preferences", "Administration" navigational menus on top of the screen.:(

Stumbled into Multiple Monitors under System, but it didn't detect the second monitor.  However, the 2nd monitor was active and with system startup messages displayed there during reboot.  But as soon as the desktop appear, that 2nd monitor lost its signal.

Any idea how to get my 2nd monitor back is appreciated!:D

Jeff

---

### Post by jmlynn on 2011-06-24
I started up ubuntu V11 using live USB stick, got deskstop screen almost like V10.04.  Here, I can reconfigure the external monitor via the "Prefeences->monitors" menu.

However, I got a totally different desktop screen from the Live USB Stick startup, here, I lost the top menu bar that houses the "Preferences", "Administrator" etc menu.
On top of that, when I use the "System Setting" and tried to configure Monitor there, it list current monitor as Unknown and is unable to see the second monitor.

Any help is greatly appreciated!

Jef,

---

### Post by MAFoElffen on 2011-06-24
> **jmlynn said:**
> Hi,

I just upgraded my Ubuntu V10.4 LTS to Ubuntu 11.  After that, I lost my external monitor and I cannot find those usual "preferences", "Administration" navigational menus on top of the screen.:(

Stumbled into Multiple Monitors under System, but it didn't detect the second monitor.  However, the 2nd monitor was active and with system startup messages displayed there during reboot.  But as soon as the desktop appear, that 2nd monitor lost its signal.

Any idea how to get my 2nd monitor back is appreciated!:D

Jeff
if from a commandline, you 
```

xrandr -q

```
Does your second monitor show in the results?

What video chipset shows up in (?)
```

lspci -vv | grep VGA

```
Is there a /etc/X11/xorg.conf file?  If so, please post.

---

### Post by jmlynn on 2011-06-24
Here is what I got.j

jmlynn@JL-TECRA-NB:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 512, current 1680 x 1050, maximum 1680 x 1050
default connected 1680x1050+0+0 0mm x 0mm
   1680x1050      50.0*    51.0  
   1400x1050      52.0  
   1280x1024      53.0  
   840x525        54.0     55.0  
   700x525        56.0  
   640x512        57.0  


jmlynn@JL-TECRA-NB:~$ lspci -vv | grep VGA
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- NoISA- VGA- MAbort- >Reset- FastB2B-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+
01:00.0 VGA compatible controller: nVidia Corporation G86M [Quadro NVS 150M] (rev a1) (prog-if 00 [VGA controller])
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset- 16bInt+ PostWrite+
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-

I don't see my external molnitor, which is Dell 1907 LCD monitor whereas my notebook is a Toshiba Tecra LCD panel.

Thanks!

Jeff

---

### Post by jmlynn on 2011-06-24
Two things I don't understand.

1) botting up the USB stick gave me the traditional Ubuntu desktop, with system menu on the top menu bar, whereas the installed version gave a different desktop without the usual menu.

2) Live >USB stick allows me to reconfigure dual monitor using the "Monitor" icon in System ->preference (or Aedministration, I forogt)

Why is that?

Jeff

---

### Post by MAFoElffen on 2011-06-24
> **jmlynn said:**
> Two things I don't understand.

1) botting up the USB stick gave me the traditional Ubuntu desktop, with system menu on the top menu bar, whereas the installed version gave a different desktop without the usual menu.

2) Live >USB stick allows me to reconfigure dual monitor using the "Monitor" icon in System ->preference (or Aedministration, I forogt)

Why is that?

Jeff
Sounds like something in the install's are different.

"nVidia Corporation G86M [Quadro NVS 150M)"  
 - Are you using current nvidia drivers?

Usual technique, if not showing up, to manually add and configure in the xorg.conf.  But you may have already ID'ed an install problem.

---

### Post by jmlynn on 2011-07-13
I have no clues to where the driver is.  However, after I many tries of trying to reconfigure Monitors and the NVidia XServer settings without any change.  But the next time when I rebooted the machine, lo and behold, I now was able to select the external monitor in extended desktop mode.

So I still had no clues what happened.  But that is ok. 

Thanks for suggestions!

Jeff

---

