---
title: "Which Kernel"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by kfarrell on 2006-04-17
I have a Dual Core AMD CPU, and I'm running breezy 32bit OS, /proc/cpu reports thus:

AMD Athlon(tm) 64 X2 Dual Core Processor 3800+

Could someone advise me which kernel would be best to run with this CPU, keeping in mind I'm running 32bit. :)

---

### Post by jazzmuzik on 2006-04-17
I don't know, I've wondered about the same thing. I had a bad experience installing a 64 bit AMD version of Fedora a while back. I got frustrated not finding libraries and plugins for the extra programs I wanted to install so I went back to the 32 bit version. When it came time to install Ubuntu I stuck with the 32 bit version. I have no idea if Ubuntu 64 bit has the same problems as Fedora... but I am wary. I've been using Ubuntu for about a month now. FWIW, the 32 bit version runs GREAT on a 64 bit AMD chip. Just some things to think about.

---

### Post by kfarrell on 2006-04-17
Yes that's the reason I didn't install 64bit, I experimented with it, but the lack of libraries etc. was very frustrating. I couldn't be arsed doing the chroot stuff to make 32bit libs work. 

As for the kernel, I was more thinking, would a SMP kernel make use of my dual core? I mean it's an expensive CPU, I'd like to use some of it's fdeatures.

---

### Post by Sutekh on 2006-04-18
[QUOTE=kfarrell]I have a Dual Core AMD CPU, and I'm running breezy 32bit OS, /proc/cpu reports thus:

AMD Athlon(tm) 64 X2 Dual Core Processor 3800+

Could someone advise me which kernel would be best to run with this CPU, keeping in mind I'm running 32bit. :)[/QUOTE]
Nice processor :)  I have one too.  

Even though Athlons are K8's, in 32 bit Ubuntu K7 is the closest match.

Use this code for the latest SMP K7 kernel with restricted modules (for video drivers/modem drivers)
```
sudo apt-get install linux-k7-smp
```

Use this code for the latest SMP K7 kernel without restricted modules
```
sudo apt-get install linux-image-k7-smp
```

---

