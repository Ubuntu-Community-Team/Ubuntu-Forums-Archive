---
title: "lcd monitor, adding ddr, hang video"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by truth_forum on 2007-01-24
newbie here. any hardware issues on lcd monitor? I am planning to change my CRT monitor to lcd (sale) am using 6.6 ubuntu lts with 9250 gecube ati radeon videocard (128mb).  

p.s. 

by the way, i recently added another 512 ddr (2 x 512) to my memory and it somehow affected my video. sometimes the mouse hangs or when i change user account the monitor's picture is affected- white stripes appear. 

is this software issue, driver issue or do i need to install another fan?  research suggest that the issue may be thermal. ..  

thanks.

---

### Post by Rhubarb on 2007-01-24
I doubt it'd be the LCD monitor at fault.

The 1st thing I'd recommend you do is to check to see if the new RAM you bought runs at the same speed your original RAM runs at.
If they're different speeds you should go into the BIOS (press Esc / Del / F2 / F10 / F11 / F12 on startup) and find a place where you can change the default RAM timings and set that to a slower speed.

You could also try pulling out your original 512MB RAM stick, and move your new stick of RAM into the original's slot.  Then power up your computer to see if it runs stably.
If it doesn't run stably, then it's either a RAM timing issue, or you've some bad RAM - try to take it back to the shop where you bought it from.

There are a few more things you can try to troubleshoot, but I don't want to go into them before you've tried swapping the RAM around / configuring the BIOS.

---

