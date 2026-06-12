---
title: "Why automatic updates break properly working things?"
date: 2008-07-16
forum: Installation &amp; Upgrades
---

### Post by dr_agon on 2008-07-16
I become more and more upset with updates of Hardy.
I am relatively new to Linux, using it extensively for slightly more than one year. I had a nice configured system couple of months ago. I kept it up to date installing all security and recommended updates (and updates of some backports applications, too). 
After the vacations I installed a bunch of updates and after reboot my XWindows started in failsafe video mode. Restoring the saved xorg.conf did not help. I managed to make it work in proper resolution, but advanced desktop effects doesn't work any more. Previously I had to enable proprietary nvidia driver, but now I don't have this option at all, and I have no time to deal with it now. 
Couple of days ago I found out that I cannot access NTFS partition on my drive. Well, I have Windows installed, so it wasn't a disaster, but a very unpleasant surprise. Now I figured out I had to modify permission while mounting it - perhaps for a security reason some additional restrictions were implemented, but I wasn't aware of this before installing an update. I even don't know if it was update to the NTFS driver, fuse module or something else which caused my problem.
After the first problem when upgrading the kernel made my VirtualBox installation unusable, I quickly browse the list of pending updates before applying them, just to know what to expect, but it is impossible for me to avoid such pitfalls as described above.
I could provide couple of more examples. 
Of course the problems I described can be solved, but this requires time, (for me - lots of time, as I'm not a Linux expert). That's why I don't like Ubuntu as much as before. Maybe I will switch to something older, but more stable, and manually install the newest versions of the few application I need?
I got the feeling, that all effort of making Ubuntu "user friendly" and more popular caused too fast deploying of updates and new releases without enough beta testing. I use Ubuntu both at work (7.04) and at home (8.04). I need something more from it than browse internet and play DVD, so I value stability and possibility of customization more than plug-and-play. Maybe Ubuntu was good for me as a first distro to learn, but I need something else now? This is sad, because I liked some features in it, and most of all, I found all the Ubuntu community most helpful in my early Linux days.
Enough complaints.

I wrote it to draw attention to the problem of updates breaking existing, properly working configuration. 
I miss two things.
[LIST=1]
[*]a log of updates to help track what caused the problem, because it may not be the most recent download;
[*]possibility to revert the system to the state before installing series of updates, without thinking which of them broke the system, similar to Windows System Restore.
[/LIST]

That's all, folks.

---

