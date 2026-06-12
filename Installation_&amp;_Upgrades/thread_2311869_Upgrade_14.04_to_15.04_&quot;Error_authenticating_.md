---
title: "Upgrade 14.04 to 15.04 &quot;Error authenticating some packages&quot;"
date: 2016-01-30
forum: Installation &amp; Upgrades
---

### Post by One4All on 2016-01-30
[Resolved]
1) The monitors worked perfectly when I used a couple of Dell adaptors for DisplayPort to DVI.  I would recommend this if anyone has problems
2) The question in the title is answered, I guess, by the fact that the latest version of Ubuntu (15.10 I guess) was about to expire
3) Here is some research I probably should have done before asking:  about.com apt-get is where I searched, and then here is the Debian reference for my reading list
 [http://www.debian.org/doc/user-manuals](http://www.debian.org/doc/user-manuals)
 [http://www.debian.org/doc/manuals/apt-guide/index.en.html](http://www.debian.org/doc/manuals/apt-guide/index.en.html)

Background (updated, in response to comments below)

Bought Dell Optiplex 7010 two or three days ago. Installed 14.04. It mainly works fine, until I want to add another monitor

The computer has two DisplayPorts in the back that I don't know how to use.

It seems if I upgrade to a newer Ubuntu, 15.04 (and then soon after to 15.10), then it will work better.
(There's discussion below where I try to get the DisplayPorts to work without upgrading to 15.04 since the upgrade isn't working.)

Problem:
Software Updater does not work.  It says "Error authenticating some packages"

It shows a list of the packages that did not authenticate:
gettext
libatomic1
libfftw3-single3
libgomp1
libitm1
libquadmath0
libstdc++6
libtsan0
onboard

Questions:
Why didn't the upgrade work?
How might I try to troubleshoot that?

Is there some other way to make this monitor work;

How do I see the logs from the Software Updater and/or try the upgrade by command line;

I tried some steps from another post I found and tried "apt-get upgrade" and it got some Vervet files
(Updated) I did restart the computer and it is still at 14.04 apparently.  I am not sure what that upgrade did.

(See [http://ubuntuforums.org/showthread.php?t=2287135](http://ubuntuforums.org/showthread.php?t=2287135) answer #2 - I learned apt-get upgrade from that. 'apt-get autoclean' is something I have to look into.)

I have run "sudo lshw" and it just shows the one VGA display and nothing about displayport or a daisychain or ....

Here's the display/video card part of lshw


```
*-display
             description: VGA compatible controller
             product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 09
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
```

The Optiplex 7010 may be some kind of custom build, I bought it as a refurb, Also it is Small Form Factor.
Here's a link to where I bought it.
[https://www.discountelectronics.com/product?product_id=207442](https://www.discountelectronics.com/product?product_id=207442)
Dell Optiplex 7010 Core i3 Small Form Factor Computer Windows 7

At the moment my best plan is to obtain a DisplayPort - DVI adaptor, and a DVI cable, and then the hardware should be better.

But I would like some help in knowing how to see the DisplayPort appear in the lshw, and how to have the monitor be recognized.

To use DisplayPort to VGA seems to be not working at all, as the monitor is not recognized.


Thank you O:)

---

### Post by grahammechanical on 2016-01-30
First, Ubuntu 15.04 is about to go end of life in a few days. So, if you do manage to upgrade to 15.04 then do not be slow about upgrading to 15.10.
Second, Ubuntu 14.04.3 should already have the kernels from 15.04. And in a few days 14.04 will get another point release to 14.04.4 that should give it the kernels in 15.10.

Two useful commands

```
uname -a
lsb_release -a
```

They will tell you what kernel is installed and what version of Ubuntu you are on.

Third, using a VGA connection will limit the resolutions available. Expect that.

What have you tried? If you are runing on a proprietary video driver, have you opened the settings utility and tried to detect displays. For the open source video driver that is a utility in system settings that has the option to detect displays.

What kind of monitor is this. Digital or CRT?

Regards.

---

### Post by One4All on 2016-01-30
What have I tried? - really not much.  The OS doesn't seem to recognize the secondary monitor or the port in any way. I imagine I could install some special driver except that seems to be how Windows work, not Linux.  (Would I need to recompile some special driver into the kernel?)   I can't see the ports listed in lshw.

I haven't tried it in Windows yet so the thing to do is boot into Windows and see if that can recognize it.  I imagine it will do that easily and then I can tell you the video resolutions it can have.

Monitor is Acer G215HV.  It is not a CRT.  [http://www.acer.com/ac/en/US/content/model/ET.WG5HP.B01](http://www.acer.com/ac/en/US/content/model/ET.WG5HP.B01) has a fact sheet.

[TABLE="class: grid, width: 400, align: left"]
[TR]
[TD]Maximum Resolution[/TD]
[TD]1920 x 1080[/TD]
[/TR]
[TR]
[TD]Standard Refresh Rate[/TD]
[TD]60 Hz[/TD]
[/TR]
[TR]
[TD]Color Supported[/TD]
[TD]16.7 Million Colors[/TD]
[/TR]
[TR]
[TD]Contrast Ratio[/TD]
[TD]20,000:1[/TD]
[/TR]
[TR]
[TD]Brightness[/TD]
[TD]200 Nit[/TD]
[/TR]
[/TABLE]



Although you didn't ask, 
```

$uname -a
Linux {name} 3.19.0-47-generic #53~14.04.1-Ubuntu SMP Mon Jan 18 16:09:14 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
$lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty

```

I have tried mostly just googling (duckduckgo actually) for 'ubuntu displayport' and a few other keywords added like 15.04 or 14.04 etc.

Thank you for the suggestion to stop trying to upgrade.

I am curious whether maintenance updates for LTS 14.04 would have improved drivers sometimes, for more hardware.  I think they would! And kernel updates sometimes too!

---

### Post by Vladlenin5000 on 2016-01-31
According to [this]("http://www.cnet.com/products/dell-optiplex-7010-core-i7-3770-3-4-ghz-monitor-none-series/specs/") your Dell Optiplex 7010 has an AMD Radeon HD 7570 graphics which most likely requires proprietary AMD drivers (fglrx) for full functionality and optimal performance.

However, there's a few details in your story that don't make sense:
1. Your desktop, according to the source above, has **DVI**,                                                                              **DisplayPort** and                                                                              **VGA**;
2. Your intended secondary monitor, according to the specs listed in your link in post#3, has **DVI** and **VGA**.
 S, considering the above, why are you using an adapter? Also keep in mind you a) cannot convert digital to analog or vice-versa with a simple, passive, adapter. You need a converter which differs from a simple adapter because it actually has electronics inside for the purpose of video conversion whereas the passive adapters are just wires. Those adapters have a very narrow scope of usage because they were and are designed for non-standard implementations, i.e., devices that either output (or accept input) from either source; and b) ALWAYS prefer digital connections whenever possible.

---

### Post by One4All on 2016-01-31
My link was inaccurate, sorry!  I have a different build, I'll try to find the info online ... editing ...

The computer has just VGA (occupied by the main monitor) and two DisplayPort.
But the OS doesn't seem to know anything at all about the DisplayPorts.

What  would they look like in lshw if they were showing up?  Did I not read  lshw right? How would I make them appear as available hardware?

Here's some different info on the hardware

```

$sudo lshw | grep '*-'
  *-core
     *-firmware
     *-cpu
        *-cache:0
        *-cache:1
        *-cache:2
     *-memory
        *-bank:0
        *-bank:1
        *-bank:2
        *-bank:3
     *-pci
        *-display
        *-usb:0
        *-communication
        *-network
        *-usb:1
        *-multimedia
        *-usb:2
        *-isa
        *-storage
        *-serial UNCLAIMED
     *-scsi:0
        *-disk
           *-volume:0
           *-volume:1
           *-volume:2
              *-logicalvolume:0
              *-logicalvolume:1
              *-logicalvolume:2
     *-scsi:1
        *-cdrom
  *-network

```

---

### Post by Vladlenin5000 on 2016-01-31
The information about the graphics card/chip is of the utmost importance. Dell has many variants for the same model.

(EDIT)

Didn't notice before but you actually posted those details in the OP. So... Intel chips do not require special drivers, they just work (most of them). The problem is in the adapter as explained before.
And I insist: Even assuming your primary monitor has absolutely no other connection than the old VGA, why use an adapter to VGA for the second one which has DVI? Don't you think it makes way more sense to use a DP-to-DVI (yes, those can be passive because no conversion is necessary from digital to digital)?

---

### Post by One4All on 2016-02-01
I think you are right, I should use DVI for the one that has DVI. Actually they BOTH have DVI so I should use DVI for both!!

---

