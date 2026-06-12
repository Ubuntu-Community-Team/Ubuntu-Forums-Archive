---
title: "Random Freezes on 64-bit Jaunty"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chris4amd on 2009-04-21
After a random amount of time, my computer freezes up.  Attempting to restart X, switch virtual terminals, or perform a soft reboot all yield nothing.  I am running a fully up to date 64-bit Ubuntu 9.04.  

My processor and motherboard temperatures are nominal.  I have attached my DMESG and LSPCI outputs.  Any thoughts?

---

### Post by manuelb on 2009-04-21
I read about some problems yesterday, raising from an Ati SB600 Usb controller bug. There was some fuss about the ATA controller too, look at this from your **dmesg**:

```

[    2.188015] ata1: softreset failed (device not ready)
[    2.188075] ata1: failed due to HW bug, retry pmp=0

```

This relates to the ATA controller.. i'll try to find what i was reading yesterday, in the meantime you could search about it on the Launchpad.

---

### Post by manuelb on 2009-04-21
So i was reading this at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350531]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/350531"), but although older, there is another one here too at [https://bugs.launchpad.net/fedora/+source/linux/+bug/285392]("https://bugs.launchpad.net/fedora/+source/linux/+bug/285392")

---

### Post by hotweiss on 2009-04-21
I have had one freeze with the 64-bit Jaunty too.

---

### Post by Enicko on 2009-04-21
Mine started out freezy a few weeks ago.  Over the course of the first couple days that time I came to grips with the fact that I would not have 3d on my ATI V5700 card until after the final release.  About the time I stopped dinking with the drivers, my freeze up issues stopped.

I also had to hard exit with the power button several times, but that seems to have cleared up gradually as well.

I had random freezing with my hardy system at home last year, over time it's completely (knocking on wooden table) stopped as well.

It did rattle me a bit though.

---

### Post by hotweiss on 2009-04-22
> **Enicko said:**
> Mine started out freezy a few weeks ago.  Over the course of the first couple days that time I came to grips with the fact that I would not have 3d on my ATI V5700 card until after the final release.  About the time I stopped dinking with the drivers, my freeze up issues stopped.

I also had to hard exit with the power button several times, but that seems to have cleared up gradually as well.

I had random freezing with my hardy system at home last year, over time it's completely (knocking on wooden table) stopped as well.

It did rattle me a bit though.

OK, I just had my second freeze now. Although I am not using the standard Ubuntu Nvidia driviers, I am using 180.51, possibly they are the cause of my problem.

---

### Post by fixture on 2009-04-22
k, this is bugging the sh*t out of me! Jaunty has gotten progressively less stable since Feb!

I am on a Thinkpad X61 (generic intel hardware, integrated graphics) running 64bit, and have been grappling with freezes for the last couple weeks.

1) this is not a kernel freeze, you can move the mouse, but no keyboard responses, i.e., caps lock has no response. When I ssh into the frozen machine, you can login, htop shows you that nothing suspicious is going on at all. No bad cpu usage, no bad mem usage, etc.

2) but the onset of these freezes on powertop does seem to be associated with random CPU frequency and p-state hikes, i.e., out of the god damn blue, with no application running, CPU runs like hell in powertop and burns lap

3) this is not kernel specific, I have using bleeding edge kernels from ubuntu and compiled 2.6.29, problem persist

4) I theorize problem is in the Xorg drivers, but the bleeding edge intel xorg drivers freezes as well

5) the sata controller does seem to have suspicious activities sometimes, though this is not necessarily connected to freezes. The only time I noticed sata problems, the sata problem preceded the freeze by about 20 mins.

kernel log below, 

Apr 22 00:35:54 xerox-L kernel: [  185.318021] ata1.00: configured for UDMA/133
Apr 22 00:35:54 xerox-L kernel: [  185.318031] ata1: EH complete
Apr 22 00:35:54 xerox-L kernel: [  185.325636] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:35:54 xerox-L kernel: [  185.331453] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:35:54 xerox-L kernel: [  185.331459] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:35:54 xerox-L kernel: [  185.358675] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:35:59 xerox-L kernel: [  189.975183] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 22 00:36:00 xerox-L kernel: [  191.417034] ata1.00: configured for UDMA/133
Apr 22 00:36:00 xerox-L kernel: [  191.417047] ata1: EH complete
Apr 22 00:36:00 xerox-L kernel: [  191.422879] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:36:00 xerox-L kernel: [  191.422928] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:36:00 xerox-L kernel: [  191.422933] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:36:00 xerox-L kernel: [  191.422995] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:37:48 xerox-L kernel: [  298.789689] ath5k phy0: noise floor calibration timeout (2412MHz)
Apr 22 00:38:25 xerox-L kernel: [  335.494013] ata1.00: configured for UDMA/133
Apr 22 00:38:25 xerox-L kernel: [  335.494023] ata1: EH complete
Apr 22 00:38:25 xerox-L kernel: [  335.511046] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:38:25 xerox-L kernel: [  335.516190] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:38:25 xerox-L kernel: [  335.516197] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:38:25 xerox-L kernel: [  335.529125] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:38:28 xerox-L kernel: [  339.187032] ata1.00: configured for UDMA/133
Apr 22 00:38:28 xerox-L kernel: [  339.187044] ata1: EH complete
Apr 22 00:38:28 xerox-L kernel: [  339.199555] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:38:28 xerox-L kernel: [  339.206276] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:38:28 xerox-L kernel: [  339.206282] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:38:28 xerox-L kernel: [  339.215101] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:38:31 xerox-L kernel: [  341.502909] ata1.00: configured for UDMA/133
Apr 22 00:38:31 xerox-L kernel: [  341.502916] ata1: EH complete
Apr 22 00:38:31 xerox-L kernel: [  341.508471] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:38:31 xerox-L kernel: [  341.512301] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:38:31 xerox-L kernel: [  341.512304] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:38:31 xerox-L kernel: [  341.556081] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:38:34 xerox-L kernel: [  345.267326] ata1.00: configured for UDMA/133
Apr 22 00:38:34 xerox-L kernel: [  345.267338] ata1: EH complete
Apr 22 00:38:34 xerox-L kernel: [  345.284603] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:38:34 xerox-L kernel: [  345.295800] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:38:34 xerox-L kernel: [  345.295807] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:38:34 xerox-L kernel: [  345.307869] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:40:56 xerox-L kernel: [  487.033051] ata1.00: configured for UDMA/133
Apr 22 00:40:56 xerox-L kernel: [  487.033065] ata1: EH complete
Apr 22 00:40:56 xerox-L kernel: [  487.045445] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:40:56 xerox-L kernel: [  487.050380] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:40:56 xerox-L kernel: [  487.050386] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:40:56 xerox-L kernel: [  487.065489] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:00 xerox-L kernel: [  489.252745] ata1.00: configured for UDMA/133
Apr 22 00:41:00 xerox-L kernel: [  489.252752] ata1: EH complete
Apr 22 00:41:00 xerox-L kernel: [  489.266939] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:00 xerox-L kernel: [  489.272209] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:00 xerox-L kernel: [  489.272213] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:00 xerox-L kernel: [  489.284269] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:00 xerox-L kernel: [  489.449744] ata1.00: configured for UDMA/133
Apr 22 00:41:00 xerox-L kernel: [  489.449750] ata1: EH complete
Apr 22 00:41:00 xerox-L kernel: [  489.462008] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:01 xerox-L kernel: [  489.478664] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:01 xerox-L kernel: [  489.478670] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:01 xerox-L kernel: [  489.500273] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:02 xerox-L kernel: [  491.865083] ata1.00: configured for UDMA/133
Apr 22 00:41:02 xerox-L kernel: [  491.865089] ata1: EH complete
Apr 22 00:41:02 xerox-L kernel: [  491.878373] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:02 xerox-L kernel: [  491.886530] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:02 xerox-L kernel: [  491.886533] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:02 xerox-L kernel: [  491.903725] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:03 xerox-L kernel: [  493.281747] ata1.00: configured for UDMA/133
Apr 22 00:41:03 xerox-L kernel: [  493.281752] ata1: EH complete
Apr 22 00:41:03 xerox-L kernel: [  493.288228] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:03 xerox-L kernel: [  493.292603] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:03 xerox-L kernel: [  493.292607] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:03 xerox-L kernel: [  493.318400] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:07 xerox-L kernel: [  495.806402] ata1.00: configured for UDMA/133
Apr 22 00:41:07 xerox-L kernel: [  495.806409] ata1: EH complete
Apr 22 00:41:07 xerox-L kernel: [  495.809172] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:07 xerox-L kernel: [  495.817535] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:07 xerox-L kernel: [  495.817539] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:07 xerox-L kernel: [  495.833494] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:08 xerox-L kernel: [  495.895200] ata1.00: configured for UDMA/133
Apr 22 00:41:08 xerox-L kernel: [  495.895208] ata1: EH complete
Apr 22 00:41:08 xerox-L kernel: [  495.906842] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:08 xerox-L kernel: [  495.919957] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:08 xerox-L kernel: [  495.919962] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:08 xerox-L kernel: [  495.940290] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:09 xerox-L kernel: [  499.333991] ata1.00: configured for UDMA/133
Apr 22 00:41:09 xerox-L kernel: [  499.334002] ata1: EH complete
Apr 22 00:41:09 xerox-L kernel: [  499.337788] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:09 xerox-L kernel: [  499.343193] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:09 xerox-L kernel: [  499.343200] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:09 xerox-L kernel: [  499.370015] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:25 xerox-L kernel: [  635.639478] ata1.00: configured for UDMA/133
Apr 22 00:43:25 xerox-L kernel: [  635.639493] ata1: EH complete
Apr 22 00:43:25 xerox-L kernel: [  635.653657] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:25 xerox-L kernel: [  635.670254] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:25 xerox-L kernel: [  635.670261] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:25 xerox-L kernel: [  635.678385] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:29 xerox-L kernel: [  639.321723] ata1.00: configured for UDMA/133
Apr 22 00:43:29 xerox-L kernel: [  639.321729] ata1: EH complete
Apr 22 00:43:29 xerox-L kernel: [  639.323301] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:29 xerox-L kernel: [  639.338739] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:29 xerox-L kernel: [  639.338742] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:29 xerox-L kernel: [  639.350437] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:29 xerox-L kernel: [  639.397779] ata1.00: configured for UDMA/133
Apr 22 00:43:29 xerox-L kernel: [  639.397785] ata1: EH complete
Apr 22 00:43:29 xerox-L kernel: [  639.409217] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:29 xerox-L kernel: [  639.410103] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:29 xerox-L kernel: [  639.410106] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:29 xerox-L kernel: [  639.420802] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:32 xerox-L kernel: [  642.132855] ata1.00: configured for UDMA/133
Apr 22 00:43:32 xerox-L kernel: [  642.132861] ata1: EH complete
Apr 22 00:43:33 xerox-L kernel: [  642.137299] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:33 xerox-L kernel: [  642.138987] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:34 xerox-L kernel: [  642.138990] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:34 xerox-L kernel: [  642.152870] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:34 xerox-L kernel: [  642.466240] ata1.00: configured for UDMA/133
Apr 22 00:43:34 xerox-L kernel: [  642.466246] ata1: EH complete
Apr 22 00:43:34 xerox-L kernel: [  642.495030] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:34 xerox-L kernel: [  642.513595] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:34 xerox-L kernel: [  642.513599] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:34 xerox-L kernel: [  642.541438] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:35 xerox-L kernel: [  645.528649] ata1.00: configured for UDMA/133
Apr 22 00:43:35 xerox-L kernel: [  645.528655] ata1: EH complete
Apr 22 00:43:36 xerox-L kernel: [  645.534336] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:36 xerox-L kernel: [  645.536388] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:36 xerox-L kernel: [  645.536391] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:36 xerox-L kernel: [  645.548283] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:36 xerox-L kernel: [  645.898521] ata1.00: configured for UDMA/133
Apr 22 00:43:36 xerox-L kernel: [  645.898527] ata1: EH complete
Apr 22 00:43:36 xerox-L kernel: [  645.902121] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:36 xerox-L kernel: [  645.916506] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:37 xerox-L kernel: [  645.916509] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:37 xerox-L kernel: [  645.931293] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:37 xerox-L kernel: [  646.007286] ata1.00: configured for UDMA/133
Apr 22 00:43:37 xerox-L kernel: [  646.007293] ata1: EH complete
Apr 22 00:43:37 xerox-L kernel: [  646.026446] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:37 xerox-L kernel: [  646.028453] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:37 xerox-L kernel: [  646.028456] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:37 xerox-L kernel: [  646.039099] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:37 xerox-L kernel: [  646.104752] ata1.00: configured for UDMA/133
Apr 22 00:43:37 xerox-L kernel: [  646.104758] ata1: EH complete
Apr 22 00:43:37 xerox-L kernel: [  646.115688] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:37 xerox-L kernel: [  646.125362] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:37 xerox-L kernel: [  646.125365] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:37 xerox-L kernel: [  646.140211] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:37 xerox-L kernel: [  646.936819] ata1.00: configured for UDMA/133
Apr 22 00:43:37 xerox-L kernel: [  646.936833] ata1: EH complete
Apr 22 00:43:37 xerox-L kernel: [  646.947598] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:37 xerox-L kernel: [  646.956569] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:37 xerox-L kernel: [  646.956573] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:37 xerox-L kernel: [  646.985334] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:42 xerox-L kernel: [  651.706382] ata1.00: configured for UDMA/133
Apr 22 00:43:43 xerox-L kernel: [  651.706388] ata1: EH complete
Apr 22 00:43:43 xerox-L kernel: [  651.713231] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:44 xerox-L kernel: [  651.731232] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:45 xerox-L kernel: [  651.731235] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:45 xerox-L kernel: [  651.741749] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:45 xerox-L kernel: [  652.965664] ata1.00: configured for UDMA/133
Apr 22 00:43:46 xerox-L kernel: [  652.965668] ata1: EH complete
Apr 22 00:43:46 xerox-L kernel: [  652.970588] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:46 xerox-L kernel: [  652.976178] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:46 xerox-L kernel: [  652.976182] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:49 xerox-L kernel: [  652.988139] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:49 xerox-L kernel: [  653.576976] ata1.00: configured for UDMA/133
Apr 22 00:43:49 xerox-L kernel: [  653.576987] ata1: EH complete
Apr 22 00:43:52 xerox-L kernel: [  653.593953] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:53 xerox-L kernel: [  653.597769] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:53 xerox-L kernel: [  653.597775] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:54 xerox-L kernel: [  653.610337] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:55 xerox-L kernel: [  654.819667] ata1.00: configured for UDMA/133
Apr 22 00:43:55 xerox-L kernel: [  654.819674] ata1: EH complete
Apr 22 00:43:56 xerox-L kernel: [  654.832172] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:56 xerox-L kernel: [  654.834878] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:56 xerox-L kernel: [  654.834882] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:56 xerox-L kernel: [  654.842642] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:57 xerox-L kernel: [  654.928742] ata1.00: configured for UDMA/133
Apr 22 00:43:57 xerox-L kernel: [  654.928749] ata1: EH complete
Apr 22 00:43:57 xerox-L kernel: [  654.957678] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:58 xerox-L kernel: [  654.973315] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:58 xerox-L kernel: [  654.973318] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:58 xerox-L kernel: [  654.980465] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:58 xerox-L kernel: [  655.937714] ata1.00: configured for UDMA/133
Apr 22 00:43:59 xerox-L kernel: [  655.937721] ata1: EH complete
Apr 22 00:43:59 xerox-L kernel: [  655.950510] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:59 xerox-L kernel: [  655.964109] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:44:00 xerox-L kernel: [  655.964112] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:44:00 xerox-L kernel: [  655.985225] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:44:00 xerox-L kernel: [  666.010807] ata1.00: configured for UDMA/133
Apr 22 00:44:00 xerox-L kernel: [  666.010813] ata1: EH complete
Apr 22 00:44:00 xerox-L kernel: [  666.016557] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:44:00 xerox-L kernel: [  666.024420] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:44:00 xerox-L kernel: [  666.024423] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:44:00 xerox-L kernel: [  666.046669] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 01:02:39 xerox-L kernel: [ 1790.307292] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK aLlcpus showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks 
Apr 22 01:02:40 xerox-L kernel: [ 1791.348501] SysRq : HELP : loglevel0-8 reBoot Crashdump tErm Full kIll saK aLlcpus showMem Nice powerOff showPc show-all-timers(Q) unRaw Sync showTasks Unmount shoW-blocked-tasks

---

### Post by fixture on 2009-04-22
xorg.log.old from time of freeze

[mi] EQ overflowing. The server is probably stuck in an infinite loop.

Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4f1b66]
1: /usr/bin/X(mieqEnqueue+0x359) [0x4d28a9]
2: /usr/bin/X(xf86PostKeyboardEvent+0x96) [0x495fa6]
3: /usr/lib/xorg/modules/input//evdev_drv.so [0x7fabb1b4dc35]
4: /usr/bin/X [0x485be5]
5: /usr/bin/X [0x476f77]
6: /lib/libpthread.so.0 [0x7fabc6ce8080]
7: /lib/libc.so.6(ioctl+0x7) [0x7fabc50f9cd7]
8: /usr/lib/libdrm_intel.so.1(drm_intel_gem_bo_start_gtt_access+0x4d) [0x7fabc30673bd]
9: /usr/lib/dri/i965_dri.so(intelFinish+0x41) [0x7fabb2458241]
10: /usr/lib/xorg/modules/extensions//libglx.so [0x7fabc3d66805]
11: /usr/lib/xorg/modules/extensions//libglx.so [0x7fabc3d659d2]
12: /usr/lib/xorg/modules/extensions//libglx.so [0x7fabc3d69de2]
13: /usr/bin/X(Dispatch+0x364) [0x44e304]
14: /usr/bin/X(main+0x3bd) [0x433d8d]
15: /lib/libc.so.6(__libc_start_main+0xe6) [0x7fabc503a5a6]
16: /usr/bin/X [0x433219]
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.
[mi] EQ overflowing. The server is probably stuck in an infinite loop.
[mi] mieqEnequeue: out-of-order valuator event; dropping.

---

