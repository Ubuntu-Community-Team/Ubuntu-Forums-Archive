---
title: "Need basic graphics card that works with Ubuntu 12.10"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by fakedave on 2012-12-21
Hello all,

I'm posting because like many I face an issue with my graphics card with Ubuntu 12.10.
I've built the whole PC recently and bought an ASUS Radeon HD 6450 (now the H/W is recognized but the system does not offer me any display plugged in that card ...).
The thing is that I don't need much power (no games, only work) and appreciate silence.

I've followed different topics and I still cannot properly install my graphics card.
At the moment I'm running on the graphics provided by my motherboard (ASUS P8Z77-V PRO/Thunderbolt) --> mini-display port + hdmi.
I need one (or 2) extra displays, normally 1920*1200 but could expand to 2500*1600 (or like).

Who knows a simple/basic but efficient graphics card that is immediately recognized by Ubuntu 12.10 without any hassle?
Thanx to let me know.

Nicolas

---

### Post by coffeecat on 2012-12-21
> **fakedave said:**
> 
I've built the whole PC recently and bought an ASUS Radeon HD 6450 (now the H/W is recognized but the system does not offer me any display plugged in that card ...).

Well, that is interesting because not only do I use a Radeon HD 6450 with Ubuntu 12.10, but mine is a silent fanless Asus too. It works just fine for my needs with the default open-source driver so I don't have to install the proprietary driver, and judging by your description of your needs, it should work just fine for you too. I also get perfectly good 1920x1080 dual-monitor output with it - I've not tried 3 monitors.

So the question is, why is your card not giving any output? Check your BIOS settings, and check your video cable. Do you get any output with another operating system? Do you see the BIOS screen when you first switch on with the monitor connected to that card?

---

### Post by fakedave on 2012-12-21
Excellent !! Thanx for your feedback.
So since the card seems to be correctly recognized as shown:
[IMG]http://i16.servimg.com/u/f16/11/28/36/70/screen10.png[/IMG]

I'm wondering how I could see the additional screen on the card.

At the moment I have 2 on my motherboard that work.
[IMG]http://i16.servimg.com/u/f16/11/28/36/70/screen11.png[/IMG]

I check my MB settings and repost later.

Thanx for your help as I appreaciate the fact that it is fanless :-)

---

### Post by Pjotr123 on 2012-12-21
If no avail, choose Nvidia. For example this one:
[http://www.asus.com/Graphics_Cards/NVIDIA_Series/EN210_SILENTDI1GD3V2LP/#overview](http://www.asus.com/Graphics_Cards/NVIDIA_Series/EN210_SILENTDI1GD3V2LP/#overview)

---

### Post by fakedave on 2012-12-21
Well, more information.

I went to my bios and forced the default graphics to be that card.
I can then see the bios screen on the new monitor and (so card & cables & monitor are working) and I go up to the ubuntu login screen (so driver seems to work, no?).

I enter my passwd, 3 screens become black for a couple of seconds and I end up with a text screen only (3rd display) that basically highlights that something is going wrong during the login.
I can't get a cursor or anything. Reset button only.

So both graphics seem to be working but I have the impression they don't work together ... 

Any idea?
What would seem useful to you to know to guide me?

Thanx

---

### Post by coffeecat on 2012-12-21
> **fakedave said:**
> 
So both graphics seem to be working but I have the impression they don't work together ... 

Any idea?
What would seem useful to you to know to guide me?



Are you trying to use both cards simultaneously, one for each monitor? I don't know whether you can get that to work. Try disabling the onboard video completely in the bios and connecting your two monitors to two of the outputs on your HD6450 card. If yours is the same as mine - it sounds as though it is - there are VGA, DVI and HDMI outputs. I use the DVI and HDMI outputs. I presume you would need to connect your Apple monitor to the HDMI via your adapters and the 24" monitor to either the VGA or DVI.

---

### Post by fakedave on 2012-12-21
aha, thanx for your feedback.

Unfortunately I want to have 3 monitors (at least) connected at the same time. (work luxury).

I thought that in modern (I had not built a pc in a while) configuration it was possible to add graphics card and keep adding monitors ...
I might have been wrong there ?

However, I don't mind purchasing a card that works with Ubuntu 12.10 and provides at least:
[LIST][*]one mini display port
[*]2 HDMI/DVI
[/LIST]

Ideas for Xmas ??

---

### Post by coffeecat on 2012-12-21
> **fakedave said:**
> 
Ideas for Xmas ??

Good luck with that! :)

As I mentioned before I've not tried 3 monitors - yet. But you've intrigued me. I'll try hooking a third monitor to the VGA output and see if I can get 3-monitor output from the one HD6450 card. Not ideal, of course. Your wish to use three digital outputs would be much better.

---

### Post by fakedave on 2012-12-21
Yes, I should have said: full digital.
But maybe in the mean time I could also give it a shot :-)

---

### Post by fakedave on 2012-12-21
Getting weirder and weirder ...
I plugged in a VGA monitor into the MB --> didn't work, lost the other screens, did not try further.

Then I took a 4th monitor that I plugged into the MB DVI--> it replaced my apple cinema display in the mini display port. So I removed it.

And I plugged the 4th monitor DVI into the HD 6450 card and ... and ... it turned out to display the ubuntu logout screen (with the dots) on ... BOTH DVI & HDMI displays.

So at the moment I have the 2 screens on the MB that work fine.
2 other screens on the HD 6450 that display a ubuntu image. I thought it was a frozen image but when I logged off, the screens actually had the dots turning ON/OFF like on the 2 primary ones. So it's alive.

It's also possible to have 4 screens at the same time, ubuntu manages that apparently, but I don't know where to tell it.

---

### Post by cwsnyder on 2012-12-21
You tell it in your /etc/X11/xorg.conf file and it can report back to your with **xrandr**.

---

### Post by fakedave on 2012-12-21
Thanx for the hint.

I have only a xorg.conf.failsafe and no xorg.conf.
It that normal?

Do you have any information or link on how to configure it? I had a look but I have to say it's not telling me much ...

I get the following with ```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Caicos [Radeon HD 6450]
```

How to get the list of the displays connected?
How to fill the xorg.conf file without putting any wrong data?

---

### Post by fakedave on 2012-12-21
Here's what I get with xrandr:

```
xrandr
Screen 0: minimum 320 x 200, current 4480 x 1440, maximum 8192 x 8192
VGA2 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
HDMI4 connected 1920x1200+2560+0 (normal left inverted right x axis y axis) 546mm x 352mm
   1920x1200      60.0*+
   1920x1080      50.0     60.0     60.0     25.0     30.0  
   1600x1200      60.0  
   1680x1050      59.9  
   1680x945       60.0  
   1400x1050      74.9     59.9  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       74.9     59.9  
   1152x864       75.0  
   1280x768       74.9     60.0  
   1280x720       50.0     60.0  
   1024x768       75.1     70.1     60.0  
   1024x576       60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   720x576        50.0  
   848x480        60.0  
   720x480        59.9  
   640x480        72.8     75.0     66.7     60.0     59.9  
   720x400        70.1  
DP2 connected 2560x1440+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440      60.0*+
   1280x720       59.9  
DP3 disconnected (normal left inverted right x axis y axis)

```

How do I make my own xorg.conf since I don't have any, only .failsafe one?

What information is necessary ?

Thanx

---

### Post by darkod on 2012-12-21
Can post #2 here help you?
[http://ubuntuforums.org/showthread.php?t=2061399](http://ubuntuforums.org/showthread.php?t=2061399)

I don't have much graphics experience myself. It's very strange not to have xorg.conf file, you probably deleted it playing with the drivers. When installing a new driver it should usually create it.

---

### Post by rrnbtter on 2012-12-21
Greetings,
A good place to start to find Linux Certified components is [http://www.ubuntu.com/certification/catalog/](http://www.ubuntu.com/certification/catalog/)

I don't do ATI but you can check you card against the OS that you are using on the above site.  If it isn't listed that doesn't mean that it won't work and if it doesn't work there may be work arounds.  But it still doesn't hurt to know if it is a certified for your OS which has an entirely different meaning in my book.

---

### Post by coffeecat on 2012-12-21
> **darkod said:**
> It's very strange not to have xorg.conf file, you probably deleted it playing with the drivers. When installing a new driver it should usually create it.

On the contrary - a default installation of Ubuntu has no xorg.conf file. It's been like that for some years now. You only get an xorg.conf file if you install the proprietary ATI or nvidia drivers, or create one. I guess the OP is still using the default radeon open source driver.

@fakedave, you were using System Settings -> Displays earlier. That's fine for setting up multi-monitors with the open source driver with just one video card. I haven't tried it with more than one graphics card, but does that show you all your monitors attached to both video cards?

---

### Post by fakedave on 2012-12-21
So unfortunately doing sudo Xorg -configure does not work for me.

So I tried to write my own from samples I found on the net.
There it is (it does not work):

```
Section "Device"
        Identifier  "MB video card"
        Driver      "intel"
        BusID       "PCI:00:02.0"
EndSection

Section "Device"
        Identifier  "Asus Radeon HD 6450"
        Driver      "amd"
        BusID       "PCI:02:00.0"
EndSection

Section "Monitor"
#   Apple Monitor
    Identifier  "Apple Computer Inc 27"
EndSection

Section "Monitor"
#   ASUS Monitor 1
    Identifier  "Ancor Communications Inc 24"
EndSection

Section "Monitor"
#   ASUS Monitor 2
    Identifier  "Ancor Communications Inc 25"
EndSection

Section "Monitor"
#   Samsung Monitor
    Identifier  "Samsung Crap 24"
EndSection

Section "Screen"
#   Apple Monitor
    Identifier "Screen0"
    Device  "MB video card"
    Monitor "Apple Computer Inc 27"
    DefaultDepth 24
EndSection

Section "Screen"
#   ASUS Monitor 1
    Identifier "Screen1"
    Device  "MB video card"
    Monitor "Ancor Communications Inc 24"
    DefaultDepth 24
EndSection

Section "Screen"
#   ASUS Monitor 2
    Identifier "Screen2"
    Device  "Asus Radeon HD 6450"
    Monitor "Ancor Communications Inc 25"
    DefaultDepth 24
EndSection

Section "Screen"
#   Samsung Monitor
    Identifier "Screen3"
    Device  "Asus Radeon HD 6450"
    Monitor "Samsung Crap 24"
    DefaultDepth 24
EndSection
```

In the device section, I assume that only the Driver actually matters. I put something random. Where can I find the proper namings ???

Then for the other sections, I simply took names and derived them into the 4 displays I have.

I guess that's not how to do BUT the PC started a failsafe X on my secondary video card and I had a text login on the primary video card SO there is surely a proper way to configure all that.

I just need to figure out how to assemble all that ...

Any help is much appreciated ;)

---

