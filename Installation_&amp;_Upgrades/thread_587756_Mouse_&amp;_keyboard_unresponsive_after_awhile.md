---
title: "Mouse &amp; keyboard unresponsive after awhile"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by RFScheer on 2007-10-23
It's a judgment call but my problem doesn't exactly fit with other threads as best I can tell however I'll bet it's a very common basis for problems.

I have been very happy with a fresh Gutsy install and thought everything was working well, however over the past day now I've experienced maybe 4 unpredictable episodes in which the Logitech MX3000 wireless mouse & keyboard essentially stop working, or almost.  When that happens, the only remedy is reboot and that works every time.  Logging out and back in doesn't help and I haven't tried Ctrl Backspace but I'm not really interested in workarounds anyway.  New batteries.  Etc.  All tried.

This hardware setup worked extremely well under Feisty, although I'll admit there were a couple of crashes over the past 6 months and there were zero under Dapper.  

About a month prior to installing Gutsy, I added a 2nd display.  You'll see all this stuff in the hardware list coming up.  The dual head setup worked well under Feisty.  I was using no visual effects under Feisty but I've selected the Extra setting from System > Preferences > Appearance > Visual Effects.  I really like the new Compiz display.  

I'm pretty sure we can see a clue in the System Monitor Resources graphs.  Every 33 seconds without fail there is a spike in CPU usage.  Both cores of my Athlon X2 spike at the same time and the amount varies depending on stuff happening.  It's not ok what I'm seeing, there's no question in my mind.  These dynamics are not going to be stable.

Take a look at my system running with no user apps running:

[IMG]http://scheerstuff.net/tarzan/worb.png[/IMG]

You see every 33 seconds the CPU usage spikes to 25% or so on both cpu's.  Running top, the culprits are Xorg and then gnome-system-mo which is the System Monitor.  Running top with 1 second delay shows Xorg leading off with perhaps 25% cpu usage replaced quickly with SM taking maybe half that.

Ok now look at what happens when Rhythmbox is running but not playing or indexing.

[IMG]http://scheerstuff.net/tarzan/wrb.png[/IMG]

Same 33 second period but now the amplitude is over 40%.  Keep in mind Rhythmbox doesn't even show up on top.  It's doing almost nothing.  

Now finally we see the situation with RB playing.

[IMG]http://scheerstuff.net/tarzan/playing.png[/IMG]

Now the cpu utilization spikes are between 50-60% while RB is utilizing 3-5% avg.  

I'm not going to keep showing screenshots of System Monitor but you probably don't have a problem believing that it's easy to achieve 100% either on spikes or avg depending on what you load the system with.  Some times when that happens, I crash.  Not always, but I'm convinced that it's during high utilization and when Xorg demands too much, something gives way.  

I also found that the Network History graph is behaving incorrectly but that's not central to this story.  Suffice to say, after this problem is resolved, we could talk about network issues.  

Here's my hardware:

```
~> sudo lshw -short
H/W path            Device     Class          Description
=========================================================
                               system         System Product Name
/0                             bus            A8V-E SE
/0/0                           memory         128KB BIOS
/0/4                           processor      AMD Athlon(tm) 64 X2 Dual Core Processor 3800+
/0/4/b                         memory         128KB L1 cache
/0/4/d                         memory         512KB L2 cache
/0/5                           processor      CPU
/0/5/c                         memory         128KB L1 cache
/0/5/e                         memory         512KB L2 cache
/0/37                          memory         2GB System Memory
/0/37/0                        memory         1GB DIMM DDR Synchronous 400 MHz (2.5 ns)
/0/37/1                        memory         DIMM [empty]
/0/37/2                        memory         1GB DIMM DDR Synchronous 400 MHz (2.5 ns)
/0/37/3                        memory         DIMM [empty]
/0/100                         bridge         K8T890 Host Bridge
/0/100/0.5                     system         K8T890 I/O APIC Interrupt Controller
/0/100/1                       bridge         VT8237 PCI bridge [K8T800/K8T890 South]
/0/100/2                       bridge         K8T890 PCI to PCI Bridge Controller
/0/100/2/0                     display        NV44 [GeForce 6200 TurboCache(TM)]
/0/100/3                       bridge         K8T890 PCI to PCI Bridge Controller
/0/100/3.1                     bridge         K8T890 PCI to PCI Bridge Controller
/0/100/3.2                     bridge         K8T890 PCI to PCI Bridge Controller
/0/100/3.3                     bridge         K8T890 PCI to PCI Bridge Controller
/0/100/c                       multimedia     RME Hammerfall DSP
/0/100/d            eth0       network        3c905 100BaseTX [Boomerang]
/0/100/f            scsi0      storage        VIA VT6420 SATA RAID Controller
/0/100/f/0.0.0      /dev/sda   disk           149GB SAMSUNG HD160JJ
/0/100/f/0.0.0/1    /dev/sda1  volume         4996MB Linux filesystem partition
/0/100/f/0.0.0/2    /dev/sda2  volume         5938MB Extended partition
/0/100/f/0.0.0/2/5  /dev/sda5  volume         5938MB Linux swap / Solaris partition
/0/100/f/0.0.0/3    /dev/sda3  volume         138GB Linux filesystem partition
/0/100/f.1                     storage        VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
/0/100/f.1/0        ide0       bus            IDE Channel 0
/0/100/f.1/0/0      /dev/hda   disk           SONY DVD RW DW-Q120A
/0/100/10                      bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                    bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.4                    bus            USB 2.0
/0/100/11                      bridge         VT8237 ISA bridge [KT600/K8T800/K8T890 South]
/0/100/11.5                    multimedia     VT8233/A/8235/8237 AC97 Audio Controller
/0/100/11.6                    communication  AC'97 Modem Controller
/0/101                         bridge         K8T890 Host Bridge
/0/102                         bridge         K8T890 Host Bridge
/0/103                         bridge         K8T890 Host Bridge
/0/104                         bridge         K8T890 Host Bridge
/0/105                         bridge         K8T890 Host Bridge
/0/106                         bridge         K8 [Athlon64/Opteron] HyperTransport Technology Configuration
/0/107                         bridge         K8 [Athlon64/Opteron] Address Map
/0/108                         bridge         K8 [Athlon64/Opteron] DRAM Controller
/0/109                         bridge         K8 [Athlon64/Opteron] Miscellaneous Control

```

---

### Post by RFScheer on 2007-10-23
Yikes, how to post the screenshots correctly? (ok, well, I guess it's obvious even to the uninformed that you have to host the images at some website).  

- Robert

---

