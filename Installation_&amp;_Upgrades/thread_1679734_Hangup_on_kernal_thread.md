---
title: "Hangup on kernal thread"
date: 2011-02-01
forum: Installation &amp; Upgrades
---

### Post by sovi3t1 on 2011-02-01
Installed Ubuntu 10 using wubi. Had trouble initially installing because it got hungup at 'kernal thread' on boot.  I hit f6 twice and selected the 'acpi workaround' at which point i was able to boot to the ubuntu desktop and complete the installation.  I restarted the computer, and it gives me the option to boot to win or ubuntu.  when i select ubuntu it brings me to a grub screen to select which version i want to boot.  When i select any of the versions they get hung on that 'kernal thread' string.  Also it does not let me hit f6 to do the workaround again.  This is confusing because I already booted into ubuntu and was able to use it.  Current machine is a Toshiba Satellite laptop with i5 processor and Windows 7.

---

### Post by bcbc on 2011-02-01
> **sovi3t1 said:**
> Installed Ubuntu 10 using wubi. Had trouble initially installing because it got hungup at 'kernal thread' on boot.  I hit f6 twice and selected the 'acpi workaround' at which point i was able to boot to the ubuntu desktop and complete the installation.  I restarted the computer, and it gives me the option to boot to win or ubuntu.  when i select ubuntu it brings me to a grub screen to select which version i want to boot.  When i select any of the versions they get hung on that 'kernal thread' string.  Also it does not let me hit f6 to do the workaround again.  This is confusing because I already booted into ubuntu and was able to use it.  Current machine is a Toshiba Satellite laptop with i5 processor and Windows 7.

You have to supply the acpi workaround every time you boot until you either fix the problem or you make the workaround permanent. 

So hit 'e' on the first menu entry, then add the workaround (for wubi installs, the acpi workaround adds "acpi=off noapic nolapic" to your boot options, so you'd change "quiet splash" to "quiet splash acpi=off noapic nolapic".)

Search on your computer brand/model (or mention it here) for fixes, but usually updating the latest bios should resolve these issues. If you can't fix it, then you need to make the workarounds permanent as described here (ignore the fact that it says "(not for wubi)" - it's the same): [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by sovi3t1 on 2011-02-01
Success!  Thanks so much for the assistance.

---

