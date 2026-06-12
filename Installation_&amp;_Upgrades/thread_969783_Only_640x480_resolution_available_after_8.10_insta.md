---
title: "Only 640x480 resolution available after 8.10 install"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by ruby644 on 2008-11-03
Hi,
I have volunteered to install Ubuntu/Edubuntu on 2 donated machines for my sons school.
The 2 machines are Dell Optiplex GX260 towers which I believe have Intel 845G/GL integrated graphics cards.
These are driving Dell E772P CRT monitors.
After multiple attempts at installing 8.10 I finally managed to get  it installed by using safe graphics mode and then installing Edubuntu successfully.
However both machines now have only 640x480 resolution and there are no other resolutions available and the monitor is shown as "unknown".
How can I get higher resolutions to display?
Any help will have to be in beginner mode as I am an absolute novice with ubuntu!
Thanks.

Changed the BIOS settings for the video memory from 1MB to 8MB and Ubuntu now has 3 screen resolutions!

---

### Post by taurus on 2008-11-03
What happens if you reconfigure the X server again?  From a terminal, run

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Once it's done, restart X with <Ctrl><Alt>Backspace.

---

### Post by openBA on 2008-11-03
You should maybe consider Ubuntu/Edubuntu 8.04 for that purpose. After a week with 8.10, I consider it as beta release.

---

### Post by ruby644 on 2008-11-03
Screen went black and had to pull plug to get a restart and still the same resolution problem.

---

### Post by ruby644 on 2008-11-05
Any other suggestions before I give up and recommend the school go with another system?
I already spent hours installing 8.10 and trying 8.04 is a bridge too far!
8.10 and Edubuntu seem to be running OK it's just at the wrong screen resolution.

---

### Post by Alajjana on 2008-11-05
> **ruby644 said:**
> Any other suggestions before I give up and recommend the school go with another system?
I already spent hours installing 8.10 and trying 8.04 is a bridge too far!
8.10 and Edubuntu seem to be running OK it's just at the wrong screen resolution.

*I am not an expert so be wary...

My install failed horribly as i am not a pro but some of my problems were fixed after if found the xorg log file. The system logs can be found off the main menu>>System>>admin>>system...

I found out that my install (among other things) didnt install GLX or DRI (whatever they are).

---

