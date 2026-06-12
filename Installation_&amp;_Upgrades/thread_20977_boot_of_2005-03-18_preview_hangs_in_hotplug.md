---
title: "boot of 2005-03-18 preview hangs in hotplug"
date: 2005-03-19
forum: Installation &amp; Upgrades
---

### Post by nkiesel on 2005-03-19
Hi,

I installed the preview (from the torrent) and everything worked fine. However, on reboot it hangs in "Starting hotplug subsystem...".

I also tried to boot with "noapic acpi=off" and after disconnecting all devices (CD-Rom), but no change.

Hardware is a old Gateway Solo 3300 notebook.

I also tried the Array 5, but this hang too (and I had to install using acpi=off, which was not needed with the 2005-03-18 preview)

The machine is dead in this stage, no keys but poweroff do anything.

---

### Post by dmallery on 2005-03-20
hi

i have the same problem with a supermicro 370de6 mobo.  neither warty nor hoary can get past this point in the install.  This is an almost server mobo with twin p3 1000s.

this mobo will run knoppix.  i too have tried all the permutations (i think)  so the problem lies somewhere else.  note that it also occurs with either 2.4 or 2.6.

my machine will allow me to power down, however.

i post this everywhere i can think of, but to no avail.  i tried the irc, but they just told me to try the boot params.

lost in new mexico...

dave

---

### Post by nbcthreat on 2005-04-08
I have the same problem sporadically on a Asus P4 mobo.

---

### Post by c_dog on 2005-04-08
There was a few APIC and APM problems with Hoary a few weeks ago. There's been quite a few problems that have gone away even in the last week. The Synaptic Touch Pad on my Compaq laptop stopped freaking out after a Speedstep finally after the last few weeks with the 040705-3 release. Might be a good time to try booting a newer Hoary.

---

