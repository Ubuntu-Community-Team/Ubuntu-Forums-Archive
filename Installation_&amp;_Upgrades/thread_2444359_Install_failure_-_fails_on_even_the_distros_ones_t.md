---
title: "Install failure - fails on even the distros ones that previously worked :-("
date: 2020-05-29
forum: Installation &amp; Upgrades
---

### Post by Sour Mash on 2020-05-29
This is an old set of hardware but it ran v19 OK and was working fine. On a whim I upgraded to v20.04 and upon reboot all I got was a black screen with a blinking cursor. No inputs worked, system was unresponsive. 

After a bit of messing about with the Boot Repair Disc - which didn't seem to report anything suspicious, nor was it able to repair anything I thought I'd just go back to v19 (there's nothing on the machine that matters, it's all backed up on another physical disc in the case) so I pulled out the install discs I had burned and couldn't find v19 - no problems there was v17.10. 

I ran it from the disc, no issue, worked fine. I installed it went well and rebooted to ... a black screen with a blinking cursor! 

I then went back to the next oldest and even found an old xubuntu v9 that I remember was the first one I tried on this hardware - same result - runs off the cd, won't run when installed.

Damn, OK I decided to run Kill Disc on the hd and clean it all out, ran that last night and started again this morning with v17.10 - again, ran from the disc OK, did the install and - you guessed it, same black screen. 

Now before I physically disconnect the back-up HD (grasping at straws here) and try again, is there anything else I should be doing to get back to a working Ubuntu? As far as I can tell all the hardware, although old, was working fine and is OK now - I could try another HD I suppose but I can't figure out what would have happened to the HD to make it so pedantic.

It's the lack of any useful feedback that's worrying me - where do you start when all you have a black screen?

Anyway, thanks in anticipation - I'm very much an enthusiastic self taught amateur here, so may be missing some fundamentals!

---

### Post by CatKiller on 2020-05-29
> **Sour Mash said:**
> all I got was a black screen with a blinking cursor. 

Without any details of your hardware it's hard to say, but this is the symptom that some people experience on Nvidia hardware when the nouveau driver is unable to correctly set the screen resolution. Using *nomodeset* as a kernel parameter tells it not to try, which gives you a low-res screen until you can install the proprietary driver.

---

### Post by Sour Mash on 2020-05-29
Thanks for the reply, I'm no expert here but wouldn't that same problem shjo up when running from a live disc? 
It didn't happen when the system was running with previous version but I'll try anything - how do I get round it when I can't boot?

---

### Post by oldfred on 2020-05-29
Post what video card/chip you have.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Only use current versions of Ubuntu, your 17.10 is EoL.
Current Releases & Flavors
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Sour Mash on 2020-05-29
Thanks,
How do I determine the hardware, bearing in mind all I have is an unresponsive black screen :-(
I'll get a live disc version running but where do I go to establish the hardware?

---

### Post by Sour Mash on 2020-05-29
OK, I'm now on the machine with a live disc version, have run lspci and got this

00:00.0 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: NVIDIA Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: NVIDIA Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: NVIDIA Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB controller: NVIDIA Corporation MCP61 USB 1.1 Controller (rev a3)
00:02.1 USB controller: NVIDIA Corporation MCP61 USB 2.0 Controller (rev a3)
00:04.0 PCI bridge: NVIDIA Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: NVIDIA Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: NVIDIA Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: NVIDIA Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: NVIDIA Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: NVIDIA Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
01:0a.0 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
01:0a.1 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
01:0a.2 USB controller: ULi Electronics Inc. USB 1.1 Controller (rev 03)
01:0a.3 USB controller: ULi Electronics Inc. USB 2.0 Controller (rev 01)
02:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV710 [Radeon HD 4350/4550]
02:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series]

---

### Post by oldfred on 2020-05-29
How old is this system?
How much RAM since very old?

Looks like a MCP61 is equivalent to the GeForce 6150.

If so, it needs the 304.xx driver which is not supported in newest Ubuntu.
[https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/](https://www.nvidia.com/en-us/drivers/unix/legacy-gpu/)

You may need 16.04.
[https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787/32](https://ubuntu-mate.community/t/nvidia-304-driver-install-in-18-04/16787/32)

---

### Post by Sour Mash on 2020-07-02
Well to update things a little, I did manage to get 20.04 running but it kept crashing, a weird sort of power failure instant off crash, no clues. I left it run overnight on a live CD and it was fine in the morning but it simply would not run for more than a few mins if trying to do anything with the system. I decided to wipe and start again but I didn't have any blank DVDs to burn so whilst waiting for some to come in the post I persevered and found some other posts that suggested the kernel was corrupt. I sort of gave up at that point and waited for the DVDs to arrive, when I came to try again, 20.04 would run OK from the newly burned live CD but reported no HDD when I tried to install. Seems the constant off and on wrecked my HDD. 
Today I'm back at it, having got 20.04 to install and run dual boot on a laptop, but every HDD I've tried in the original system is either appearing dead or won't mount or is telling me I don't have permission to view the drive! Grr - I'll start a new thread on disc salvage - I've got 5 big old SATA drives here, there's gotta be a good one amongst them! Also, one has my digital music collection on it!
Why is upgrading to 20.04 so hard? I've tried it about 5 times on 2 different machines and only got one running (don't get me wrong, it's quite goo and appears worth some pain, but this is seriously bad!).
Anyway, this thread is done.

---

