---
title: "Dell Vostro 1500 laptop seems to be locked at a low processor speed?"
date: 2017-02-02
forum: MINT
---

### Post by RallyDarkstrike on 2017-02-02
Hi all,

I've set up an older Dell Vostro 1500 laptop with 4G RAM for my mother that has a 1.6ghz dual-core Intel Core 2 processor and which is running Linux Mint 18 MATE 64-bit. It's not been bad so far, but lately it's seemed really slow even though she only really uses it for internet (Firefox or Chrome with maybe 4 tabs open at once) and card games like AisleRiot. I decided to see if I could use the CPU Frequency Scaling plugin for Panel to force the processor to a higher speed. This works fine on my personal laptop (running an AMD processor) and my  spare desktop PC, which runs a 3.0ghz Intel Core 2 processor. 

However, the scaling tool on her laptop will always stay locked at 800mhz no matter what I select (performance, ondemand, a specific clock speed, etc) where it works correctly on my other two machines. Is the slowness her laptop is experiencing due to the processor somehow staying locked at 800mhz rather than Speedstep kicking in to the full 1.6ghz where necessary?

I checked the BIOS and Speedstep is, indeed, enabled. Disabling it in the BIOS very oddly locks the processor at it's lowest possible speed (or so the BIOS says), so that is not a preferred option as that leaves me with the same problem...anybody have any ideas what is going on and how to solve it? More info can be provided as needed as I have remote access to it from here!

AFAIK, Mint uses the CPU Scaling drivers/etc as Ubuntu does (as it is  Ubuntu-based), so hoping somebody here or on the Mint forums can help!

Cheers and thanks! :)

---

### Post by DuckHook on 2017-02-03
*Thread moved to **MINT** as the more appropriate forum.*

Mint does many things differently from Ubuntu, especially in the Video subsystem. Please don't assume that because it is "Ubuntu-based" that the two are simply interchangeable.

I do not run Mint. Combined with what has already been stated above, this should serve as fair warning for the advice that follows:

Your mother's laptop is not underpowered. Based on your description, it has ample specs to run the OS and apps you've mentioned and it is counterproductive to juice the HW. Though common practice in the gaming community, this just causes grief in general computing, giving rise to erratic behaviour, unreproducible errors, crashes and just wasted time and general frustration. As an old geezer who sympathizes with your mother, please don't put her through that.

Googling shows that there are a wide range of Vostro 1500 builds out there. Not that we doubt you, but just to double-check, please post output of:```
sudo lshw -c system -c processor -c display -c memory -sanitize
``````
free -hw
``````
cat /etc/default/grub
``````
lspci
```
Please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Since it's obvious you've already added stuff and changed things, please provide complete answers to the following:

[LIST=1]
[*]Have you modified the DE with things like compiz, 3D desktop effects, rotating cubes, etc?
[*]Have you added PPAs? If so, what are they?
[*]Provide a complete list of any other changes you've made that depart from a default install.
[/LIST]
This next bit requires you to act with within a given time. The easiest way to see what processes are eating up your CPU cycles is with the simple command:```
top
```However, *top* is an app that constantly refreshes so it's very difficult to copy and paste its output if it is run without modifiers. Therefore:

[LIST=1]
[*]Run a typical desktop session that your mother would run, including opening up all the apps and browser tabs that cause the slowdown.
[*]Open a terminal and run *top* with the following flags:```
top -i -d 10
```This will filter for only those processes taking up CPU cycles and slow *top* down to 10 seconds between refreshes. If this is still too fast to select and copy, increase number to 15 or 20.
[*]Let *top* run in this manner for two or three cycles, then, using your mouse, select all output of a cycle, right click, and copy. Post that output.
[/LIST]
You may also wish to have your mother try out a LiveUSB session of Ubuntu-mate, Lubuntu or Xubuntu. I'm not trying to "convert" you from MINT. But I have no experience with it, so can only recommend what I know will work, and can help you to fix. If your mother's computer is already slow, do not use any of the Ubuntu/Gnome/Kubuntu flavours. These are all resource-heavy and even slower than MATE.

But we are getting a little ahead of ourselves. First, let's hear your answers to what's already been asked.

---

### Post by RallyDarkstrike on 2017-02-03
Hi,

Thanks for the reply! I am not merely thinking it is slow from looking at the specs. I have run MINT, Lubuntu and some other Linux distros on worse hardware and it was more then fine for the purpose (I have a Intel Core i7 desktop running Win10, but my personal laptop was an old Dell Inspiron 6000 with Pentium 4 3ghz up until a few months ago!)

The issue with her is that the processor is NOT running at full speed, even under heavy load - instead, it is staying locked at 800mhz rather than bumping up to the factory max 1.6ghz it should be running at when needed on demand. THAT is what is making it slow, not just 'appear' slow. I never intended to Overclock it at all - 1.6ghz is the stock rating on the processor. I was simply trying to use the frequency scaling tool to get the processor to even run at stock speed.

I am headed to work so don't have time for all the commands right now until I get home (will reply in  hours or so), but here is the output of the first command you listed - I can also tell you that I don't recall having added any extra PPAs to her computer that I can remember - I did uninstall some of the original choices Mint had made for software, but the rest I re-added as replacements were from the repositories. Kodi is, I believe, the only program and other set of PPAs I have added (and she almost never uses it anyway):
```
computer                  
    description: Portable Computer
    product: Vostro 1500
    vendor: Dell Inc.
    serial: [REMOVED]
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: boot=normal chassis=portable uuid=[REMOVED]
  *-firmware
       description: BIOS
       vendor: Dell Inc.
       physical id: 0
       version: A00
       date: 06/14/2007
       size: 64KiB
       capacity: 960KiB
       capabilities: isa pci pcmcia pnp upgrade shadowing cdboot bootselect int13floppy720 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp smartbattery biosbootspecification netboot
  *-cpu
       description: CPU
       product: Intel(R) Core(TM)2 Duo CPU     T5470  @ 1.60GHz
       vendor: Intel Corp.
       physical id: 400
       bus info: cpu@0
       slot: Microprocessor
       size: 800MHz
       capacity: 1601MHz
       width: 64 bits
       clock: 200MHz
       capabilities: x86-64 fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm ida cpufreq
       configuration: cores=2 enabledcores=2 threads=2
     *-cache:0
          description: L1 cache
          physical id: 700
          size: 32KiB
          capacity: 32KiB
          capabilities: internal write-back data
          configuration: level=1
     *-cache:1
          description: L2 cache
          physical id: 701
          size: 2MiB
          capacity: 2MiB
          clock: 66MHz (15.0ns)
          capabilities: pipeline-burst internal varies unified
          configuration: level=2
  *-memory
       description: System Memory
       physical id: 1000
       slot: System board or motherboard
       size: 4GiB
     *-bank:0
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: 16HTF25664HY-800G1
          vendor: Micron Technology
          physical id: 0
          serial: [REMOVED]
          slot: DIMM_A
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM DDR Synchronous 667 MHz (1.5 ns)
          product: 16HTF25664HZ-800H1
          vendor: Micron Technology
          physical id: 1
          serial: [REMOVED]
          slot: DIMM_B
          size: 2GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
  *-display:0
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:fea00000-feafffff memory:e0000000-efffffff ioport:eff8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:feb00000-febfffff

```

---

### Post by RallyDarkstrike on 2017-02-03
Sorry for the double-post - at work now, but with a few minutes to kill, so adding to mom's system's info.

I, of course can't run any of those commands until I get home, but I can also mention that I am pretty sure it is running Metacity rather than Compiz. Mint comes with both installed and the ability to switch between them, but I always have it set to Metacity on her machine for the sake of performance as she doesn't need any fancy effects.

As for changes from a default install - not sure I can remember them all as it was awhile ago. Not that I changed a lot at all, mind you, just that my memory is fuzzy. I know I removed the default Text Editor app and installed GEdit. I also removed some of the default apps I know she wouldn't be using (Thunderbird Mail, Pidgin, some of the audio/video player stuff and some others). I did install VLC for video, Audacity for music, Skype (from the *.deb on Skype's website), and some other programs in the repositories. Essentially, I made no SYSTEM changes that I am aware of in relation to the install (drivers, GRUB, window / file managers, etc) - that aspect of the system should be running as it was autodetected when I first installed Mint.

Will reply again when I get home and have a chance to run the other commands for you!

---

### Post by RallyDarkstrike on 2017-02-03
OK, home now - results of the 'free -hw' command:
```
free -hw
              total        used        free      shared     buffers       cache   available
Mem:           3.8G        1.5G        848M        114M        224M        1.3G        2.0G
Swap:          2.0G          0B        2.0G

```

Results of the 'cat /etc/default/grub' command:
```
cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

Results of lspci:
```
lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

Results of the top command:
```
top - 15:58:52 up 16:06,  1 user,  load average: 1.26, 1.44, 0.93
Tasks: 191 total,   1 running, 189 sleeping,   0 stopped,   1 zombie
%Cpu(s):  5.1 us,  4.5 sy,  0.0 ni, 90.1 id,  0.3 wa,  0.0 hi,  0.1 si,  0.0 st
KiB Mem :  4036984 total,   968620 free,  1423560 used,  1644804 buff/cache
KiB Swap:  2085884 total,  2085884 free,        0 used.  2194696 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND     
 1395 root      20   0  429092  94736  57492 S   9.1  2.3  30:52.70 Xorg        
11455 donna     20   0  658836  67168  56748 S   3.5  1.7   0:05.05 mate-termi+ 
11440 donna     20   0  791004 115228 100648 S   3.3  2.9   1:15.72 remmina     
 4898 donna     20   0 2522612 981.6m 148684 S   3.1 24.9 338:17.64 firefox     
 1770 donna      9 -11  435284  12960   9828 S   2.5  0.3  11:49.13 pulseaudio  
 1827 donna     20   0  677744 190688  89620 S   2.4  4.7  17:47.22 skype       
 1720 donna     20   0  642292  25616  20560 S   0.5  0.6   3:37.47 marco       
11948 root      20   0   93268   7656   6528 S   0.4  0.2   0:00.04 cupsd       
   22 root      39  19       0      0      0 S   0.2  0.0   0:46.67 khugepaged  
 5635 root      20   0       0      0      0 S   0.2  0.0   0:18.58 kworker/u4+ 
11414 root      20   0       0      0      0 S   0.2  0.0   0:03.14 kworker/0:2 
11482 root      20   0       0      0      0 S   0.2  0.0   0:02.00 kworker/1:1 
11946 donna     20   0   41800   3780   3168 R   0.2  0.1   0:00.15 top         
11950 lp        20   0   81244   5720   4956 S   0.2  0.1   0:00.02 dbus        
    1 root      20   0  119936   6144   4032 S   0.1  0.2   0:07.44 systemd     
  744 message+  20   0   44116   5008   3580 S   0.1  0.1   0:12.76 dbus-daemon 
  794 root      20   0  449180  16368  13664 S   0.1  0.4   0:19.61 NetworkMan+
```

As a note - Remmina and Terminal aren't always open on mom's laptop, of course, but were only open from me issuing the commands requested by you and from me remoting into another PC on our network for a moment.

---

### Post by DuckHook on 2017-02-03
What app (please provide exact package name) are you using when you try to set cpu frequency?

[list=1]
[*]Not all frequency applets report properly. Check to see if her CPU is indeed being throttled:```
watch grep \"cpu MHz\" /proc/cpuinfo
```To quit this process, use <Ctrl>+<c>. Make sure you run this in the conditions that slow down the computer (i.e. with all problematic apps running, etc). Try to stress the system by playing an HD video or tux racer or something. If the CPUs break 800 MHz, then the problem is not throttling.
[*]Sometimes, the bottleneck is actually video issues. Check for a common problem with ```
glxinfo | grep "renderer string"
```Post output. If it returns "llvmpipe", then her system is using software rendering which would account for her slowdown. The solution in that case is to get get video working properly and has nothing to do with the CPU.
[*]Post output of the following:```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
``````
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
[/list]
**WARNING**

What follows is both distro-dependant and version-dependant and applicable to 'buntu Xenial. I have no idea if it works on MINT. As already mentioned, MINT does things differently. It could end up breaking your mother's system including HW damage such as burning out the CPU, so the two of you must undertand your risks and proceed at your (and her) own risk. Risk mitigation starts with having all of her data backed up.

If the first set of procedures show that the CPUs are indeed being throttled, then your can try the following:

[LIST=1]
[*]Your mother's computer is too old to use intel_pstate and probably uses the older acpi-cpufreq governor. Check with:```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_driver
```
[*]If above returns: "acpi-cpufreq:, then for now, let's first try a least harm approach:```
sudo echo performance | tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor >/dev/null && sudo echo performance | tee /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor >/dev/null
```
[*]Run through the whole earlier stress test using the *watch&#8230;* command.
[*]If the *performance* setting now allows higher CPU frequencies, install the *cpufrequtils* tool:```
apt install cpufrequtils
```
[*]To make above settings permanent on reboot:```
sudo cpufreq-set -g performance
```
[*]Reboot, then check with:```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
[/LIST]
If still that doesn't work or still throttled, we can try other things, but try the above for now.

---

### Post by RallyDarkstrike on 2017-02-03
I use the MATE Panel CPU Frequency Scaling Monitor applet to change the processor settings - the same I use on all of my machines as it works perfectly on them. No idea the package name as it came with the default MINT install...?

For your first 'grep' command - the output didn't jump above 800mhz once.

As for your second command - the laptop is using its onboard Intel graphics card:
```
OpenGL renderer string: Mesa DRI Intel(R) 965GM
```

For your first 'cat' command, the output was:
```
conservative ondemand userspace powersave performance
```

For your second 'cat' command:
```
ondemand
``` [COLOR=#ff0000](EDIT - Realized I accidentally pasted your command again here when I first posted this, sorry for the confusion - fixed now!)[/COLOR]

As for your third 'cat' command, yes, the output was:
```
acpi-cpufreq
```

Your 'least harm' approach command fails with:
```
tee: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Permission denied

```

cpufrequtils is already installed AFAIK...?

---

### Post by DuckHook on 2017-02-03
> **RallyDarkstrike said:**
> I use the MATE Panel CPU Frequency Scaling Monitor applet to change the processor settings - the same I use on all of my machines as it works perfectly on them. No idea the package name as it came with the default MINT install...?
Then can't help you there. Don't use either MINT or MATE.
> Your 'least harm' approach command fails&#8230;
Then let's try, first get temporary root shell:```
sudo -i
```&#8230;then *without* sudo:```
echo performance | tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor >/dev/null && echo performance | tee /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor >/dev/null
``````
exit
```

---

### Post by RallyDarkstrike on 2017-02-03
The commands went through this time using your above instruction - that  being said, no change. I tried streaming an HD video on Youtube and it  was incredibly laggy with the grep command showing in a Terminal window  that the CPU stayed locked at 800mhz the entire time :(

---

### Post by RallyDarkstrike on 2017-02-03
Sorry, once again for the double post, but....you're not going to believe this, but I've solved the issue!

It  was the battery..........during one of my Google searches, I came  across a short post on another forum with almost no replies from 2011. A  user mentioned he couldn't get his older HP laptop to go beyond a  certain speed and one of his two replies mentioned to check the power  cable and battery as sometimes certain brands have their BIOS lock the  processor at a lower speed when the power cable isn't charging correctly  or the battery is below a certain charge.

Sure enough, I've  known the battery in that laptop has been shot for a long time (ever  since we were given it as a used machine for free about a year ago) as  it will only last a a very short time on battery. Mom only ever uses it  plugged in on the same desk anyway, so none of us ever thought anything  of it. Turns out the battery has been slowly losing what little ability  to hold a charge it has left in the last few months - as a result, it  must've just dropped below the aforementioned  'lock-the-processor-at-a-lower-speed' threshold in the last few weeks.

I  thought, what the hell...shut it down, removed the battery, plugged it  in on A/C only, booted it back up and voila! Low and behold, scaling is  working perfectly on demand again! [IMG]https://forums.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG]

Thanks  for all the attempted help though sir, you are a scholar and a  gentleman! Hope this helps another user somewhere down the road!!!

---

### Post by DuckHook on 2017-02-03
It's kind of you to thank me, but I do feel a little bit the blind idiot. As an old HW hound, I've heard of the this effect before. You would think that I would have the presence of mind to check it out. But noooo&#8230; just stubbornly beat my head against the wall.

My hat is off to you, though. That's a fine piece of detective work to chase down such an obscure cause.

You may wish to back out all of those superfluous apps that we tried installing. It's best not to leave them hanging around if not needed.

Good Luck and Happy&#8230; well&#8230; in your case, it would be Happy Linux-ing!

---

### Post by RallyDarkstrike on 2017-02-03
Thanks! I'm just lucky I stumbled upon it! I may have a modern Windows gaming machine, but I hate seeing perfectly good hardware go to waste, and that laptop is more than ample for what mom needs....I didn't want to have to give up on it, so I'm just lucky I sorted it out! I'll just leave the battery out for now and all should be well!

No worries about missing the solution...it's a pretty obscure one to remember, let alone find info on!

There will be many more happy years of Linuxing, hopefully! Aside from mom's laptop running Mint 18.1 MATE - my laptop, and my spare desktop both run Mint 18.1 MATE as well, and I have a few test distros in VirtualMachines on my Windows desktop for fun! :)

---

