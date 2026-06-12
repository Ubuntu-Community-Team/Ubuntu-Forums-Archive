---
title: "Jaunty Jackalope freezes on laptop"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by devosion on 2009-04-19
The freeze that occurs is strange in that I am still able to use my mouse, but X does not respond. I have not yet given the OS enough to time to see if it comes out of the freeze. I usually wait about 2 minutes then have to do a hard reset everytime to get it out. At first I thought the freeze occured due to too many windows open, if possible, but as I gave it a shot, and had compiz enabled, the bug never occured. This allowed me to nail down the specifics and I believe it has either to do with firefox or flash. Is anyone experiencing a similar problem? Any fixes?

Im using an intel graphic card (X1300 I believe) with 1gig of ram.

---

### Post by SeanBlader on 2009-04-19
I can confirm this, but I have an Intel GMA X4500HD chip on my laptop. I would also suspect that it might be due to Firefox or Flash.

If I knew how to get logs on restart I totally would next time it happened.

---

### Post by olskar on 2009-04-19
This seems to be a big problem, three other threads mention it :(

[http://ubuntuforums.org/showthread.php?t=1128583](http://ubuntuforums.org/showthread.php?t=1128583)
[http://ubuntuforums.org/showthread.php?t=1127591](http://ubuntuforums.org/showthread.php?t=1127591)
[http://ubuntuforums.org/showthread.php?t=1129414](http://ubuntuforums.org/showthread.php?t=1129414)


Time to make a sticky out of these?

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

Apr 22 00:35:54 xerox-L kernel: [ 185.318021] ata1.00: configured for UDMA/133
Apr 22 00:35:54 xerox-L kernel: [ 185.318031] ata1: EH complete
Apr 22 00:35:54 xerox-L kernel: [ 185.325636] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:35:54 xerox-L kernel: [ 185.331453] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:35:54 xerox-L kernel: [ 185.331459] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:35:54 xerox-L kernel: [ 185.358675] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:35:59 xerox-L kernel: [ 189.975183] CE: hpet increasing min_delta_ns to 15000 nsec
Apr 22 00:36:00 xerox-L kernel: [ 191.417034] ata1.00: configured for UDMA/133
Apr 22 00:36:00 xerox-L kernel: [ 191.417047] ata1: EH complete
Apr 22 00:36:00 xerox-L kernel: [ 191.422879] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:36:00 xerox-L kernel: [ 191.422928] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:36:00 xerox-L kernel: [ 191.422933] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:36:00 xerox-L kernel: [ 191.422995] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:37:48 xerox-L kernel: [ 298.789689] ath5k phy0: noise floor calibration timeout (2412MHz)
Apr 22 00:38:25 xerox-L kernel: [ 335.494013] ata1.00: configured for UDMA/133
Apr 22 00:38:25 xerox-L kernel: [ 335.494023] ata1: EH complete
Apr 22 00:38:25 xerox-L kernel: [ 335.511046] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:38:25 xerox-L kernel: [ 335.516190] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:38:25 xerox-L kernel: [ 335.516197] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:38:25 xerox-L kernel: [ 335.529125] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:38:28 xerox-L kernel: [ 339.187032] ata1.00: configured for UDMA/133
Apr 22 00:38:28 xerox-L kernel: [ 339.187044] ata1: EH complete
Apr 22 00:38:28 xerox-L kernel: [ 339.199555] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:38:28 xerox-L kernel: [ 339.206276] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:38:28 xerox-L kernel: [ 339.206282] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:38:28 xerox-L kernel: [ 339.215101] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:38:31 xerox-L kernel: [ 341.502909] ata1.00: configured for UDMA/133
Apr 22 00:38:31 xerox-L kernel: [ 341.502916] ata1: EH complete
Apr 22 00:38:31 xerox-L kernel: [ 341.508471] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:38:31 xerox-L kernel: [ 341.512301] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:38:31 xerox-L kernel: [ 341.512304] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:38:31 xerox-L kernel: [ 341.556081] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:38:34 xerox-L kernel: [ 345.267326] ata1.00: configured for UDMA/133
Apr 22 00:38:34 xerox-L kernel: [ 345.267338] ata1: EH complete
Apr 22 00:38:34 xerox-L kernel: [ 345.284603] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:38:34 xerox-L kernel: [ 345.295800] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:38:34 xerox-L kernel: [ 345.295807] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:38:34 xerox-L kernel: [ 345.307869] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:40:56 xerox-L kernel: [ 487.033051] ata1.00: configured for UDMA/133
Apr 22 00:40:56 xerox-L kernel: [ 487.033065] ata1: EH complete
Apr 22 00:40:56 xerox-L kernel: [ 487.045445] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:40:56 xerox-L kernel: [ 487.050380] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:40:56 xerox-L kernel: [ 487.050386] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:40:56 xerox-L kernel: [ 487.065489] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:00 xerox-L kernel: [ 489.252745] ata1.00: configured for UDMA/133
Apr 22 00:41:00 xerox-L kernel: [ 489.252752] ata1: EH complete
Apr 22 00:41:00 xerox-L kernel: [ 489.266939] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:00 xerox-L kernel: [ 489.272209] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:00 xerox-L kernel: [ 489.272213] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:00 xerox-L kernel: [ 489.284269] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:00 xerox-L kernel: [ 489.449744] ata1.00: configured for UDMA/133
Apr 22 00:41:00 xerox-L kernel: [ 489.449750] ata1: EH complete
Apr 22 00:41:00 xerox-L kernel: [ 489.462008] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:01 xerox-L kernel: [ 489.478664] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:01 xerox-L kernel: [ 489.478670] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:01 xerox-L kernel: [ 489.500273] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:02 xerox-L kernel: [ 491.865083] ata1.00: configured for UDMA/133
Apr 22 00:41:02 xerox-L kernel: [ 491.865089] ata1: EH complete
Apr 22 00:41:02 xerox-L kernel: [ 491.878373] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:02 xerox-L kernel: [ 491.886530] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:02 xerox-L kernel: [ 491.886533] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:02 xerox-L kernel: [ 491.903725] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:03 xerox-L kernel: [ 493.281747] ata1.00: configured for UDMA/133
Apr 22 00:41:03 xerox-L kernel: [ 493.281752] ata1: EH complete
Apr 22 00:41:03 xerox-L kernel: [ 493.288228] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:03 xerox-L kernel: [ 493.292603] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:03 xerox-L kernel: [ 493.292607] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:03 xerox-L kernel: [ 493.318400] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:07 xerox-L kernel: [ 495.806402] ata1.00: configured for UDMA/133
Apr 22 00:41:07 xerox-L kernel: [ 495.806409] ata1: EH complete
Apr 22 00:41:07 xerox-L kernel: [ 495.809172] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:07 xerox-L kernel: [ 495.817535] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:07 xerox-L kernel: [ 495.817539] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:07 xerox-L kernel: [ 495.833494] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:08 xerox-L kernel: [ 495.895200] ata1.00: configured for UDMA/133
Apr 22 00:41:08 xerox-L kernel: [ 495.895208] ata1: EH complete
Apr 22 00:41:08 xerox-L kernel: [ 495.906842] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:08 xerox-L kernel: [ 495.919957] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:08 xerox-L kernel: [ 495.919962] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:08 xerox-L kernel: [ 495.940290] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:41:09 xerox-L kernel: [ 499.333991] ata1.00: configured for UDMA/133
Apr 22 00:41:09 xerox-L kernel: [ 499.334002] ata1: EH complete
Apr 22 00:41:09 xerox-L kernel: [ 499.337788] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:41:09 xerox-L kernel: [ 499.343193] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:41:09 xerox-L kernel: [ 499.343200] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:41:09 xerox-L kernel: [ 499.370015] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:25 xerox-L kernel: [ 635.639478] ata1.00: configured for UDMA/133
Apr 22 00:43:25 xerox-L kernel: [ 635.639493] ata1: EH complete
Apr 22 00:43:25 xerox-L kernel: [ 635.653657] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:25 xerox-L kernel: [ 635.670254] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:25 xerox-L kernel: [ 635.670261] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:25 xerox-L kernel: [ 635.678385] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:29 xerox-L kernel: [ 639.321723] ata1.00: configured for UDMA/133
Apr 22 00:43:29 xerox-L kernel: [ 639.321729] ata1: EH complete
Apr 22 00:43:29 xerox-L kernel: [ 639.323301] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:29 xerox-L kernel: [ 639.338739] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:29 xerox-L kernel: [ 639.338742] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:29 xerox-L kernel: [ 639.350437] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:29 xerox-L kernel: [ 639.397779] ata1.00: configured for UDMA/133
Apr 22 00:43:29 xerox-L kernel: [ 639.397785] ata1: EH complete
Apr 22 00:43:29 xerox-L kernel: [ 639.409217] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:29 xerox-L kernel: [ 639.410103] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:29 xerox-L kernel: [ 639.410106] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:29 xerox-L kernel: [ 639.420802] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:32 xerox-L kernel: [ 642.132855] ata1.00: configured for UDMA/133
Apr 22 00:43:32 xerox-L kernel: [ 642.132861] ata1: EH complete
Apr 22 00:43:33 xerox-L kernel: [ 642.137299] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:33 xerox-L kernel: [ 642.138987] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:34 xerox-L kernel: [ 642.138990] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:34 xerox-L kernel: [ 642.152870] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:34 xerox-L kernel: [ 642.466240] ata1.00: configured for UDMA/133
Apr 22 00:43:34 xerox-L kernel: [ 642.466246] ata1: EH complete
Apr 22 00:43:34 xerox-L kernel: [ 642.495030] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:34 xerox-L kernel: [ 642.513595] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:34 xerox-L kernel: [ 642.513599] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:34 xerox-L kernel: [ 642.541438] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:35 xerox-L kernel: [ 645.528649] ata1.00: configured for UDMA/133
Apr 22 00:43:35 xerox-L kernel: [ 645.528655] ata1: EH complete
Apr 22 00:43:36 xerox-L kernel: [ 645.534336] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:36 xerox-L kernel: [ 645.536388] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:36 xerox-L kernel: [ 645.536391] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:36 xerox-L kernel: [ 645.548283] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:36 xerox-L kernel: [ 645.898521] ata1.00: configured for UDMA/133
Apr 22 00:43:36 xerox-L kernel: [ 645.898527] ata1: EH complete
Apr 22 00:43:36 xerox-L kernel: [ 645.902121] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:36 xerox-L kernel: [ 645.916506] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:37 xerox-L kernel: [ 645.916509] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:37 xerox-L kernel: [ 645.931293] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:37 xerox-L kernel: [ 646.007286] ata1.00: configured for UDMA/133
Apr 22 00:43:37 xerox-L kernel: [ 646.007293] ata1: EH complete
Apr 22 00:43:37 xerox-L kernel: [ 646.026446] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:37 xerox-L kernel: [ 646.028453] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:37 xerox-L kernel: [ 646.028456] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:37 xerox-L kernel: [ 646.039099] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:37 xerox-L kernel: [ 646.104752] ata1.00: configured for UDMA/133
Apr 22 00:43:37 xerox-L kernel: [ 646.104758] ata1: EH complete
Apr 22 00:43:37 xerox-L kernel: [ 646.115688] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:37 xerox-L kernel: [ 646.125362] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:37 xerox-L kernel: [ 646.125365] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:37 xerox-L kernel: [ 646.140211] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:37 xerox-L kernel: [ 646.936819] ata1.00: configured for UDMA/133
Apr 22 00:43:37 xerox-L kernel: [ 646.936833] ata1: EH complete
Apr 22 00:43:37 xerox-L kernel: [ 646.947598] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:37 xerox-L kernel: [ 646.956569] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:37 xerox-L kernel: [ 646.956573] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:37 xerox-L kernel: [ 646.985334] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:42 xerox-L kernel: [ 651.706382] ata1.00: configured for UDMA/133
Apr 22 00:43:43 xerox-L kernel: [ 651.706388] ata1: EH complete
Apr 22 00:43:43 xerox-L kernel: [ 651.713231] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:44 xerox-L kernel: [ 651.731232] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:45 xerox-L kernel: [ 651.731235] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:45 xerox-L kernel: [ 651.741749] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:45 xerox-L kernel: [ 652.965664] ata1.00: configured for UDMA/133
Apr 22 00:43:46 xerox-L kernel: [ 652.965668] ata1: EH complete
Apr 22 00:43:46 xerox-L kernel: [ 652.970588] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:46 xerox-L kernel: [ 652.976178] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:46 xerox-L kernel: [ 652.976182] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:49 xerox-L kernel: [ 652.988139] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:49 xerox-L kernel: [ 653.576976] ata1.00: configured for UDMA/133
Apr 22 00:43:49 xerox-L kernel: [ 653.576987] ata1: EH complete
Apr 22 00:43:52 xerox-L kernel: [ 653.593953] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:53 xerox-L kernel: [ 653.597769] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:53 xerox-L kernel: [ 653.597775] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:54 xerox-L kernel: [ 653.610337] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:55 xerox-L kernel: [ 654.819667] ata1.00: configured for UDMA/133
Apr 22 00:43:55 xerox-L kernel: [ 654.819674] ata1: EH complete
Apr 22 00:43:56 xerox-L kernel: [ 654.832172] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:56 xerox-L kernel: [ 654.834878] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:56 xerox-L kernel: [ 654.834882] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:56 xerox-L kernel: [ 654.842642] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:57 xerox-L kernel: [ 654.928742] ata1.00: configured for UDMA/133
Apr 22 00:43:57 xerox-L kernel: [ 654.928749] ata1: EH complete
Apr 22 00:43:57 xerox-L kernel: [ 654.957678] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:58 xerox-L kernel: [ 654.973315] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:43:58 xerox-L kernel: [ 654.973318] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:43:58 xerox-L kernel: [ 654.980465] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:43:58 xerox-L kernel: [ 655.937714] ata1.00: configured for UDMA/133
Apr 22 00:43:59 xerox-L kernel: [ 655.937721] ata1: EH complete
Apr 22 00:43:59 xerox-L kernel: [ 655.950510] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:43:59 xerox-L kernel: [ 655.964109] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:44:00 xerox-L kernel: [ 655.964112] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:44:00 xerox-L kernel: [ 655.985225] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Apr 22 00:44:00 xerox-L kernel: [ 666.010807] ata1.00: configured for UDMA/133
Apr 22 00:44:00 xerox-L kernel: [ 666.010813] ata1: EH complete
Apr 22 00:44:00 xerox-L kernel: [ 666.016557] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
Apr 22 00:44:00 xerox-L kernel: [ 666.024420] sd 0:0:0:0: [sda] Write Protect is off
Apr 22 00:44:00 xerox-L kernel: [ 666.024423] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 22 00:44:00 xerox-L kernel: [ 666.046669] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
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

### Post by 00b00nt00 on 2009-04-22
I tried UXA acceleration, by amending the xorg.conf, but this resulted in random freezes.

I cured this by disabling Compiz. Maybe this will work for you.

---

### Post by zevans on 2009-04-22
We're more or less in a situation where UXA is the future performance roadmap but EXA is the current should-be-stable release. For this reason EXA is the default in Jaunty and there is a note in the Release Notes.

Unfortunately EXA isn't quite stable either, but most people seem to do OK with EXA on (which is the default, so you'll get that if you don't put any UXA lines in xorg.conf) AND an additional option in the Device section: 

```

Option "EXAOptimizeMigration" "true"
Option "MigrationHeuristic" "greedy"

```

If you search bugs.launchpad.net for the above strings you'll find quite a few bugs related to this, and it looks like there are multiple bugs.

Really good summary of the situation here:
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by zevans on 2009-04-22
Re Compiz: the Reflections feature in it is pretty much guaranteed to trigger the bug, by the look of latest updates to several of the bug reports... it's not a Compiz bug alone though. Other aggressive 3D usage can also trigger it (kwin effects in my case.)

---

### Post by matthew.ball on 2009-04-22
I'm on an nvidia card, these same random crashes occur, and likewise they have nearly all been while using firefox (I assume they have, but cannot guarantee it).

I do have compiz enabled, but I have turned all the effects off, I just want to use awn.

Perhaps I should look for an alternative.

---

### Post by gotgenes on 2009-04-22
Have a look at [Bug #332549]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/332549/") and see if this affects you. If so, make a note of it.

---

