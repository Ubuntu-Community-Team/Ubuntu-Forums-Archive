---
title: "[SOLVED] HP Vista Laptop: Drivers Issues"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by Lazywolf on 2008-06-04
Hi!

Today was a historic first for me; I actually downloaded and installed Linux (Ubuntu 8.4) for the first time ever! So far I like  what I've seen, but have some issues.

I went to the  [Howto: Ubuntu on HP dv9000 series laptop (Covers dv9000 and dv9500 series)]("http://ubuntuforums.org/showthread.php?t=512059&highlight=6000+series") thread first off so as to be able to use wireless networking and enable the video card (I saw some sweet [screenshots]("http://youtube.com/watch?v=EAP5bhApQcI") on Youtube earlier today).

I went to the blog link at the top for the updated instructions in PDF, but when I follow the steps it comes up with "file not found" or something similar for the video, camera, and wireless network drivers.

How do I get this to work?
My system:
dv6885se
Core™2 Duo mobile processor T8100 2.1GHz
Intel® PRO/Wireless 4965AGN network connection
3GB DDR2 memory
800MHz frontside bus
250GB Serial ATA hard drive (5400 rpm)
NVIDIA GeForce Go 8400M GS with 256MB dedicated graphic memory
Microsoft Windows Vista Home Premium Edition

I'm tired and have to go take a practice a+ exam for my certification test tomorrow, so I may have missed something obvious, but any help would be awesome! Thanks!

---

### Post by PmDematagoda on 2008-06-04
About the Nvidia driver, where did you download it to(Give the path)?

---

### Post by Lazywolf on 2008-06-05
Looks Like I'm connected!

---

### Post by Lazywolf on 2008-06-05
> **PmDematagoda said:**
> About the Nvidia driver, where did you download it to(Give the path)?
I tried to use EnvyNG with this advice:
> Alternate way of installing video drivers:
EnvyNG is a tool written in Python allowing for automatic compilation of the most recent graphics driver for ATI
and nVidia cards. This tool can be found by searching in Synaptic Package Manager (System->Administration-
Synaptic Package Manager) for EnvyNG and selecting to install it. After installation, EnvyNG can be found in
Applications->System Tools->EnvyNG.

I couldn't find it in the Synaptic Package Manager, so I downloaded it [here]("http://linux.softpedia.com/progDownload/EnvyNG-Download-36961.html") and supposedly installed it, but it won't show up in the add/remove programs or the package manager.

I also get this when I go into hardware drivers:

[Screenshot]("http://linux.softpedia.com/progDownload/EnvyNG-Download-36961.html")

Sorry if this is something obvious that I'm just not getting!

---

### Post by Lazywolf on 2008-06-05
I'm embarrassed now...
So somehow everything listed above got resolved-the last issue is that the screen resolution is only 640x480 when it should be much higher. How do I resolve that?

---

### Post by Unix_Slayer on 2008-06-05
> **Lazywolf said:**
> I'm embarrassed now...
So somehow everything listed above got resolved-the last issue is that the screen resolution is only 640x480 when it should be much higher. How do I resolve that?


On start menu ==> System Settings / Display

---

### Post by Lazywolf on 2008-06-05
Now I think I'm finally good! Thanks!:)

---

