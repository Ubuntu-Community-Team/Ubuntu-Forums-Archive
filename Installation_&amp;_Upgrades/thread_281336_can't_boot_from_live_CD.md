---
title: "can't boot from live CD"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by liveforfunnow on 2006-10-20
Ok. I've tried this a few different times, and searched the forums, but i am stuck.

i have liveCDs for both 6.06 and 6.1rc. I get the same error when trying to boot from it. the kernel loads, i select "Start LiveCD or Installer," wait, and the orangeish backgroud appears. i hear the "welcome" sound, but the splash picture (the rectangular icon with the ubuntu name and logo) appears distorted, with vertical lines corrupting it. boot stalls here; the compy is frozen. my only choice is to hard-reboot and return to winblows. Help!

if it is of relevance, i have a 7800GT nvidia, 1gb corsair mem, and 2 sata2 hard drives: a 250GB with XP installed, and a 400GB formatted NTFS, but blank otherwise. i built this machine specifically for Ubuntu, but i can't install. 

any advice anyone has would be much appreciated.

thanks!

---

### Post by lloyd_b on 2006-10-20
Suggestion:  Use the "alternate" install CD rather than the LiveCd version.

The alternate CD uses a text-based installer that seems to be somewhat more robust than the LiveCD.

Lloyd B.

---

### Post by Kateikyoushi on 2006-10-21
Did you try the safe video mode ? If it doesn't work fall back on the alternate install cd.

---

### Post by lfloyd on 2006-10-21
in boot options try live acpi=off

---

### Post by Kateikyoushi on 2006-10-21
A few more boot options in case that is still not enough.

At boot menu prees F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by liveforfunnow on 2006-10-22
thanks all. a livecd safe graphical mode installation  worked!

---

