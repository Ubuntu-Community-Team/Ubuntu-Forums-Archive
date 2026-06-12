---
title: "Occasionally boots into &quot;low graphics mode&quot;"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Aries K on 2010-04-10
Hi, just testing the beta 2 here. :P When I restart sometimes my machine boots into "low graphics mode". It gives me the options to boot into low graphics mode, restart x, and 3 or 4 other options I forget. Usually after a couple of restarts the problem fixes itself and everything is A-ok unless I restart or something. Is anyone else having this issue? Other than that I am having no problems with Lucid whatsoever. My specs are:

Acer M1640
-1.8GHZ Intel Dual Core
-4GB of Crucial ram
-Nvidia 7050 Onboard Graphics
-250GB HD (Ubuntu)
-160GB HD (80GB X2 Raid 0/1) (Windows 7)

EDIT: This seems more likely to happen after doing a restart from a session where I was booted into Windows 7 previously if that helps anyone.

---

### Post by dino99 on 2010-04-10
is it a fresh install or an dist-upgrade ?
if its a fresh lucid, as it dont need xorg.conf, you can rename yours in case you want to recover it and reboot to see the difference.

you can look at : system admin hardware drivers and see if activation is done too.

---

### Post by Aries K on 2010-04-10
It is a fresh Lucid. The activation for the system admin Hardware Drivers are done too. :P Where can I find the "xorg.conf" so I can rename it? Thanks for your assistance.

---

### Post by mrowth on 2010-04-10
> **Aries K said:**
> Hi, just testing the beta 2 here. :P When I restart sometimes my machine boots into "low graphics mode". It gives me the options to boot into low graphics mode, restart x, and 3 or 4 other options I forget. Usually after a couple of restarts the problem fixes itself and everything is A-ok unless I restart or something. Is anyone else having this issue? Other than that I am having no problems with Lucid whatsoever. My specs are:

Acer M1640
-1.8GHZ Intel Dual Core
-4GB of Crucial ram
-Nvidia 7050 Onboard Graphics
-250GB HD (Ubuntu)
-160GB HD (80GB X2 Raid 0/1) (Windows 7)

EDIT: This seems more likely to happen after doing a restart from a session where I was booted into Windows 7 previously if that helps anyone.

Yes. I have the following problem: 

More and more often I just get the Ubuntu-will-run-in-low-graphics-mode dialogue (from which there is no escape except into an empty black screen or through Ctrl-Alt-Del) and the following error:

(EE) Apr 10 11:13:17 NVIDIA(0): Failed to allocate primary surface: out of memory
(EE) NVIDIA(0):  *** Aborting ***

X still starts fine when I boot with a text console or, apparently, GRUB's gfxpayload setting set to 640x480. Better (higher) console resolutions may work... but usually only once. So if change the resolution every time I boot I can sort of muddle through with some trial and error. 

I have a Geforce 7950 GT (AGP) on an Asus A8V Deluxe Wi-Fi G board, booting with acpi_sleep=s3_mode, s3_bios and noapic options. Using the proprietary Nvidia driver from the repos (nvidia-current, was it?)). Fully up-to-date 10.04 beta, upgraded from Ubuntu-Studio 9.04 or 9.10 (forgot which). Reinstalled video driver, didn't help.

---

### Post by Taoye on 2010-04-10
Mine does this too... every couple boots I get low graphics mode, even though I haven't made any changes to my system, to the nvidia drivers, or to my xorg.conf.

My system is a MacBook Pro 5-5, up to date after a fresh install of beta 2 (installed on my 2nd partition using boot camp), using the nvidia-current drivers.

---

### Post by cariboo on 2010-04-10
IF you have to change the resolution on every boot, you can save the changes to /etc/X11/xorg.conf by running nividia-settings as root. To do so, press Alt-F2 and type:

```
gksu nvidia-settings
```

Make your changes, then click Save To X Configuration File. Despite what several people say, the xorg.conf file is still used to overcome some problems when using the restricted nvidia drivers.

---

### Post by autocrosser on 2010-04-10
I can confirm---My system with a custom xorg is not having this problem---my wife's unit was having the problem until I created a xorg for it.....both using Nvidia cards & the nvidia-current driver.

---

### Post by Aries K on 2010-04-10
So basically I renamed the xorg.conf and restarted and see that removes the driver. I reinstall the driver and the xorg.conf file is back. So the only fix for this is removing the driver and using the generic one? :( Or did I just do something wrong? Thanks again.

---

### Post by mrowth on 2010-04-10
I've never not had an Xorg.conf. I wouldn't know where else to set up the resolution and dual monitors.

---

### Post by Aries K on 2010-04-10
> **mrowth said:**
> I've never not had an Xorg.conf. I wouldn't know where else to set up the resolution and dual monitors.

Yeah that makes sense, xorg.config is definitely needed if you want to run the Nvidia proprietary driver (at least from my observation). Before I file a bug is there a workaround for this? Just want to make sure I do not file a duplicate bug or something.

---

### Post by Aries K on 2010-04-10
I found this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/521260](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/521260)

Looks like it is a kernel issue causing this. According to the comments in the bug report:

"Looks like something is wrong with the kernel DRM. We're likely to pull in the 2.6.33 DRM which may well fix this. You can test it by installing one of the mainline kernel builds.

Meanwhile, popping this over to the kernel team."

If I am right hopefully the next kernel update should fix this. I clicked the "affects me too" and left a comment checking to see will this kernel update help out the Nvidia users as well. If you are a Nvidia user feel free to chime in as well so this can be alleviated once in for all. ):P

---

### Post by Aries K on 2010-04-13
For NVIDIA users I filed a separate bug since that is what Ben Blout recommended. Feel free to chime in and mark "this affects me too" if it does affect you. [https://bugs.launchpad.net/ubuntu/+bug/562565](https://bugs.launchpad.net/ubuntu/+bug/562565)

---

