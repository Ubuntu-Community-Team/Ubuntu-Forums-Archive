---
title: "Dualboot - Install 7.10...black screen..??"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by toga34 on 2008-01-22
[FONT="Verdana"][COLOR="Navy"]I would like to complete install but run into snafu.

I would like dualboot vista/ubuntu 7.10
so I downloaded live cd and rebooted...selected start or install...
starts to load....
keymap...
loading hardware drivers...
etc...
starting gnome graphic something...

then the whole screen goes black...and stays that way..

I've tried 6.06 desktop...7.10 desktop...

tried safe mode....

..I did shrink vista partion to make room so i know there is enough space...NE1 know what the problem might be and what I can do to fix...thank you for your help in advance.

my specs are:

Operating System: Windows Vista&#8482; Home Premium (6.0, Build 6000) (6000.vista_gdr.071009-1548)
           Language: English (Regional Setting: English)
System Manufacturer: Hewlett-Packard
       System Model: HP Pavilion dv9000 (GA355UA#ABA)  
               BIOS: PhoenixBIOS 4.0 Release 6.1     
          Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-56 (2 CPUs), ~1.8GHz
             Memory: 1918MB RAM
          Page File: 932MB used, 3127MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 10



my vids...

Card name: NVIDIA GeForce Go 6150
     Manufacturer: NVIDIA
        Chip type: GeForce Go 6150
         DAC type: Integrated RAMDAC
       Device Key: Enum\PCI\VEN_10DE&DEV_0244&SUBSYS_30B7103C&REV_A2
   Display Memory: 394 MB
 Dedicated Memory: 122 MB
    Shared Memory: 271 MB
     Current Mode: 1440 x 900 (32 bit) (60Hz)
          Monitor: Generic PnP Monitor
      Driver Name: nvd3dum.dll
   Driver Version: 7.15.0010.9746 (English)
      DDI Version: 9Ex
Driver Attributes: Final Retail
 Driver Date/Size: 12/6/2006 22:25:00, 3055616 bytes
      WHQL Logo'd: Yes
  WHQL Date Stamp: 
Device Identifier: {D7B71E3E-4104-11CF-9E55-BD1002C2CA35}
        Vendor ID: 0x10DE
        Device ID: 0x0244
        SubSys ID: 0x30B7103C
      Revision ID: 0x00A2
      Revision ID: 0x00A2



Video Compressors:
WMVideo8 Encoder DMO,0x00600800,1,1,,
WMVideo9 Encoder DMO,0x00600800,1,1,,
MSScreen 9 encoder DMO,0x00600800,1,1,,
DivX Encoder Filter,0x00200000,1,1,divxenc.ax,5.02.0000.1257
DV Video Encoder,0x00200000,0,0,,6.06.6000.16386
MJPEG Compressor,0x00200000,0,0,,6.06.6000.16587
Roxio MPEG1 Encoder,0x00200000,1,1,MPEG1VidCodec.dll,9.00.0002.0006
Roxio MPEG2 Encoder,0x00200000,1,1,MPEG2VidCodec.dll,9.00.0002.0006
Cinepak Codec by Radius,0x00200000,1,1,,6.06.6000.16386
DivX® 5.2.1 Codec,0x00200000,1,1,,6.06.6000.16386
Intel IYUV codec,0x00200000,1,1,,6.06.6000.16386
Intel IYUV codec,0x00200000,1,1,,6.06.6000.16386
Microsoft RLE,0x00200000,1,1,,6.06.6000.16386
Microsoft Video 1,0x00200000,1,1,,6.06.6000.16386


I know most would say that 1st off the problem is windows..i agree but I need the ******* to run photoshop cs3....[/COLOR][/FONT]

---

### Post by toga34 on 2008-01-22
I get the funny feling I'm being ignored, every one else atleast gets some reply, weather it helps or not but can any one think of why the black screen of death is upon me?

---

### Post by EricMeijer on 2008-01-24
Not being ignored, but sometimes it takes a while before someone who can answer your question is reading your post. We are all volunteers.

Now a suggestion to solve your problem: Try to install with the alternate CD. It uses textmode.
Further: Don't burn your CD with too high a speed. It saves you from writing errors which are vulnarable to these kind of installation CD's.

If you encounter any post installation graphics problems I advise you to enter: sudo nano /etc/X11/xorg.conf
change in the section "Device" the Driver to "vesa".
Close the file with Cntrl + x
Initialize using  "sudo /etc/init.d/gdm start
Possibly you can configure your graphics card in graphics mode now.

---

### Post by minidido on 2008-01-24
I am also having the smae problem.

Dual booting ubuntu, If i try to run the live CD it loads the hard ware drivers etc. Then displays a black screen and i have to Physically restrt my computer.

I also have a Turion 64 with 2 gigs of ram.

---

### Post by EricMeijer on 2008-01-24
Download and burn the alternate CD !
Here's the link.

[http://nl.releases.ubuntu.com/7.10/](http://nl.releases.ubuntu.com/7.10/)

Find your documentation here:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

