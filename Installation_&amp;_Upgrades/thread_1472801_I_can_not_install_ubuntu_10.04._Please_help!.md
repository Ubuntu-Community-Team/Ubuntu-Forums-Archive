---
title: "I can not install ubuntu 10.04. Please help!"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by trfillos on 2010-05-04
Hello,
I would like to install ubuntu 10.04 LTS on my computer. The system is:

 - Precessor: I7 980X
 - Mobo: ASUS P6X58D-Premium
 - Ram: 12 GB DDR3
 - VGA: XFX ATI HD5970BE
 - HD: ocz Z-Drive m84 (512GB) 78GB unallocated space for linux.
 - OS: win XP pro 32 & win 7 pro 64
 
I have try to install ubuntu 10.04 CD (32 and 64 bit versions) and the amd64 DVD. All the above fail with exactly the same behavior.

During installation after the ubuntu logo with the animating dots below both monitors are entering in stand-by mode. After that I can not see anything...

With the previous release of ubuntu (9.10) I had no problem to install...
Is there any solution? Any updated iso image? Please help!

Thank you very much for your time.

Best regards,
Triantafillos

---

### Post by divergex on 2010-05-04
I have had success by holding down the Shift key during boot until a Grub menu appears. From there, select the first entry and press "e" to get an editor, then go to the bottom and add on its own line:

nomodeset

That has enabled me to boot on two different PCs. I think (and someone please correct me if I'm wrong) the incorrect resolution/refresh rate is being chosen on initial boot after install.

---

### Post by trfillos on 2010-05-04
Unfortunately no luck with the nomodeset option.

I selected this option from the menu by pressing F6 and start the live version but no luck. I had the same as above.

---

### Post by trfillos on 2010-05-05
Anyone? Where are the experts?

---

### Post by happ on 2010-05-05
Try to change your disks configuration in BIOS, from AHCI o IDE. After installation change it back. It worked to me. 

Another solution is clean install Ubuntu 9.10, and than upgrade to 10.04.

It seams that version of Ubuntu does not like combination of x58 Intel chipset, ATI graphic and solid state drives in AHCI mode.

---

### Post by dino99 on 2010-05-05
instead of booting with "nomodeset", try with radeon.modeset=0

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560243](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560243)

---

### Post by trfillos on 2010-05-05
> **dino99 said:**
> instead of booting with "nomodeset", try with radeon.modeset=0

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560243](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560243)

I will test it as soon as I return to my home.

Thank you.

---

### Post by ff1-ff1 on 2010-05-05
despite all advises presented here i have 1 question:
did you try to start system from cd in live mode? From your description i may conclude that you tried to install system only.Try to boot in live mode to desktop and after that (from icon INSTALL presented on desktop) try to install system.
By the way -you wrote that earlier you installed former ubuntu version without problem.My question- did you possessed in these time same graphic card like this now (top ati)?

---

### Post by trfillos on 2010-05-05
> **ff1-ff1 said:**
> despite all advises presented here i have 1 question:
did you try to start system from cd in live mode? From your description i may conclude that you tried to install system only.Try to boot in live mode to desktop and after that (from icon INSTALL presented on desktop) try to install system.
By the way -you wrote that earlier you installed former ubuntu version without problem.My question- did you possessed in these time same graphic card like this now (top ati)?

Yes I tried to start in live mode. No difference.
I had 9.10 on the same machine. No problem except an annoying window at the lower right corner of both monitors saying something like "AMD hardware not supported" or something like that.

---

### Post by trfillos on 2010-05-05
> **dino99 said:**
> instead of booting with "nomodeset", try with radeon.modeset=0

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560243](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/560243)

No luck again... All the same

---

### Post by jm.mico on 2010-05-05
Try in the grub boot mode, "noapic" boot option. Worked yesteday for a colleage which had karmic and with lucid could not boot (or took 10-15min).

Give it a try.

Jm.

---

### Post by b4nn1k on 2010-05-05
I am having the same issue on trying a dual boot install with win7 where my monitor shuts off after a couple mins of the ubuntu screen. Only common thing i see between the 2 computer is an ati video card i have the ati5770. Any other suggestions would be great.

---

### Post by trfillos on 2010-05-06
> **b4nn1k said:**
> I am having the same issue on trying a dual boot install with win7 where my monitor shuts off after a couple mins of the ubuntu screen. Only common thing i see between the 2 computer is an ati video card i have the ati5770. Any other suggestions would be great.

mine is 5970...

I have tried the PCLinux OS 2010.1 live cd and works fine. Unfortunately it is 32bits and I would like to have a 64bits linux on my machine. So I will wait a couple of weeks for ubuntu to fix it and then I will see what to do (maybe f13).

---

### Post by OrestesEreinion on 2010-05-06
I am having the same issue. If it will help, I have a HP dv1000 which is a Pentium M @ 1.5 GHz and an intel 855 grfx chip IIRC. Furthermore, I tried using Linux Mint 9 RC(Lucid based) and when I booted in compatibility mode I was able to get to the desktop. Unfortunately I don't seem to be able to get into compatibility mode by hitting escape using the Lucid LiveCD.Is there some other way to do this now?.

---

### Post by Sam Weesie on 2010-05-06
I'm also having the same problem. The VM hangs in the same way on the same place.

Configuration:
Gigabyte GA-EX58-UD5 / i920 / 6 GB
ASUS ENGTS250 video
Host Windows 7 x64
VM Workstation 7.01

I have the same problem installing 10.04; both the 32 and 64 bit versions. I tried burning an CD and installing from it but same problem. Ubutu 9.10 installs/runs with no problem.
The 10.04 server version also installs with no errors.

Below are the last lines of the VM install log.
Maybe this gives somebody a clue.
I assumed the problem was with VM but now I'm not so sure anymore.
--------------------------------------------------
May 03 23:03:17.620: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
May 03 23:03:17.637: vcpu-0| VIDE: Truncating 0x46 from 65530 bytes to 32768
May 03 23:03:17.693: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
May 03 23:03:26.165: vmx| GuestRpcSendTimedOut: message to toolbox-dnd timed out.
May 03 23:03:31.056: vcpu-0| VIDE: Truncating 0x46 from 65530 bytes to 32768
May 03 23:03:31.056: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
May 03 23:03:31.414: vcpu-0| VIDE: Truncating 0x46 from 65530 bytes to 32768
May 03 23:03:31.416: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
May 03 23:03:32.857: vcpu-0| Keyboard: invalid mouse sample rate 102 Hz, using 100 instead
May 03 23:03:33.929: vcpu-0| CDROM: Emulate GET CONFIGURATION RT 0 start feature 0
May 03 23:03:34.384: vcpu-0| VMMouse: CMD Read ID
May 03 23:03:34.384: vcpu-0| VMMouse: CMD Disable
May 03 23:03:34.384: vcpu-0| VMMouse: Disabling VMMouse mode
May 03 23:03:34.392: vcpu-0| VMMouse: CMD Read ID
May 03 23:03:34.392: vcpu-0| VMMouse: CMD Disable
May 03 23:03:34.392: vcpu-0| VMMouse: Disabling VMMouse mode
May 03 23:03:35.950: vcpu-0| SCSI DEVICE (scsi0:0): No transfer information for *UNKNOWN (0x85)* (0x85)
May 03 23:03:35.950: vcpu-0| SCSI (scsi0:0): SCSI-3 16-byte CDB format not supported (LUN 0).
May 03 23:03:35.951: vcpu-0| SCSI DEVICE (scsi0:0): No transfer information for *UNKNOWN (0x85)* (0x85)
May 03 23:03:35.951: vcpu-0| SCSI (scsi0:0): SCSI-3 16-byte CDB format not supported (LUN 0).
May 03 23:03:35.951: vcpu-0| SCSI DEVICE (scsi0:0): No transfer information for *UNKNOWN (0x85)* (0x85)
May 03 23:03:35.951: vcpu-0| SCSI (scsi0:0): SCSI-3 16-byte CDB format not supported (LUN 0).
May 03 23:03:39.499: vcpu-0| SOUND 074.727635 PCISoundWin32 mixerGetLineInfo error 1024
May 03 23:03:48.852: mks| SVGA: Sync FIFO with SVGA disabled
May 03 23:03:48.861: mks| HostOps hideCursor before defineCursor!
May 03 23:03:48.873: vcpu-0| Guest OS = 0x5008
May 03 23:03:48.873: mks| Guest display topology changed: numDisplays 1
May 03 23:03:48.899: mks| HostOps hideCursor before defineCursor!
May 03 23:03:57.236: vcpu-0| VMMouse: CMD Read ID
May 03 23:03:57.237: vcpu-0| VMMouse: CMD Disable
May 03 23:03:57.237: vcpu-0| VMMouse: Disabling VMMouse mode
May 03 23:03:57.237: vcpu-0| VMMouse: CMD Read ID
May 03 23:04:32.646: vcpu-0| Setting thread 42 stack size to 1048576
----------------------

---

### Post by ronparent on 2010-05-06
Just some general comments since advice so far hasn't gotten you anywhere.

Fix on your boot problems by getting your system to boot the live cd first. Once you find out and apply the fix for what is blocking the loading on your system you can proceed to the install.

Get to the menu by hitting any key when the initial splash screen appears on booting the CD. Then hit f6 after the language is selected to bring up the boot options to eneble or disable. Whether or not you select an option to modify, hit end to place the cursor at the end of the boot line, navigate back to the end of splash and backspace to delete splash and quiet. Booting with quiet splash deleted will allow the boot scripts to scroll the screen during boot. Based on what you have described, where it stops will give you (and us if you report it here) a clue to what is stooping your system. I general, the sooner the stop, the earlier the boot option in the list is liklier to address it.

Deleting the splash option itself solves some boot problems. But you may need to systematically try all of the f6 options until you find one or a combination of two or more that when applied will allow you system to boot. In my case I found this a time consuming lengthy process with the live CD so I resorted to tempoaritly installing to a spare 80gb IDE on another machine. I then pluged that drive into my current machine, set it as boot, and, then repeatedly booted it until the right combination was found. In case you have more than one monitor, I did have to unplug one to be able to boot - you can replug it only after installing the restricted ATI drivers.

Finally, if anything tried works, I would expect you might have a problem installing your permanent system to the ssd unless you have already aligned. In my case since I wasn't installing to it, It wasn't a problem, but, gparted showed it a an anallocated drive even though win7 was installed on it.

Good luck. Post if you find your solution.

---

### Post by zhi hao on 2010-05-14
> **trfillos said:**
> No luck again... All the same

Same here... I'm using a much lower end LG E300 laptop with T5750 Core 2 duo and X1250 integrated. I can install but i then my screen goes blank. I tried using nomodest after splash but still no luck. I installed 10.04 using Wubi...
Can anyone pls help? Thanks in advance...

---

### Post by bestmann on 2010-05-14
I tried to follow all instructions without any luck. I do not understand what happens why can not install it. [COLOR=#000000]See I'm not alone with this problem.[/COLOR]

---

### Post by joaojotta on 2010-06-07
> **happ said:**
> Another solution is clean install Ubuntu 9.10, and than upgrade to 10.04.
That didn't work with me. It installs but, when booting, the same problem happens.

I'll try the other options when I get home.

---

### Post by davidkk on 2011-07-19
I can notice I'm not the only one with this problem.I can't install either.I I wonder where is the problem.

---

