---
title: "No sound in 10.04 beta2"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ulvergr on 2010-04-09
Hello,
today i installed 10.04 beta2 i have problem with the sound....i don't have sound!Can anybody help me?in previous versions 9.04-9.10 i didn't had any problems.
(the volume is up,lol)
thank you.

---

### Post by sandyd on 2010-04-09
> **ulvergr said:**
> Hello,
today i installed 10.04 beta2 i have problem with the sound....i don't have sound!Can anybody help me?in previous versions 9.04-9.10 i didn't had any problems.
(the volume is up,lol)
thank you.
theirs these problems cause its a beta.
when going to a beta, prepare for heavy breakage.

can you post the output of ```

lspci
```

---

### Post by overdrank on 2010-04-09
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by cariboo on 2010-04-09
Open a terminal and type:

```
pulseaudio -k
```

to see if your sound starts working.

---

### Post by Captain_Kirk on 2010-04-09
do you login as "root"? Sound doesn't work there anymore (root-punishment :lolflag:)

---

### Post by crjackson on 2010-04-09
> **Captain_Kirk said:**
> do you login as "root"? Sound doesn't work there anymore (root-punishment :lolflag:)

If you are logged in on a LiveCD/USB you are always root.  For me, I have to "sudo killall pulseaudio" in the terminal.  After that sound works for the LiveUSB here.

---

### Post by cariboo on 2010-04-10
I just ran the command as the normal ubuntu user on the Live CD, I could see an immediate change in the sound icon in the notification area, then played the .spx file in the example folder. pulseaudio -k does the same thing as killall pulseaudio. From pulseaudio -h

```
pulseaudio -h
pulseaudio [options]

COMMANDS:
  -h, --help                            Show this help
      --version                         Show version
      --dump-conf                       Dump default configuration
      --dump-modules                    Dump list of available modules
      --dump-resample-methods           Dump available resample methods
      --cleanup-shm                     Cleanup stale shared memory segments
      --start                           Start the daemon if it is not running
  -k  --kill                            Kill a running daemon
      --check                           Check for a running daemon (only returns exit code)

```

---

### Post by ulvergr on 2010-04-10
> **cariboo907 said:**
> Open a terminal and type:

```
pulseaudio -k
```to see if your sound starts working.


the sound now works also the icon has changed,but after the restart i have the same problem
i have installed 10.04 in 2 pc's.
one desktop and one live usb.

---

### Post by feiy on 2010-04-10
me too,after update 04.09,and i try pulseaudio -k,but no sound also!

---

### Post by tica vun on 2010-04-10
Confirming. Sound didn't work after update, pulseaudio -k fixed it.

---

### Post by feiy on 2010-04-10
pulseaudio -k can't fixed it in my thinkpad x200

feiy@feiy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

---

### Post by Rifester on 2010-04-10
I also have no sound on the live CD.    After typing pulseaudio -k in terminal the volume icon changed and sound worked.  This is the first sound issue I have ever had in Linux.  Could anybody tell me why?   Is this because of a new version of pulse audio in Lucid Lynx?  I had no problems in Karmic, Jaunty, etc.

Thanks!
Mark

lspci:


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

---

### Post by kouter on 2010-04-10
only have sound in amarok, none in games, flash, or vlc.

```
pulseaudio -k
```

does NOT work for me =/


```
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
```

---

### Post by kouter on 2010-04-10
recent update or [this script]("http://www.webupd8.org/2010/04/ubuntu-1004-first-time-use-script-02.html") fixed the sound problem.

---

### Post by sandyd on 2010-04-10
> **feiy said:**
> pulseaudio -k can't fixed it in my thinkpad x200

feiy@feiy-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)
00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)
00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
thats odd.
i have exactly the same card as you in my laptop, and it works okay.
in this case, ill start from the begining...

tell me, is your user in the pulse-rt and the pulse-access groups?

can you post the output of
```

cat /etc/asound.conf
```?

if it says /etc/asound.conf does not exist, run
```

gksudo gedit /etc/asound.conf
```

plunk this in
```

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
```

restart, and try sound.
}

---

### Post by sandyd on 2010-04-10
> **MRife said:**
> I also have no sound on the live CD.    After typing pulseaudio -k in terminal the volume icon changed and sound worked.  This is the first sound issue I have ever had in Linux.  Could anybody tell me why?   Is this because of a new version of pulse audio in Lucid Lynx?  I had no problems in Karmic, Jaunty, etc.

Thanks!
Mark

lspci:


00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
pulseaudio was always rather finky.

fyi, this is the current problem. [https://bugs.launchpad.net/bugs/557421](https://bugs.launchpad.net/bugs/557421)

suprisingly, pulseaudio works OOB without fiddling for the first time that ive had it on my computer.....

---

### Post by cariboo on 2010-04-10
See bug #[lpbug]549738[/lpbug] post #9 for an explanation of what is happening. This time it isn't a pulse problem. :)

---

### Post by sandyd on 2010-04-11
what the heck?....

---

### Post by steviepoophd on 2010-04-13
I have the same behavior on my HP Pavilion dv7 laptop.  Beta 1 had sound and Beta 2 did not.

---

### Post by murthy on 2010-04-18
I had the same problem.  **'pulseaudio -k'** worked for me, but only after opening the mixer and increasing the volume (which was muted).

---

### Post by thedevilisbad on 2010-04-20
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller




I don't have any sound either, nothing shows up in the status bad, and I can't really mess with sound settings because my card isn't detecting like it used to. "pulseaudio -k" didn't do squat for me.

---

### Post by dino99 on 2010-04-20
This howto might help you with your problem:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

- note that is for hda driver, but you can easily find your way with your hardware chipset

- the best you can do when things goes wrong is to remove/purge all alsa & pulse packages installed and the hidden related files ( .pulse* )

- clean your cache: sudo apt-get clean/autoclean/autoremove
- sudo apt-get install -f
- sudo apt-get update ( be sure first that your sources.list only point to lucid and comment all third party repo and ppa )

- then install & run gconf cleaner
- reboot
-reinstall alsa & pulseaudio & paprefs
- reboot

- goto system -- pref --sound to see if your hardware is correctly detected
- install & run gnome-alsamixer: set your tweaks
- run alsamixer

---

