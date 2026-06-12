---
title: "Warning:Do not install KDE with these specs.."
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by buried on 2008-04-05
DO not install Kubuntu-desktop on Ubuntu Gutsy Gibbon with these specs:
ATI Radeon xpress 1100
AMD Turion 64 x2 mobile
2.5 gb ram
It is as buggy as hell, and if you shut down your computer, Ubuntu won't boot, unless you go to the terminal and 
"sudo apt-get remove kubuntu-desktop konsole"

---

### Post by p_quarles on 2008-04-05
Moved to Installations & Upgrades.

Have you tried actually asking for help with those problems? Those are pretty common hardware components, so I have trouble that they don't work with Linux. ATI GPUs are notorious for needing extra setup, of course, but plenty of people get them working just fine.

---

### Post by onebadpenny on 2008-04-06
Hi *smile*
I'm a complete linux noob, though I'm by no means computer illiterate, so take this for whatever it's worth...

Those are my exact specs and KDE is (now) running fine for me. I first installed from a Kubuntu live CD. That installation worked ok right up until I ran all of those updates you get when you first install. Among other things, the grub update destroyed grub. Knowing full well that I've no idea (still) what I'm doing, I figured I did something wrong so I deleted the partition and reinstalled Kubuntu. Same thing happened. I really wanted to use KDE, but whatever. I deleted the partition again and installed Ubuntu. Got it working fine with a few ATI tweaks and fumbled my way through learning Gnome and linux. Then I found out I could  install the KDE package and run it as a different session. I could even make it the default session... yeah, this is old news to most, but my researching linux before installing consisted of reading about the new KDE4 upgrade (wtf is KDE? Gnome?? Ubuntu?? wtf?), thinking that crashing my laptop might be fun, downloading Ub and Kub iso;s, and the rest you just got.. so where was I? sessions, right. I installed the KDE package - not the whole KDE desktop because I wasn't sure that it wouldn't install OpenOffice all over again. Anyways, installing KDE that way worked perfectly, and my wireless works! 
Since then I have installed KDE4 - worked great, blew all that out and installed the 64 bit version. Had the same problem with the Kubuntu/Grub updates. Used the same fix and life is good...
That's a lot of words to say that it worked ok for me. I apologize, I'm not usually so verbose. yada.

---

### Post by buried on 2008-04-06
Yes, but your running Kubuntu natively and you didn't install the full kubuntu-desktop.

---

### Post by p_quarles on 2008-04-06
> **buried said:**
> Yes, but your running Kubuntu natively and you didn't install the full kubuntu-desktop.
Installing the kubuntu-desktop dummy package is all that the Kubuntu installer disk does.

---

