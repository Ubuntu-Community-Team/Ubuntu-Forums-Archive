---
title: "2 Issues with fresh Natty Narwahk install"
date: 2011-05-07
forum: Installation &amp; Upgrades
---

### Post by raidensix on 2011-05-07
Hi,

I did a fresh install of Natty Narwhal and have the following issues:

1. Wake/Resume from suspend does not work. The fans start up and that's pretty much it. The screen just goes to power save mode.
This did not happen with Meerkat.

2. The sound is always muted on login. I get the drum roll but then then the sound is set to mute.

Shuttle SN78SH7
3.0 GHz AMD Phenom II
2x2GB DDR2-800 RAM

Any help appreciated.

---

### Post by MAFoElffen on 2011-05-07
> **raidensix said:**
> Hi,

I did a fresh install of Natty Narwhal and have the following issues:

1. Wake/Resume from suspend does not work. The fans start up and that's pretty much it. The screen just goes to power save mode.
This did not happen with Meerkat.

2. The sound is always muted on login. I get the drum roll but then then the sound is set to mute.

Shuttle SN78SH7
3.0 GHz AMD Phenom II
2x2GB DDR2-800 RAM

Any help appreciated.
I don't know for sure on the sound, but adding " 
```

acpi_osi="Linux"

```to the kernel boot line.. In a terminal:
     ```

     cd/etc/default sudo gedit grub

```Edit the line "GRUB_CMDLINE_LINUX_DEFAULT".  Add your new options, for example:
     ```

     GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vga=771 acpi_osi=/"Linux/" "

```Now in a terminal run
     [code]
     sudo update-grub
[code]

May fix both your problems.  There is an open LP bug on this you should subscribe to.

---

### Post by raidensix on 2011-05-08
I tried that and both problems are still there. Anything else you can suggest?

---

