---
title: "Feisty and no sound after install"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by huckey on 2007-04-22
Hi,
   I used to have Edgy and tried to upgrade to Feisty which I did successfully but then I messed up with my video drivers and since my Edgy was only a week old (that's more or less how experienced with Linux I am :-) ) I decided to do a clean install of Feisty.

   After I have installed Feisty I now seem to have a problem with both my sound card (more important) and my webcam (less important). I know I had my sound card working OK in Edgy (I do not know about the webcam).

   Here is my lspci:
 ```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV31 [GeForce FX 5600XT] (rev a1)
02:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
02:05.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
02:0c.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
02:0c.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port

```

   And here is my lsdev:
```
Device            DMA   IRQ  I/O Ports
------------------------------------------------
0000:00:1d.0                 eec0-eedf
0000:00:1d.1                 ef00-ef1f
0000:00:1d.2                 ef20-ef3f
0000:00:1d.3                 ef40-ef5f
0000:00:1f.0                 0480-04bf 0800-087f
0000:00:1f.1                 0170-0177 01f0-01f7 0376-0376 03f6-03f6 fc00-fc0f
0000:00:1f.2                 ef90-ef9f efa0-efa7 efa8-efab efac-efaf efe0-efe7
0000:00:1f.3                 0400-041f
0000:02:03.0                   dc00-dc7f
0000:02:05.0                   d800-d8ff
0000:02:0c.0                   df80-df9f
0000:02:0c.1                   dfe0-dfe7
acpi                      9 
ACPI                           0800-0803   0804-0805   0808-080b   0828-082f
cascade             4       
dma                          0080-008f
dma1                         0000-001f
dma2                         00c0-00df
ehci_hcd:usb5            19 
EMU10K1                  20      df80-df9f
emu10k1-gp                       dfe0-dfe7
eth0                     22 
floppy              2     6  03f2-03f5 03f7-03f7
fpu                          00f0-00ff
i8042                  1 12 
iTCO_wdt                       0860-087f
keyboard                     0060-006f
libata                14 15 18    0170-0177   01f0-01f7   0376-0376   03f6-03f6   ef90-ef9f   efa0-efa7   efa8-efab   efac-efaf   efe0-efe7   fc00-fc0f
nvidia                   16 
ohci1394                 21 
parport0            3     7  0378-037a 037b-037f 0778-077a
PCI                          0cf8-0cff d000-dfff
pic1                         0020-0021
pic2                         00a0-00a1
pnp                          0290-0297 0680-06ff
rtc                       8  0070-0077
serial                       02f8-02ff 03f8-03ff
skge                             d800-d8ff
timer                     0 
timer0                       0040-0043
timer1                       0050-0053
uhci_hcd                       eec0-eedf   ef00-ef1f   ef20-ef3f   ef40-ef5f
uhci_hcd:usb2            17 
vga+                         03c0-03df

```

   And that's my lsusb (for the webcam):
```
Bus 005 Device 006: ID 05e3:070e Genesys Logic, Inc. 
Bus 005 Device 005: ID 1058:0901 Western Digital Technologies, Inc. 
Bus 005 Device 003: ID 04b8:0122 Seiko Epson Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 046d:08f6 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000
```  
   Sound tests available in System->Preferences->Sound produce no sound though buttons have a green tick (which I assume stands for OK). Also playing video in Totem does not produce any sound.

   Can you help me with getting sound working (more important) and my webcam working too (less important)?

Huckey

---

### Post by pepsi_max2k on 2007-04-22
Have you got both onboard sound and a sound card? could be that feisty has set a different sound system than the one you want to use a default. see [http://ubuntuforums.org/showpost.php?p=2501007&postcount=2](http://ubuntuforums.org/showpost.php?p=2501007&postcount=2)

---

### Post by huckey on 2007-04-22
Hi,
  I actually have an onboard sound card but I have it disabled in BIOS. I have also checked the list of available sound cards following the tip in the thread you quoted and the system shows only my Creative Audigy sound card. Therefore, using methods described there is not applicable for my situation, alas.

   Are there any other ways to try to solve the issue with sound?

   Thanks!


Huckey

---

### Post by huckey on 2007-04-23
Hi all,
  I have browsed through many threads here and I can see that there are more people having problems with Audigy sound cards and Feisty.

  I did some additional checks and:
- sound works with Edgy Live CD;
- sound _does not work_ with Feisty Live CD;
- sound _does not work_ with fresh Feisty installation.

   In one of the threads someone suggested that this results from different version of ALSA being used with Edgy and with Feisty. If this suggestion is sensible, can someone advise me how to get an older version of ALSA installed?

  On top of that I discovered that when testing sound in System->Preferences->Sound in Edgy Live CD I get the orange rectangle moving from one side of the progress bar to another while sound is played. When testing sound with Feisty I can see that the orange rectangle is frozen in the left hand end of the progress bar. Maybe this is a hint.

   I am getting a bit desperate now. Do you have any ideas how to solve the issue with no sound?

Huckey

---

### Post by Gibran on 2007-04-26
> **huckey said:**
> Hi all,
  I have browsed through many threads here and I can see that there are more people having problems with Audigy sound cards and Feisty.

  I did some additional checks and:
- sound works with Edgy Live CD;
- sound _does not work_ with Feisty Live CD;
- sound _does not work_ with fresh Feisty installation.

   In one of the threads someone suggested that this results from different version of ALSA being used with Edgy and with Feisty. If this suggestion is sensible, can someone advise me how to get an older version of ALSA installed?

  On top of that I discovered that when testing sound in System->Preferences->Sound in Edgy Live CD I get the orange rectangle moving from one side of the progress bar to another while sound is played. When testing sound with Feisty I can see that the orange rectangle is frozen in the left hand end of the progress bar. Maybe this is a hint.

   I am getting a bit desperate now. Do you have any ideas how to solve the issue with no sound?

Huckey


Excellent post, that is exactly my problem as well. Help, anyone?

---

### Post by Maxtorm on 2007-04-26
My sound broke after a Feisty install and I now have it working again.  I did the following:
```
asoundconf reset-default-card
alsamixer
```
For some reasons, almost all of the alsa channels were muted (MM).  I just unmuted them (M key in alsamixer) and everything is back to the way it was in Edgy.

---

### Post by Gibran on 2007-04-26
> **Maxtorm said:**
> My sound broke after a Feisty install and I now have it working again.  I did the following:
```
asoundconf reset-default-card
alsamixer
```
For some reasons, almost all of the alsa channels were muted (MM).  I just unmuted them (M key in alsamixer) and everything is back to the way it was in Edgy.


Thank you, but unfortunately it did not work for me. Still stuck!!

---

### Post by djamu on 2007-04-26
go here, 

[http://ubuntuforums.org/showthread.php?t=419974]("http://ubuntuforums.org/showthread.php?t=419974")

feisty sets the audigy digital output as default, 
double click the audio icon ( top bar )>  switches > disable digital

---

### Post by Gibran on 2007-04-27
> **djamu said:**
> go here, 

[http://ubuntuforums.org/showthread.php?t=419974]("http://ubuntuforums.org/showthread.php?t=419974")

feisty sets the audigy digital output as default, 
double click the audio icon ( top bar )>  switches > disable digital

Problem solved, thanks!

---

### Post by djamu on 2007-04-27
you're welcome

---

