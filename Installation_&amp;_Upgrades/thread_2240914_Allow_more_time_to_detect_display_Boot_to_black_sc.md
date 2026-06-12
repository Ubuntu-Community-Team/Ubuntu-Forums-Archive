---
title: "Allow more time to detect display? Boot to black screen"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by HP001 on 2014-08-23
Hi all,
I upgraded 12.04 lts to 1404 lts 2 weeks ago. After days with black screen issues, I can now boot and completed the upgrade but still encount one problem:
- Every time my PC is cold (temperature) the boot process is ok. Display not fully detected but GUI is visible and I can see bios flash screen.
- Second and all successive boots give black screen. The monitor displays: 'No signal detected' and turns itself off.
This was never happen with 12.04 lts. Now I can use 14.04 lts every morning or after 5-6 hrs for the next usage.

I have Radeon 7950 dual dvi, relatively new MSI mainboard z77 chipset, monitor Benq 16:9 full hd, now connect to only one monitor/display to ease the debug process.

Can someone help me to point out some threads about delaying the monitor detection or forcing gui even no monitor had been detected?

Please let me know if you need more info about my hardware. Thank you.

-----------
xrandr fails to get info about the display. Currently use 1920x1080.
lshw returns: display0 Unclaimed

---

### Post by HP001 on 2014-08-25
No suggestions?

I am currently use the default ubuntu graphical driver.
Before I try to switch to another graphical driver, like AMD one, if the screen is not coming up, is it possible to switch back?
It looks like that Ubuntu grub also modify the bios sequence to start up the ubuntu first and I cannot see the bios screen during reboot.

Currently it helps when i added Ctrl+Alt+Backspace to 'reboot' the unity desktop if something hang durring trying and optimilization.
 Verifying the optimization had been difficult and time consuming due I have to wait for the next day to get into the PC. Very annoying issue.

---

### Post by HP001 on 2014-09-02
Update:
Changed monitor, changed DVI cable. Looks like problem has been gone, or not repeatable.
People with driver experience also note this issue; somewhere needs a reset but not done properly.

---

