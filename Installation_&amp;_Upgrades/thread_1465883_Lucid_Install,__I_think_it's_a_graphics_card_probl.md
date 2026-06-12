---
title: "Lucid Install,  I think it's a graphics card problem, but not sure.. help?"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Rasa1111 on 2010-04-29
Hey all, 
  Hey Irihapeti~ lol

I know the last thing anyone wants/or needs at the moment is another thread needing help....
 and I do apologize for starting yet another new thread, seeking help
on the day of a new release, when there are already tons of people seeking help,
but my problem was on the verge of hijacking a thread,
 and the kind Soul of Irihapeti suggested that I do make a thread, so here I am, .... 
Thanks man, hope you see my thread! lol

i agree, it does sound like a graphics card problem, but i really dont know much about that, so......

  
 My problem, 
 
 I have gone through 4 discs now,  and all the discs check out fine.... 
no problem with the discs I am now quite sure....

 I start my machine,  and all goes well for a brief time.... 

 It boots and loads up, and the pretty screen comes up, 
 Then I have the option to either ..
"Try 10.04 without any changes"
            or 
"Install 10.04 LTS"

   I choose "try w/out changes" , 
and the screen to "choose your language" comes up,
I choose it, ...   machine acts like its going to progress....

 then, 1 of 2 things have been happening... 

1) Screen goes black, and into 'power saving mode', (no signal to monitor)....
and no matter how long it sits, it progresses no further. 

  or 2)  after choosing my language,  the screen goes black 
(but with power to it~ /backlit black).. and starts flashing white/grey vertical lines at me, 
but only on the top half of the monitor.....  
 and this is what it continues doing, and doing, and doing... no progression after that. 

I have been asked to post the output of  this
> sudo lspci -vv -nnhere,  so this is what I have... (sorry it's long)

```
00:00.0 Host bridge [0600]: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface [8086:2560] (rev 03)
    Subsystem: Dell Device [1028:0147]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort+ <MAbort+ >SERR- <PERR- INTx-
    Latency: 0
    Region 0: Memory at e8000000 (32-bit, prefetchable) [size=64M]
    Capabilities: [e4] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)
    Subsystem: Dell Device [1028:0147]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e0000000 (32-bit, prefetchable) [size=128M]
    Region 1: Memory at ee000000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 1
        Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: i915
    Kernel modules: i915

00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 02)
    Subsystem: Dell Device [1028:0147]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 16
    Region 4: I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 02)
    Subsystem: Dell Device [1028:0147]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 19
    Region 4: I/O ports at d000 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 02)
    Subsystem: Dell Device [1028:0147]
    Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin C routed to IRQ 18
    Region 4: I/O ports at d400 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 02) (prog-if 20)
    Subsystem: Dell Device [1028:0147]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin D routed to IRQ 23
    Region 0: Memory at ee080000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 82)
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR+ INTx-
    Latency: 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
    I/O behind bridge: 0000c000-0000cfff
    Memory behind bridge: ec000000-edffffff
    Prefetchable memory behind bridge: 40000000-400fffff
    Secondary status: 66MHz- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort+ <MAbort- <SERR- <PERR-
    BridgeCtl: Parity- SERR+ NoISA+ VGA- MAbort- >Reset- FastB2B-
        PriDiscTmr- SecDiscTmr- DiscTmrStat- DiscTmrSERREn-
    Kernel modules: shpchp

00:1f.0 ISA bridge [0601]: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge [8086:24c0] (rev 02)
    Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface [0101]: Intel Corporation 82801DB (ICH4) IDE Controller [8086:24cb] (rev 02) (prog-if 8a [Master SecP PriP])
    Subsystem: Dell Device [1028:0147]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin A routed to IRQ 18
    Region 0: I/O ports at 01f0 [size=8]
    Region 1: I/O ports at 03f4 [size=1]
    Region 2: I/O ports at 0170 [size=8]
    Region 3: I/O ports at 0374 [size=1]
    Region 4: I/O ports at f000 [size=16]
    Region 5: Memory at 40100000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: ata_piix

00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 02)
    Subsystem: Dell Device [1028:0147]
    Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Interrupt: pin B routed to IRQ 11
    Region 4: I/O ports at 0500 [size=32]
    Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 02)
    Subsystem: Dell Device [1028:0147]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 0
    Interrupt: pin B routed to IRQ 17
    Region 0: I/O ports at e000 [size=256]
    Region 1: I/O ports at e400 [size=64]
    Region 2: Memory at ee081000 (32-bit, non-prefetchable) [size=512]
    Region 3: Memory at ee082000 (32-bit, non-prefetchable) [size=256]
    Capabilities: [50] Power Management version 2
        Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: Intel ICH
    Kernel modules: snd-intel8x0

01:06.0 Modem [0703]: Broadcom Corporation BCM4212 v.90 56k modem [14e4:4212] (rev 02)
    Subsystem: Dell Device [1028:0001]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 18
    Region 0: Memory at ed002000 (32-bit, non-prefetchable) [size=4K]
    Region 1: I/O ports at c000 [size=16]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=2 PME-
    Kernel driver in use: serial

01:09.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Dell Device [1028:8127]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort+ <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32
    Interrupt: pin A routed to IRQ 17
    Region 0: Memory at ed000000 (32-bit, non-prefetchable) [size=8K]
    [virtual] Expansion ROM at 40000000 [disabled] [size=16K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
        Status: D0 PME-Enable- DSel=0 DScale=2 PME-
    Kernel driver in use: b44
    Kernel modules: b44



``` can anyone help a brother out? 

 I mean, really I am just trying to 'test drive' 10.04, and see if it is going to work as well as my karmic does,  and I see all the people posting how amazing it is, and I cant even check it out. lol

 I do love Karmic Koala , 
( it runs flawlessly on my box)
but would like to learn how to take care of this, if possible. 

 many thanks. 

 rasa
<3

---

### Post by Irihapeti on 2010-04-29
Yes, I think you may be right about it being a graphics card problem. I think you may have the same problem that I did on my beat-up old Toshiba Satellite A10.

So, here is what *should* work:

At the very first screen, the one with just the rectangle (it's meant to be a keyboard) and a human figure, press any key - spacebar will do.

Then choose your language.

Then make sure you have "Try Ubuntu without any changes" selected, and then press F6

Add this to the end of the command line: ```
i915.modeset=0 xforcevesa
```

Then press enter and it should boot successfully.

Now, mine is a slightly different graphics chip from yours, so we'll just have to see what happens.

---

### Post by Rasa1111 on 2010-04-29
ahh thank you bro. 
 yeah, my box is rather "old" next to most today. lol

Dell Dimension 2350
 2.3 GHz CPU
1 GB Ram

 Im going to try it out now, Ill post back shortly. Thanks again man,
much appreciated! 
Praises.
Rasa

---

### Post by Shigoki-linux on 2010-04-29
ya. same thing is happening to me. but i just only get a blank screen. it comes up, and after waiting like 15 seconds, blank screen, monitor go to sleep. i hope this is just a bug that will be sorted out asap.

---

### Post by Rasa1111 on 2010-04-29
Wow! 

 That worked!! :D
Amazing, man!!  lol 

Thank you!!

(posting this from Lucid Lynx now.. BIG lucid lynx).. lol

only issue i see now is.....
well,....   It is not detecting my monitors resolution... 
 everything is just really BIG! lol

 Ive attached a few screenshots to show.

 I went into "monitors" , and for some reason I cant select anything, 
and I cant change the resolution from anything but 640x480. 

 Is this just because Im running from the CD? 
I dont remember Karmic doing this from the CD though. 

 What do you think is the problem?

 I cant believe that worked so well though! 
that's awesome. 

 you rock Irihapeti!

---

### Post by Irihapeti on 2010-04-29
Hey, this is great news!

There have been some changes since Karmic. I also was able to boot Karmic with no immediate problems, but there were some lockups later on that weren't fun.

I'm not quite sure why it's running in low graphics mode (640x480) but I would guess that you have a monitor that's widescreen i.e. not the old 4:3 ratio. My EeePC with a wide screen did something similar.

You probably have a file called /etc/X11/xorg.conf  Can you post the contents of that?

Meanwhile I see what I can find about fixing this.

---

### Post by Rasa1111 on 2010-04-29
Great news indeed, friend! 
> 
You probably have a file called /etc/X11/xorg.conf  Can you post the  contents of that?sure I would love to... 
but my n00bness is preventing me from finding it.....

 Ive used the "search for files" under apps/accessories...
but it didnt find it. 

 Do you know of an easy way for me to find said file? or its contents?
through terminal maybe? 

my monitors normal resolution is 1024 x 768. 

 I am looking through google and its given links, and find some similar probs, but no solutions.... yet..  like this link... [http://guide.ubuntuforums.org/showthread.php?t=1352344](http://guide.ubuntuforums.org/showthread.php?t=1352344)

 thank you again.
your time and help is greatly appreciated!
may the karma return to you mate.  :) <3

---

### Post by Irihapeti on 2010-04-29
Well, 1024x768 is the same as my old Toshiba, and it's the old 4:3 ratio, not widescreen, so I don't know why it isn't working.

You could see if that setting exists in System -> Preferences -> Monitors 

To get the contents of that file easily, in a terminal type:
```
cat /etc/X11/xorg.conf
```

---

### Post by Rasa1111 on 2010-04-29
niice, thanks. :)

 here is the contents from terminal...

> ubuntu@ubuntu:~$ cat /etc/X11/xorg.conf
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection


 i don't get it...  lol

but as an added note of positivity...
even in low graphics mode....
I am impressed! lol

:)

Praises

---

### Post by Irihapeti on 2010-04-29
That's exactly the same as I have, so that's fine.

Now for some fun stuff. This is an experiment, so I want to take it carefully, and if anyone else watching this thread is better informed, please speak up.

First of all, let's back up that xorg.conf file, because we are going to play with it and we want a fallback in case it all turns to custard. :)

In a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

And again in a terminal:
```
xrandr
```
and ```
cvt 1024 768
```

---

### Post by Rasa1111 on 2010-04-29
> **Irihapeti said:**
> That's exactly the same as I have, so that's fine.

Now for some fun stuff. This is an experiment, so I want to take it carefully, and if anyone else watching this thread is better informed, please speak up.

First of all, let's back up that xorg.conf file, because we are going to play with it and we want a fallback in case it all turns to custard. :)

In a terminal:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```And again in a terminal:
```
xrandr
```and ```
cvt 1024 768
```

sweet,

done.
done.
and done!  :) lol 
thanks! 

all done, Ive got terminal minmized..
dont know if I should close it or what next. 

did i mention... you rock?!?  lol  :D
thanks so much, 
we need to get you a ' pay raise' somehow ....  :lol:  ;)

edit: oops, just looking at terminal again, 
did you want me to post anything that came back from those commands?

---

### Post by Irihapeti on 2010-04-29
Did running those terminal commands actually fix something, or did they just create messages on the screen?

Posting the output of the messages might be useful.

I'm getting to the limits of my knowledge here, so we may need to find someone else who knows more than  I do :)

---

### Post by neuroscientist on 2010-04-30
I have a Dell 700m with Intel 855GM graphics.  In order to upgrade to 10.04, I had to add "i915.modeset=0 xforcevesa" to the command line as mentioned above.

I am experiencing the same problem with increasing screen resolution mentioned by Rasa1111.  I believe my normal max is 1280 X 800.  I can set my resolution to 1024 X 768, but I used to have it higher using 9.10.

What can I do?

---

### Post by Rasa1111 on 2010-04-30
> Did running those terminal commands actually fix something, or did they  just create messages on the screen?

Posting the output of the messages might be useful.

I'm getting to the limits of my knowledge here, so we may need to find  someone else who knows more than  I do :smile:

hey, 
no worries, you've been a huge help! 

no it didnt actually change anything, 
i was thinking maybe restarting was needed,
but then remembered its running from the CD and any changes would probably be gone upon restart right?
i also wanted to wait for your reply before i did restart. . :lol: 

heres what came out in terminal..
> ubuntu@ubuntu:~$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 640 x 480, current 640 x 480, maximum 640 x 480
default connected 640x480+0+0 0mm x 0mm
   640x480         0.0* 
ubuntu@ubuntu:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
ubuntu@ubuntu:~$ 

 what did that do/ should have done anyway? 

the Universe is good,
 im sure it will send another helpful, 
kind soul in eventually. lol :)
 thanks friend! 

 how to get out of low graphics mode... hmm.........

<3

---

### Post by Rasa1111 on 2010-04-30
> **neuroscientist said:**
> I have a Dell 700m with Intel 855GM graphics.  In order to upgrade to 10.04, I had to add "i915.modeset=0 xforcevesa" to the command line as mentioned above.

I am experiencing the same problem with increasing screen resolution mentioned by Rasa1111.  I believe my normal max is 1280 X 800.  I can set my resolution to 1024 X 768, but I used to have it higher using 9.10.

What can I do?


 hey friend, 
so we are in this together... good deal.. we will get it figured out eventually... lol :popcorn:
ohh, and you upgraded to.... not running from CD...

hmm...
i searching.....

---

### Post by neuroscientist on 2010-04-30
Yes, I did a clean install of 10.04.

What did "i915.modeset=0 xforcevesa" do?

Is there a way to change the mode to allow higher resolutions?

---

### Post by Irihapeti on 2010-04-30
Rasa1111
I think that Lucid isn't properly picking up your screen definition.
The output on my Toshiba laptop is:

```
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  

```
 Notice that xrandr on your machine doesn't say anything about the 1024 x 768 resolution.

I'm not sure how to go from here. I tried some experiments on my laptop and it just made a big mess (fixed now). I don't want to do that to you people. You could ask a question on Launchpad and/or file a bug report. I'll keep looking around and if I find anything interesting I can post back here.

---

### Post by neuroscientist on 2010-04-30
What about doing this to get a driver?

[http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/)

---

### Post by Irihapeti on 2010-04-30
> **neuroscientist said:**
> What about doing this to get a driver?

[http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/](http://absolutebeginner.wordpress.com/2006/07/26/installing-intel-815852855-graphics-controller-drivers-on-ubuntu-debian/)

The date on the post is 2006, and a lot has changed in Ubuntu since then. So I doubt that it would work. The drivers are in the current kernel but they aren't working properly. Some fixes are in the pipeline, but meantime we need to get something working as a stopgap.

---

### Post by neuroscientist on 2010-04-30
Your right, I tried it an it didn't work.

---

### Post by Irihapeti on 2010-04-30
I think I'm getting somewhere with this. Could you run in a terminal:
```
xvidtune
```

DO NOT adjust anything if it gives you a way to do that. I am interested in what it displays in the terminal, which will be something like this:

```
Vendor: (null), Model: (null)
Num hsync: 1, Num vsync: 1
hsync range 0:  30.00 -  81.00
vsync range 0:  56.00 -  75.00

```

---

### Post by Rasa1111 on 2010-04-30
hi bro, 
sure, 
 this is what i get.. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=154769&stc=1&d=1272609960[/IMG]
hmm... no idea there..
 thanks for still helping. :)

---

### Post by Chronon on 2010-04-30
If you look through the currently reported bugs for Lucid, you will see a pair of them for Intel chips.  One of them is here:
[https://bugs.launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-intel/+bug/541511](https://bugs.launchpad.net/ubuntu/lucid/+source/xserver-xorg-video-intel/+bug/541511)

---

### Post by Irihapeti on 2010-04-30
Rasa1111:
Here is a modified xorg.conf that I think (hope!) will do something useful. In case you are wondering, I got the numbers from the stuff you posted earlier.

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Intel"
	Modelname	"Old 1024x768"
	Horizsync	31.00-63.00
	Vertrefresh	56.0-75.00
	Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection	"Display"
		Depth	24
		Virtual 1024 768
		Modes	"1024x768_60"
	EndSubSection
EndSection

```

You can edit your existing xorg.conf by typing
```
gksu gedit /etc/X11/xorg.conf
```

The easiest way is probably to copy the whole of the code block above and paste it over the existing text, but that's up to you.

When you've saved that, log out and in again. At the login screen, type "ubuntu" as the user name and leave the password blank.

There's a slight risk of doing some damage to the monitor if it's wrong, or so they say, so if there's flickering or anything that looks serious, run the command
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```
and then log out and in again.

---

### Post by dolson on 2010-04-30
^^ He should only have to change "vesa" to "intel" and then save and reboot. The monitor and other lines shouldn't be needed.

I also added the DRI line, as seen here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

(I have this same issue and used the workaround to install).

Edit: Oh, I also created a new file /etc/modprobe.d/i915-kms.conf and put the following line in it:
options i915 modeset=1

I don't know if that helps at all, but so far, so good.

---

### Post by Irihapeti on 2010-04-30
@dolson
I'd say you probably know more about it than I do, so I'm happy for you to take over. I'll still stick around in case there's anything useful I can add.

---

### Post by Rasa1111 on 2010-04-30
@ **Irihapeti**

  Thank you man. :)

 Here is what happened,  it doesn't make sense to me, but it happened...

 I did as you said, and pasted over the contents and saved it,
  then I went to log out, ...  and screen went black, but a little box popped up warning me about low graphics mode..
and gave me a list of options,  I chose "restore to default" because it made most sense to me.. lol..

 then, all i got was the black prompt screen, waiting for me to type a command, but I didnt know what to type...

so i used r.e.i.s.u.b to restart it......  and then it got interesting.........

 At the purple screen " [keyboard]= (human)" ... I hit spacebar as you suggested earlier..
chose english....   and instead of hitting F6 this time...  I just chose " try without changes"..
 to see if anything fruitful would emerge...... 

and wouldnt you know it.. here I am typing to you on a normal resolution screen!! :lol:

check it out... screenshot attached.. 

Interesting............

 So, If im getting this right...
   If i let the CD just load on its own (without me hitting spacebar at the purple screen)...
and wait until the "GUI install or try without changes" window pops up,
 the system will not load up...... 

If i DO hit spacebar at the purple screen (instead of letting it load up to the gui window), and then choose the "try without changes"
 Its starts perfectly fine.. 

does that sound about right?  lol

 if that's the case..
next question:....  what does this mean if I were to do do a full install?
does it sound like id run into this again? 
or what if i just did the "upgrade" instead? 

because.. as happened to neuroscientist, 
he had it fully installed and still encountered this problem... 

 Thank you Irihapeti, you are beautiful. .. and beyond helpful!

**Dolson**, thanks for joining and the info. :)
we could give our friend Irihapeti a break here.   lol  :KS

new Q to you:
 So, does it sound to you like I should be ok installing it.. or will I likely run into this again once its installed? or dont you have any idea?
sorry for being a pain. lol

 many thanks.

:)

 edit: darn!! i really do love Karmic...
but now that this is working as it should... 
i am really tempted to install it.... 
even though i should sleep...  lol :/

---

### Post by Irihapeti on 2010-04-30
Well, Rasa1111, I don't know quite what's happened there, but if it's working, great.

I've learned some stuff along the way, and that can't be bad.

If I may make a suggestion, it would be to get a good night's sleep and then do an install.

---

### Post by Rasa1111 on 2010-04-30
> **Irihapeti said:**
> Well, Rasa1111, I don't know quite what's happened there, but if it's working, great.

I've learned some stuff along the way, and that can't be bad.

If I may make a suggestion, it would be to get a good night's sleep **and then do an install**.


 aww but I dont wanna sleeep. :lol:

naw, i agree, good advice..... again!  lol :)

I will do that :KS

 so you think a fresh install is better than the upgrade then?

theoretically...
if I were to click this icon on the desktop , from the CD.. "Install Ubuntu 10.04 LTS"
what would that do to whatever files that are in my pc, in karmic?
Should I take them and put them on my external first, or will Ubuntu keep them?
(i feel that's a dumb question) lol

  With an 'upgrade' ...
all my files and applications/programs would stay where they are right?
(i think so anyway)
if so, does that change if i were to 'install" rather than 'upgrade'?  

ok, sleep for a few hours i guess.. :lol:

Thanks soo much! you have made, out of a stressful  and completely lost situation..
a pleasurable experience!! lol  well done. <3

 I too learned a bit today.. lol, 
thanks a ton.:P zzzzzzzzz

ohh, 
i cant believe how fast this is! lol
i thought karmic was fast and responsive.. 
firefox to..,
definitely faster. 
crazy.
niiice.   \|/ <3 :)

---

### Post by Irihapeti on 2010-04-30
Well, I don't know whether it was me who 
> ..."made, out of a stressful and completely lost situation..
a pleasurable experience!!"

In fact, it may have been a case of the blind leading the blind :)

If you click that icon, the installer will wipe out all your files. So, back up first. Copy your home folder to an external disk or whatever.

An upgrade should, in theory, keep all your settings. In practice, they seem often to cause a lot of problems. YMMV, as they say. It still pays to [backup]("http://ubuntuforums.org/showpost.php?p=9161389&postcount=1"), though, in case nasty things happen.

---

### Post by drorlev on 2010-04-30
Hi guys.

Can anyone let me know if there is a similar solution for an ATI graphich card?
The card is ATI Radeon Xpress 1250

I'm running an LG E300 which functioned ok with Karmic.

Thanks,
dror

---

### Post by neuroscientist on 2010-04-30
I used workaround A found here:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

...and am looking at a 1280 X 800 (16:10) screen resolution!

Thanks all.

---

### Post by drysdan on 2010-04-30
I got my HP dv1000 (with Intel 855gm) to boot from the livecd properly, with full 1280x768 by pressing f6 at the menu and adding this to the command line:

```
i915.modeset=1
```

It's basically the same as Workaround A that neuroscientist linked to, but it's at the command line in the boot menu.  

I haven't taken the plunge and done a full install, but it booted and ran great from the livecd.

---

### Post by Unicast on 2010-04-30
> **drysdan said:**
> I got my HP dv1000 (with Intel 855gm) to boot from the livecd properly, with full 1280x768 by pressing f6 at the menu and adding this to the command line:

```
i915.modeset=1
```

It's basically the same as Workaround A that neuroscientist linked to, but it's at the command line in the boot menu.  

I haven't taken the plunge and done a full install, but it booted and ran great from the livecd.

I had the same problem with my dell laptop - spec below (855GM chipset)

I did a full install after booting the live cd using the kernel option "i915.modeset=1"

Then I edited grub, instructions here: [http://ubuntuforums.org/showpost.php?p=9171045&postcount=11](http://ubuntuforums.org/showpost.php?p=9171045&postcount=11)

Hope this helps someone.

Quite disappointing to see this bug is still in the final version of 10.04

---

### Post by Rasa1111 on 2010-04-30
Hey all, 

 Lucid is installed! :)

 All i did, 

Was, as Irihapeti told me,
 press the spacebar at the purple screen, ..

and then did everything 'as normal' .. clicked install, and it installed.
I am using it now, everything looks as it should. :)
( but i didnt save my firefox bookmarks!! DOHH!)

Question though.... 

I see software center works a little differently now, 

VLC just took like 15 minutes to install, ( installed much faster in karmic)

actually...  everything I try to get in software center seems to take an exceptionally long time for some reason.. 

 Now, I cant find VLC anywhere in my system, after that long 'install'.
what happened? 

VLC isnt even showing up in software center under "installed software" now either... 

also,... in synaptic...
 I tried to find VLC player, and Ubuntu restricted extras,
but I cannot find them in there anywhere?

what am i doing wrong? or is it the system? 

or have I not done something that needs to be done? i dont know.. 

Thanks everyone for the posts!

 Im gonna try to figure this out.. be back inna bit...  lol

praises

---

### Post by Irihapeti on 2010-04-30
Rasa1111:
Good that you've got it installed.

Ubuntu-restricted-extras is definitely in the repositories. Maybe you need to check "repositories" in Synaptic and make sure that you have all four main sources checked.

---

### Post by Halavar on 2010-04-30
It seems to be a persistent issue with the 82845/855 graphic chipsets.  It did this to me in the 9.04 release as well.  Amusingly enough, it was apparently fixed for the 9.10 release, which installed clean.  It's back though in Lucid.  Doesn't matter whether I try a fresh install or an upgrade, it doesn't like the chipset still.  <sigh>

Apparently it's an upstream issue, which could take awhile for a fix, if ever.  That said, the 845/855 series was pretty prolific for better or for worse, so it may come sooner than later.

---

### Post by Irihapeti on 2010-04-30
Yes, it's an upstream issue. I've had a bug open on this issue for some months now and done quite a bit of testing. If you want to help, some of you could file new bug reports or contribute to existing ones (hint, hint).

The vesa driver is a basic generic driver which at least allows you to get up and running. I have to run the vesa driver on my main computer (a different graphics chip altogether) as well. That means no Compiz, but I can live with that.

---

### Post by Rasa1111 on 2010-04-30
> **Irihapeti said:**
> Rasa1111:
Good that you've got it installed.

Ubuntu-restricted-extras is definitely in the repositories. Maybe you need to check "repositories" in Synaptic and make sure that you have all four main sources checked.

  and She is right again! hehe. 

 I got it all working great now, VLC is installed and running, and restricted extras is almost done installing. :D

I just had to change the server location.. 
seems the 'regular' one was overloaded with lots of people. :)

good stuff, thanks!!:KS <3

---

### Post by bill1357 on 2010-04-30
Thank's to all.
This is what worked for me.


 echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
 sudo update-initramfs -u

---

### Post by Rasa1111 on 2010-04-30
good to hear bill. :)

 New question:... lol..

 I have installed stellarium, 
however, when I try to open it... 

my screen goes buggy for a second,  and the same thing that was happening earlier with the CD's happens. ( screen goes black, and starts flashing white vertical stripes across the top half of the screen)

 then i have to use alt-sysrq/ reisub to get it to restart. 

seems like another 'graphics card' issue... 

 and i may have missed the 'already posted solution...
if so i apologize..

 but what should I do? lol

*hides face*........

---

### Post by Irihapeti on 2010-04-30
Rasa1111
Have you got visual effects turned on? If so, try turning that off and see what happens.

You might still find that you need the vesa graphics driver. These Intel bugs seem to be tricky things, and what will work for one person doesn't for another one. The problem then is that some programs don't work with visual effects turned off. :(

Reporting a bug might also be useful. :)

---

### Post by Rasa1111 on 2010-04-30
> **Irihapeti said:**
> Rasa1111
Have you got visual effects turned on? If so, try turning that off and see what happens.

You might still find that you need the vesa graphics driver. These Intel bugs seem to be tricky things, and what will work for one person doesn't for another one. The problem then is that some programs don't work with visual effects turned off. :(

Reporting a bug might also be useful. :)

 thanks again. :)
i will report a bug for sure. 

yeah I have special efects turned off. (my pc wont even run compiz/special effects) lol
thats cool tho, i dont mind. 

in regards to the vesa driver....

is that something i can just download/install?
if so, from where, and how?

 I remember previous posts/threads talking about it,
but I really dont know which thread of the many it is in. lol

 thanks a million. :)

---

### Post by Irihapeti on 2010-04-30
The vesa driver is already in the kernel. To activate it, you'd need to edit your xorg.conf, like we talked about earlier in this thread, and log out and in again.

Of course, it still may not work properly. This is one of the frustrating things about graphics bugs, unfortunately.

Edit: if you don't have an xorg.conf, then make one.

---

### Post by Ambystoma on 2010-04-30
> **Unicast said:**
> I had the same problem with my dell laptop - spec below (855GM chipset)

I did a full install after booting the live cd using the kernel option "i915.modeset=1"

Then I edited grub, instructions here: [http://ubuntuforums.org/showpost.php?p=9171045&postcount=11](http://ubuntuforums.org/showpost.php?p=9171045&postcount=11)

Hope this helps someone.

Quite disappointing to see this bug is still in the final version of 10.04

@Unicast, 
Thanks so much for the info. I finally got it to work w/ your instructions, and a couple of tweaks. Chiefly, I had to boot into the live cd again once Lucid was finally installed to make a couple of permanent changes to two config files (including grub).  I've detailed what worked for me in the master bug thread (#541511) in post #118. Hope it helps someone also. BTW, my PC is a Dell D400 with the i855 graphics card. Thanks again.

---

### Post by dolson on 2010-04-30
> **Irihapeti said:**
> @dolson
I'd say you probably know more about it than I do, so I'm happy for you to take over. I'll still stick around in case there's anything useful I can add.

I didn't mean to step on any toes or anything, just was reporting what had worked for me... However, it ended up that the system locked up for me after a while, so the "fix" didn't really fix the issue.

This is really disappointing. I'm setting up Ubuntu on a Windows user's PC, trying to convert them since they were sick of Windows being crappy. And it turns out that Linux won't even run without locking up randomly... Argh.

---

### Post by Irihapeti on 2010-04-30
> **dolson said:**
> I didn't mean to step on any toes or anything, just was reporting what had worked for me... However, it ended up that the system locked up for me after a while, so the "fix" didn't really fix the issue.

This is really disappointing. I'm setting up Ubuntu on a Windows user's PC, trying to convert them since they were sick of Windows being crappy. And it turns out that Linux won't even run without locking up randomly... Argh.

No, you weren't stepping on any toes. I just looked at your join date, a couple of years earlier than mine, and made an assumption that you'd know more.

The Intel graphics bugs are a real pain, and there's no guarantee that if you follow a particular bug fix and it appears to work, you won't still get a lockup. The only thing I can say for sure is that the vesa fix does work. If you want to go that way, you'd have a system that's basically usable. I've had to use it for the last nearly three years on my desktop PC.

I think I have a better idea now what we need to do to get vesa to work, so I'm willing to contribute.

---

### Post by dolson on 2010-04-30
> **Irihapeti said:**
> No, you weren't stepping on any toes. I just looked at your join date, a couple of years earlier than mine, and made an assumption that you'd know more.

The Intel graphics bugs are a real pain, and there's no guarantee that if you follow a particular bug fix and it appears to work, you won't still get a lockup. The only thing I can say for sure is that the vesa fix does work. If you want to go that way, you'd have a system that's basically usable. I've had to use it for the last nearly three years on my desktop PC.

I think I have a better idea now what we need to do to get vesa to work, so I'm willing to contribute.

I've run Linux exclusively since 2002, but it's been about 4 years since I did anything more than daily use and really basic troubleshooting. I did some packaging back before Ubuntu Studio became a flavor of Ubuntu (I started the original project, which was actually a wiki), but it's been quite a while... And my knowledge seems to get outdated with each Ubuntu release.

Anyhow, I was using vesa after the install, but couldn't get it out of 640x480 without changing back to intel... And I'm not sure how to change that.

---

### Post by Irihapeti on 2010-04-30
> **dolson said:**
> Anyhow, I was using vesa after the install, but couldn't get it out of 640x480 without changing back to intel... And I'm not sure how to change that.

Well, what should work is to use a xorg.conf file like the one I posted for Rasa1111 earlier.

You would need to generate your own modeline values by running ```
cvt X Y
``` where X is the horizontal resolution you  want, and Y is the vertical. For instance, on my EeePC it is 1024 and 600.

You can get the horizsync and vertrefresh values from your monitor's manual if you have one or from its setup menu. If it's a laptop, then neither of those options may be available, and the values I've put in the xorg.conf file will *probably* be OK, but watch out for flicker or excessive fan noise (overheating). Running xvidtune may tell you something, but on my EeePC it did nothing whatever. You can of course tweak the values, log out and in again, and see what that does.

---

### Post by dolson on 2010-04-30
> **Irihapeti said:**
> Well, what should work is to use a xorg.conf file like the one I posted for Rasa1111 earlier.

You would need to generate your own modeline values by running ```
cvt X Y
``` where X is the horizontal resolution you  want, and Y is the vertical. For instance, on my EeePC it is 1024 and 600.

You can get the horizsync and vertrefresh values from your monitor's manual if you have one or from its setup menu. If it's a laptop, then neither of those options may be available, and the values I've put in the xorg.conf file will *probably* be OK, but watch out for flicker or excessive fan noise (overheating). Running xvidtune may tell you something, but on my EeePC it did nothing whatever. You can of course tweak the values, log out and in again, and see what that does.

Thanks for that. I'm not sure I can do this though, because I have the PC at my house, while her monitor is different. I have an LCD, the PC owner has a CRT by another company.

I may look at downgrading the kernel, as it's supposedly a solution.

It really boggles my mind how this regression managed to occur.

---

### Post by Irihapeti on 2010-04-30
Monitor manuals are sometimes available online, or you may find one for a similar model.

---

### Post by Unicast on 2010-05-01
@Ambystoma
You're most welcome.

Just feel it's such a shame that this bug wasn't squashed before 10.04 was released.

10.04 beta2 ran perfectly, and then they went and broke things in the RC. #fail

---

### Post by dr.frankinfurter on 2010-05-01
I have a similar problem. I was enable to run the live cd using the 'i915.modeset=1' boot parameter. I installed and now the same parameter won't work when I run it through grub. The best I can get is getting to the failsafex command from the safeboot. Then it defaults me to that 'your graphics has failed' menu thing. The menu is displayed in 640x480 resolution so... I can't do anything. I tried the solution posted by Irihapeti for Rasa1111 earlier (I tweaked it using the data I got from my own 'xrandr' and 'crt' outputs) and... I got an error saying the xorg.conf file couldn't be parsed and I ended up in the 'your graphics has failed please choose an option' thing. I don't know what's it called, but I remember seeing it when I had graphics problems with 9.10 (and with 8.04).

 Anyways, what should I do? 

 I've already spent hours upon hours trying to fix this issue. Honestly, I'm wondering why I should stick with Ubuntu. Release after release I encounter nothing but bugs upon bugs. Now, in this release, I can't even boot the dang thing. What good is Ubuntu if I can't even get to the desktop? And, what does it say about an operating system that requires extensive fiddling just to get it to function at a basic level? I'm thinking about abandoning ship and picking up a distribution that takes stability seriously or maybe even go back to Windows (I have it on a partition but if I can't even 'use' my Linux partition..). I saw that the chipset bug was reported so I didn't report it myself - but the more important question is why in the world wasn't it fixed? Anyways, /rant.

 Any help would be appreciated.

---

### Post by drysdan on 2010-05-01
> **dr.frankinfurter said:**
> I have a similar problem. I was enable to run the live cd using the 'i915.modeset=1' boot parameter. I installed and now the same parameter won't work when I run it through grub. The best I can get is getting to the failsafex command from the safeboot. Then it defaults me to that 'your graphics has failed' menu thing. The menu is displayed in 640x480 resolution so... I can't do anything. I tried the solution posted by Irihapeti for Rasa1111 earlier (I tweaked it using the data I got from my own 'xrandr' and 'crt' outputs) and... I got an error saying the xorg.conf file couldn't be parsed and I ended up in the 'your graphics has failed please choose an option' thing. I don't know what's it called, but I remember seeing it when I had graphics problems with 9.10 (and with 8.04).

 Anyways, what should I do? 

 I've already spent hours upon hours trying to fix this issue. Honestly, I'm wondering why I should stick with Ubuntu. Release after release I encounter nothing but bugs upon bugs. Now, in this release, I can't even boot the dang thing. What good is Ubuntu if I can't even get to the desktop? And, what does it say about an operating system that requires extensive fiddling just to get it to function at a basic level? I'm thinking about abandoning ship and picking up a distribution that takes stability seriously or maybe even go back to Windows (I have it on a partition but if I can't even 'use' my Linux partition..). I saw that the chipset bug was reported so I didn't report it myself - but the more important question is why in the world wasn't it fixed? Anyways, /rant.

 Any help would be appreciated.


I had that issue too.  Here's what I did:

In the GRUB list, boot into recovery mode.  When the menu comes up, scroll to the bottom, to open a root shell.
At the shell prompt, enter this command:

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
```

followed by this command:

```
sudo update-initramfs -u
```

then type 'reboot'


Basically, this makes the modeset=1 a permanent feature, rather than enabling it in GRUB.  If it booted normally from the livecd with i915.modeset=1, then this should make it boot normally from there on.

(this set of commands was taken from solution 'A' at [https://wiki.ubuntu.com/X/Bugs/Lucid8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucid8xxFreezes")


Hope it helps!

---

### Post by drorlev on 2010-05-01
> **drysdan said:**
> I had that issue too.  Here's what I did:

In the GRUB list, boot into recovery mode.  When the menu comes up, scroll to the bottom, to open a root shell.
At the shell prompt, enter this command:

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
```

followed by this command:

```
sudo update-initramfs -u
```

then type 'reboot'


Basically, this makes the modeset=1 a permanent feature, rather than enabling it in GRUB.  If it booted normally from the livecd with i915.modeset=1, then this should make it boot normally from there on.

(this set of commands was taken from solution 'A' at [https://wiki.ubuntu.com/X/Bugs/Lucid8xxFreezes]("https://wiki.ubuntu.com/X/Bugs/Lucid8xxFreezes")


Hope it helps!

Hi, what works for me is adding 'nomodeset' to the boot options using the live-cd.
Does it mean that if I replace ```
echo options i915 modeset=1
``` with ```
echo options nomodeset
``` I should be ok?

Thanks,
dror

---

### Post by drorlev on 2010-05-01
I finally solved my problem \\:D/ 

by creating the file: 
/etc/modprobe.d/radeon-kms.conf 

with this ```
options nomodeset
```

inspired by what is written on KMS [here]("https://wiki.ubuntu.com/X/KernelModeSetting"). -=D>

Now, Lucid Lynx :guitar:

dror

---

### Post by AbdRahim on 2010-05-01
after unicast's suggestion install went fine.  On reboot I get the blank screen again so how do I makke th grub modifications?  Try without installing also gives blank screen.

---

### Post by AbdRahim on 2010-05-01
after unicast's suggestion install went fine.  On reboot I get the blank screen again so how do I makke th grub modifications?  Try without installing also gives blank screen. Can't get to recovery mode.

---

### Post by romulus on 2010-05-01
I have same issue

---

### Post by romulus on 2010-05-01
I will try same fix too.

---

### Post by Rackstar on 2010-05-01
> **romulus said:**
> I have same issue

People having the same issue, please comment or click "this affects me too" on the bug on launchpad:
[https://bugs.launchpad.net/ubiquity/+bug/572868](https://bugs.launchpad.net/ubiquity/+bug/572868)

Your contribution to the bug will improve the importance, and likeliness of it being fixed for those who are less computerliterate to fix it themselves.

---

### Post by romulus on 2010-05-01
i915.modeset=0 xforcevesa not working for me:confused:

---

### Post by AbdRahim on 2010-05-01
Solution B worked to get the system up and running. 

Thanks all.

AbdRahim

---

### Post by dolson on 2010-05-02
I tried messing with xorg.conf stuff, modelines, different kernel module options, blah blah blah.

The system still randomly screws up. I could be using it for 5 minutes or maybe 5 hours, doing something or doing nothing, and suddenly, BAM, screen blinks a couple times and goes completely black, system won't respond to anything, not even Alt+SysRq+[KSUB]...

The best I can do is 1024x768 intel driver with random lockups, or 640x480 with vesa, with no apparent lockups. The latter is NOT workable in the year 2010. Seriously.

I am pretty agitated by this. I wish I knew how to fix it for everyone, because I totally would. 10.04 is running fine on my netbook, so if I could just get around this problem on this desktop, I'd be happy with it. I can't even just buy a new video card, because this isn't my system, and it doesn't have an AGP slot (thanks a lot, Dell!).

---

### Post by Irihapeti on 2010-05-02
@dolson
That sounds really frustrating, and I'm sorry that I can't suggest anything else you could do.

Have you filed a bug report? I know that it's probably not going to anything for you right now, but might help get this thing sorted out in the longer term. The package to file against is xserver-xorg-video-intel.

---

### Post by Rasa1111 on 2010-05-02
@dolson, 
yeah dell* is* kinda lame eh.

 I still have a couple minor issues with my graphics card apparently.. 
but nothing i cant deal with for now... until i can wrap my thoughts around the fixes.. lol

but, while these bugs are annoying, 
isnt this rather "normal" to have some 'serious' bugs, for a little while after a release? even LTS? 

i mean, if Lucid is "this good" in general already....
shouldn't we be pretty optimistic that canonical/ubuntu team, will have this worked out for folks in the near future?

 I dont know really, just asking the more experienced users pretty much,
let me know if my thinking is 'whacky'. lol  :)

---

### Post by Irihapeti on 2010-05-02
Rasa1111, you are right. *Every* new release has bugs, LTS or not. Two years ago, I remember seeing messages like: "Hardy is the worst release by far!!" and so on. Nowadays, you're more likely to hear how solid Hardy is.

It looks like there's more to this modeline stuff than I first thought. I thought that because I'd added an entry to my Hardy xorg.conf to make my wide screen work properly, that it would work in Lucid. Unfortunately, it doesn't seem to be behaving.

So, sorry to everyone I've led up a garden path. :oops:

---

### Post by Rasa1111 on 2010-05-02
Irihapeti~ 
definitely....  
I read many things today, with people talking about how hardy is "the best by far" and dont want to stop using it. lol  :)

I think when Lucid is fully ironed out...
there wont be another OS that can touch it, honestly. 

I mentioned in my previous post,
 the couple remaining bugs i have...

 I just wanted to add how small and tolerable they are..

Once in a great while,  out of nowhere, my screen will go blank(black)..
as if the signal has been lost, .. then it immediately starts blinking from all black, (no signal)
to black backlit (signal) and across the top half of the screen, is vertical white stripes...

 the only way i can get out of it is to restart using reisub, 
but the startup time is soo fast.. it really isnt too much of a bother to have to restart. lol

 the only other problem.. ( which leads to the same thing mentioned above)..
is when I try to open Stellarium...  it instantly quits and goes funky on me. lol

 i have stellarium on my Karmic box to though, so thats ok for now to. 

Im sure this will all be worked out soon enough. 

I am usually pretty anal about bugs and glitches in things.. and not being able to figure them out..
but to be honest.. i find lucid so great, I just dont care enough about them to stop using it. lol

 as well as karmic performed on this machine... (I really didnt think it could get much better)..
I am sure that even with the bugs, Lucid works even better!
 that to me... is amazing , friends. . lol

Irihapeti~  You were (i believe) one of the first people to start working on and helping with this problem, ..  no apologies are needed from you friend, you have already helped many.. and continue to do a great job at it....
 and i am most thankful for your presence here.  :)

lots of +Karma to you. <3<3<3
thanks you.

---

### Post by dolson on 2010-05-02
> **Irihapeti said:**
> @dolson
That sounds really frustrating, and I'm sorry that I can't suggest anything else you could do.
Not your fault. I tried using Ubuntu 9.10, but it was having similar issues - half the time it wouldn't boot into X.

> Have you filed a bug report? I know that it's probably not going to anything for you right now, but might help get this thing sorted out in the longer term. The package to file against is xserver-xorg-video-intel.

Nope. It would just get marked as a dupe of #541511, along with about 20 others. lol

The bug has been in there since at least mid-March (January if you look at the upstream bug report).

Maybe it will be ironed out eventually, but this is a PC for someone's mother, and she's gonna want her computer back fairly soon... I'll probably order a PCI video card off of eBay from Hong Kong, and foot the bill. I doubt it will be fixed in the meantime, but if so, great, I'll keep the card for the next time this happens.

---

### Post by Irihapeti on 2010-05-02
@Rasa1111:
Thank you for your kind words. I appreciate them.

Here's something you could try. Go to System -> Preferences -> Keyboard, click on the Layouts tab and then the Options button. Click on "key sequence to kill the X server" and check the box. When you get a lockup, you should be able to press control-alt-backspace (NOT delete), have the screen go completely blank for a second or two and then get the login screen. If it works, it's quicker than rebooting.

---

### Post by Rasa1111 on 2010-05-02
> **Irihapeti said:**
> @Rasa1111:
Thank you for your kind words. I appreciate them.

Here's something you could try. Go to System -> Preferences -> Keyboard, click on the Layouts tab and then the Options button. Click on "key sequence to kill the X server" and check the box. When you get a lockup, you should be able to press control-alt-backspace (NOT delete), have the screen go completely blank for a second or two and then get the login screen. If it works, it's quicker than rebooting.

 most welcome. 

i forgot about that, good call, thanks. 
that was one thing in karmic that did not work for me, 
i had gone in and set it just like that, so alt-ctrl-backspace would kill x server, 
but it only "worked" a couple of times, but never took me back to login screen, it just kept my screen black with a blinking line, so ... i got good at using reisub. :lol:

thatll be niice if it works in lucid!  
darn.. now ive gotta try. lol :p

:KS

---

### Post by dolson on 2010-05-02
> **Rasa1111 said:**
> most welcome. 

i forgot about that, good call, thanks. 
that was one thing in karmic that did not work for me, 
i had gone in and set it just like that, so alt-ctrl-backspace would kill x server, 
but it only "worked" a couple of times, but never took me back to login screen, it just kept my screen black with a blinking line, so ... i got good at using reisub. :lol:

thatll be niice if it works in lucid!  
darn.. now ive gotta try. lol :p

:KS

Doesn't work for me - does exactly what you described. Maybe you'll have better luck.

---

### Post by parlaan on 2010-05-02
I've been reading alot about these graphics issues with Intel based Graphics.  I"ve had the same problem.  Just so everyone knows, this isn't an issue with the .31 Kernel, and from what I've read, the .33 Kernel.  I was able to load and install the Beta #1 I believe, because it came with the .31 kernel.  When the final release came out, the only way I could do a new install was to install 9.10.  Update it, then do an upgrade to 10.04.  Of course, it broke when rebooting ( because it had the .32 kernel).  I brought up the grub menu, booted to the .31 kernel and deleted the .32 entries in Grub.  It's been working perfectly ever since.

I know it is a graphics issue, but I'm pretty sure it is a graphics issue with the .32 kernel.

---

### Post by Rasa1111 on 2010-05-02
> Doesn't work for me - does exactly what you described. Maybe you'll have  better luck.same here my bro. 
oh well, reisub has grown on me. lol :p

@parlaan~ wow, niice!! 
if you get bored and would like to elaborate further (for n00bs) on how to do that, (remove "bad" kernel)
it would be greatly appreciated!  thanks! 

i will/would be lost without it... lol  :)

---

### Post by Irihapeti on 2010-05-02
@parlaan
The problem is not necessarily restricted to the 2.6.32 kernel. There are two bugs I specifically know of which date back to when Karmic was released. One of them is one I filed, and I was testing with so-called mainline kernels and cutting-edge xserver-xorg-video-intel files. (Anyone who wants the sordid details can read about them in bug 477256 :) )

Actually, the real problem is that there isn't just one problem. There seem to be lots of variations on the same theme, and it's highly frustrating for everyone, devs included.

However, if something works for you, by all means use it. I'm currently running a mainline kernel on my desktop machine because it fixes another bug that hasn't yet been sorted out in the standard kernel.

---

### Post by zeroxp on 2010-05-03
I was so upset last night when the CD not work on my toshiba satellite A50(with the 855GME).

You guys are great. Good to know there are already work rounds for this. i'll try when i get home.


edit: the i915.modeset=1 options load the CD version up! 1024 x 768.
i'll proceed with a full install.

---

### Post by xvntnine on 2010-05-03
Greetings,

I have an HP Pavilion ze4903us notebook with  [        Intel 82852/82855 GM/GME Graphics Controller]("http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-30788-1&lc=en&dlc=en&cc=us&lang=en&os=228&product=434844").  Irihapeti's initial suggestion of using i915.modeset-0 xforcevesa got me running so I can do an installation - I'm running at 1024x768.  
I'm assuming that there will be an update to fix this as everything worked fine out of the box so to speak with karmic...  This issue and the time that I've spent trying to work around it have somewhat dimmed my enthusiasm for ubuntu.  Hopefully the response will be exceptional and this will have been a valuable learning experience for future releases for everyone concerned.

---

### Post by Rasa1111 on 2010-05-03
> **zeroxp said:**
> I was so upset last night when the CD not work on my toshiba satellite A50(with the 855GME).

You guys are great. Good to know there are already work rounds for this. i'll try when i get home.


edit: the i915.modeset=1 options load the CD version up! 1024 x 768.
i'll proceed with a full install.


:D happy to hear it!!

---

### Post by zeroxp on 2010-05-03
install was successful. the compiz 3D box works too!\\:D/

---

### Post by Rasa1111 on 2010-05-03
> **zeroxp said:**
> install was successful. the compiz 3D box works too!\\:D/

woohoo! \\:D/
thats awesome. 

hope you like it as much as i do!

---

### Post by dr.frankinfurter on 2010-05-10
> **drysdan said:**
> I had that issue too.  Here's what I did:

In the GRUB list, boot into recovery mode.  When the menu comes up, scroll to the bottom, to open a root shell.
At the shell prompt, enter this command:

```
echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
```followed by this command:

```
sudo update-initramfs -u
```then type 'reboot'


Basically, this makes the modeset=1 a permanent feature, rather than enabling it in GRUB.  If it booted normally from the livecd with i915.modeset=1, then this should make it boot normally from there on.

(this set of commands was taken from solution 'A' at [https://wiki.ubuntu.com/X/Bugs/Lucid8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucid8xxFreezes)


Hope it helps!

Thanks for the reply. Well, I tried to drop down to a root shell with networking so that I could apt-get the nvidia-common and nvida-settings packages and just have the nvidia tools generate an xorg.conf file (I have a GeForce 8800 GTS). It didn't work, I just got the same problem as when I tried to boot into the regular desktop. Trying to add the 'i915.modeset=1' parameter through GRUB didn't help either. Frustration ](*,)

---

### Post by cariboo on 2010-05-10
> **dr.frankinfurter said:**
> Thanks for the reply. Well, I tried to drop down to a root shell with networking so that I could apt-get the nvidia-common and nvida-settings packages and just have the nvidia tools generate an xorg.conf file (I have a GeForce 8800 GTS). It didn't work, I just got the same problem as when I tried to boot into the regular desktop. Trying to add the 'i915.modeset=1' parameter through GRUB didn't help either. Frustration ](*,)

The i915.modset=1 only works on Intel graphics chipsets. If your having trouble installing the drivers, use synaptic to install then, then open a terminal and type:

```
sudo nvidia-xconfig
```

to create a new /etc/X11/xorg.conf file, then reboot. You should then be taken to a properly working desktop. I have two systems both running nvidia graphics cards, a 9400GT and a GT210 the above solution works for both of them. 

One other thing you might have to do is run nvidia-settings as root to save your resolution settings press Alt-F2 and type:

```
gksu nvidia-settings
```

set your resolution, then click Save to X Configuration file.

---

### Post by zippytex on 2010-05-16
[QUOTE=Irihapeti;9197865]Yes, I think you may be right about it being a graphics card problem. I think you may have the same problem that I did on my beat-up old Toshiba Satellite A10.

So, here is what *should* work:

At the very first screen, the one with just the rectangle (it's meant to be a keyboard) and a human figure, press any key - spacebar will do.

Then choose your language.

Then make sure you have "Try Ubuntu without any changes" selected, and then press F6

Add this to the end of the command line: ```
i915.modeset=0 xforcevesa
```



I just wanted to say thanks!  I have a intel 855/856 chip on a Toshiba laptop and this CURED the problem!  Rebooted just fine.  Thanks!!!!

.

---

### Post by twrock on 2010-05-17
> **zippytex said:**
> ```
i915.modeset=0 xforcevesa
```

I have a intel 855/856 chip on a Toshiba laptop and this CURED the problem!  Rebooted just fine.  Thanks!!!!


I'm curious about two things.
-What is your screen resolution now?
-What happens if you try to play any video?

Thanks.

---

### Post by adenewton on 2010-05-20
My older Toshiba Satellite A50 seems to have this problem, it dual boots with Windows XP, and when using the fix it seems grub dies after install and I can't boot either.

I just get a grub recovery console terminal, and I have no idea what to do from here.

Had to reinstall 9.10 to fix.

Have added myself to the bug info, hope this get's fixed soon. Really annoying, and a poor effort to have a bug that affects such a common graphics driver in an LTS release that prevents you from even installing.

---

### Post by Irihapeti on 2010-05-20
> **adenewton said:**
> My older Toshiba Satellite A50 seems to have this problem, it dual boots with Windows XP, and when using the fix it seems grub dies after install and I can't boot either.

I just get a grub recovery console terminal, and I have no idea what to do from here.

Had to reinstall 9.10 to fix.

Have added myself to the bug info, hope this get's fixed soon. Really annoying, and a poor effort to have a bug that affects such a common graphics driver in an LTS release that prevents you from even installing.

I'm not sure that the behaviour you describe is due to the graphics issue. It sounds more like a separate grub problem to me.

---

### Post by Silvertones on 2010-05-22
Well I can get the live CD to boot up with either
```
i915.modeset=0 xforcevesa
```or this


```
i915.modeset=0 xforceintel
```The problem is the screen resolution is only 1024X768 when it should be 1400X1050.

Is there a way to fix this? This is my first upgrade so be simple with the info. Maybe we wait for a fix? Do you think a fix is in the works or is just how it's going to be?
Thanks

---

### Post by Irihapeti on 2010-05-22
> **Silvertones said:**
> Well I can get the live CD to boot up with either
```
i915.modeset=0 xforcevesa
```or this


```
i915.modeset=0 xforceintel
```The problem is the screen resolution is only 1024X768 when it should be 1400X1050.

Is there a way to fix this? This is my first upgrade so be simple with the info. Maybe we wait for a fix? Do you think a fix is in the works or is just how it's going to be?
Thanks

I don't know how long this is going to take to be fixed. Unfortunately, the problem isn't just in Ubuntu but further upstream. I believe other distros are affected as well.

I discovered [another post]("http://ubuntuforums.org/showpost.php?p=9312054&postcount=5") with a possible fix. I haven't tried this myself, so I don't know how well it will work. You would need to add "1400x1050" to the appropriate line. Also, if you are using standard Ubuntu, substitute "gedit" for "mousepad" in the relevant command.

If you want to try it with a live CD, you'll need to log out and in again instead of rebooting.

---

### Post by zippytex on 2010-06-18
Thank you so much!  This works perfectly on my intel 855/56 graphics card in my Toshiba M35x-s311.  Knowledge is a powerful thing!!!  Thanks!

---

### Post by pythonsyntax on 2010-06-30
I get a black sceen after the install  i have try the 
i915 modeset=1  that seem to work but after the install i get a blacksceen anyway around this?

---

### Post by pythonsyntax on 2010-07-05
anyone

---

### Post by twrock on 2010-07-18
> **pythonsyntax said:**
> I get a black sceen after the install  i have try the 
i915 modeset=1  that seem to work but after the install i get a blacksceen anyway around this?

Go back through the thread. There is information here on how to add that code to GRUB so that it is permanent (is loaded every time you boot).

---

