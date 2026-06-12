---
title: "Failed to install Fiesty"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by cnctech77 on 2007-04-26
Every time I try to install ununtu from the liveCD, it fails, I cannot even get into the installation gui. It shows this error message "... keneral panic" and with "...native_apic_write_atomic...", some times "io_apic_set_pci_routing".  Any idea about these?

My pc is a normal P4 hp computer, only thing is that my pc has two graphics cards, integrated intel card and a pci nvidia card.

---

### Post by Flendon on 2007-04-29
Have you tried turning off ACPI support? Try hitting F6 and adding acpi=off to the list of commands. I noticed that in the help documents while digging for a fix for another install issue.

---

