---
title: "Ubuntu 11.04-Program and driver installation problems"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by Goranm on 2011-10-28
Hello! 
 
I have a problem with installing programs in Ubuntu 11.04. I can't install any programs, including drivers, for Linux. Not to mention Windows programs and drivers. I have Wine installed, and only update works. Even after making files executable, nothing. I get error reports, and that in order to install, say, my graphics driver I have to be root, but when I am root, it doesn't work. GUI doesn't help either.
 
Any help appreciated. 
 
Thanks!
 
Goran

---

### Post by varunendra on 2011-10-30
I am just posting here as a BUMP hoping a **graphics** expert would see it and take it from here.

@Goranm,
From your previous thread, I assume you are mostly concerned about your display driver here. In order to let us know about your display hardware, please post output of:
```
sudo lshw -C display
```

While you post the above outputs, please try this:
Make sure you are connected to internet. Open Software-Center > open "Edit" menu > click "Software Sources" > (supply your password) > make sure the check-box against "Proprietary drivers for devices" option has tick-mark in it. Close the box, let Software Center refresh itself, then close it.
Now press Alt+F2, type **jockey-gtk** in the search box and press 'Enter' (or click its icon that appears while typing). This will open "Additional Drivers" box. See if any driver for your graphics is offered there. If there is, just click it, then click "Activate". Close the box and restart to see if it works.

To install other programs for Ubuntu, you can use either "Software Center" or Synaptic Package Manager.


[B]_PS_:
[/B]About windows programs:
Wine can install and run many windows programs, but not all of them. There are many popular ones that won't run on wine. If you specifically need any of those, you should either consider a dual boot with windows, or using a virtualization solution like virtualbox.

About windows drivers:
Except for a few wireless drivers (through ndiswrapper), no windows drivers work on Linux, through wine or any other way. So there is nothing to try.

---

### Post by oldos2er on 2011-10-30
For Windows programs, check the Wine app database to see if there's a chance they will work. [http://appdb.winehq.org/](http://appdb.winehq.org/)

You should probably look for native Linux solutions instead of trying to run Windows apps; Linux is not Windows and is not meant to be a replacement for Windows.
 
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by Goranm on 2011-10-31
> 
 
You should probably look for native Linux solutions instead of trying to run Windows apps; Linux is not Windows and is not meant to be a replacement for Windows.
 
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
 
Hello! 
 
Thanks for replying! 
 
Yes, I did that. I tried to find the drivers I could for Linux, but there are no any. Particularly I need a driver for my audio card, a professional studio recording card, **M-AUDIO DELTA 44**. 
There is a link to a Linux driver for the card, but I was not able to find it there. 
I did install the graphics driver. 
 
That's why I need WINE, but can't install it for some reason. 
**sudo apt-get install wine1.2 **does not finish the job for some reason. It stops. 
But, I think it's because of my internet connection. I had problems with that. 
[http://ubuntuforums.org/showthread.php?t=1849353](http://ubuntuforums.org/showthread.php?t=1849353)
 
So, basically, the drivers I need I can't find for Linux. 
 
Yes, I am relatively new to Linux, but I am completely aware it is not a replacement for Windows. :) That's why I got it in the first place. And I love using the Terminal in Ubuntu! 
Thanks for the link, though! Interesting reading. And I couldn't agree more! 
 
Goran

---

### Post by oldos2er on 2011-10-31
Windows drivers won't run with Wine; they won't work with Linux, period.

Can you post the output of **lspci** ? From the small amount of googling I did, your sound card show work.

---

### Post by Goranm on 2011-11-02
> **oldos2er said:**
>  
Can you post the output of **lspci** ? From the small amount of googling I did, your sound card show work.
 
As requested. :) 
 
Output:
[LIST]
[*]**lscpi**
[/LIST]```

00:00.0 RAM memory: nVidia Corporation MCP61 LPC Bridge (rev a1) 
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2) 
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2) 
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2) 
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) 
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3) 
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1) 
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2) 
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2) 
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2) 
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2) 
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control 
01:06.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02) 
01:07.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI 
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1) 

``` 
 
I hope that helps. I need sound! :)

---

### Post by Goranm on 2011-11-02
> **varunendra said:**
> I am just posting here as a BUMP hoping a **graphics** expert would see it and take it from here.
 
@Goranm,
From your previous thread, I assume you are mostly concerned about your display driver here. In order to let us know about your display hardware, please post output of:
```
sudo lshw -C display
```

 
I took care of the graphics driver. 
 
Thanks!

---

### Post by oldos2er on 2011-11-02
"Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)"

Ubuntu sees your sound card. Have you checked to see if sound is muted? That sometimes happens after installation. Run **alsamixer** in a terminal to check.

---

### Post by Goranm on 2011-11-02
> **oldos2er said:**
> "Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)"
 
Ubuntu sees your sound card. Have you checked to see if sound is muted? That sometimes happens after installation. Run **alsamixer** in a terminal to check.
 
Yes, I know it does see it. But, that is the integrated sound card which I do not use, I use ***M AUDIO DELTA 44*** instead. I need to install drivers for that one. That's a professional sound card, that's why I need it.

---

### Post by oldos2er on 2011-11-02
How is the other sound card installed? PCI or ?

---

### Post by Goranm on 2011-11-03
> **oldos2er said:**
> How is the other sound card installed? PCI or ?
 
Yes, PCI.

---

