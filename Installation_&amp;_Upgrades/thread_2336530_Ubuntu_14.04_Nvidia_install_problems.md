---
title: "Ubuntu 14.04 Nvidia install problems"
date: 2016-09-09
forum: Installation &amp; Upgrades
---

### Post by namesnonames on 2016-09-09
So I've been trying to get Ubuntu 14.04 to recognize my Nvidia card and use it. My end goal is to use the cuda capabilities for tensorflow and other ML libs and the like. First issue would be getting Nvidia to play nice though so I tried following previous forum posts for 2 days now, nothing has really worked, so I am making this post. If I missed a post somewhere that you believe will be helpful please link. This feels like an awkward post because there are so many other posts about the same type of thing, but I have been trying and nothing has been working, as such in this post I will be trying to balance between keeping the information to just what I think is necessary, while also highlighting previous approaches that I have taken.

**System Setup:**

[LIST]
[*]Machine: Dell Inspiron 15 7000 series 
[*]Dual boot: Windows 8.1 / Ubuntu 14.04 
[*]Processor: i7-4510U CPU @ 2.00GHz × 4 
[*]RAM: 16GB 
[*]Integrated Graphics: Intel Haswell Mobile 
[*]Discrete Graphics Card: Nvidia 750M 
[/LIST]
 
**Current State:**
After chasing different methods of installation and encountering different issues I've decided to re-install Ubuntu 14.04 (again) but this time post all information I have found to be relevant based on other similar posts. Below is a list of everything I have done since the install.

- The Software Updater program wanted to install updates so I let it do that.
- I ran a few commands to get what I have understood to be relevant. ( see output below )

```

$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    Subsystem: Dell Device 05fa
    Kernel driver in use: i915
--
04:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
    Subsystem: Dell Device 05fa
    Kernel driver in use: nouveau


$ sudo dpkg -l | grep -i nvidia


$ sudo lshw -C display
  *-display
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:e3000000-e33fffff memory:c0000000-cfffffff ioport:5000(size=64)
  *-display
       description: 3D controller
       product: GK107M [GeForce GT 750M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nouveau latency=0
       resources: irq:49 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:3000(size=128)

```
Notice how the *dpkg -l doesn't show anything but then my Additional Drivers tab does.I'm not sure if that's normal or if that is indicative of an issue.*

Here is what the Additional Drivers Menu looked like directly after first login on a clean install.
[http://i.imgur.com/PaFeQFw.png](http://i.imgur.com/PaFeQFw.png)
- Because the dpkg command wasn't showing anything I decided to try installing them using these commands in tty1 (using these based on [http://goo.gl/M7ZRxg](http://goo.gl/M7ZRxg) ):
```

sudo service lightdm stop
sudo apt-get install nvidia-current nvidia-settings
sudo nvidia-xconfig
sudo reboot

```

- After the reboot I tried to see if Ubuntu was using the nvidia card based on [http://goo.gl/WovfFu](http://goo.gl/WovfFu):
```

$ nvidia-settings

** (nvidia-settings:2426): WARNING **: PRIME: Failed to execute child process "/usr/bin/prime-supported" (No such file or directory)
** Message: PRIME: is it supported? no

```
Some warnings seen above are displayed, but the window launches. It doesn't look right though, as seen in the image below it only has the two items in the list on the left.
There are no profiles or rules in "Application Profiles". In a previous installation I had a third option in the list that let me switch between Intel and Nvidia for the graphics device but that never worked for me, giving various errors.
If that information seems relevant let me know and I can post it.
[http://i.imgur.com/r3Xc0wt.png](http://i.imgur.com/r3Xc0wt.png)


Since having ran the nvidia installation above the output from the same set of commands as earlier is as follows:
```

$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    Subsystem: Dell Device 05fa
    Kernel driver in use: i915
--
04:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
    Subsystem: Dell Device 05fa
    Kernel driver in use: nvidia

$ sudo dpkg -l | grep -i nvidia
ii  libcuda1-304                                          304.131-0ubuntu0.14.04.2                            amd64        NVIDIA CUDA runtime library
ii  nvidia-304                                            304.131-0ubuntu0.14.04.2                            amd64        NVIDIA legacy binary driver - version 304.131
ii  nvidia-current                                        304.131-0ubuntu0.14.04.2                            amd64        Transitional package for nvidia-current
ii  nvidia-libopencl1-304                                 304.131-0ubuntu0.14.04.2                            amd64        NVIDIA OpenCL Driver and ICD Loader library
ii  nvidia-opencl-icd-304                                 304.131-0ubuntu0.14.04.2                            amd64        NVIDIA OpenCL ICD
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver

$ sudo lshw -C display
  *-display
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:e3000000-e33fffff memory:c0000000-cfffffff ioport:5000(size=64)
  *-display
       description: 3D controller
       product: GK107M [GeForce GT 750M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:3000(size=128)

```
Notes: 

[LIST]
[*]- The *dpkg *command is now showing several items. However it is showing 304 but the original settings showed in additional drivers was 340 and 352. It also feels odd that the '*current*' installation gave me 304 when I believe the newest drivers are in the 370's. 
[*]- The Additional Drivers tab does not show 304 and still has the nouvea option selected. 
[*]- Both the lspci and lshw commands now show nvidia instead of nouvea for the driver. 
[/LIST]
 
It would seem from the lshw and lspci commands that it is installed correctly, but the nvidia-settings doesn't seem to look correct.

I have tried only a small amount here because after having tried any number of things I have decided to just see what input I can get from the forum before proceeding. 

I have no objections to re-installing Ubuntu again if need be. I do require though that I stay in 14.04 because of unrelated reasons, though I have not yet installed those programs on this installation and plan on not until this issue is sorted first. I may make a few changes to the installation so I can still do work (mainly just installing a text editor to code in the meantime), hopefully none of that will interfere debugging. Just in case I will keep a log of changes I've made in-case they become relevant.

Thank you in advance for any time or effort sent my way I really appreciate it. Any progress would just make my day. =)

---

### Post by ubfan1 on 2016-09-09
Purge the nvidia 304 packages, then go back to the Additional Drivers and click on the 352...tested to install that version of the nvidia packages.  If that does not work, try the 352...updated one at the bottom.  Don't know why nvidia-current didn't work for this.

---

### Post by namesnonames on 2016-09-09
> **ubfan1 said:**
> Purge the nvidia 304 packages, then go back to the Additional Drivers and click on the 352...tested to install that version of the nvidia packages.  If that does not work, try the 352...updated one at the bottom.  Don't know why nvidia-current didn't work for this.

First of all thank you for responding.

I uninstalled the 304 packages with the following commands:
```

sudo apt-get purge nvidia-304
sudo apt-get purge nvidia-opencl-icd-304 nvidia-libopencl1-304
sudo apt-get purge libcuda1-304

```

I then went to the Additional Drivers again and selected the 352...tested as suggested. Clicked the apply changes button everything was fine. The nvidia-settings window still looked the same. So I decided to run the set of commands from early (lspci, lshw, dpkg  I have these in a script and have been running them after every major action). The result at that point was:
```

$ lspci -k | grep -EA2 'VGA|3D'
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    Subsystem: Dell Device 05fa
    Kernel driver in use: i915
--
04:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)
    Subsystem: Dell Device 05fa
    Kernel driver in use: nvidia

$ sudo dpkg -l | grep -i nvidia
ii  bbswitch-dkms                                         0.7-2ubuntu1                                        amd64        Interface for toggling the power on nVidia Optimus video cards
ii  libcuda1-352                                          352.63-0ubuntu0.14.04.1                             amd64        NVIDIA CUDA runtime library
ii  nvidia-352                                            352.63-0ubuntu0.14.04.1                             amd64        NVIDIA binary driver - version 352.63
ii  nvidia-opencl-icd-352                                 352.63-0ubuntu0.14.04.1                             amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver

$ sudo lshw -C display
  *-display
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:e3000000-e33fffff memory:c0000000-cfffffff ioport:5000(size=64)
  *-display
       description: 3D controller
       product: GK107M [GeForce GT 750M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:3000(size=128)

```

I then rebooted to a black login screen. The little drum noise did play if that matters. I went into the tty1 re-ran the info script mentioned above. I diffed the output with the pre-reboot output and got:
```

$ diff REPLY1-post352-postreboot REPLY1-post352-pre-reboot
28c28
<        resources: irq:47 memory:e3000000-e33fffff memory:c0000000-cfffffff ioport:5000(size=64)
---
>        resources: irq:44 memory:e3000000-e33fffff memory:c0000000-cfffffff ioport:5000(size=64)
40c40
<        resources: irq:49 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:3000(size=128)
---
>        resources: irq:16 memory:e2000000-e2ffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:3000(size=128)

```
Not sure how important that information is, but it seems like the irq numbers changed.

I then wanted to see if I could get back to using the integrated graphics so I tried the following:
```

$ prime-select query 
nvidia

$ prime-switch intel 
Segmentation fault (core dumped)

```
In previous attempts prime-switch had at least not seg-faulted, though I wasn't surprised as I had seen it segfault in yet other attempts.

Still stuck with only the tty for now. =\

---

### Post by namesnonames on 2016-09-09
As an after thought I ran dmesg it had what I beleive to be some relevant information:
```

dmesg | grep -i vga
[    0.290951] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.290954] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.290957] vgaarb: loaded
[    0.290958] vgaarb: bridge control possible 0000:00:02.0
[    0.689412] fb0: EFI VGA frame buffer device
[   11.839381] fb: switching to inteldrmfb from EFI VGA
[   11.839486] [drm] Replacing VGA console driver
[   11.877671] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   14.062469] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   14.062474] bbswitch: Found discrete VGA device 0000:04:00.0: \_SB_.PCI0.RP05.PEGP
[   15.068071] vgaarb: this pci device is not a vga device
[   15.556488] vgaarb: this pci device is not a vga device

```
```

dmesg | grep -i nvidia
[   12.452069] nvidia: module license 'NVIDIA' taints kernel.
[   12.454547] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[   12.459882] nvidia 0000:04:00.0: enabling device (0006 -> 0007)
[   13.155999] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:04:00.0 on minor 1
[   13.156008] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  352.63  Sat Nov  7 21:25:42 PST 2015

```
I also thought the last 21 lines in particular were interesting.
```

dmesg | tail -n 21
[   14.062463] bbswitch: version 0.7
[   14.062469] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[   14.062474] bbswitch: Found discrete VGA device 0000:04:00.0: \_SB_.PCI0.RP05.PEGP
[   14.062482] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   14.062577] bbswitch: detected an Optimus _DSM function
[   14.062584] bbswitch: Succesfully loaded. Discrete card 0000:04:00.0 is on
[   15.068071] vgaarb: this pci device is not a vga device
[   15.070510] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.070536] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.070547] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.070558] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.070569] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.070579] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.070647] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.070659] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.092259] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20150619/nsarguments-95)
[   15.556488] vgaarb: this pci device is not a vga device
[   42.560445] audit_printk_skb: 168 callbacks suppressed
[   42.560447] audit: type=1400 audit(1473442252.339:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1889 comm="apparmor_parser"
[   42.560454] audit: type=1400 audit(1473442252.339:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1889 comm="apparmor_parser"
[   42.560736] audit: type=1400 audit(1473442252.339:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1889 comm="apparmor_parser"

```

I've put all of the documentation I have into a [drive folder]("https://drive.google.com/drive/folders/0BwYjV9kPFXnfdXhvRjQ4S1pVd1k?usp=sharing") that I have opened to the public if you would like to dig through it more.
I'm not sure if this is the best way to share the information that I have. I am open to changing how I provide the info. 

Thanks again.

---

### Post by ubfan1 on 2016-09-09
Are you using bumblebee?  I'd go to your BIOS/UEFI settings and if you have the option, select the "discrete" video option (as opposed to the "integrated" or "optimus" choice).  Then get the nvidia side of things fixed up before trying the video capability to switch back and forth between the nvidia and integrated.

---

### Post by namesnonames on 2016-09-09
> 
Are you using bumblebee?

After having looked up what bumblebee is I don't believe that I am. Everything that I've done regarding graphics I've listed here so unless it installed with other things I have not installed it. Should I install bumblebee ? and if so how would you suggest I proceed?
I found different sources saying very different things. For example [here]("http://nlug.ml1.co.uk/2016/02/an-almost-authoritative-guide-to-nvidia-prime-and-bumblebee/5065") says **"DO NOT** install bumblebee-nvidia" and [here]("https://wiki.ubuntu.com/Bumblebee") gives the exact opposite advice putting bumblebee-nvidia in the install list. So how would you proceed?

> 
I'd go to your BIOS/UEFI settings and if you have the option, select  the "discrete" video option (as opposed to the "integrated" or "optimus"  choice).

I went into the BIOS and the UEFI settings and could not find anything relating to graphics card options. I did find something that had two options and they were 'Legacy Boot' and 'UEFI' but I don't think that's what you meant.

> 
Then get the nvidia side of things fixed up before trying the video  capability to switch back and forth between the nvidia and integrated.

I'm totally on board with that, the only reason I was trying to get back to the intel was because the gui wasn't working and in previous endeavors that command had at least made the gui usable. I'm not comfortable with using CLI based editors so I was just trying to get to a point were it was usable for other purposes.

Thanks again!! =)

---

### Post by ubfan1 on 2016-09-10
The "bbswitch" in your listing seems to be bumblebee, of which I have little knowledge.  You did get the 352 nvidia driver on a display successfully.  There are lots of potential kernel switches to try for a black screen problem, starting with "nomodeset".  some others to try (although I guess any nouveau blacklist is not needed):
nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Older Intel video card:
i915.modeset=1 or i915.modeset=0
newer:
i915.i915_enable_rc6=1
i915.enable_execlists=0

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

Skylake needs this (15.04...):
i915.preliminary_hw_support=1
noveau.blacklist=1 edd=on nolapic pcie_aspm=force tpm_tis.interrupts=0 
Maybe
intel_idle.max_cstate=1 nouveau.modeset=0

---

### Post by namesnonames on 2016-09-10
A MIRACLE!!!!???!!!!?

(This happened prior to ubfan1's post #7, but I am slow at posting)

So I figured I would go digging around and  look at some config files and see if anything jumped out at an untrained  eye. I however did not end up doing this because when I booted up,  expecting to see a black screen and switch to tty1, there was instead  just the normal login screen, and everything seems fine right now. I've  added the dmesg output, the output from my info script, and a screenshot of the nvidia-settings window. I've added this into a file called "Post miracle" on the drive location linked earlier. I am really at a loss for why it behaves differently now. I will try restarting it again and see if everything is still ok.

I have not tried anything listed in the ubfan1's most recent post yet. I will hold off because I think this is working. Do you have any suggestions on how to test it more fully? I was looking at nvidia-smi and this is the current output:

```

$ nvidia-smi
Fri Sep  9 22:32:25 2016       
+------------------------------------------------------+                       
| NVIDIA-SMI 352.63     Driver Version: 352.63         |                       
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GT 750M     Off  | 0000:04:00.0     N/A |                  N/A |
| N/A   51C    P8    N/A /  N/A |    204MiB /  2047MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0                  Not Supported                                         |
+-----------------------------------------------------------------------------+



```

It just feels like magic right now and I am not sure why it's suddenly working. Any ideas on what might have happened? This was after the third or fourth reboot since getting the first black screen.

---

### Post by namesnonames on 2016-09-10
I found out what is different!!! I turned it on and waited .... if you look at the dmesg output at about the 866 second mark (14 .4 minutes) a large amount of things happened and that's when the screen comes back from black. I had been away from my computer when it started which is why it seemed spontaneous at first. The question is now how do I make it not take 14 minutes to begin working? I am going to post some log files that I think are relevant into the drive folder ([link]("https://drive.google.com/drive/folders/0BwYjV9kPFXnfdXhvRjQ4S1pVd1k?usp=sharing") again for convenience) I'm putting them into the post_miracle folder again though I don't think anything is significantly different from before other than I waited and then for some reason it decides to work. ¯\_(&#12484;)_/¯

For record I added the following log/settings files to the drive folder:
/var/crash/_usr_bin_gpu-manager.1000.crash
/var/log/gpu-manager.log
/var/log/Xorg.0.log
/var/log/prime-supported.log
/home/names/.nvidia-settings-rc
/home/names/.xsession-errors
/home/names/.Xauthority

There also exists this file, but it was taking a while and I didn't care to wait for it to upload. 
/var/crash/_usr_bin_Xorg.0.crash

---

### Post by namesnonames on 2016-09-11
Alright so after having played around with it for a day or so I found that the delay is until it decides to sleep. As it turns out I can trigger this by closing the laptop lid, but I would like to add something or other to my startup scripts to emulate that. Any ideas?

---

### Post by mc4man on 2016-09-12
If one is using 14.04.5 release image then you're getting the lts-xenial xorg & mesa. That version has a bug with nvidia-prime that gives no display until  the display goes to sleep & then is woken up. The default time out to sleep is 300 secs. 
This can occur either at the login screen or after logging in (one could blindly login, I've done so many times..
current bug for 14.04.5
[https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1610476](https://bugs.launchpad.net/ubuntu/+source/nvidia-prime/+bug/1610476)

This was a bug starting in 15.10 that was not really fixed, instead they patched ubuntu-drivers-common to use modesetting instead of SNA but that patch was never applied to ubuntu-drivers-common in 14.04 (nor should it be.

orig. bug - [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1501041](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1501041)
The bs bug that resulted in so-called fix - [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507676](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1507676)

What you can do is set the timeout to sleep for the unity greeter to like 3-4 secs. Then boot to greeter login, (you'll hear the bell), wait 4 sec or so, move mouse & then all will be well for that session inc. any subsequent log out/ins
Instructions on how to do that upon request.

---

### Post by namesnonames on 2016-09-12
> **mc4man said:**
> 
What you can do is set the timeout to sleep for the unity greeter to like 3-4 secs. Then boot to greeter login, (you'll hear the bell), wait 4 sec or so, move mouse & then all will be well for that session inc. any subsequent log out/ins
Instructions on how to do that upon request.

Yes please!!! :D

---

### Post by namesnonames on 2016-09-12
So I think I did it, but there was no change. To make sure I did it right, what I did was opened /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml, found the idle-timeout tag and changed the value from 300 to 5. Rebooted and waited 10 seconds after the login screen sounded. Screen did not un-black when mouse and keyboard were used. =\

I also tried forcing the screen off and on again to emulate the lid close by putting the following in my rc.local file.
```

xset -display :0.0 dpms force off
sleep 0.01
xset -display :0.0 dpms force on

```

---

### Post by mc4man on 2016-09-12
You do this this way. It must be done exactly as shown.
```
 sudo -H gedit /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml
```
scroll down to bottom, you'll see the line to edit highlighted in screen 1

Change 300 to 3  see scr. 2
Save file & close out gedit, in terminal run this command, _it must run without any error or comment._ If you edit as shown there will be none, terminal will just return to prompt. If there was a printed error or comment you must fix before logging out or restarting.
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```
If ^ goes well then reboot, when you hear the login bell wait 3+ seconds then move mouse or start typing in password. Screen will wake up, ect. (refrain from moving mouse too early, let screen timeout..

---

### Post by namesnonames on 2016-09-12
That did the trick. It feels weird, is there a better solution in the works? This feels like a janky workaround. :lolflag: 

Thanks again to everyone!!!!

---

### Post by mc4man on 2016-09-12
> **namesnonames said:**
> That did the trick. It feels weird, is there a better solution in the works? This feels like a janky workaround. :lolflag: 

Thanks again to everyone!!!!
Use 16.04 as I doubt 14.04 will be 'fixed' as there is no acceptable fix.
Here on 14.04 I just use an earlier image so xorg/mesa is at 10.x & this doesn't occur
(- plus then I can also get vsync & no tearing while using the nvidia drivers, with modesetting this can't  be done

---

### Post by namesnonames on 2016-09-12
> **mc4man said:**
> Use 16.04 as I doubt 14.04 will be 'fixed' as there is no acceptable fix.
Here on 14.04 I just use an earlier image so xorg/mesa is at 10.x & this doesn't occur
(- plus then I can also get vsync & no tearing while using the nvidia drivers, with modesetting this can't  be done

The only issue with that is that I use ROS and the robot I work with only has support for ROS-Indigo which is only officially supported up to Trusty.
I think I can use a docker according to [this]("https://github.com/jbohren/rosdocked") but that is getting off topic for this thread. I am going to go ahead and mark this as solved.

Thanks again for all the help!!!

---

