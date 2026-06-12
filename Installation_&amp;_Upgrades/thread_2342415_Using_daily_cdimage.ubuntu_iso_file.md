---
title: "Using daily cdimage.ubuntu iso file?"
date: 2016-11-06
forum: Installation &amp; Upgrades
---

### Post by ajgreeny on 2016-11-06
I am just about to clean install and move from my current Xubuntu-14.04 installation to Xubuntu-16.04 and have downloaded the most recent daily .iso image file from [http://cdimage.ubuntu.com/xubuntu/xenial/daily-live/current/](http://cdimage.ubuntu.com/xubuntu/xenial/daily-live/current/) (with a date of 4th Nov 2016)

Am I correct in thinking this is a good way to do a clean install saving time updating after installing the OS, or am I asking for unknown troubles and untested packages?  The live system runs very well from USB, and the only difference I can see between this live system and my VirtualBox install of Xubuntu-16.04 is the kernel version, which is one point version higher in the live .iso file than in my fully updated installed VM.

Has anyone else successfully clean-installed from that daily iso file, or a previous one?
Did you have any problems at all that you could put down to using the daily .iso as opposed to using the standard install .iso file?

---

### Post by sudodus on 2016-11-06
I think it is a good idea :-) In principle, you will get the same system or very similar, if you install from the Xubuntu 16.04.1 LTS iso file and update & upgrade.

If you want a persistent live system, it is even better to start from the current daily live iso file, because you cannot upgrade the kernel in such a system.

-o-

But it is a different matter with a not yet released version.

-o-

***Edit:*** I think you should turn off the proposed repository to get a smooth ride (in this case xenial-proposed).

---

### Post by ajgreeny on 2016-11-06
Thanks sudodus; that is what I thought, or perhaps more truthfully, it's what I hoped, as I've never used a daily version before.

I always have the proposed repos disabled in my OSs as it seems a bit too risky to use them, and I read of many problems when users have enabled them without realising what it might mean, ie don't use them unless you can fix the problems they may cause.

I have sued the daily iso files to install VMs in VBox several times, and I update the iso files with zsync if there is a problem, but so far I have not had any real difficulties using these daily isos, so I simply wanted to check before overwriting my main installed version.

I'll update this very soon with all info about how it works; as I say the live OS, now from an updated 6th Nov 2016 iso is still running beautifully smoothly and fast.

---

### Post by bearlake on 2016-11-06
Just to add a little.

I like having my /home in its own partition on the test drive.

If things break you can always do a fresh install with a newer daily version.

Using zesty can update an existing daily build saving time and download usage.

I can do a fresh install and have all programs working in 15 min pointing the install to use the existing /home.

---

### Post by ajgreeny on 2016-11-06
Yes, I've been using a separate /home partition for many years now so my OS version upgrades only take about 15 - 30 minutes as well, plus the time adding all the other installed packages that I need as I find I want use them.

---

