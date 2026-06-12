---
title: "can't go higher then 9.04?!"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by 2roombas on 2010-04-13
I have tried numerous times to upgrade to 9.10, different  .iso's, different methods (update manager vs. live CD, fresh install) on my Dell Dimension 2350 desktop. Every single time there is a screen freeze after awhile.  Hard boot, repeat, etc. The screen will remain visible, but it will become  completely non-responsive. Eventually I sigh and reload 9.04, which has aways worked perfectly on this computer (after loading the restricted-extras of course).

I have also recently tried the beta 2 of 10.04, hoping that was just a Karmic problem I had. Again I tried it by doing the update method (yes, going to 9.10 first then  to 10.04, long day!) and a fresh install. I was pleased at first, but as soon as I could smile... crash!. The monitor flicks, goes black, then shuts down (the green "on" light will turn to amber, on but off). The CPU light remains green, but of course all I could do is press the button to shut down the computer.  

I have never filed a bug report before, but will do that if needed. I read the "directions" to filing bugs (in Absolute Beginners Talk) and and it says to be sure this bug is not already filed. Hm, if I have not filed one before how am I supposed to know the answer to that?!?

BTW I had 9.10, plus now I have 10.04 running on my Dell Inspirion 1550 laptop with no problem at all. In fact 10.04 has been on that computer since Alpha 3.  Lucid is awesome!:)

---

### Post by 2roombas on 2010-04-13
I found this from a similar problem. Would this help at all?  I'm not sure what it will do?!
> 
I eventually have found a solution:

1. Load CD and reboot;
2. Hold LEFT SHIFT key for a while;
3. Screen asks:"Load boot in graphic mode?" Answer=n (No!)
4. Installer Boot Menu appears;
5. IMMEDIATELY press TAB key to edit:
6. Add the following to the line "vmlinuz...":
"vga=792 acpi=off noapic radeon.modeset=0"
7. Plymouth splash screen appears with 5 dots changing to red;
8. Gnome Desktop appears, so select "Install Ubuntu 10.04", ENTER;
9. Follow screen prompts to select keyboard type, time, etc;
10. Select partition where Lucid will be installed, etc.
   

---

### Post by 2roombas on 2010-04-13
Someone told me o run lspci... Does this mean anything? Am I even posting this in the right place?

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:06.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by Dayofswords on 2010-04-13
maybe the 9.10 wont work on your pc

i have a small form computer that cant even boot the livecd

have you tried booting thre livecd? to see if it even works?

---

### Post by 2roombas on 2010-04-13
Yes I spent a very long day yesterday trying all sorts of scenarios (day off work syndrome :)) Both 9.10 and 10.04 will work (visual effedcts off)for a while, but 9.10 will randomly freeze, whereas lucid simply flickers then shuts down the monitor.

---

