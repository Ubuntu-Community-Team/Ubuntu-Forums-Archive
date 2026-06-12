---
title: "Won't recognize 2nd video card (AMD Radeon HD 8570)"
date: 2014-06-20
forum: Installation &amp; Upgrades
---

### Post by UncleBoarder on 2014-06-20
New computer, new install of 14.04. Both cards are AMD Radeon HD8570.  Both are known good.  Computer can output video on either card.  

Each AMD video card has two video ports, 1 DVI, 1 HDMI.  I've checked both cards and all connections work in their current card slots... but not all at the same time.

I can't get both cards to fire up at once.  The BIOS has a setting for auto-detect, or select one AMD card, or the other. In the BIOS, if I select one AMD card, then that one works.  Or the  other card and then THAT one works, but not both.  If I select Auto it's  the same as selecting the first AMD card, I can't get video from the  second card if Auto is selected.


[LIST]
[*]The drivers from AMD caused my first card to die (or coincidence) but I read a post online that suggested NOT using the AMD drivers under 14.04 so I don't want to try that again.
[*]The drivers from Ubuntu Additional Drivers gives me ONE display.  It doesn't even recognize the second monitor on the FIRST card so it's the worst.
[*]The drivers I'm using are from ubuntu-x-swat/x-updates repository and they work the best so far.  At least I see two of my 3 monitors.  Both on the first card only.  (Second card is still not displaying)
[/LIST]

The second card DOES work, I've proved it over and over.  How do I get video from the second card WITH the first card??

And lastly, my coworker has the same hardware with Windows 8 and it recognizes both video cards without problem.  Please don't make me go back to Windows.

---

### Post by T.J. on 2014-06-20
I can offer a couple of ideas, although the Catalyst drivers from AMD are known to create problems with multi-card setups, even on Windows.  

1. If you are using the Catalyst driver from AMD, it likes to assume control of all AMD video cards, even if one is not configured, and can block your setup from working properly.  I'd suggest using the open Radeon driver if it is an option.
2. You may have to manually configure your card and monitor pairings to match what you expect.  This is not as hard as it sounds, but you do need some help if you do not have the necessary experience.

Can you paste the output of the* lspci * command  to start?

---

### Post by UncleBoarder on 2014-06-20
Did a quick search... where do I get Open Radeon drivers?

00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 8 Series/C220 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d4)
00:1c.1 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d4)
00:1c.4 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #5 (rev d4)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Q87 Express LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland [Radeon HD 8570 / R7 240 OEM]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]
03:00.0 PCI bridge: Texas Instruments XIO2001 PCI Express-to-PCI Bridge
05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Oland [Radeon HD 8570 / R7 240 OEM]
05:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]

---

### Post by QIII on 2014-06-20
The open source driver is already in use if you see something on your monitor.

Where did you see not to use the proprietary fglrx driver with 14.04?  I use it and it works fine.

How did you install it?

Did you do

```
sudo amdconfig --adapter=all --initial
```

To set up both cards?

Are you using Xinerama?

---

### Post by UncleBoarder on 2014-06-20
It appears (on ubuntu.com) that my OLAND Radeon HD 8xxx series is not yet supported.  It's weird because it says they should be supported by the time 13.10 is released yet the document was last edited this month. So... I don't know what to do.

---

### Post by UncleBoarder on 2014-06-20
Ah... I sent before I saw your post.  I did "amdconfig --initial"... not "--adapter=all".  I just tried the full command as you suggest... rebooted... and it made no difference.

I am not uxing Xinerama.

Don't Install Radeon Proprietary Drivers --> [http://www.reddit.com/r/Ubuntu/comments/23gcr0/if_youre_using_1404_dont_install_the_radeon/](http://www.reddit.com/r/Ubuntu/comments/23gcr0/if_youre_using_1404_dont_install_the_radeon/)

---

### Post by QIII on 2014-06-20
The beta driver is a beta.  It is "as is" while in development.

If that is the one they are talking about, it's not surprising.

But to say, based on that, that you should not install fglrx at all is, frankly, asinine.

I'm using the version from the Trusty repo and I have verified that the last non-beta from the AMD/ATI  site works.

---

### Post by UncleBoarder on 2014-06-20
LOL... I'd say 'asinine' requires knowledge of the pros and cons, when posts were made, and who is the best authority.  Since that's difficult, I'm simply strugling though a problem... with your help, thank-you. :-)

I just don't want to make the same mistake twice.  But you're telling me you've done it and it works.  Ok... I'll willing to give it a try.

From here?  [http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64#amd-catalyst-packages](http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64#amd-catalyst-packages)

---

### Post by QIII on 2014-06-20
Since you are using two cards (and thus not Eyefinity if not Crossfired and Eyefinity capable) you will have to use Xinerama.  There are some drawbacks to Xinerama, like not being able to span a single desktop across all three monitors.

I'll see if I can find a very old thread where I helped someone get set up with Xinerama.  I'm afraid I haven't used it in years.

In case you are wondering, here are three monitors with a desktop spanning them, using a single card supporting multimple monitors and Eyefinity ... using Catalyst on Trusty (14.04):

[http://i.imgur.com/UJwbhxv.jpg](http://i.imgur.com/UJwbhxv.jpg)

I'm still fiddling with the conky on the far left.

---

### Post by UncleBoarder on 2014-06-20
hmm... I'm running 10.04 on my other computer with 2 Nvidia cards (3 monitors) and I am NOT running Xinerama.  Why would it be needed just because I've changed to AMD?

---

### Post by QIII on 2014-06-20
Are your Nvidia cards in SLI?

Could be that Xinerama is no longer needed these days.

---

### Post by UncleBoarder on 2014-06-20
(No SLI)

I tried to installed amd-driver-installer-14.10.1006.1001-x86.x86_64.run but it kept complaining that the fglrx drivers were already installed.  I ran all the apt-get --purge commands I could find but it still thinks fglrx is installed.  So I ran it with --force.

It kind of worked... now my second card/3rd monitor is alive.  But it's low res, black screen with just a large "X" for a mouse cursor.  What does that mean?  I still can't use it.  Suggestion?

---

### Post by QIII on 2014-06-20
Did you try installing with both the .run file from ATI and through the Trusty repo?

If you did and didn't uninstall properly between, things could be funky.

---

### Post by UncleBoarder on 2014-06-20
I just --forced the .run file over the existing fglrx drivers.  I understand that could cause funky-ness but I couldn't get it to uninstall.  So this is what I've done next...

I tried to 'apt-get remove --purge fglrx*' and that worked this time without error.  Great!

Next I did the .run again.  It also installed without error... YES!

Rebooted...

Now I'm back to my original problem.  No video at all on second card/3rd monitor.

I don't get it!

---

### Post by UncleBoarder on 2014-06-20
Wait... my fault... I forgot to run amdcccle and re-enable the second monitor.  Ok... back to the black screen with the big, low-res "X" for a cursor.

---

### Post by QIII on 2014-06-20
OK.

Did you run

```
sudo amdconfig --adapter=all --initial
``` this time?

---

### Post by UncleBoarder on 2014-06-20
I did.

---

### Post by QIII on 2014-06-20
m'Kay.

Can you post the contents of your /etc/X11/xorg.conf file?

Please use code tags:

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by UncleBoarder on 2014-06-20
```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
    Screen         "amdcccle-Screen[5]-0" RightOf "aticonfig-Screen[0]-0"
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1200"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-Default monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "640x480"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "Default Card 0"
    BusID       "PCI:1@0:0:0"
EndSection

Section "Device"
    Identifier  "Default Card 1"
    BusID       "PCI:5@0:0:0"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:1:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[5]-0"
    Driver      "fglrx"
    Option        "Monitor-Default monitor" "1-Default monitor"
    BusID       "PCI:5:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[5]-0"
    Device     "amdcccle-Device[5]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

---

### Post by UncleBoarder on 2014-06-20
Yeah, I see the 640x480... changed it to 1920x1200 and rebooted.

Still a black screen with the "X" but the screen res looks better.

---

### Post by QIII on 2014-06-20
Open Catalyst Control Center and see if it detects the monitor.

---

### Post by UncleBoarder on 2014-06-21
amdcccle does see the monitor but it showed disabled.  It did not detect/enable it automatically, I made the choice to enable it in the GUI. If I click on Identify it does show the monitor numbers properly on the screens.  But I'm still in the same place, the second card/monitor is black... except for the "x" cursor, or the red "identify box" from amdcccle.

---

### Post by UncleBoarder on 2014-06-23
bump

---

