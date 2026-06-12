---
title: "Issues with Intrepid and sound."
date: 2008-10-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by AreonEpta on 2008-10-14
Just got my HP DV5-1000US laptop. It has the new Broadcom 4328 a/b/g/n as well as the new Intel G45 series HD graphics. I had Hardy installed and it took me some time to get hte broadcom to work, and the video never worked right. My sound was great though.

Now, I decided to install Intrepid beta. I figured that is was supposed to have the Intel drivers for my chipset as well as the new version of X.Org so it should fix all my issues. Well, it did. Except that is made some of it's own.

Graphics are great, wireless I got working using the Broadcom STA. Everything was great when I first started up. Live disk was great. First boot was great. But after doing nothing but letting the distro update the beta to the newest version, and rebooting, the sound was gone. When Ubuntu started all I got was a little crackling and popping instead of the drums and stuff welcoming me on. So I updated a few more things, rebooted a few more times, and nothing.

I was getting worried, when I bumped into the Sound entry in System --> Preferences. I started playing with things and I got the sound test (and subsequently the sound under Pidgin) to work under "HDA Intel STAC92xx Analog (OSS)" as opposed to the standard "HDA Intel STAC92xx Digital (ALSA)". So I went under events and tried out the startup sounds, and it still crackled. After the sounds finished playing, I tried Pidgin again, and it worked.

So I'm baffled. I have no idea what would be causing this to occur. I have no idea how to fix this. I'm game for any solutions, and for sitting here F5ing til I get it fixed. I have no REAL idea what I'm doing with linux, but the following may help. Let me know if there is anything else you all would like me to post for you to help diagnose the problem.

Feel free to contact me on AIM: areonepta

lspci
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

---

### Post by AreonEpta on 2008-10-14
Music is working just fine. Still no luck with the startup.

Also, I'd like to know how to associate the special buttons near my monitor (the ones that control sound among other things) with master volume.

---

### Post by AreonEpta on 2008-10-15
Okay, so from the online bug listing, it seems this is a very widespread and well known bug. I'd still like a fix, but that's cool if one does not exist. Bump for any kind of reply.

---

### Post by philinux on 2008-10-15
Click the report button on your first thread and ask the mods to move your thread to here.
[Ibex]("http://ubuntuforums.org/forumdisplay.php?f=346") 

You'll get more joy there.

---

### Post by overdrank on 2008-10-15
moved :)

---

### Post by philinux on 2008-10-15
Make sure you're up todate.

sudo apt-get update && sudo apt-get upgrade

Might fix it. This happens a lot when testing alphas and betas.

---

### Post by psyke83 on 2008-10-15
You're having problems with PulseAudio.

ALSA applications remap to PulseAudio automatically - therefore in System/Preferences/Sound, choosing ALSA output is equivalent to PulseAudio output.

There is a comprehensive thread already dealing with PulseAudio [here]("http://ubuntuforums.org/showthread.php?t=866965").

Specifically for your case, it may be an issue with the volume levels.

Ensure the ALSA pcm controls are not muted:

```
$ alsamixer -Dhw
```

Then, follow the troubleshooting steps using the PulseAudio utilities (see the link).

---

