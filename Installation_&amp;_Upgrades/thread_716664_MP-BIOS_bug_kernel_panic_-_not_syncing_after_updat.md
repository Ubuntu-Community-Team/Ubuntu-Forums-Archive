---
title: "MP-BIOS bug kernel panic - not syncing after updates"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by blackcoffeeblue on 2008-03-06
Greetings all,

I'm having a little trouble booting up here, thought I'd check if any of you have seen this before. I installed 7.10 Gutsy (my first distro) last night - seemed to be working fine initially. This morning I downloaded & installed the recommended updates (probably over a hundred) now I'm getting this after rebooting..

> Starting up...
[ 0.464000] MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 0.468000] Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot with apic - debug and send a report. Then try booting with the 'noapic' option.

Can anyone make sense of that? :confused: What should I do?

---

### Post by chrisccoulson on 2008-03-06
Try what it says - booting with the noapic option.

To do this, hit [ESC] as Grub loads, to bring up the Grub menu. Then press [E] to edit the default Grub entry. Use the arrow keys to select the line beginning 'kernel' and press [E] again. On the end of the line, append 'noapic'. Press [RETURN], and then press [B] to boot.

To make it permanant once you've booted, you'll have to edit your /boot/grub/menu.lst.

A [quick search]("http://www.google.co.uk/search?hl=en&q=MP-BIOS+bug%3A+8254+timer+not+connected+to+IO-APIC&meta=") on Google returns lots of results. Google is your friend ;)

---

### Post by blackcoffeeblue on 2008-03-06
Thanks mate, that worked. I'll try searching for a solution in future before I go running to the forums :lolflag: Thanks again.

---

