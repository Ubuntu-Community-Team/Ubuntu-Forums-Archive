---
title: "Difficulty installing nVidia drivers on installation"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by ben1828 on 2010-05-23
Hello,

First of all, I am very new to Ubuntu, having grown rather tired of Windows 'characteristics'

Secondly, I have looked for the answer to my query on both this and other forums quite thoroughly, but keep running up against hurdles. If the answer to my query is obvious, please excuse me - I have tried!

Acer Revo. Have installed the latest version of Ubuntu which is coming up as 10.04 LTS. 64bit.  It all installed first time, error free and is quite lovely. However, it's a bit slower than it should be. Looking around I note that the default installation does not include the nVidia drivers and installing these will bring it up to full speed.

Have downloaded the drivers from nVidia's site (it auto-detected the o/s and h/w so I accepted those) and gave me a 40mb text file. I then found out that I should save this, which I did as a .run.  Getting this to extract was another difficulty, but another suggestion in a terminal window would "stop something" and "exit X" giving me the opportunity to login again, and execute the .run file which appeared to be doing it's stuff.

However, it failed and looking at the log I'm at a bit of a loss as to what to do next. I can't find any significant pointers on nVidia's site and the lack of others having problems makes me suspect it's me doing something silly.

I'm quite keen to continue work through the installation to make it work correctly and would be grateful for any pointers.

Many thanks

Ben

The last snippit of the log file is below
[FONT="Courier New"][COLOR="Navy"]-> Kernel messages:
   [   20.804348]   domain 1: span 0,2 level MC
   [   20.804355]    groups: 0,2 (cpu_power = 1178)
   [   20.804368]    domain 2: span 0-3 level CPU
   [   20.804375]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
   [   20.804395] CPU3 attaching sched-domain:
   [   20.804402]  domain 0: span 1,3 level SIBLING
   [   20.804410]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
   [   20.804426]   domain 1: span 1,3 level MC
   [   20.804434]    groups: 1,3 (cpu_power = 1178)
   [   20.804446]    domain 2: span 0-3 level CPU
   [   20.804453]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
   [   27.930494] eth0: no IPv6 routers present
   [  258.824554] [drm] nouveau 0000:03:00.0: nouveau_channel_free: freeing
   fifo 2
   [  387.940820] nvidia: module license 'NVIDIA' taints kernel.
   [  387.940830] Disabling lock debugging due to kernel taint
   [  389.713877] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 20
   [  389.713891] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 20
   (level, low) -> IRQ 20
   [  389.714322] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  389.714331] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  389.714334] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  389.714337] NVRM: device(s).
   [  389.714344] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  389.714347] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  389.714350] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  389.714356] NVRM: No NVIDIA graphics adapter probed![/COLOR][/FONT]

---

### Post by dabang on 2010-05-23
Is there any reason not to use the proprietary driver which is offered by Ubuntu? Just go to "System -> Systemsettings -> Hardware Drivers". This should do the trick.

---

### Post by wojox on 2010-05-23
> Looking around I note that the default installation does not include the nVidia drivers and installing these will bring it up to full speed.

Have you updated your installation since installing?

---

### Post by skarme on 2010-05-23
> **ben1828 said:**
> Hello,

First of all, I am very new to Ubuntu, having grown rather tired of Windows 'characteristics'

Secondly, I have looked for the answer to my query on both this and other forums quite thoroughly, but keep running up against hurdles. If the answer to my query is obvious, please excuse me - I have tried!

Acer Revo. Have installed the latest version of Ubuntu which is coming up as 10.04 LTS. 64bit.  It all installed first time, error free and is quite lovely. However, it's a bit slower than it should be. Looking around I note that the default installation does not include the nVidia drivers and installing these will bring it up to full speed.

Have downloaded the drivers from nVidia's site (it auto-detected the o/s and h/w so I accepted those) and gave me a 40mb text file. I then found out that I should save this, which I did as a .run.  Getting this to extract was another difficulty, but another suggestion in a terminal window would "stop something" and "exit X" giving me the opportunity to login again, and execute the .run file which appeared to be doing it's stuff.

However, it failed and looking at the log I'm at a bit of a loss as to what to do next. I can't find any significant pointers on nVidia's site and the lack of others having problems makes me suspect it's me doing something silly.

I'm quite keen to continue work through the installation to make it work correctly and would be grateful for any pointers.

Many thanks

Ben

The last snippit of the log file is below
[FONT=Courier New][COLOR=Navy]-> Kernel messages:
   [   20.804348]   domain 1: span 0,2 level MC
   [   20.804355]    groups: 0,2 (cpu_power = 1178)
   [   20.804368]    domain 2: span 0-3 level CPU
   [   20.804375]     groups: 0,2 (cpu_power = 1178) 1,3 (cpu_power = 1178)
   [   20.804395] CPU3 attaching sched-domain:
   [   20.804402]  domain 0: span 1,3 level SIBLING
   [   20.804410]   groups: 3 (cpu_power = 589) 1 (cpu_power = 589)
   [   20.804426]   domain 1: span 1,3 level MC
   [   20.804434]    groups: 1,3 (cpu_power = 1178)
   [   20.804446]    domain 2: span 0-3 level CPU
   [   20.804453]     groups: 1,3 (cpu_power = 1178) 0,2 (cpu_power = 1178)
   [   27.930494] eth0: no IPv6 routers present
   [  258.824554] [drm] nouveau 0000:03:00.0: nouveau_channel_free: freeing
   fifo 2
   [  387.940820] nvidia: module license 'NVIDIA' taints kernel.
   [  387.940830] Disabling lock debugging due to kernel taint
   [  389.713877] ACPI: PCI Interrupt Link [LPMU] enabled at IRQ 20
   [  389.713891] nvidia 0000:00:03.5: PCI INT B -> Link[LPMU] -> GSI 20
   (level, low) -> IRQ 20
   [  389.714322] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  389.714331] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  389.714334] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  389.714337] NVRM: device(s).
   [  389.714344] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  389.714347] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  389.714350] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  389.714356] NVRM: No NVIDIA graphics adapter probed![/COLOR][/FONT]

It implies stopping x server and then installing the drivers and again restarting the x server.
However you may install the drivers this way....(check the link for screenshots)
*[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia) *

---

### Post by ben1828 on 2010-05-23
In response to dabang's question on why not using the proprietory drivers...

They only offer basic functionality, which is preventing me from watching videos in anything higher than average quality. The video card can support much more, but the drivers need to be manually loaded (so I understand).

---

### Post by ben1828 on 2010-05-23
> **wojox said:**
> Have you updated your installation since installing?

Yes.

It picked up quite a lot, installed, rebooted and ran it again. Nothing since.

---

### Post by ben1828 on 2010-05-23
> **skarme said:**
> It implies stopping x server and then installing the drivers and again restarting the x server.
However you may install the drivers this way....(check the link for screenshots)
*[http://www.psychocats.net/ubuntu/nvidia](http://www.psychocats.net/ubuntu/nvidia) *
Thank you, I will try that :)

---

### Post by wojox on 2010-05-23
Try this HowTo [http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx](http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx)

---

### Post by oldfred on 2010-05-23
the default driver says it supports your device ION.

[http://www.nvidia.com/object/linux_display_ia32_185.18.36.html](http://www.nvidia.com/object/linux_display_ia32_185.18.36.html)

If you manual install you probably have to reinstall with every kernel download. I would try the default install first before experimenting with installs of the very latest nvidia driver.

---

### Post by dabang on 2010-05-24
> They only offer basic functionality, which is preventing me from watching videos in anything higher than average quality. The video card can support much more, but the drivers need to be manually loaded (so I understand).


No, I didn't mean the default nouveau driver, but the proprietary Nvidia driver, which is the same you downloaded from Nvidia's website. Installing this driver from Ubuntu's repositories is much easier.

---

### Post by ben1828 on 2010-05-28
Thanks for all the help.
 
With everything I'd been trying I got into a bit of mess, so reinstalled from scratch and started again.
 
First step was to try installing the driver from Ubuntu's repositories. Of course, it worked first time.
 
Thank you!
 
:)

---

