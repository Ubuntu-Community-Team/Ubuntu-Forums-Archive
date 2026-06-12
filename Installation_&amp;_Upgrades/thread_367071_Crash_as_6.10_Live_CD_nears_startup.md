---
title: "Crash as 6.10 Live CD nears startup"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by Argg on 2007-02-21
I'm trying Ubuntu for the first time today.

Burned a CD of the 6.10 Live CD for i386

Machine specs: 
Shuttle XPC SD31P with Pentium D, and if I remember right, 2 GB ram. Windows XP installed on one HD, planning to install Ubuntu to second drive.
Sapphire ATI 9800 video card.
IOGear DVI KVM switch connecting this machine and a Mac to same Dell monitor and USB mouse and keyboard.

I get it started off the CD okay, and get the menu screen with choices like Boot from CD or Install Ubuntu and Boot from CD in safe graphics mode plus some others. Choosing either of those firs two, I get the orange progress bar first sweeping back and forth, then starting to really progress. It gets about 90% done then the logo and bar shift downwards and go to what looks like dithered 8 bit, there is a spray of little clusters of blue pixels just below the bar and below that some green and red noise draws across the bottom, shifts a bit, and then it hangs. This looks to me like it is trying to shift graphics modes and choking out.

I'd guess there is something about my hardware configuration that this version isn't compatible with. 

Take out the KVM switch from the setup and try again, maybe?

Anything else I should do?


Edit:
I tried the CD on a vanilla eMachines PC in the next room, and it worked there and finished the boot. Watching that boot-up's progress, it looks like it leaves that orange progress bar screen and starts the GUI right at the point where it hangs on my PC.

---

### Post by Kateikyoushi on 2007-02-21
Boot from the cd at the menu press F6 then start with these options

Boot: linux noapic
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false

If nothing works out try the alternate install CD's text install.

---

