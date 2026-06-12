---
title: "Lubuntu install issue"
date: 2019-12-27
forum: Installation &amp; Upgrades
---

### Post by ksandene on 2019-12-27
Hello

I have tried to search the forum and other places online, but i cannot find anyone who have had the same issue as me during installation of Lubuntu.
Really hope someone here can give me som tips on what I am doing wrong. 

I should first say that I am a total newbe on this. I have downloaded an ISO file named lubuntu-19.04-desktop-amd64 from [https://lubuntu.net/downloads/](https://lubuntu.net/downloads/). I have burned this ISO as a bootable disc. When I reboot the computer, it boots from the disk and I get a Lubuntu menu. So far so good. But from there, I cannot proceed. I have an option on the lubuntu boot menu to called "Start lubuntu". If I select that one, nothing happens, and the computer seem to freeze up. 

My question is why? 
Do I have the wrong ISO file? 
Is my computer too old? It is an HP Probook 4510s from 2009 with the following specs:
Processor: Intel(R) Core(TM)2 Duo CPU  T6570 @ 2.10 GHz  2.10 GHz
Installed memory (RAM): 2.00 GB
System type: 64-bit Operating System

Please help. It is currently running Window 7 and is so slow it is totally useless. Was hoping to install a light weight OS to squeeze some last juice from this ole thing.

---

### Post by ajgreeny on 2019-12-27
I think you might do better with the 18.04.3 iso of Lubuntu from [https://lubuntu.me/downloads](https://lubuntu.me/downloads) which will remain supported until April 2021 and in theory you could then try updating to 20.04 when that is available.

There are two different sites from which the iso images are available, the .net which you used and the .me which is the more official website for lubuntu.

---

### Post by guiverc on 2019-12-27
I personally would use Lubuntu 19.10 & forget about 19.04 (it reaches EOL ~17-Jan-2020 which is approaching fast). 

I would also download it from the official site. If you're unsure where to get it; don't ask google, but for any Ubuntu flavor I'd use ubuntu.com (ie. [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)) which will take you to the official site for each flavor. There are many sites that offer Lubuntu for download, only one is under Ubuntu/Lubuntu control.

Lubuntu 18.04 LTS is supported until 2021-April; however it's unclear if a re-install will be required to upgrade to 20.04 LTS because 18.04 uses LXDE desktop, all later releases use LXQt, and LXDE -> LXQt had issues so was unsupported for 18.04->18.10/19.04/19.10 thus it may remain that way for 20.04.  It's possible yes (I did it on this box), however it's unsupported.  This is the reason I'm suggesting 19.10.

I tested Lubuntu (18.04->19.04) (x86) on single core pentium M 1gb laptops (2003-2005) so it'll run on yours. Also it turns out your box is very similar to one common test laptop I use for x86_64 (18.04->20.04) Lubuntu (Xubuntu & others too on occasion), ie.

[I]lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)

[/I]My thinkpad sl510 has 18.04 LTS on it currently (both Xubuntu & Lubuntu desktops are installed) and both run fine. I use this for QA-testing using 'live' images; from 18.04 through to current (development) 20.04.

I do like Xubuntu too, and whilst Lubuntu (LXDE) is actually lighter than XFCE, the applications you choose to use can actually cause Xubuntu/XFCE to be equally light (possibly even lighter if you use GTK+3 apps). This maybe too technical for you - if so ignore it, except you have a second choice of Xubuntu if it's more to your liking.  Xubuntu 18.04 LTS also does have a known upgrade path to 20.04 LTS (which currently I can't guarantee for Lubuntu 18.04 LTS; at least a supported one; outside of a re-install [*which is actually faster anyway*]).

The official Lubuntu site ([http://lubuntu.me/](http://lubuntu.me/)) also has a manual, pages you may find useful are :-

[https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)
[https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)

In the installation page (1.3) you'll note near the top there is a "*Check disc for defects*" option.  I recommend using that to ensure your media is written correctly, it takes only a short while, but saves hours-days of diagnosing problems if you have a bad write (they happen too regularly in my experience). The '*Check disc for defects*' option on your current 19.04 thumb-drive (CD/dvd) may reveal your existing install problem! (note it isn't check your hdd/ssd, but checks the install media itself).

---

### Post by VMC on 2019-12-27
It could be just a poorly burnt dvd. I think there's a check disk on the menu. Also if you could edit the boot and remove "quiet" and "splash", and see what happens. I find it easier to use usb to boot.

---

### Post by slickymaster on 2019-12-27
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by GhX6GZMB on 2019-12-27
@ksandene, welcome :)

From your hardware list, Lubuntu is indeed the right choice.

You'll get the correct .iso from here:

[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

I'm running 19.10 myself and have had 0 issues until now,

---

### Post by RobGoss on 2019-12-28
Have you tried creating a Bootable **USB** instead of a **DVD,** it might work best

Looking at the specs of your machine I would stick with the lighter versions of Ubuntu for best performance

---

