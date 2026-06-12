---
title: "Does realtime kernel installation require new graphics driver install?"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by phil the dill on 2008-08-09
I recently installed the UbuntuStudio audio package into an already configured and working Ubuntu 8.04 setup via Synaptic. A realtime kernel was installed during this process (which I hadn't realised was going to happen!). After dealing with grub issues, I can now boot into the realtime kernel but the graphics drivers for my Nvidia 6800GT don't load.

Does installing the realtime kernel require installing new graphics drivers, or should it work with my previous drivers? If it requires installing new graphics drivers, will I still be able to boot into the generic (non-realtime) kernel and use my previous graphics drivers? 

In other words, does Ubuntu retain drivers and other config stuff for each kernel, or are all kernels expected to use the same driver?

---

### Post by caljohnsmith on 2008-08-09
To my knowledge, you shouldn't need to install new graphics drivers if your graphics driver comes in the standard module packages that you should have installed for your new kernel, such as:
[LIST]
[*]linux-restricted-modules-2.6.24-19-rt
[*]linux-ubuntu-modules-2.6.24-19-rt
[/LIST]
Each kernel you have has its own drivers in a directory tree starting in the /lib/modules/ directory. Does your graphics require using some other restricted driver? If so you might have to enable it in System > Admin/Prefs > Restricted Drivers (I'm not in Ubuntu right now, that's from memory).

---

### Post by phil the dill on 2008-08-09
caljohnsmith: 

Thanks for the reply. I'm using the Envy-NG graphics drivers for my Nvidia 6800GT card with dual monitors. It took me about 3 weeks to get the xorg stuff working properly (including my Wacom USB graphics tablet) and I found that the Envy driver was the only one that worked the way I wanted. It has to compile the binaries so I suppose that's why it doesn't work with a new kernel.

So does this mean that if I boot into the realtime kernel and (re)install the Envy driver it won't interfere with my config on the generic (non-realtime) kernel? Will I be able to boot back into the generic kernel and find everything unchanged? I'm concerned because it was such a hassle getting xorg configured that I don't want to mess it up.

---

### Post by caljohnsmith on 2008-08-09
Phil, the first thing I would do would be to make a backup of all the files you had to tweak to get your graphics working, such as the xorg.conf. That way no matter what you do with your drivers and such you will always have the working files to go back to. :)

That said, it sounds to me like you woulld have to recompile that envy driver again while your are in the new realtime kernel so that the new driver gets placed in the /lib/modules/2.6.24-**-rt directory. And if when you originally did that in the generic kernel, if it didn't harm your xorg settings, then it should be the same with the realtime kernel. But if it did change your xorg settings, well, that's why I recommend judiciously backing all those xorg files first before doing any recompiling. :)

---

### Post by phil the dill on 2008-08-10
Thanks, I'll give it a try.

---

### Post by markbuntu on 2008-08-10
You should really uninstall the nvidia driver before installing the rt kernel. There is a bug report on this at launchpad. This also goes for the ati driver. 

I just installed the rt kernel yesterday on my amd64 install and it seriously broke the video driver, so broken it would not uninstall until I did a force downgrade to it. Only then would it uninstall. 

Then I was stuck with no video driver and had to do recovery mode, fix x and edit my xorg config to use the VESA driver to get my desktop back. Then I could reinstall the proprietary driver and everything was OK.

So, my advice to you, remove the nvidia driver and set your xorg.conf back to vesa before you install the rt kernel. And make sure the restricted kernel modules are included, they should be anyway.

---

### Post by phil the dill on 2008-08-10
markbuntu: 

The realtime kernel is already installed. Unfortunately I didn't realise a realtime kernel was going to be installed. I was following a recommendation on a linux audio forum about installing the audio section of UbuntuStudio, and it made no reference to a realtime kernel. I didn't see any reference to realtime kernel installation in the description of the UbuntuStudio audio package on Synaptic. I thought I was just installing a few audio programs. So the first I knew about a realtime kernel being installed was when the grub config dialog appeared. 

As it turns out it hasn't affected my generic kernel installation on my Intel P4, although I have read of problems on amd chipsets. Apparently that's what happened to you.

---

### Post by markbuntu on 2008-08-11
I don't think you understand the problem. It is specific to nvidia and ati video cards using the restricted drivers and the rt kernel. That is why you had the gub problems and why the rt kernel will not boot for you but the generic will. The rt kernel did did not load the restricted nvidia kernel modules. 

When I had my problems, the generic kernel was not affected until I tried to reload the drivers while running the rt kernel to get it working properly. If you don't want to go through what I did, leave the rt kernel alone and don't try to fix it.

---

### Post by phil the dill on 2008-08-13
markbuntu: So you're saying that I have to run the realtime kernel without any graphics drivers if I want to retain use of the current drivers in the generic kernel? In 640 x 480, without using Twinview to utilise my dual monitors? If that's the case then there's not much point in using the realtime kernel at all - some of the audio program guis are barely useable at 1024 x 768, let alone anything smaller.

Can you give me a pointer to the bug report on this problem? I did a quick search and I couldn't find anything recent that sounded similar.

Is the realtime kernel needed for the UbuntuStudio audio programs? As I mentioned earlier, I didn't even realise the realtime kernel was going to be installed - the Synaptic information about 'ubuntustudio-audio' merely describes it as "A collection of applications aimed at audio creation and editing." with no reference to the realtime kernel being installed. So if it isn't necessary then it might be best to just get rid of the realtime kernel installation and run the audio programs on the generic kernel.

---

### Post by markbuntu on 2008-08-13
The rt kernel is only really necessary for doing live recording or for live dj applications. It enables jack to get top priority over cpu time to prevent lags in audio processing which, if you are doing anything live, can be a real problem. If you are not doing anything live, you may be able to get by without the rt kernel.

Well no, you should not be stuck in 640x480. The newer VESA drivers are capable of much higher resolutions as you can see when you use gnome safe mode which utilizes them. You can also look in your Xorg.0.log to find the VESA capabilities of your video card.

I got the rt kernel to work in my amd64ubuntustudio install thorugh the above pain in the you know what. I have had no success at all with my i386ubuntustudio install, grub gives me error 15 when I try to run the rt kernel. It is a mystery. But then again, I have not tried fooling around with the restricted drivers either. Maybe that is the amd problem you are talking about.

All you can do is try. If you don't load up the cpu too much, the apps should run OK. As I said, it mostly affect live activities.

I will try to find that bug report again and get back to you.(my firefox history was turned off so I need to do it the hard way. lol)

---

