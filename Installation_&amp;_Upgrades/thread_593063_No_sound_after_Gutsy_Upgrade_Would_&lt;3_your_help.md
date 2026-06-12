---
title: "No sound after Gutsy Upgrade? Would &lt;3 your help!"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by bocmaxima on 2007-10-26
I did some searching for this problem, found a lot of others having the problem, but not many solutions. I get this error when trying to test the sound from my nForce2 onboard sound card

```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing.
```

I haven't the faintest idea what to do now. It was working beautifully under Feisty. I need this working again as it is critical to my business (dont fix what isnt broken, right? haha). I very much appreciate any ideas you may have for me. Thanks in advance.

:guitar:

---

### Post by Pumalite on 2007-10-26
You have to see if your sound card is being recognized and the module loaded (sudo lshw -C sound)or if it is the alsa-mixer problems. etc. I'll give you a collection of links to find your solution:
[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound+problem+solutions+guide)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://www.alsa-project.org/main/index.php/MainPage](http://www.alsa-project.org/main/index.php/MainPage)

---

### Post by aleska on 2007-10-29
> **Pumalite said:**
> You have to see if your sound card is being recognized and the module loaded (sudo lshw -C sound)or if it is the alsa-mixer problems. etc. 

So, I just did sudo lshw -C sound and got the following:
>   *-multimedia UNCLAIMED  
       description: Audio device
       product: MCP51 High Definition Audio
       vendor: nVidia Corporation
       physical id: 10.1
       bus info: pci@0000:00:10.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

So, what now?  
BTW - same for me, everything worked peachy with absolutely no tweaking necessary for Feisty.  I just did a Gutsy upgrade and now no sound.
I click on the sound icon top right menu bar, and it tells me:
> No volume control GStreamer plugins and/or devices found.
Any help greatly appreciated!

---

### Post by Pumalite on 2007-10-29
You can check in Synaptic if your GStreamer plugins are installed or not, but I bet they are and that your problem is this:
*-multimedia UNCLAIMED
description: Audio device
Which means the module for your sound card is not being loaded and that is a kernel problem. If that is the case, I'd do a clean reinstall after saving data.

---

### Post by ArtInvent on 2007-12-19
I had a very similar problem after a Gutsy upgrade. Sound card absolutely not recognized, unable to even start alsa-mixer at all. I've posted it elsewhere as I feel this is a bug in the upgrade process. After pulling my hair out and messing with alsa drivers packages, reinstalling, messing with config files etc. etc. I had no luck. It seemed that all was as it should be yet the kernel was simply somehow not recognizing the hardware at boot. Plus I knew that my sound card works fine in Ubuntus past.

I rebooted and in Grub selected some of the other kernels. This made sound work fine again but the graphics display would not use the correct nVidia driver, I guess you have to install and enable the proprietary driver for each kernel which is hell on wheels. This seemed like a worse problem than no sound so I went back to the latest kernel.  In Synaptics I checked all the installed kernels and their packages. These are all grouped under** linux-  linux-image  linux-headers** etc.  The kernel that I was using after the upgrade defaulted to 2.6.22-14-386 but in checking the packages there was no linux-headers package installed for that kernel. I installed the package** linux-headers-2.6.22-14-386** and rebooted, but still no luck. In perusing the installed packages I saw that there was a meta-package called linux-386 that installed some other related kernel packages for the latest 386 kernel. So I thought, what the hell, worth a try. Installed, rebooted, presto, sound is back in full, graphics are perfect.

So the lesson is, check your linux version with command ** uname -r** and make sure you have all the right kernel headers and packages installed. Find the kernel you are using and then make sure the package billing itself as the 'complete Linux kernel' for that is installed.

---

