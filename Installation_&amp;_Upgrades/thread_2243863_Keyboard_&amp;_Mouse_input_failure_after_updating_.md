---
title: "Keyboard &amp; Mouse input failure after updating 14.04"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by majk2 on 2014-09-11
Everything was working great yesterday. I did the latest update for 14.04 last night and now my keyboard and mouse are not working.

I have a dual boot environment Windows7 and Ubuntu 14.04.

The problem is I can't even enter into the recovery environment to attempt a repair, as the keyboard is not recognised even at the Grub screen stage of launch. So I cannot make a selection I just have to wait for it to load Ubuntu 14.04 but once launched the keyboard and mouse are dead so cannot do anything further.

I have tried multiple reboots and swapping USB ports and keyboard mouse combinations but none work. I have even booted from my live CD and reinstalled Grub 2 from terminal and using GUI grub reinstaller, but the problem persists.

*Oh and the mouse & keyboard work fine when I boot from the live CD so it is not a hardware issue.*

Any ideas how I should solve this would be greatly appreciated.

---

### Post by majk2 on 2014-09-12
[COLOR=#444444][FONT=UbuntuRegular];) I ended up booting and holding down shift just at the end of Bios screen this takes you into the Grub window without a time limit. I had to do this a few times and finally I was able to use the down arrow for a moment that allowed me to select the advanced boot. Once there I selected an older safe boot & repair (not the most recent one as this was also faulty) once in the older safe boot and repair I was able to use repair & fix what ever the problem was. Booting normally now.[/FONT][/COLOR][COLOR=#444444][FONT=UbuntuRegular] Now I just need to sort out the screen resolution problem that also snuck in with the latest update![/FONT][/COLOR]

---

