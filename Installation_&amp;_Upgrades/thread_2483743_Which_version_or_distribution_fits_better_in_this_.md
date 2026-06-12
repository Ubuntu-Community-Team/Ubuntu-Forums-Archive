---
title: "Which version or distribution fits better in this computer"
date: 2023-02-07
forum: Installation &amp; Upgrades
---

### Post by alexlaijin17 on 2023-02-07
I was wondering if I could upgrade my old little computer for just learning with some apps concretely and browsing internet. My Firefox and chromium actually work too slowly and  can’t have many addons updated.

Memoria: 991,1 MiB
Procesador: Intel ® Atom.™' CPU N455 @ 1.66GHz x2
Gráficos: intel® IGDx86/MMX/SSEZ
Tipo de SO: 32-bit
Disco: 313,0 GB

---

### Post by ne29914 on 2023-02-07
The N455 is actually a 64-bit IS type, so one of the lightweight distributions (Lubuntu, Xubuntu etc.) would work, 1.66 GHz is also OK.
The big problem is your RAM size. In my experience 2 GB is minimum.
Can you upgrade this? An extra 1 GB is 5 Euros today.
For the browser, drop Firefox and install a faster one, eg, Brave.

---

### Post by TheFu on 2023-02-07
The Atom N455 is a bit of a dog.  [https://www.cpubenchmark.net/cpu.php?cpu=Intel+Atom+N455+%40+1.66GHz](https://www.cpubenchmark.net/cpu.php?cpu=Intel+Atom+N455+%40+1.66GHz)  180 passmarks.  In general, I find that 1500 passmarks are the minimal for a happy experience with a light Linux DE.  For that Atom box, I wouldn't use any GUI.  As a pure-server, it would be fine for something like a home Nextcloud instance, but 

How do I say this nicely.  For $75, an off-lease computer with a Core i5 can be found with a 3000 passmark, 8GB RAM and 200+GB HDD.  Just saying.

If you want to go really light, check out Tiny Core Linux. [http://tinycorelinux.net/downloads.html](http://tinycorelinux.net/downloads.html)  It should run completely from RAM after being loaded. The "full version" is under 170MB.

---

### Post by guiverc on 2023-02-08
The atom CPU I used most in QA was an older 32-bit version of what you have, ie. 

```
asus eepc 1000HE (intel atom n270, 1gb, intel mobile 945gse integrated)
```

The *atom* was a cut-price CPU by intel that has little actual processing *grunt*, with its selling point being the long battery life (*as it walks instead of runs, it uses less battery power*).

As my intel atom was 32-bit or *i386* (*in Debian & Ubuntu terminology, i686 in Linux terms*), the last Ubuntu release I could QA-test was *disco* or 19.04, as 32-bit didn't exist in *live* ISOs after then.  Both Xubuntu & Lubuntu *ran* pretty well, but as for which I was going to use, I'd go by what I wanted to use it for, specially what apps as Xubuntu & Lubuntu have very different software stacks (*on releases beyond 18.04, even somewhat on 18.04 too*). I'd likely install whichever I wanted, then add packages so it runs without a desktop (ie. WM etc only).

I still have that asus eepc, and whilst I'd have to boot it to confirm what's on it now, but I'd expect to see a Debian on it when booted (the last Ubuntu release to support it is 18.04, which is now EOL for *flavors *like Lubuntu/Xubuntu). I still do have a *i386* device with 18.04 on it, but most have Debian on them now). I'd expect my old asus eeepc would have both LXDE & XFCE desktops installed; though I'd likely use neither and login to a session using one of the WMs I've also installed.

I don't use my eeepc (or 32-bit boxes) much these days, but that eepc still has great battery life, I don't care if it gets knocked around, so I'll still grab & take it with me *'here and there'* for tasks such as data entry, or very light browsing, but I'd choose the session I use depending on what I do. Mine has limited RAM, but with a 160GB HDD I can afford to have multiple DEs installed & select which I use (*inc. none & just use a WM instead of DE+WM*) by what task I'll perform in that session as its the RAM that is limited, not the disk space (extra unused DE's (*desktops*) & WM's (*window managers*) sitting on disk don't waste much of that 160GB disk, but that 1GB of RAM is precious!!!)

I don't decide what DE I use based on hardware, at least not usually.

(FYI: I did do some QA on other atoms, but they're not in my QA-list anymore so I can't provide specs; why I copy/pasted details for the old 1000HE.  Also as Lubuntu has been LXQt since Lubuntu 18.10, if wondering why I mention I'd expect to see LXDE & Xfce; I mentioned those as I had both Xubuntu & Lubuntu installed on it up to 18.04 (*the last supported Ubuntu, and LXQt & Xfce for 18.10+19.04*), but found whilst Lubuntu/LXQt is the *lightest* *flavor* of Ubuntu now, I tended to use more GTK *apps* than Qt5 *apps  *on the eepc, thus why I'd expect to find both LXDE (GTK2) & Xfce (GTK3).. Quite possibly LXQt is there too, but I do know it's got many WM's installed including ICEWM I'll probably use more often than LXDE/Xfce/LXQt on it)

---

### Post by TheFu on 2023-02-08
I had a hand-me-down Asus eepc 1000HE w/ 2G of RAM.  Traveled with it for a few years.  It was an amazing machine at the time.  It couldn't deal with video playback over 600p and the battery life was getting worse and worse.  Still, I'd put it into checked luggage and not worry about it being stolen.  When I travel, I try to have 23 hour layovers in interesting cities and really don't want to lug around a laptop too.  For layovers like that, you leave your checked luggage with the airline. One less thing to worry about.

Eventually, I gave The Eee away to someone who needed a computer. He destroyed it in just a few months. That taught me a lesson.  Always make someone pay, even just a little, for a computer, or they won't treat it well.  I'm not out to make a profit, just want the system I'm not using anymore to be useful to someone.

The Eee came with a lite distro, I recall.  My replacement was an Acer Chromebook C720 which was lighter, had a longer battery, had a higher resolution and a 1500 passmark Celeron CPU. That celeron could run VMs!

---

### Post by ubfan1 on 2023-02-08
For a 1GB Intel Compute Stick STCK1A8LFC (Atom Z3735F), I put Debian on the 5GB internal storage, but like Antix 19 (ICE/ROX gui) booting off a microSD.  I do use 1GB swap with "zswap.enabled=1 zswap.compressor=lz4" added to /etc/default/grub at the "quiet splash".

---

### Post by ActionParsnip on 2023-02-08
I'd go for something like Puppy

---

### Post by bobnutfield on 2023-02-09
I have an old Asus Aspire One with an Atom N27o and 1 GB RAM.  It runs Bodhi Linux quite briskly, but in my opinion it's a crappy distro.  I agree with the previous post.  Puppy would be a good choice and if I decide to put it back in service I'll install that.

---

### Post by him610 on 2023-02-10
I have a 32bit netbook with similar specs - Acer Aspire One 	A110L ZG5, Intel Atom N270 1.6 GHz, RAM 1.536MB. 

Not every distro provides a 32bit version anymore. There is a 32bit version, Raspberry Pi Desktop OS compatiable with PC and Mac 32bit systems that I have installed on my Acer Aspire One. It works fine; it is based on Debian Bullseye, released July 2022. 

It can be found here: [https://www.raspberrypi.com/software/operating-systems/]("https://www.raspberrypi.com/software/operating-systems/") Look for it at the bottom of the page.

---

