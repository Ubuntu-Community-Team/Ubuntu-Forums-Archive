---
title: "How to probe for RAM before installing?"
date: 2008-04-08
forum: Installation &amp; Upgrades
---

### Post by SubGothius on 2008-04-08
I have been given an old Toshiba Satellite 1605CDS laptop that I have been hotrodding like the old jalopy she is -- gave it a K6-2+ 550 w/ some Nano Diamond thermal grease (so it might OC to 600!), a DVD/CD-R combo drive, and a 256MB RAM stick -- on which I've been planning to install Xubuntu Gutsy (or maybe straight to Hardy by the time I'm done!).

The new amount of system RAM posts in the BIOS as 287MB (31MB on-mobo + 256MB module -- seems to be 1MB of on-board RAM absent somehow, maybe used for VRAM), but the Alternate installer complains of having less than 32MB of RAM and won't get very far if I try to press ahead with a low-mem install anyway, seems to halt after the installer module-loading stage

If I run the memory test item from the boot screen, it initially sees only the 31MB onboard RAM, but selecting the tester's memory probe config item "finds" the other 256MB and runs the memory tests normally from there; however, the only way to exit the memory test is to reboot, so I can't just exit to resume installing with the full memory being found this way.

I have read that Win98 sees a 256MB RAM stick on these machines w/ no problem, but Win2k and up don't, possibly due to some issue related to an absent/nonstandard ACPI vs. the Win2k HAL. Is there some command I could run in an Alt-F2 console to probe for more RAM before starting the installer, or some kernel argument I could specify as a boot option? I have tried 'noacpi' and 'acpi=off' already to no avail (should those go before or after the last presupplied bootvar of '--'?).

---

### Post by SubGothius on 2008-04-09
Bump?

---

### Post by Claus7 on 2008-04-11
Hello,

you can do the following:

[LIST]
[*]sudo lshw

[*]sudo lshw-gtk 
[*](after you have installed it from synaptic)

[*]sudo dmidecode

[*]dmesg | grep -i memory

[*]or you can go to your bios and see...
[/LIST]

Unfortunately in my case I cannot see the frequency of my memory...

Hope this helped,
Regards!

---

