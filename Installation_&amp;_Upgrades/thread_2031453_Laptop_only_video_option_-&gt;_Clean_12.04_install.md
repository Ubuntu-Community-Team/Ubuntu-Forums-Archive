---
title: "Laptop only video option -&gt; Clean 12.04 install"
date: 2012-07-22
forum: Installation &amp; Upgrades
---

### Post by k7faq on 2012-07-22
Need some expert advise here please.

Burned up a clean download copy of Ubuntu 12.04 32bit to cd and installed. 500GB drive partitioned nearly 50/50 for Winbloze7 and Ubuntu 12.04.

Everything appears to have installed properly. In the System Settings | Additional Drivers the NVIDIA driver is referenced. HOWEVER and this is where I need help: In the System Settings | Display it shows only a "Laptop" display.  This is entirely inaccurate. The i7 system is a desktop with only one of two twin video cards installed. The driver details are below from having run a ```
lspci -v | less
```I need help correcting this video configuration please. I use multiple monitors heavily. Presently it will only acknowledge one of the monitors etc.

Thank you.

Video Driver Details:
```

03:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7900 GTX] (rev a1) (prog-if 00 [VGA controller])
        Subsystem: NVIDIA Corporation Device 0343
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at bc00 [size=128]
        [virtual] Expansion ROM at fbbe0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia_current_updates, nvidia_current, nouveau, nvidiafb

```

---

### Post by bogan on 2012-07-22
Hi!, **K7faq,**

That 'System Settings>Displays', and 'Details' Show a Desktop screen as 'Laptop', or failing to recognize the Graphics and its driver, are known bugs in 12.04 - ignore it.

In System Settings>Displays, there should be a 'Detect Displays' box, have you selected  that?

Alternatively run' Nvidia Xserver Setting's from Dash, or ```
gksu nvidia-settings 
```from a tty.

There are many Threads reporting current difficulties with dual monitors and nvidia cards and drivers.

How are monitors connected?
 DVI? HDMI? VGA? Adapters?

Do both each show OK singly?

PleasePost the output of:     ```
sudo apt-cache policy nvidia-current* 
cat /sys/module/nvidia/version
```Chao!,**bogan**.

---

### Post by k7faq on 2012-07-22
```
sudo apt-cache policy nvidia-current* 
[sudo] password for steven: 
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
        100 /var/lib/dpkg/status
nvidia-current-updates:
  Installed: 295.49-0ubuntu0.1
  Candidate: 295.49-0ubuntu0.1
  Version table:
 *** 295.49-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted i386 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
nvidia-current-updates-dev:
  Installed: (none)
  Candidate: 295.49-0ubuntu0.1
  Version table:
     295.49-0ubuntu0.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/restricted i386 Packages
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
nvidia-current-dev:
  Installed: (none)
  Candidate: 295.40-0ubuntu1
  Version table:
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted i386 Packages
nvidia-current-modaliases:
  Installed: (none)
  Candidate: (none)
  Version table:

```

```
cat /sys/module/nvidia/version
295.49
steven@i7:/etc/apache2$ 

```

---

### Post by k7faq on 2012-07-22
Hi Bogan,

Thanks for the response!  The X Server Config seemed to help quite a bit. Now I have two displays up. It is kind of odd, but not bad, that they are separate instances rather than a Primary / Secondary instance. (i.e. as if you were running two separate tty sessions).

Overall this is much better than where I was and I believe I need to look further at this X Server and the NVIDIA driver issue to better understand the problem.

Thanks again for your help!

Steven

---

