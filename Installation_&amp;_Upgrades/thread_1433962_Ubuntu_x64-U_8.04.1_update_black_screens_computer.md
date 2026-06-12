---
title: "Ubuntu x64-U_8.04.1 update black_screens computer"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by nss0000 on 2010-03-19
Gents:

Running Asus_M2N/AMD_5600/4-G Crucial/nv7600: x64-U_8.04.1-LTS

I returned from a 3-day road-trip, turned on my computer and checked email ... without issue. Punched-up FireFox. Then I noticed an "update" icon including a new OS_update ... I accepted. DLoad and install happened without issue as I have done "50" times. I was prompted to <reboot> and accepted that offer.

The <reboot> fails. Only a black-screen returns. No SPLASH no text no-nothing. <no-signal> to screen. 

Assuming the OS-update has ... done-evil... what are my options ? I have no LAN access to that BSODed kit.

---

### Post by quadproc on 2010-03-19
> **nss0000 said:**
> Gents:
...
Assuming the OS-update has ... done-evil... what are my options ? I have no LAN access to that BSODed kit.

It sounds like your system is going through thge normal startup to the point where X windows should be running and interacting with your keyboard and video hardware, but for whatever reason X isn't working correctly.

Did you try any of the function keys such as F2 or F7?  Sometimes those will get around some software problems and allow you to interact with the system.

The fact that the screen is black and is not a command line interface suggests that the X server did start.

I would try booting into recovery mode and using the CLI to try to see what the system is doing.  In particular, I would look in /var/log/Xorg.0.log and I would probably look in the /etc/X11/xorg.conf file to see if the updates damaged something there.

Good luck!

quadproc

---

### Post by nss0000 on 2010-03-19
> **quadproc said:**
> It sounds like your system is going through thge normal startup to the point where X windows should be running and interacting with your keyboard and video hardware, but for whatever reason X isn't working correctly.

Did you try any of the function keys such as F2 or F7?  Sometimes those will get around some software problems and allow you to interact with the system.

The fact that the screen is black and is not a command line interface suggests that the X server did start.

I would try booting into recovery mode and using the CLI to try to see what the system is doing.  In particular, I would look in /var/log/Xorg.0.log and I would probably look in the /etc/X11/xorg.conf file to see if the updates damaged something there.

Good luck!

quadproc

QP:

Thanks for the quick response: I tried F2 & F7 to no avail. 

THEN: I tried to boot from my UBUNTU_install CD. Nothing ...BLACK screen only. THEN I tried getting to BIOS ... again BLACK screen only. 

Some keyboard lights flash. The ethernet_NIC card light is on ... router-light goes.on and the case fans spin. BUT--- could the motherboard or Vid_card have fried ??

---

### Post by quadproc on 2010-03-19
> **nss0000 said:**
> QP:

Thanks for the quick response: I tried F2 & F7 to no avail. 

THEN: I tried to boot from my UBUNTU_install CD. Nothing ...BLACK screen only. THEN I tried getting to BIOS ... again BLACK screen only. 

Some keyboard lights flash. The ethernet_NIC card light is on ... router-light goes.on and the case fans spin. BUT--- could the motherboard or Vid_card have fried ??

This does sound like a possible hardware failure, although the correlation with the updates makes the updates highly suspect.  OTOH, failing to work with the CD really suggests a hardware problem, and not being able to see the usual BIOS startup spiel pretty much eliminates the Linux software.

You say that the router light goes on - does this mean that the router is seeing data, or does it just indicate that a carrier is present?

The keyboard lights flashing suggest that at least parts of the BIOS are alive and functioning.

Could it be the monitor, or the monitor cable?  Sometimes a connector will come loose enough to not connect but will still look like it is plugged in.

One other thing that might be useful - if you have a voltmeter then you could check the power supply voltages going to the motherboard.  Systems normally have lots of +5, some +12, and optionally they may have -5 also.  You might also find +3.3 in some systems.  Generally, the tolerance on these voltages is +- 5%.

Hope this helps.

quadproc

---

### Post by nss0000 on 2010-03-19
> **quadproc said:**
> This does sound like a possible hardware failure, although the correlation with the updates makes the updates highly suspect.  OTOH, failing to work with the CD really suggests a hardware problem, and not being able to see the usual BIOS startup spiel pretty much eliminates the Linux software.

You say that the router light goes on - does this mean that the router is seeing data, or does it just indicate that a carrier is present?

The keyboard lights flashing suggest that at least parts of the BIOS are alive and functioning.

Could it be the monitor, or the monitor cable?  Sometimes a connector will come loose enough to not connect but will still look like it is plugged in.

One other thing that might be useful - if you have a voltmeter then you could check the power supply voltages going to the motherboard.  Systems normally have lots of +5, some +12, and optionally they may have -5 also.  You might also find +3.3 in some systems.  Generally, the tolerance on these voltages is +- 5%.

Hope this helps.

quadproc

Appreciate you staying with this issue:

I have swapped monitors/cables ... after another <no signal> monitor-text the screen stays BLACK. I can't answer the router-light question.

Am a bit hesitant to poke about a "hot" mobo with metal probes. A wholesale power-failure would I guess kill fans & HDD (I believe I can hear it spin_up). 
 
My spare vid-cards are all AGP ... so it's off to CompUsa  tomorrow morning for the cheapest PCI vidcard I would-NOT be embarrassed to put in a new (legacy) mobo should THAT failure prove the cause. I assume I can still get a mobo for an AMD dual_5600 cpu.   

Thanks again for your comments and suggestions. **BTW** I've got the "same" dated OS-upgrade (but U_9.1) sitting on input to this (newer) AMD_965/MSI_gd70 kit and I would bake-in-hot-pipes-upsidedown before installing that new Ubuntu software without knowing what BLACK-screened the other system.

---

### Post by nss0000 on 2010-03-20
Well ... there's good-news and bad-news: First the good news:

**BLACK-screen** was a toasted graphics_card. Clue was ... when I removed all RAM and booted I got the "friendly" 3-beeps! So I installed a new EVGA-nv9400; a nominal boot returned all displays at original screen resolution of 1260x1040. I DID note that no "proprietary" vid_driver was enabled. 

Actually something of a miracle considering how I beat-up on the OS after the 1st BLACK-screen. That's the good news:

Bad news is I foolishly switched display drivers from the nv165 to nv195 and NOW I'm stuck at a screen-res of 640x480 ! Most of the screen is mostly hidden and moving-about to try anything is not easy. I was originally at 1260x1040 and would be pleased to return to that screen resolution. 

How do I convince X-WIN to play nice? As I said it's VERY tough for me to navigate the 640x480 screen. I can't even "push stuff around".

---

### Post by quadproc on 2010-03-20
> **nss0000 said:**
> 

Bad news is I foolishly switched display drivers from the nv165 to nv195 and NOW I'm stuck at a screen-res of 640x480 ! Most of the screen is mostly hidden and moving-about to try anything is not easy. I was originally at 1260x1040 and would be pleased to return to that screen resolution. 

How do I convince X-WIN to play nice? As I said it's VERY tough for me to navigate the 640x480 screen. I can't even "push stuff around".

I don't have any Nvidea experience myself so I can't directly help with that, but here are a couple of general principles that may help:

The xorg.conf file can contain many things related to the display.  You may need to add some entries for your video card/monitor to enable the resolution that you want.  Personally, I try to keep my xorg.conf as simple as I can but there are some things that just don't happen unless you give some guidance to X windows.

Some (these days, many) monitors will report their capabilities electronically back to the video card where the X server can see them and act on them.  I don't know if your monitor does this but you might check to see if there is some monitor control to enable this.

Finally, xrandr allows you to interactively change display resolutions by using the CLI:
```

xrandr -s <n>

```where <n> is a small integer that selects one of the available resolutions.  Executing xrandr --verbose should give you a list of choices.Some versions apparently allow using a spec such as 1200x960 for <n>.

Glad to read that your system is now alive!

quadproc

---

### Post by nss0000 on 2010-03-20
> **quadproc said:**
> I don't have any Nvidea experience myself so I can't directly help with that, but here are a couple of general principles that may help:

The xorg.conf file can contain many things related to the display.  You may need to add some entries for your video card/monitor to enable the resolution that you want.  Personally, I try to keep my xorg.conf as simple as I can but there are some things that just don't happen unless you give some guidance to X windows.

Some (these days, many) monitors will report their capabilities electronically back to the video card where the X server can see them and act on them.  I don't know if your monitor does this but you might check to see if there is some monitor control to enable this.

Finally, xrandr allows you to interactively change display resolutions by using the CLI:
```

xrandr -s <n>

```where <n> is a small integer that selects one of the available resolutions.  Executing xrandr --verbose should give you a list of choices.Some versions apparently allow using a spec such as 1200x960 for <n>.

Glad to read that your system is now alive!

quadproc

I will try your advise with <xrandr>... it's a bit of a challenge to **GRAB** the tool-bar before overlaid with the temperature-bar !!

BTW: I have been able to blunder_about and DLoad & install ( thru envy ) the NVidia graphics card GUI-tool. You can imagine screen-fulls of Debian apt-get whoo.haa. It reports that native screen-display is 1280x1040 ... and that X-WIN has it set for 640x480. But --- I cannot get to all parts of THAT NVidia GUI screen-display assuming I could use it to change X-WIN setting ... the screen characters are just too BIG and screen-display will not "slide"!

---

### Post by nss0000 on 2010-03-21
Gents:

I have repaired screen display ... thanks to posts on various websites. It may help others if I point to the tasks I performed without claiming to understand them ... or be sure my "terms" are correct. But, ofcourse the order-of-command and "typography" is crucial:

PROBLEM: I was "trapped" in a low-res screen display that made **any** interaction with the computer difficult and use of **any** GUI-function practically impossible. 

TASK#1: destroy your current X-Windows & build a NEW xorg.conf file:

I got to a "terminal": then:

< sudo apt-get remove --purge xserver-xorg >
<sudo apt-get install xserver-xorg> 
<sudo dpkg-reconfigure xserver-xorg>

TASK#2: Get required NVIDIA tool support

<sudo apt-get install nvidia-xconfig>
<sudo apt-get install nvidia-glx-new>
<sudo apt-get install nvidia-settings>

TASK#3: ( ?! )

<sudo nvidia-xconfig>

There's a re-boot here ... and afterward I landed in a perfectly automagically configured GUI. It was (previously) advised to run from the terminal:

<sudo nvidia-settings> ... but this always got me error-boxes.

Wish I could make this entire process less-obscure ... I would not  presumed to instruct if I found all the needed steps in-one-place I could point-to. But I didn't. The last day has been a **very** unpleasant experience. A more skillful poster can certainly **clean-up** my comments. 

And UBUNTU/X-WIN developers ought to get their usrland graphics systems_control out of the late 1980s! There is no rational excuse. No wonder the Linux desktop struggles for 1% of usrland market.

---

