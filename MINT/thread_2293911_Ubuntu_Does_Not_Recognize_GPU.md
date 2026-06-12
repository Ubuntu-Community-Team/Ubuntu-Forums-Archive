---
title: "Ubuntu Does Not Recognize GPU"
date: 2015-09-08
forum: MINT
---

### Post by &amp;*@Fth&amp;% on 2015-09-08
When I open the driver configurer, nothing shows up. It's a completely blank list with the revert and apply buttons disabled. In addition, if I plug my monitor into my GPU (radeon HD 7950) I get no output, but I get output from my motherboard. Everything is obviously running on integrated graphics, and games are very laggy. If I install fglrx or fglrx-updates, aticonfig reports that it couldn't find a graphics adapter. How do I fix this?

---

### Post by efflandt on 2015-09-08
Does your BIOS have any option to disable the integrated graphics? The only computer I have with integrated graphics is a laptop with Intel and Nvidia graphics and installing nvidia drivers defaults to Nvidia graphics, but allows me to select which graphics to use in NVIDIA X Server Settings. I don't have any dual graphics computer with AMD graphics.

Which Ubuntu version are you running? If you say what CPU and integrated graphics you have (or how your graphics are listed in lspci) someone else may know more about how to handle that.

---

### Post by Bucky Ball on 2015-09-09
Run this in a terminal:

```
sudo lshw -C video
```

Please post the output back here between code tags (see last link in my signature).

When you say 'driver configurer' do you mean 'Additional Drivers'?

---

### Post by &amp;*@Fth&amp;% on 2015-09-09
@efflandt If I disable integrated graphics, I get no video output whatsoever. I use 14.04 LTS, and I have an i5 4690k.
@Bucky Ball That command returns this:
```
  *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
```
And yes, I mean additional drivers.

---

### Post by Yellow Pasque on 2015-09-09
>  If I disable integrated graphics, I get no video output whatsoever.
You need to concentrate on that. If you have integrated graphics enabled, the BIOS/EFI probably initializes that and doesn't initialize the discrete graphics card (at least that's how it used to work in the days of BIOS). In other words, you should expect to see nothing in the 'Additional Drivers' dialog when using integrated graphics.

---

### Post by Bashing-om on 2015-09-09
superrobowizard; Hello;

So far all we know is the Intel chip set. Is the ATI card enabled in bios ?
There 'was' a bug for the ATI proprietary driver install, that is supposed to be recently fixed, 
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1424491)
but let's look at what is and then see about installing a driver.
Post back the outputs of terminal commands:
```

sudo ubuntu-drivers devices
sudo ubuntu-drivers list

```
We see then where we go, and what we do.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by &amp;*@Fth&amp;% on 2015-09-09
@Temujin I'll try that a bit later today, and post an update. If that is the case, that would be an awesomely easy solution!
@Bashing-om Both return nothing, they just run for a couple seconds and then exit. Devices returns absolutely nothing, while list just outputs an empty line. As I'm running Mint I also tried mint-drivers in case it's really picky, but the command doesn't seem to exist.

---

### Post by Bashing-om on 2015-09-09
superrobowizard; Humm .. 

OK, guess that the "ubuntu-drivers" commands are just that - ubuntu specific.
What do we get from:
```

lspci -vnn | grep -i VGA
lspci -nnk | grep -iA2 VGA
lspci -vnn | grep -i 3D

```
In an attempt to identify the hardware ( maybe we also need to look at the PCI id ) to match a driver.

We can do that
[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2015-09-09
> **superrobowizard said:**
> @Temujin I'll try that a bit later today, and post an update. If that is the case, that would be an awesomely easy solution

I didn't give a solution. I just said that not seeing anything in "Additional Drivers" dialog is an expected outcome when you're using the integrated graphics.

---

### Post by &amp;*@Fth&amp;% on 2015-09-09
@Temujin Well, I done a bad. Now I have no display output and can't even see the BIOS to turn integrated graphics back on again. (Sent using my phone)

---

### Post by Yellow Pasque on 2015-09-09
Well, you can remove the Radeon or reset your CMOS (see your mobo's manual).

---

### Post by &amp;*@Fth&amp;% on 2015-09-10
Removing the card doesn't help, and neither did resetting my motherboard. (I'm sure it worked because I previously had the computer set to shut down after holding the power button, but now it shuts down on a tap, which is the default setting)

---

### Post by Yellow Pasque on 2015-09-10
> I done a bad. Now I have no display output
So what exactly did you do?

---

### Post by &amp;*@Fth&amp;% on 2015-09-10
I turned off integrated graphics in the BIOS.

---

### Post by Yellow Pasque on 2015-09-10
How did you do that? BIOS's that I've seen don't give you an option to enable/disable integrated graphics (IGP). They give you an order to initialize graphics, e.g. look in PCI(-e) slot first before initializing IGP, or vice versa. If you don't have any other graphics in your system, the IGP should be used no matter what.

---

### Post by &amp;*@Fth&amp;% on 2015-09-11
Well, I get no video output. Nothing from the GPU or CPU, with the GPU plugged in _or_ unplugged.

---

### Post by Bashing-om on 2015-09-11
superrobowizard; Hummmm ........

Hardware failure ? Do you see bios's splash - boot info - screen when you power up the box from a cold start ?

If you can see bios, then we are looking at a misconfiguration in bios, and/or a graphics issue within the operating system. With the ATI (radeon) chip set the boot parameter 'nomodeset' may prove effective to boot the system to the GUI. 

There is a process
[INDENT][INDENT][INDENT]fault isolation to restoration
[/INDENT][/INDENT][/INDENT]

---

### Post by &amp;*@Fth&amp;% on 2015-09-11
Hmm... I didn't think about that. No, I get no display at all. Not even the BIOS splash. One thing I suspect is maybe some thermal paste got into the CPU socket, but that's not very likely. Hmmm...

---

### Post by Bashing-om on 2015-09-11
superrobowizard; UnGood;

Is this a desk top or other type machine ?

IF a desktop, open the case, do the fans spin up when you start the machine ? .. check all connections, -- power supply can and does fail  ( hey check that fuse !) . If all looks good in the case, swap out the monitor cable for a known good one  - the on/off button on the monitor is in the 'on'  position for sure for sure ! 

Then there is to pull the battery, and maybe - depending on the motherboard reset (jumper pins) CMOS to defaults ??


Until such time as you see the bios splash screen, nothing else matters.

[INDENT][INDENT]I hate when these happen
[/INDENT][/INDENT]

---

### Post by Yellow Pasque on 2015-09-11
Also, see if you can get any POST codes. Your mobo may have an LED that conveniently shows them to you, or there is always the old-fashioned way of listening to the beeps (hook up the case speaker if you never did).

---

### Post by &amp;*@Fth&amp;% on 2015-09-11
This is a home-built itx desktop. The fans do run, and the power LED on the case turns on when I turn on the power. The monitor connection is good (I've been doing my non-testing stuff on another PC with the hard drive transplanted), As above, I connected the pins and reset the CMOS and it didn't help. And from a bit of digging around, it seems my MOBO can't even give postcodes (gigabyte ga-z97n-wifi).

I've managed to get things going now, but I've got red speckles all over my monitor. I don know if that's the HDMI cable being funky, or if my integrated graphics is dying, but It works at least. What do I do now?

---

### Post by Bashing-om on 2015-09-13
superrobowizard; Well ... 

That is a load off. 
Yeah, possible it is the graphics driver.
What release are you on ?
What results when you boot with the "nomodeset" boot parameter ?
What results when you boot up liveDVD ?

[INDENT]it be fault isolation
[INDENT][INDENT][INDENT]to get restoration
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;*@Fth&amp;% on 2015-09-13
I use Linux Mint 17.2 (Ubuntu 14.04). And I don think it's the drivers, because the red funkiness occurs even in the BIOS and GRUB. I have the feeling it may be something that will go away when I get the GPU working. If not, that's not the primary concern. To answer an earlier question, the outputs of lspci are here: [http://pastebin.com/hR2BwMyt](http://pastebin.com/hR2BwMyt)

---

### Post by howefield on 2015-09-13
Thread moved to the "*MINT*" forum.

---

### Post by &amp;*@Fth&amp;% on 2015-09-13
@howefield Sorry, I thought that was where I posted it. Oops!

On another note, the red speckles are gone, so that's good.

---

### Post by &amp;*@Fth&amp;% on 2015-09-14
Well, I've found a piece of very useful information. I have another known-to-work PC, so I put my SSD in that, and it booted up fine. But, when I swapped out that GPU for the troublesome one, I bot the splash screen, I got GRUB, but I didn't get further than that. Swapped back in the good card, and kablam it works. (I didn't get a graphical environment because the other computer has an AMD FX CPU and thus no integrated graphics). Now either the broken drivers I installed somehow wrote something to the card that bricked it, or it was it's time to die and it was just a freak coincidence that it happened when it did. If I broke the GPU's firmware, could I fix it myself by restoring it to it's default state or something like that, or should I pop over to a microcenter and see if they can fix it? Or will I just have to strait up buy a new GPU?

---

### Post by Bashing-om on 2015-09-15
superrobowizard; Hey;

Not all bad news. If it were me I would :
update and upgrade the system
purge the graphic's driver
See what results with the open source driver
then install proprietary drivers and see what results when purging re-installing other versions of the driver.
Bear in mind, to this time we have seen no evidence that the ATI card is active. If that ATI card is bad, or turned off in bios. The system will not recognize there is the ATI card available .

IF The ATI card is viable. Is this the driver we want ?
[http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064](http://support.amd.com/en-us/download/desktop?os=Ubuntu%20x86%2064)
See if you concur; do the 'search' from here :
[http://support.amd.com/en-us/download](http://support.amd.com/en-us/download)

Then we check and insure our software repository has the recommended driver or if it is in our trusted PPA. In 'buntu obtaining a driver from OEM is the means of last resort, as then it is on you to manually maintain that driver and the system at large .

However, until the system sees that card, it does not exist.

[INDENT][INDENT]can not fix what does not exist
[/INDENT][/INDENT]

---

### Post by &amp;*@Fth&amp;% on 2015-09-15
Thanks, it worked! Huzzah!

---

### Post by Bashing-om on 2015-09-16
superrobowizard;; Great !

> **superrobowizard said:**
> Thanks, it worked! Huzzah!

So please enlighten me as to what "worked" ?

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by &amp;*@Fth&amp;% on 2015-09-16
Well actually, I recently found out it didn't work entirely... But here's what I did anyway:
[I]sudo apt-get purge fglrx*
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xserver-xorg-video-ati
sudo reboot
sudo apt-get install fglrx
sudo apt-get install fglrx-amdcccle
sudo reboot[/I]

Now about that *almost working* part... X crashes if I use the driver manager to switch to the open source drivers, and then it kicks me into a command line. But, from there, I can *sudo apt-get install fglrx* and then *sudo reboot* and all is well again.
The thing is, I actually *want* to use the open source drivers... It isn't necessary, but I would like it, as there is significantly better 2d performance with the Xorg driver.

---

### Post by Bashing-om on 2015-09-17
superrobowizard; Welp ;

We can :
> 
The thing is, I actually want to use the open source drivers... It isn't necessary, but I would like it, as there is significantly better 2d performance with the Xorg driver.

I agree, I get better performance on my old system, running ATI for the graphics, with the open source driver.
Before we purge and reinstall, let's do a bit of background on what we are working with.
As I do not know Mint - and how it may differ from mainline ubuntu; what returns:
```

hwe-support-status --verbose
ls -al /usr/bin/hwe-support-status

``` to see what the kernel and Xserver situation is ( release ).

[INDENT][INDENT]linux
[INDENT][INDENT][INDENT]we do have options
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by &amp;*@Fth&amp;% on 2015-09-19
hwe-support-status is not a command, and /usr/bin/hwe-support-status is not a file or directory :(

---

### Post by &amp;*@Fth&amp;% on 2015-09-20
"Xorg -version" prints this:

X.Org X Server 1.15.1
Release Date: 2014-04-13
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.2.0-76-generic x86_64 Ubuntu
Current Operating System: Linux [PC NAME] 3.16.0-38-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-38-generic root=UUID=08fbf948-9860-4678-b9ac-6554e23af18e ro noprompt quiet splash vt.handoff=7
Build Date: 12 February 2015  02:49:29PM
xorg-server 2:1.15.1-0ubuntu2.7 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2

---

### Post by &amp;*@Fth&amp;% on 2015-09-21
I managed to install the open-source drivers by putting my hard drive in a different computer, installing it there, then putting it back. Unfortunately it doesn't seem to have as good 3D performance, but that's a trade-off I'm willing to make.

---

