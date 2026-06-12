---
title: "New Video Card and now Lockups : ("
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by mark2741 on 2007-06-18
This are 3 major variables to my issue and I will explain each so I hope it all makes sense:

Over the weekend I spent a lot of time trying to get virtualization going. After both VirtualBox and VMware Server throwing errors when trying to install Windows XP Pro into them (but not Damn Small Linux) I figured out the problem was due to the ACPI error that is well documented in these forums. I had been living with it for the few weeks I'd been running Feisty without issue other than virtualization. 

So I went in and did the acpi=off fix in the boot options per a previous post I found on the subject. Once I did that the system booted without the APIC Timer error like it did before, and now virtualization works like a champ....but now my system freezes/locks up whenever I run the virtual machine for too long and also whenever I do anything processor intensive (so it's not just restricted to the virtualization program).

I *think* this is due to this: on Saturday I installed a new video card - an evga GeForce 7600GS. I had an onboard ATI express 200M and it couldn't run nexuiz or anything so I went with an NVidia card and am happy with it, but I think it draws too much power so I just bought a new power supply and everything seems okay for now. I bought an Antec TruePower Trio 430w supply. Previously it was a 300w no-name (came with the PC - an HP m7470n) and I don't think could handle the tv tuner, multiple usb/firewire and SATA drive, along with the upgraded PCI-E video card I just installed.

One more thing I just noticed...I can't power off Ubuntu! I assume this is because ACPI is turned off? So when I shutdown Ubuntu the shutdown process completes but just sits there. Progress bar is at zero (no fill) but I have to use the switch on the PC to shutdown. Is this okay to do?

So my questions are:

a. If my PC still locks up, what should I look for causing the problem?
b. Is it okay to turn off the PC manually via the shutdown?

---

