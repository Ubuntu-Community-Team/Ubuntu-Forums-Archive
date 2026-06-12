---
title: "Feedback on initial installation of 14.04 on older system"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by Nosphky on 2014-04-24
After 2 unsuccessful attempts to install Ubuntu Desktop 13.10 on a pc from the 2002 ish era, I decided to try with Lubuntu.  This machine has an AMD K7/Duron processor and only 384mega of RAM and was last used some years' ago running Windows XP.  (But I did check it out fully functioning before trying to install Ubuntu).

I installed from a CD.  Procedure was straightforward if lengthy and the only item causing concern was the time-zone.  Installation correctly identified my keyboard as GB and therefore presumably assumed my time-zone was UK.  It gave me 3 options - Yes, No, GoBack.  I selected No expecting to be able to select the correct time-zone but installation simply passed onto the next step.  I went back and retried 2 more times but result was always the same.

That was the only hiccup I encountered in the installation process.

After installation, a reboot was called for and made.  This presented Lubuntu to me with 3  visible problems :

1.  wrong time
2.  US keyboard despite having seen GB confirmed during installation
3.  the desktop display did not fill the screen and seemed to have an offset to the left because there was a 5 cms black vertical section on the righthand side of the screen and no 'menu' icon visible on the top panel.

A right click on the top panel got me the panel preferences and I set the panel to display vertically on the right side of the screen and was able to access the 'menu' icon from which I corrected the time zone but was unable to change the keyboard type.

Another reboot, next morning, made the keyboard come up as GB - I don't know how that happened - but ok, good.

Problem to fix is the display.   At boot time, the Lubuntu splash screen is perfectly centred but something goes astray afterwards.

---

### Post by ubfan1 on 2014-04-24
When you switch to a virtual terminal (Alt-Ctrl-F2) (really function keys 1-6 should be active) is the offset still present?  If so, look for monitor adjustments to recenter the running display.  If not, then in xorg.conf, a new mode-line will fix the problem.  If you don't even have an xorg.conf file anymore (/etc/X11/xorg.conf), you will need to generate one.  Look to any vendor supplied display settings program first, it may offer to generate one, otherwise, the X server itself may generate one, but the     gotcha is that the X server cannot be running while you do it.

---

### Post by Nosphky on 2014-04-24
Thanks, Ubfan1 :   I can switch to a virtual terminal using alt-ctrl-F2 and the screen seems to be well displayed although its non-graphic.  I judge that it's ok because I can see all the left hand end of text lines.   

I logged in ok and exited but, unfortunately, I'm not clued up enough to know how to get back to the desktop gui so it was a hardware reset / reboot to get back.

Then I checked the /etc/X11/ directory for a xorg.conf file but there isn't one.

So how to generate one ?  I'll need some help with procedure here.

I'm reluctant to fiddle with settings on the monitor (a HPw2207) because it also serves my main pc (a dual boot Windows7 and UbuntuStudio 13.10 setup).  Both machines are set up with a KVM switch so I use same screen, keyboard and trackball for both, switching from one to the other by a small push button on the table top.   This set up has been working perfectly for several weeks during which time the older machine (now on Lubuntu) was on Windows XP.

---

### Post by Nosphky on 2014-04-24
As I explore Lubuntu more, the general performance level is clunky and slow.  After clicking on file manager, for example, nothing happens for about 2 seconds.  When I slide a window across the screen, it moves slowly.  When I type a line of text, there is a visible delay between the appearance of each letter.   This is contrary to my experience in adding UbuntuStudio to my main machine and a dual boot Ubuntu desktop to my wife's XP machine.  In both those cases, Ubuntu works as fast as windows and even faster in most cases.
 
Input Method Configuration shows following :

"Current configuration for the input method:
 * Active configuration: ibus (normally missing)
 * Automatic configuration: ibus (normally ibus or fcitx or uim)
 * Number of valid choices: 2 (normally 1)
The configuration set by im-config is activated by re-starting X.
Explicit selection is not required to enable the automatic configuration, if the active one is default/auto/cjkv/missing.
  Available input methods: ibus xim
Unless you really need them all, please make sure to install only one input method tool."

I really don't know what ibus is but I see that normally there should be 1 input method and I somehow have 2 - could there be a conflict slowing down the display and causing the displacement ?

---

### Post by ubfan1 on 2014-04-24
From a virtual terminal 1-6, use Alt-F7  (no ctrl needed) to get back to the X (Gui ) screen.  OK, different machines' graphics will sometimes do what you described, so the solution is changing the X display by generating a new modeline, and inserting it into an xorg.conf.  See [http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there) for generating a new xorg.conf file.  Hopefully, the new xorg.conf will have a section with modelines already present, so you can just edit or add yours to the list.  The DANGEROUS program xvidtune will allow you to interactively move the screen around on the display, and when satisfied, generate a modeline for it.  Do not make any drastic changes, you risk overdriving your monitor and destroying it.  If you cannot successfully move the screen to where you want it, better leave things alone, the graphics card has it's limits.  Maybe you can have a medium settings (manually set) to make it usable for both systems.

---

### Post by ubfan1 on 2014-04-24
I get pretty much the same on in-config output, so that's probably not the issue.  Maybe a graphics driver -- I have use the Nvidia driver, and some releases do have the slow window drag problem.  Maybe a proprietary driver is available for your hardware?  I think the "additional drivers" is  under the "update-manager"'s fourth tab.  See what's offered.  You might try the manual approach to see if the windows side will successfully auto adjust itself also.

---

### Post by Nosphky on 2014-04-24
Thanks - that gives something to get going on in the next day or so.

---

### Post by mörgæs on 2014-04-24
We can't take for granted that any additional drivers are available. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Nosphky on 2014-04-26
Hi Mörgæs :  2 points :

- I don't understand the reference to CODE tags - I suppose it is a protection mechanism - how to do it ?

- second point is a little more difficult.  I thought my display could be improved by installing a graphics card rather than just relying on the mother board functionality. (I've never been interested in gaming or videos so I've never used dedicated graphics cards)   Given the age of the pc,  the only card I could get was AGP  Twintech FX5500.  

The first restart after plugging in the card was promising.  The Lubuntu splash screen was much sharper.  The main screen came up and occupied the whole of the screen (no unused black 5cm margin on the lright hand side) and was much sharper in definition than previously.  The 'top panel' was vertically on the right , where I had had to place it to read the icons (see message above).

Unfortunately, there was nothing behind the icons.  Clicking didn't start anything, no right click context menu so no way to put the top panel back on top where it belonged.  Keyboard indication was back to US.   Ctrl-alt-F2 opened a terminal where the situation was marginally worse than before - the first text column was partly missing so first letter on each line had to be guessed at.  Alt-F7 got me back to the gui but unable to do anything.

A hardware reset brought up the same case - except this second time, the keyboard was correctly shown as GB, but no ability to do anything by clicking on icons or right clicking.

I will try a re-install this weekend, if possible.

---

### Post by coffeecat on 2014-04-26
> **Nosphky said:**
> 
- I don't understand the reference to CODE tags - I suppose it is a protection mechanism - how to do it ?


Not a protection mechanism - just a way of presenting terminal output in a readable way with formatting preserved, which doesn't happen if you post bare into your posted text.

[http://ubuntuforums.org/showthread.php?t=2054969&p=12231647#post12231647](http://ubuntuforums.org/showthread.php?t=2054969&p=12231647#post12231647)

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

In short:

[noparse]```
Your terminal output
```[/noparse]

Appears as:

```
Your terminal output
```

Quick and easy way: use the advanced editor, not the quick reply editor, and then the # icon in the editor toolbar.

**Edit**: when using BBCode, you may find it easier not to use the wysiwyg editor. Either Settings -> General Settings -> change your default for all postings under Message Editor Interface. Or, to toggle from one editor interface to another in a single post, use the first icon that looks something like A/A in the message toolbar.

---

### Post by Nosphky on 2014-04-26
Thanks for the explanation Coffeecat.

I just rebooted the machine - yet again- and this time it stalled with display of this message :

"SIS630_smbus 0000:00:04.0: SIS630 compatible bus not detected, module not installed" 
I've no idea what that's about and since the pc stalled, I used the hardware reset and the reboot then went ahead perfectly giving me a fine desktop with excellent resolution and icons which could be clicked.
I reset the top panel to the top and all seems well with the world.

It must have taken 7 or 8 reboots for Lubuntu to sort it all out.

Although all appears well, I did the -  sudo lshw -sanitize > lshw.txt   with the hope that someone can tell me if all is well.  The output of this operation is given below :

```
computer
    description: Desktop Computer
    product: 1234567890
    vendor: Uknown Chassis Manufacture
    version: 1234567890
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=desktop
  *-core
       description: Motherboard
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 062710
          date: 07/15/97
          size: 64KiB
          capacity: 192KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Duron(tm) Processor
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 6.7.1
          slot: Sockey-A
          size: 1300MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: Internal Cache
             size: 128KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: Internal Cache
             size: 64KiB
             capacity: 1MiB
             capabilities: synchronous internal write-back unified
     *-memory
          description: System memory
          physical id: 1
          size: 368MiB
     *-pci
          description: Host bridge
          product: 730 Host
          vendor: Silicon Integrated Systems [SiS]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-sis latency=32
          resources: irq:0 memory:d0000000-d3ffffff
        *-ide
             description: IDE interface
             product: 5513 IDE Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: d0
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=pata_sis latency=128
             resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:ff00(size=16)
        *-isa
             description: ISA bridge
             product: SiS85C503/5513 (LPC Bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: SiS900 PCI Fast Ethernet
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.1
             bus info: pci@0000:00:01.1
             logical name: eth0
             version: 82
             serial: [REMOVED]
             size: 100Mbit/s
             capacity: 100Mbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=[REMOVED] latency=64 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100Mbit/s
             resources: irq:3 ioport:cc00(size=256) memory:cfffb000-cfffbfff memory:cffc0000-cffdffff
        *-usb:0
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.2
             bus info: pci@0000:00:01.2
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:11 memory:cfffc000-cfffcfff
        *-usb:1
             description: USB controller
             product: USB 1.1 Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.3
             bus info: pci@0000:00:01.3
             version: 07
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master
             configuration: driver=ohci-pci latency=64 maxlatency=80
             resources: irq:11 memory:cfffd000-cfffdfff
        *-multimedia
             description: Multimedia audio controller
             product: SiS PCI Audio Accelerator
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.4
             bus info: pci@0000:00:01.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_trident latency=64 maxlatency=24 mingnt=2
             resources: irq:11 ioport:d000(size=256) memory:cfffe000-cfffefff
        *-communication UNCLAIMED
             description: Modem
             product: AC'97 Modem Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 1.6
             bus info: pci@0000:00:01.6
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=64 maxlatency=11 mingnt=52
             resources: ioport:d800(size=256) ioport:d400(size=128)
        *-pci
             description: PCI bridge
             product: AGP Port (virtual PCI-to-PCI bridge)
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master vga_palette
             resources: ioport:a000(size=4096) memory:cde00000-cfefffff memory:adc00000-cdcfffff
           *-display UNCLAIMED
                description: VGA compatible controller
                product: NV34 [GeForce FX 5500]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 32 bits
                clock: 66MHz
                capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
                configuration: latency=64 maxlatency=1 mingnt=5
                resources: memory:ce000000-ceffffff memory:b0000000-bfffffff memory:cfee0000-cfefffff
     *-scsi
          physical id: 2
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: Maxtor 2F040J0
             vendor: Maxtor
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: VAM5
             serial: [REMOVED]
             size: 38GiB (41GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000d0078
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 9536MiB
                capacity: 9536MiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2014-04-23 03:28:58 filesystem=ext4 lastmountpoint=/ modified=2014-04-26 19:08:16 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2014-04-26 19:08:18 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 28GiB
                capacity: 28GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 733MiB
                   capabilities: nofs
              *-logicalvolume:1
                   description: Linux filesystem partition
                   physical id: 6
                   logical name: /dev/sda6
                   logical name: /home
                   capacity: 28GiB
                   configuration: mount.fstype=ext4 mount.options=rw,relatime,data=ordered state=mounted
        *-cdrom
             description: DVD reader
             product: COMBO SOHC-5236V
             vendor: LITE-ON
             physical id: 0.1.0
             bus info: scsi@0:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: R$0G
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
```

Philip

---

### Post by mörgæs on 2014-04-26
Your processor does not have SSE2 so you will not be able to run the latest Flash. 

The FX 5500 graphics card is fine and there might be additional drivers available for it (as opposed to old ATI cards). 

First of all you should give the poor thing some more memory. You might be able to install on 384 MB using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"), but that's not the same as having a useable system afterwards.

Please see the link in my signature for more details.

---

### Post by Nosphky on 2014-04-27
> **mörgæs said:**
> Your processor does not have SSE2 so you will not be able to run the latest Flash. 

The FX 5500 graphics card is fine and there might be additional drivers available for it (as opposed to old ATI cards). 

First of all you should give the poor thing some more memory. You might be able to install on 384 MB using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"), but that's not the same as having a useable system afterwards.

Please see the link in my signature for more details.

Thanks for that.  My display problem is pretty well fixed so I'll mark this as solved.

When I dug this machine out of hiding in my hangar, I tried it out and found I had to change the bios battery.  I asked in the local computer shop if the guy had any more sticks of ram because this machine only had 192 MB !!   He told me it was an obsolete type but he did find 1 second hand memory module in a box which he gave me. 

So I am lucky to get it going with 384 MB.  But if I can find any more, I'll increase it.

I did install Lubuntu from the alternate-iso  after failing to get ubuntu 13.10 to install from either a usb stick or from a CD.

My intention is to see if I can get a small server running on this pc.   But for now, the graphics are fine and I don't need flash.

I'll have a look at the links you suggest.

Thanks to all who helped me on my way.

---

