---
title: "very wierd problem."
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by Busch on 2006-11-20
I recently was using slackware but got tired of having to configure everything all the time when i wanted to try something new. so I heard about ubuntu and decided to try it out because its supposed to "Just Work."  Its wierd though I use the normal install CD i can get to the part where it says start/install ubuntu.  I click that. it loads. and when it is done loading it will show a black screen like some graphic interface is loading up. then it will just blink off and my monitor's "green light thing" the light that shows if the moniter is on or not. just keeps blinking repeatedly and nothing ever happens.

I have used the alternate CD. was able to install. got to grub, loaded up ubuntu. but after that, same thing.  monitor light kept blinking repeatedly and nothing happens after.

please help ive never had that problem before :mad:

I have an amd athlon xp 2100 proccessor, nvidia gefore 6200 graphics card, creative soundblaster sound card.  if you want to know any other things about my computer just ask.

---

### Post by dbott67 on 2006-11-20
It may be related to refresh rate.  

Are you using an LCD panel?

Can you 'borrow' a CRT and try using it?

I had to boot into Gnome 'Safe Mode' off the Live CD, but even then my monitor blanked out.  Fortunately for me, my monitor reported that it was out of range and to adjust the frequency to 60 Hz.

**_My Work-Around (for those without a spare CRT):_**

1. After booting Live CD, my monitor blanked outand reported that it was out of range and to adjust the frequency to 60 Hz.

2. I pressed CTRL-ALT-F1 and got dropped into the terminal.

3. From the terminal I typed:
```
sudo nano /etc/X11/xorg.conf
```

4. I modified the "Monitor" section to include the following line:
```

Section "Monitor"
        Identifier      "Dell 2007 FP"
        Option          "DPMS"
        **[COLOR="Red"]VertRefresh     60-60[/COLOR]**
EndSection
```

5. I saved the file and then pressed CTRL-ALT-F7 to get back into the GUI.

Hope this helps.

-Dave

---

### Post by Busch on 2006-11-20
That seems like it might work.  Ill go try that after I get done with school here.

---

### Post by Windows_Is_God on 2006-11-20
Hi, yeah like when I press CTRL-ALT-F7 it loads the terminal then it stays for about 5 seconds then switches to a black screen. I am using a CRT monitor and a NVIDIA GeForce4 MX 440 graphics card.

---

### Post by dbott67 on 2006-11-20
> **Windows_Is_God said:**
> Hi, yeah like when I press CTRL-ALT-F7 it loads the terminal then it stays for about 5 seconds then switches to a black screen. I am using a CRT monitor and a NVIDIA GeForce4 MX 440 graphics card.

You'll probably need to add VertRefresh & HorizRefresh rates for your monitor.  What's the make & model of your monitor?

Can you post the output of your xorg.conf file?
```
cat /etc/X11/xorg.conf
```

If you can get to the terminal, I used to have the same video card and you could edit the file to look like mine:


```
Section "Device"
        Identifier      "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        [B][COLOR="Red"]Driver          "nv"
        BusID           "PCI:1:0:0"[/COLOR][/B]
EndSection

[COLOR="Blue"]Section "Monitor"
        Identifier      "DELL 2007FP"
        VertRefresh      60
        Option          "DPMS"
EndSection[/COLOR]

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        [COLOR="Blue"]Monitor         "DELL 2007FP"[/COLOR]
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

The key differences will be the "monitor" section and perhaps the BUS ID under the "device" section.

Before you edit the file, we would need to insert the appropriate refresh rates (or modelines0)

There are 2 nVidia drivers 'nv' and 'nvidia' avaiable.  The 'nvidia' one is the closed-source binary that you would need to install to enable 3D.

---

### Post by Busch on 2006-11-20
thx dbott, i think ill go and try the refresh rate change first.. now that i think about it, it looks very close like a bad refresh rate.

---

### Post by Windows_Is_God on 2006-11-20
Like, for my monitor it just says Plug and Play monitor and thats it...it's the monitor that came with my comp when I bought it in like 2001-2002 time. My comp is a Packard Bell iMedia 4608...a very ancient and obsolete model. My CPU is 1Ghz and I only have 512Mb of RAM. :D

---

### Post by dbott67 on 2006-11-20
Nothing on the back of the monitor?  Maybe a 17" A727 monitor?

Like the one in this picture?:
[http://support.packardbell.com/uk/item/index.php?pn=P480409301&g=1400](http://support.packardbell.com/uk/item/index.php?pn=P480409301&g=1400)

---

### Post by Windows_Is_God on 2006-11-20
Actually it's a 15" A527 Monitor.

---

### Post by Busch on 2006-11-20
well no go on changing to terminal by doing ctrl+alt+f7.. when the xserver starts its like NOTHING works at all. it's p*ssing me off. im going to go and try that dapper drake ubuntu maybe ill have better luck with that version.  I mean I can get to consol after install with the recovery whatever you can choose to boot. but i dont even have an xorg file or any X11 file to edit anyways. 

I should have known nothing "just works" for me :)

---

### Post by dbott67 on 2006-11-20
> **Busch said:**
> well no go on changing to terminal by doing ctrl+alt+f7.. when the xserver starts its like NOTHING works at all. it's p*ssing me off. im going to go and try that dapper drake ubuntu maybe ill have better luck with that version.  I mean I can get to consol after install with the recovery whatever you can choose to boot. but i dont even have an xorg file or any X11 file to edit anyways. 

I should have known nothing "just works" for me :)

Dapper may be a good idea... I didn't have the monitor blanking issue in Dapper... only in Edgy.  Once Dapper is installed, you can upgrade to Edgy if you want.

---

### Post by dbott67 on 2006-11-20
> **Windows_Is_God said:**
> Actually it's a 15" A527 Monitor.

From a [PB support site]("http://support.packardbell.com/cz/mypc/?PibItemNr=spec_A527&PibItemParent=platform_monitor_A527#show"):
```
General

Display Type: Display / CRT

Width: 36 cm
Depth: 39.2 cm
Height: 37.7 cm
Weight: 10.9 kg
Enclosure Colour: White, blue
Compatibility: PC

Display
Diagonal Size: 15"
Viewable Size: 13.7"
Dot Pitch / Pixel Pitch: 0.28 mm
[COLOR="Red"]**Max Resolution: 1024 x 768 / 60 Hz**[/COLOR]
Colour support: 24-bit (16.7 million colours)

Max Sync Rate (V x H): 120 Hz x 54 kHz

Factory Preset Resolution Modes:

    * 720 x 400 / 70 Hz
    * 640 x 480 / 85 Hz
    * 640 x 480 / 60 Hz
    * 640 x 480 / 75 Hz
    **[COLOR="Red"]* 1024 x 768 / 60 Hz[/COLOR]**
    * 800 x 600 / 85 Hz
    * 800 x 600 / 75 Hz
    * 800 x 600 / 60 Hz

Front Panel Controls: Power on/off, adjust +/- , select

On-Screen Controls: Contrast, brightness, H/V-position, H/V-size, pincushion distortion, degauss, trapezoid, parallelogram, recall settings

Interface: VGA (HD-15)

Features: Anti-glare, anti-static, anti-reflective
Image

Image Aspect Ratio: 4:3
Video Input

Analogue video Signal: RGB
```

You'll need to adjust your xorg.conf file.  Copy and paste the new Modeline below to **Monitor** section of your xorg.conf file:
```
# V-freq: 60.00 Hz  // h-freq: 47.80 KHz
 Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796 
```

-Dave

---

### Post by Windows_Is_God on 2006-11-20
erm...just out of interest...how do I access the xorg.conf file?

---

### Post by dbott67 on 2006-11-20
Just type the following commands into a terminal window (or copy & paste):

1. Backup the existing file first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.2006-11-20-bak
```

2. Edit from a text-based editor:
```
sudo nano /etc/X11/xorg.conf
```

-Dave

---

### Post by Windows_Is_God on 2006-11-20
Yeah but the terminal window only stays on for like 5 seconds then instantly shuts down again? how am I supposed to type all that out in 5 seconds lol.

---

### Post by dbott67 on 2006-11-20
What?!?!  You can't type that fast?

Can you press CTRL-ALT-F1 to get to a terminal?

-Dave

---

### Post by Windows_Is_God on 2006-11-20
Well I press CTRL-ALT-F1 and a terminal comes up then I start typing and it goes again then I just get a black screen?

---

### Post by dbott67 on 2006-11-20
Just for clarification, this is happening from the 'Live CD', correct?

Have you tried booting into the Gnome "Safe Mode"?

Also, what are the other choices for booting from the Live CD?  Can you print them out here?

Thanks,
Dave

---

### Post by Windows_Is_God on 2006-11-20
Well the only choices I get from a live CD boot are:

Start or install ubuntu
Start ubuntu in safe graphics mode
Check CD for defects
Memory test
Boot from first hard drive

then there are a whole bunch of stuff from F1 to F6.

---

### Post by Windows_Is_God on 2006-11-20
Hello dbott67...are you there lol?

---

### Post by Busch on 2006-11-20
Windows, you could try using the alternate install cd.  thats what worked for me to actually "install" it.  all it is is texted base install, easy to understand. I was able to just press enter most of the time :).

---

### Post by dbott67 on 2006-11-20
> **Windows_Is_God said:**
> Hello dbott67...are you there lol?

I'm back now... had to pick up my daughter, eat dinner... soon it will be bath time & stories for the girls and then I'll be back again...

Busch's suggestion is good if you can download the "Alternate image ISO".

Have you tried the "Start ubuntu in safe graphics mode" option?

Keep posting, I'll be in and out throughout the evening.

-Dave

---

### Post by Busch on 2006-11-20
HAHA the dapper version worked like a charm for me (in my standards anyway).  and my wireless network actually worked without configuring!! it took me a LONG time to get wireless working on slackware. and my moues scroll works without me having to go in the xorg file and changing one thing :)

---

### Post by Windows_Is_God on 2006-11-20
Yes i've tried the "Start ubuntu in safe graphics mode" option.

Also what is/where can I download the alternate image ISO?

Also if you were wondering I have broadband. :D

---

### Post by dbott67 on 2006-11-20
> **Windows_Is_God said:**
> Yes i've tried the "Start ubuntu in safe graphics mode" option.

Also what is/where can I download the alternate image ISO?

Also if you were wondering I have broadband. :D

You can go to the [www.ubuntu.com](www.ubuntu.com) and click on the "download" section.  Pick a version (6.10, 6.06 LTS, etc).  There are 3 choices: Desktop, Server & Alternate.

If you live in the US, you can try:

[http://ubuntu.cs.utah.edu/releases/edgy/ubuntu-6.10-alternate-i386.iso](http://ubuntu.cs.utah.edu/releases/edgy/ubuntu-6.10-alternate-i386.iso)

---

### Post by Windows_Is_God on 2006-11-21
k so i've started to download the alternate so far it's going strong at about 230KB/sec .:D

---

### Post by Windows_Is_God on 2006-11-21
Well it's burnt to disk ok so i'll try it quick before I have to go to school lol. :D

---

### Post by Windows_Is_God on 2006-11-21
Well i've tested it and it seems to work...although I havn't installed it yet lol. :D

---

