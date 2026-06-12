---
title: "Lubuntu 14.04 install. No text. Keyboard not working."
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by MadMax2 on 2014-05-31
I have a compaq presario B2000 laptop and I am trying to install Lubuntu  [lubuntu-14.04-desktop-i386.iso.]
 Everything going well except there is no keyboard entry so can't continue.

-cpu
          description: CPU
          product: Intel(R) Pentium(R) M processor 1500MHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.9.5
          slot: U1
          size: 1500MHz
          capacity: 1500MHz
          width: 32 bits

Thanks Anyone

Keyboard works with Kernel	Linux 3.2.0-23-generic (i686)

Could be old bios? If so can I get a new chip? This is old laptop

---

### Post by MadMax2 on 2014-06-03
Lubuntu 14.04 install. No text. Keyboard not working. - Can't install Lubuntu 14.04 as laptop keyboard not working.

I get to Language [Enter] Timezone [Enter] Keyboard Layout [Enter] > When name and password [empty forms] appear typing leaves spaces blank (no text formed.

Is there a work around - bring up a terminal  and install missing package (whatever it is)?

---

### Post by Bashing-om on 2014-06-04
MadMax2: Hi ! 

A PAE issue ?

See:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)
[http://ubuntuforums.org/showthread.php?t=2211590](http://ubuntuforums.org/showthread.php?t=2211590) <- Now 14.04 Lubuntu has support for non-pae:

Just
[INDENT][INDENT]hope this helps[/INDENT][/INDENT]

---

### Post by MadMax2 on 2014-06-04
This is a[ repeat ]("http://ubuntuforums.org/showthread.php?t=2227268")of earlier post

I get to Language [Enter] Timezone [Enter] Keyboard Layout [Enter] > When name and password [empty forms] appear typing leaves spaces blank.

Is there a work around - bring up a terminal (Ctrl + Alt + T) and install missing package (whatever it is)? 
I never thought to try that as I thought text wouldn't work in terminal if it doesn't work in LXDE?

I reinstalled 12.04 but I would like to keep up to date.

---

### Post by QIII on 2014-06-04
*Threads **merged.***

Please do not start multiple threads for the same issue.  If you do not get a response, bump the original thread by responding to it with the word "Bump".

---

### Post by MadMax2 on 2014-06-04
> **QIII said:**
> *Threads **merged.***

Please do not start multiple threads for the same issue.  If you do not get a response, bump the original thread by responding to it with the word "Bump".
 As in unanswered thread thread I reply "Bump" and start a new one?

---

### Post by MadMax2 on 2014-06-04
> D. Install the development version 14.04 as described at the top of the page. The new option 'forcepae' does the same as Fake-PAE and makes the installation straightforward. Be aware that as of today (2014-03-16) 14.04 is still in development, so expect the unexpected. 
............
I did that the mouse worked but not text input [white spaces in field] so installation failed.
There's no key to bring up terminal? Crl Apt T didn't work.

Got this message:
[errno 2 no such file or directory:'/target/lib/firmware/asihpi/dsp6600.bin]

---

### Post by sudodus on 2014-06-04
0. It seems that you have got past the PAE issue (I guess you use forcepae).


1. I cannot find any information about the RAM (size). Your problem might be that you have too little RAM for the desktop installer.

Are you trying to install from the desktop iso file (where the first entry in the main boot menu (after language) is 'Try Lubuntu ...'? This is an installer with a graphical interface.

Or are you trying to install from the alternate iso file (where the first entry the main boot menu (after language) is 'Install Lubuntu ...'? This is an installer with menus in a text interface, and it needs less RAM than the desktop installer.


2. It might also be a problem with the driver for graphics or wifi. Please specify the

- graphics chip/card
- wifi chip/card


*. See this link for more details to help you get Lubuntu working

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods)

---

### Post by MadMax2 on 2014-06-04
~$ free -m
             total       used       free     shared    buffers     cached
Mem:           479        465         13          0         13        225
-/+ buffers/cache:        226        252
Swap:          492          0        492
john@john-Presario-B2000-PD257PA-AB5:~$ 

That is running 12.04.4.

> Are you trying to install from the desktop iso file (where the first entry in the main boot menu (after language) is 'Try Lubuntu ...'? This is an installer with a graphical interface. yes it's the graphical install
*-display:0
            description: VGA compatible controller
            product: 82852/855GM Integrated Graphics Device
            vendor: Intel Corporation
            physical id: 2
            bus info: pci@0000:00:02.0
            version: 02
            width: 32 bits
            clock: 33MHz
            capabilities: pm vga_controller bus_master cap_list rom
            configuration: driver=i915 latency=0
            resources: irq:11 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
*-display:1 UNCLAIMED
            description: Display controller
            product: 82852/855GM Integrated Graphics Device
            vendor: Intel Corporation
            physical id: 2.1
            bus info: pci@0000:00:02.1
            version: 02
            width: 32 bits
            clock: 33MHz
            capabilities: pm cap_list
            configuration: latency=0
            resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff

  description: Wireless interface
               product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
               vendor: Intel Corporation
               physical id: 2
               bus info: pci@0000:02:02.0
               logical name: eth1
               version: 04
               serial: 00:0c:f1:36:4c:ec
               width: 32 bits
               clock: 33MHz
               capabilities: pm bus_master cap_list ethernet physical wireless
               configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
               resources: irq:11 memory:e0200000-e0200fff
          *-network:1

---

### Post by QIII on 2014-06-04
> **MadMax2 said:**
> As in unanswered thread thread I reply "Bump" and start a new one?

No.  *Don't* start a new thread.

Bump the one you already started.  Do not start multiple threads about the same problem in different areas of the Forums.

---

### Post by MadMax2 on 2014-06-04
I didn't understand* bump*; I associated it with *dump* (as in bump someone off).

---

### Post by MadMax2 on 2014-06-04
I see Lubuntu 14.04 is supported for two more years.
I tried installing bodhi-2.4.0-nonpae-32.iso  It started and just ground to a halt (not enough ram?.
Also tried Lubuntu 14.04 mini.iso but couldn't find a way to enter "forcepae".

---

### Post by QIII on 2014-06-04
Bump it to the top of the queue to get it noticed again.  But no more often than once every 24 hours.

---

### Post by sudodus on 2014-06-05
> **MadMax2 said:**
> ~$ free -m
             total       used       free     shared    buffers     cached
Mem:           479        465         13          0         13        225
-/+ buffers/cache:        226        252
Swap:          492          0        492
john@john-Presario-B2000-PD257PA-AB5:~$ 

This indicates 512 MB RAM (some is pre-allocated). It should be enough to run Lubuntu.

If you still have problems installing, I suggest you try the [alternate installer]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"). 
> 
That is running 12.04.4.

 yes it's the graphical install
*-display:0
            description: VGA compatible controller
            product: 82852/855GM Integrated Graphics Device
            vendor: Intel Corporation
            physical id: 2
            bus info: pci@0000:00:02.0
            version: 02
            width: 32 bits
            clock: 33MHz
            capabilities: pm vga_controller bus_master cap_list rom
            configuration: driver=i915 latency=0
            resources: irq:11 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
*-display:1 UNCLAIMED
            description: Display controller
            product: 82852/855GM Integrated Graphics Device
            vendor: Intel Corporation
            physical id: 2.1
            bus info: pci@0000:00:02.1
            version: 02
            width: 32 bits
            clock: 33MHz
            capabilities: pm cap_list
            configuration: latency=0
            resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff

You might be helped by UXA acceleration according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)
> 
  description: Wireless interface
               product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
               vendor: Intel Corporation
               physical id: 2
               bus info: pci@0000:02:02.0
               logical name: eth1
               version: 04
               serial: 00:0c:f1:36:4c:ec
               width: 32 bits
               clock: 33MHz
               capabilities: pm bus_master cap_list ethernet physical wireless
               configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 multicast=yes wireless=unassociated
               resources: irq:11 memory:e0200000-e0200fff
          *-network:1

I think Intel network (wired and wireless) should be OK.

---

### Post by MadMax2 on 2014-06-05
It works fine with lubuntu 12.04.4 (I see it is supported two more years). Maybe I should retry 14.0x in a month or 2?

---

### Post by sudodus on 2014-06-05
The problem is that Lubuntu 12.04 did not come with long time support. It passed end of life long ago. The engine under the hood is Ubuntu 12.04 LTS, which receives updates (including security updates), but the Lubuntu specific program packages do not. So I would not recommend it. You can use it, but you are on your own concerning security updates.

There are re-spins that promise long time support until April 2017 based on Ubuntu 12.04 LTS: ***Bento, Bodhi, LXLE***. I would recommend these instead of Lubuntu 12.04.

-o-

But you might be successful if you try some tweaks with Lubuntu 14.04 LTS. It works in many old computers.

*Edit*: There will be bugfixes in a month or two. Wait for the first point release, Lubuntu 14.04.1. But do not expect new drivers for graphics or similar improvements if that is what you need.

---

