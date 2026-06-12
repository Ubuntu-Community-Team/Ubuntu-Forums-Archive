---
title: "gnome-panel doesn't launch with gnome when booting"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by jiapei100 on 2011-04-30
Hi, all:

After a upgrading from Ubuntu 10.10 to Ubuntu 11.04, everything seems to be fine, only except gnome-panel.
Every time when I reboot my system, the desktop shows up fine (that means gnome launched), but there is menu bar at all. Nothing on the screen only except a desktop.

I tried to launch Chrom and found that it's gnome-panel issue. Now, I can launch gnome-panel from bash, but how can I let my gnome-panel automatically be launched with gnome itself during the booting?


Best Regards
Pei

---

### Post by dino99 on 2011-04-30
unity replace gnome-panel by default now
so if you dont want unity, from synaptic: remove/purge unity & ubuntu-desktop

the other solution is to select "classic" while logging in gdm

---

### Post by jiapei100 on 2011-05-01
Thank you so much for your prompt reply.
My problem is: unity is not automatically start now as well.
Beside a desktop with some of documentations and hard drives displayed on the background, there is nothing there at all...

I need to try to launch a terminal first, so that I can launch gnome-panel or unity from within a bash command.

Can you please give me a hand?

Cheers
Pei

> **dino99 said:**
> unity replace gnome-panel by default now
so if you dont want unity, from synaptic: remove/purge unity & ubuntu-desktop

the other solution is to select "classic" while logging in gdm

---

### Post by jiapei100 on 2011-05-01
Happened to notice that I've got exactly the same problem here at

[http://ubuntuforums.org/showthread.php?t=1700843]("http://ubuntuforums.org/showthread.php?t=1700843")


What can I do? Can I just use unity-2D? Or I've got to shift back to Gnome since my video card is ATI Mobility Radeon X1600, which seems to be too old to support compaz 3D ??


Rgds
Pei

---

### Post by jiapei100 on 2011-05-01
Happened to notice that I've got exactly the same problem here at

[http://ubuntuforums.org/showthread.php?t=1700843]("http://ubuntuforums.org/showthread.php?t=1700843")


What can I do? Can I just use unity-2D? Or I've got to shift back to Gnome since my video card is ATI Mobility Radeon X1600, which seems to be too old to support compiz 3D ??


Rgds
Pei

---

### Post by jiapei100 on 2011-05-01
Problem seems to be solved by picking up unity 2, instead of default unity, which seems require 3D support first...

Rgds

---

