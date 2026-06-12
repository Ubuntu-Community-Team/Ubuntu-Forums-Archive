---
title: "My installation barely starts"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by AngusM on 2007-03-02
I have an 800MHz Celeron, and I've been trying to install 6.06. Unfortunately, I don't get much farther than the bootup menu. What happens is a status screen comes up and lists various tasks it's performing, then spends a long time on "configurating drivers" or something like that. When I look at the screen again, it's completely blank except for a blinking cursor at the top left, and it stays that way. I've also tried installing in safe graphics mode, but only with the same effect. Where do I start?

---

### Post by Kateikyoushi on 2007-03-02
How much memory do you have in that machine ?

---

### Post by AngusM on 2007-03-02
512Mb w/1Mb reserved for the video

---

### Post by Kateikyoushi on 2007-03-02
Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by AngusM on 2007-03-02
I was rather confused by your instructions. I've never known kernel parameters to be specified in multi-line format like that, and this case was no exception. So I tried putting them all on one line, and I was given a few errors. I think they were about irqroute and acpi as options.
     In the end, it had the same effect: freezing on a blank text screen.

---

### Post by Kateikyoushi on 2007-03-03
Sorry, I did not mean to enter all of them the same time.
In this case all I can recommend is to give the alternate CD a try.

---

