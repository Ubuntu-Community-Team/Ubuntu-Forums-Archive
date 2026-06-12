---
title: "hardy acpi cpu consumption and buggy ondemand freqscale"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by urbanusta on 2008-05-02
Hi All:

Just upgraded to Hardy from Feisty on a P4 3.2GHz 2GB HP zd7000 i686 and experiencing problems mostly with acpi. After the upgrade, I noticed my fans running overtime (which is usual after every time I upgrade). However, fixing cpufreq scaling did not work as expected (p4_clockmod). With ondemand governor, switch to the lowest clock freq. (400MHz) happens when no load exists, however, system powers off hard (similar to CPU therm. protection) first time CPU hits 100%.

The second thing is even without cpufreq. scaling (module not loaded at all), I have a cooler system (CPU at 40 deg. celcius @ 3.2GHz vs. CPU at 55 deg. celcius @ 3.2GHz) when I boot hardy (in recovery mode with root shell) with 2.6.22-14 kernel instead of 2.6.24-16. No abnormal CPU consumption visible from ps aux, but I clearly hear fans speeding up and down with changing load. Problem goes away when I boot 2.6.24-16 with acpi=off

Anyone with similar experience? Thanks.

---

