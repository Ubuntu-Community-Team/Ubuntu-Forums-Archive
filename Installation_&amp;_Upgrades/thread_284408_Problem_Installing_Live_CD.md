---
title: "Problem Installing Live CD"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by mfox04 on 2006-10-25
I am attempting to install Ubuntu 6.011 on an HP laptop, and the installation hangs up immediately after the opening music and the screen turns deep burgundy color (the Ubuntu desktop?). I have seen other postings from people who hang up at a similar place, and I have not understood the suggestions that have been made. For instance, Kateikyoushi has helpfully written:

Could try safe video mode just in case or to boot with these options.

Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

But I do not know exactly what this means, or how to execute this in the startup process. Thanks to anyone who can help me troubleshoot.

---

### Post by bg1256 on 2006-10-25
Are you sure it's not just taking awhile to boot?  It takes 2-3 minutes to boot a live CD on my laptop, though it's not overwhelmingly powerful.

---

### Post by mfox04 on 2006-10-25
No, I have tried this several times, and it proceeds exactly the same way: the installation process begins, files are installed, the Ubuntu music starts, and then a window comes up in the middle of the screen, and then it hangs up. I tried using an alternate disk image from the Ubuntu site, and got exactly the same results.

---

### Post by Kateikyoushi on 2006-10-25
When you boot from the live cd you will see this screen [(LINK)]("http://shots.osdir.com/slideshows/original.php?release=738&slide=1"), here you can select safe video mode for installation or enter boot options by pressing F6, just type those commands and press enter, one at a time you can figure out which one you need.
Hopefully the install will proceed in safe video mode.

---

### Post by mfox04 on 2006-10-25
So when I make the selection for the safe graphics mode, will there be a prompt where I should enter the commands? I assume I only try one at a time, and enter them as written. I am very new to this, and greatly appreciate the help.

---

### Post by Kateikyoushi on 2006-10-25
First just try the safe video mode by selecting it with the arrow keys and hit enter. 
If it doesn't work then at the menu what you see in the  image press F6 as the bottom line suggests. Then you get a prompt where you can enter those boot options.

---

### Post by mfox04 on 2006-10-25
Enter them exactly as written?

---

