---
title: "Can't install - just black screen"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by dreamer81 on 2007-12-18
I insert the ubuntu desktop disk
A menu pops up and I select the upper one that says "install & start ubuntu"

It says kernel loading

and then my screen just goes black...

any idea whats wrong???

i tried both the 32 bit and 64 bit...

my graphics card is a 8800GTS

---

### Post by omegamike3 on 2007-12-18
You can try checking the disk, just in case the burn went wrong. You can try the safe graphics mode. Or, if you're not needing to use the 'live' portion of the disk, you could use the alternative disk which I've had the most luck with. It's isn't pretty as it's just a simple text interface, but it's still simple and gets the job done. :)

---

### Post by dreamer81 on 2007-12-18
where do I get the alternative disk?

EDIT:
nevermind i found it :) thanx, I will try that

---

### Post by dreamer81 on 2007-12-18
Ok i got it installed with the alternate CD...

but once I launch ubuntu, it gives me a black screen as well.

I can fine log in to recovery mode, and has access to the prompt.

I suspect it being my MSI motherboard... and ACPI?

---

### Post by dabl on 2007-12-20
No, it's the 8800GTS card.  The "black screen on boot" problem is fairly well documented. For the moment (i.e. until a better fix is found) just boot "recovery mode", then Ctrl-D at the prompt, and get your GUI login that way.  :(

---

### Post by dabl on 2007-12-21
Actually, here are 2 further tidbits:

1. Using the beta 169.04 driver on my Gutsy 64-bit system, my 8800GTS 320 works when I remove "quiet" from the kernel boot line in /boot/grub/menu.lst.  I figured that out after observing that it works correctly when booting through recovery mode, which does not use the "quiet" or the "splash" options in the kernel boot line.  I don't have a "vga=" option in there either, although I'm going to play with it some more and see what else I can get it to do.

2. Nvidia just released the new driver -- I'll be installing it tonight:

[http://www.nvidia.com/object/linux_display_amd64_169.07.html](http://www.nvidia.com/object/linux_display_amd64_169.07.html)

:)

---

