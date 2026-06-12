---
title: "Cannot install anything on Clamshell iBook"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by MikeRapin on 2007-03-10
I saw this thread after searching for a while: [http://ubuntuforums.org/showthread.php?t=201438](http://ubuntuforums.org/showthread.php?t=201438)
but there was no solution at all, and I am having the exact same issue, but I have a 10GB HD instead of a 20GB. 

I've tried Ubuntu 6.06 and 6.10, and Xubuntu 6.10 and the alternate CD with no success and am getting the exact same error. 

Does anyone have any idea on how I can fix this error?

---

### Post by Kateikyoushi on 2007-03-11
Boot from the cd at the menu press F6 then press E to edit the startupline and add add these options to the end of the line.

noapic
nolapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
nolapic
framebuffer=false
linux irqpoll

This might help.

---

### Post by MikeRapin on 2007-03-11
I booted into my Ubuntu 6.10 cd and pressing F6 didn't do anything at the boot menu, but I tried adding everything you mentioned in the boot command like this:

```
live noapic nolapic pci=irqroute pci=noacpi acpi=off pci=acpi nolapic framebuffer=false linux irqpoll
```

but that didn't change anything, and I got 3 errors on top of my original error saying that PCI didn't know what a few of those commands were.

---

### Post by MikeRapin on 2007-03-12
Can anyone offer help on this issue?

---

