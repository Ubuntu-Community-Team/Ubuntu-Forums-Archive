---
title: "Preformance degradation after upgrade to 15.04"
date: 2015-06-18
forum: Installation &amp; Upgrades
---

### Post by reg4c on 2015-06-18
Hello all, 

after upgrading to 15.04 my laptop has suffered a serious degradation in preformance. On 14.10 it ran extremely smoothly -- I really cannot complain about anything.

However, a week or so ago I upgraded to 15.04 and everything seems to have taken a preformance hit but I don't really know what to do. 

I've already disabled the Intel Power(something) that idles the CPU in favor of battery life but that didn't help much. 

**TL;DR: What are some ways that I can attempt to improve preformance after upgrading to 15.04?**

---

### Post by Bucky Ball on 2015-06-18
*Thread moved to **Installation & Upgrades**.*

Run these:

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```	

Reboot. Might not help but depending on when you downloaded the ISO, it might.

---

### Post by reg4c on 2015-06-18
I ran that again, just in case, but no packages need to be upgraded. 

Some more details:

I've added to /etc/modprobe.d/blacklist-powerclamp.conf as per some tutorial to disable the CPU throttling:
blacklist intel_powerclamp

uname -a
[HTML]3.19.0-20-generic #20-Ubuntu SMP Fri May 29 10:10:47 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
[/HTML]
lspci
[HTML]00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M] (rev ff)
01:00.1 Audio device: NVIDIA Corporation GK107 HDMI Audio Controller (rev ff)
07:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)
08:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)
09:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
09:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
[/HTML]

Would upgrading the kernel manually help perhaps?

---

### Post by jimmy-frydkaer on 2015-06-18
How much RAM does the device have?

I have an older MSI laptop that cannot run versions newer than Ubuntu GNOME 14.04 - Installing/upgrading to Ubuntu GNOME 14.10 kills of performance totally. It has a 1.4 GHz Celeron CPU and 2 gig of RAM. Running Ubuntu 14.04 with Unity is a nightmare in performance. 

Maybe 15.04 is simply to heavy on the hardware.

---

### Post by reg4c on 2015-06-18
Hiya, 

8GB of RAM and 2.6GHz i7 so I highly doubt it's the hardware.

---

### Post by LastDino on 2015-06-18
> **reg4c said:**
> Hiya, 

8GB of RAM and 2.6GHz i7 so I highly doubt it's the hardware.

Its really difficult to gauge what's wrong on such wide range problem. I would honestly start by trying to install fresh copy of 15.04 rather than trying to fix this.

However, before going that way, you could probably try finding where the conflict lies, like; is the performance low when there are particular applications running or it's slow in general? You can also try to see what process are actually hoarding all the resources to make it slow or try to shift between kernels??  Highly unlikely since 14.10 was running fine, but have you tried different drivers for your graphic card?
I'm just trying to throw stones in the water here, if there is nothing particular standing out to you, there is really no reason for it to be slow, especially on that kind of hardware.

---

### Post by v3.xx on 2015-06-18
What graphic driver are you running?

You are now running systemd instead of upstart.  This sounds unrelated, but easy enough to switch over and try.

[https://wiki.ubuntu.com/SystemdForUpstartUsers#Switching_init_systems](https://wiki.ubuntu.com/SystemdForUpstartUsers#Switching_init_systems)

And a curiosity
I see you run the 3.19 kernel; is that the standard 15.04 kernel?  Asking because thats the kernel I am running in 15.10.

---

### Post by reg4c on 2015-06-20
After some testing what slows it down the most is video: VLC runs for the first minute or so after which it starts slowing down everything, YouTube HTML5 player works however, but Flash video does not. 

As for the graphics drivers when I run lshw -c video it only outputs the Intel graphics and not the Nvidia one which leads me to believe that bumblebeed might not be working. 
I'm looking into potential solutions now.

---

### Post by akash14 on 2015-06-20
As You Told You Upgrade to 15.04, update all packages and reboot may be fix you.. 

Run:
> sudo apt-get update && sudo apt-get upgrade

---

### Post by ubfan1 on 2015-06-20
See if the Nvidia module is loaded:
lsmod |sort
If not, see if the Nvidia module even exists:
find /lib/modules -name "*nvidia*"
If the only nvidia module (a file ending in ".ko") is the framebuffer nvidiafb.ko
try to reinstall the nvidia driver in a terminal (assuming nvidia-current) and see what errors are produced:
sudo apt-get --reinstall install nvidia-current
Installing the Nvidia driver from the "additiona drivers" tab in software & updates sometimes has silent failures.

---

### Post by reg4c on 2015-07-06
This thread is probably dead but I had tried reinstalling the graphics drivers. 

I've also done some further testing and it's video that makes it slow mostly -- flash and VLC specifically. Now, I know Ubuntu and flash don't exactly get along but given Chrome's native extension it used to work fine. As for VLC this is a totally new thing, it just to worked splendidly before. I even upgraded to the newest one but the issue still persists.

---

