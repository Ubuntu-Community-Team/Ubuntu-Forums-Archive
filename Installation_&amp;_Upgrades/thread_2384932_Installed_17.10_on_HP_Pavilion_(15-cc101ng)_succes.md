---
title: "Installed 17.10 on HP Pavilion (15-cc101ng) successfully"
date: 2018-02-14
forum: Installation &amp; Upgrades
---

### Post by tloprok on 2018-02-14
Dear community,

I just wanted to report that I have successfully installed Artful (17.10) on my new HP Pavilion (15-cc101ng).

Before installing I made the win10 partition with windows disk manager smaller.

The runtime on battery was short after the installation about 5h. Then I switched the Nvidia graphics to Intels on-chip ([FONT=courier new]sudo prime-select intel[/FONT]) and used [FONT=courier new]powertop[/FONT] and the battery runtime increased to 10h.

The touch pad is recognized very well - all gestures work. Even the built-in position sensor works, that makes flip the screen automatically. when tipping the notebook.
All function keys work also fine.

The Grub boot loader is selectable pressing F9 at boot sequence.

So hopefully this information is useful for someone, who want's to install linux on this HP.

Cya
Thomas

---

### Post by mörgæs on 2018-02-14
Thanks for posting. If you add to the [compatibility thread]("https://ubuntuforums.org/showthread.php?t=1543006") there is a better chance that people will find it.

---

