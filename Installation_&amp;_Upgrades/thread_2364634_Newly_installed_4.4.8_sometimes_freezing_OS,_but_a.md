---
title: "Newly installed 4.4.8 sometimes freezing OS, but always having one core at 100%!"
date: 2017-06-26
forum: Installation &amp; Upgrades
---

### Post by crazybear on 2017-06-26
> **OMG! I made a BIG mistake in the title, which I now can't edit. I did NOT mean 4.4.8, but 4.8.0-56  Sorry! Someone fix that if they like.**

Hmmm. Not sure what is going on, but worrying. I had been having trouble with my AMD Radeon GPU [3 monitor system] in 16.04, so I had read that installing the new hwe and kernel 4.4.8 often solved this. Just struggled to install the 4.4.8 and did. It has certainly solved the monitor problems [one monitor would often was totally unclear or black] - but a few days in and I noticed first often freezing of the system. That seems to have morphed into high cpu usage with one core [of 12] ALWAYS at 100% even when all programs but the most basic are closed. This NEVER happened in 12.04, 14.04 - nor in 16.04 before these new kernels. Also, a few times I have seen the system load go from 1.xx to HUGE numbers and VERY quickly!

Bash Om had written me on the end of the fixing the thread on problematic install of 4.4.8:

> 
[COLOR=#000000]I do not see a freeze as related to this thread . Start a new thread on this new issue.[/COLOR]
[COLOR=#000000]How are you able to restart the system when the freeze occurs ?[/COLOR]
[COLOR=#000000]When the system freezes do you still have keyboard input ?[/COLOR]
[COLOR=#000000]Magic SysRq key method: hold down the Alt+SysRq keys and slowly run through the sequence R,E,I,S,U,B - after the B, your system will reboot (or if you want to shut it down, make the last letter o). For systems without a SysRq label on the key, it's the Prt Scr key.[/COLOR]
[COLOR=#000000]As we do want a graceful resumption of service . Else real bad things can happen .[/COLOR]

[COLOR=#000000]In this new thread show:[/COLOR]
[COLOR=#000000]Code:
lspci -k|grep -iEA5 'vga|3d'
sudo lshw -C display[/COLOR]
[COLOR=#000000]Make sure it is not the graphics causing the freeze.[/COLOR]

Here is the answer to the above - I don't see it is any problem with the graphics...but not an expert on this for sure.

```

$ lspci -k|grep -iEA5 'vga|3d'
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT2 [Radeon HD 7970 GHz Edition]
    Kernel driver in use: radeon
    Kernel modules: radeon
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti HDMI Audio [Radeon HD 7870 XT / 7950/7970]
    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Tahiti XT HDMI Audio [Radeon HD 7970 Series]

~$ sudo lshw -C display
[sudo] password for peter-and-crazybear: 
  *-display               
       description: VGA compatible controller
       product: Tahiti XT [Radeon HD 7970/8970 OEM / R9 280X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:44 memory:e0000000-efffffff memory:fb480000-fb4bffff ioport:7e00(size=256) memory:c0000-dffff

```

He asked how I was able to turn off the system. I did NOT now of this method at all, so have never used it - testing if enabled I got a response not listed.
```

$ cat /proc/sys/kernel/sysrq
176

```

The ONLY way I was able to close a freeze was by pressing the computer shut down button for a **hard shut down**. Now, in the past few days, I've had NO freezing, but see one core always at 100% and occasionally the system load going much much too high without reason [and when it does, it does so _very_ quickly!]. When the cpu is being overworked, of course the temperatures rise - thank goodness I have an oversized and efficient cpu cooler...but think I need  to find the problem here! Core temps usually do not exceed 38C, but now have sometimes risen to 58C! CPU is intel i7-990X with 12 unlocked cores - with a LOT of capacity! Not only does one core always now run at 100%, but total cpu usage is a lot higher than before, even with the 4.4.8 - which was VERY very low just after installation. I just tried rebooting with one kernel lower and got the monitor problem again - which his strange and worrying! What is going on?! Thanks.

---

### Post by crazybear on 2017-06-27
Aha, <maybe> I found a 'solution' to this myself. I had been using the newest 4.8.0-56 and that one was running the cpu crazy and sometimes causing the fast rise in system load. On a hunch, I dropped down one to 4.8.0-54 and SO FAR [two days] everything has been smooth! Looking on the internet, I found no one else having that problem though with the [56]. I'll wait a few more days and if it holds stable, I'll consider it solved and hope newer kernels will not have the problem of the newest one. The difference between the two kernels is large in cpu usage, temps, system load and no freezes YET with this [54].

---

