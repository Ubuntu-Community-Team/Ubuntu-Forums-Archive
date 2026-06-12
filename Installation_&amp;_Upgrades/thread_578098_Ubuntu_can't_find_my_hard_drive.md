---
title: "Ubuntu can't find my hard drive"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by jdunk90 on 2007-10-16
Ubuntu will boot with my CD, but when I go to install it it can't find my hard drive to save it to.  This is a new build computer, but the HDD is recoqnized in BIOS.  How can I get the OS installed?

---

### Post by logos34 on 2007-10-17
Is it detected by gparted?

menu>system>admin>gnome partition editor

---

### Post by jdunk90 on 2007-10-17
No, it isn't detecting any devices there

---

### Post by logos34 on 2007-10-18
try different Bios hard disk detection settings--'auto', 'user', 'LBA', etc.

---

### Post by jdunk90 on 2007-10-18
I don't have those options for the hard drive, they are only available for the CD drive

---

### Post by Imsati on 2007-10-22
Hello, jdunk! It's Imsati from CF.

I recently had a problem with my SATA drives. I have 4 SATA ports and two drives. I thought I had plugged the cables into the SATA0 and SATA1 ports on my motherboard, but had in fact plugged them into SATA1 and SATA2, end experienced a similar problem as you mentioned in this Thread--I could only see one of the HDDs. How many SATA ports do you have and have you checked to make sure you're plugged into the first two (whatever number they may be--0+1, 1+2)?

---

### Post by EvilNed on 2007-10-25
Got the same problem here. I have a built in SIL3112 SATA adapter on my ASUS A8NX motherboard (nforce 2 chipset). The second HD is a 40 gig Maxtor IDE drive with an ide to sata connector on it.  7.04 found it just fine, as did every other Ubuntu I have used.

---

### Post by EvilNed on 2007-11-08
Here is my kernel dmesg information. I also submitted through the hardware database collection too. 
33fa0a5d5a9b586d0864bc7601803b17 is my submission  ID.


[  664.325372] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  664.333345] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  664.333376]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  664.333411]  [<c0131470>] process_timeout+0x0/0x10
[  664.333421]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  664.333432]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  664.333449]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  664.333460]  [<c0138331>] run_workqueue+0x81/0x110
[  664.333467]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  664.333474]  [<c0138d30>] worker_thread+0x0/0x100
[  664.333478]  [<c0138dd0>] worker_thread+0xa0/0x100
[  664.333482]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  664.333489]  [<c0138d30>] worker_thread+0x0/0x100
[  664.333492]  [<c013bb12>] kthread+0x42/0x70
[  664.333495]  [<c013bad0>] kthread+0x0/0x70
[  664.333500]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  664.333508]  =======================
[  664.333893] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  664.333899] ata2.00: limiting speed to UDMA7:PIO5
[  664.836609] ata2: hard resetting port
[  665.715347] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  665.724631] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  665.724663]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  665.724698]  [<c0131470>] process_timeout+0x0/0x10
[  665.724708]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  665.724720]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  665.724762]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  665.724774]  [<c0138331>] run_workqueue+0x81/0x110
[  665.724780]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  665.724787]  [<c0138d30>] worker_thread+0x0/0x100
[  665.724791]  [<c0138dd0>] worker_thread+0xa0/0x100
[  665.724795]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  665.724802]  [<c0138d30>] worker_thread+0x0/0x100
[  665.724805]  [<c013bb12>] kthread+0x42/0x70
[  665.724808]  [<c013bad0>] kthread+0x0/0x70
[  665.724812]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  665.724821]  =======================
[  665.725204] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  666.226573] ata2: hard resetting port
[  667.105298] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  667.105318] ata2: EH pending after completion, repeating EH (cnt=3)
[  667.105329] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  667.820230] ata2: soft resetting port
[  667.976024] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  667.983992] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  667.984024]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  667.984059]  [<c0131470>] process_timeout+0x0/0x10
[  667.984069]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  667.984080]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  667.984097]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  667.984108]  [<c0138331>] run_workqueue+0x81/0x110
[  667.984115]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  667.984122]  [<c0138d30>] worker_thread+0x0/0x100
[  667.984126]  [<c0138dd0>] worker_thread+0xa0/0x100
[  667.984131]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  667.984137]  [<c0138d30>] worker_thread+0x0/0x100
[  667.984140]  [<c013bb12>] kthread+0x42/0x70
[  667.984143]  [<c013bad0>] kthread+0x0/0x70
[  667.984148]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  667.984157]  =======================
[  667.984541] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  668.487253] ata2: hard resetting port
[  669.365993] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  669.373954] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  669.373986]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  669.374023]  [<c0131470>] process_timeout+0x0/0x10
[  669.374032]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  669.374044]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  669.374061]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  669.374072]  [<c0138331>] run_workqueue+0x81/0x110
[  669.374078]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  669.374085]  [<c0138d30>] worker_thread+0x0/0x100
[  669.374089]  [<c0138dd0>] worker_thread+0xa0/0x100
[  669.374094]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  669.374100]  [<c0138d30>] worker_thread+0x0/0x100
[  669.374104]  [<c013bb12>] kthread+0x42/0x70
[  669.374107]  [<c013bad0>] kthread+0x0/0x70
[  669.374111]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  669.374120]  =======================
[  669.374504] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  669.374510] ata2.00: limiting speed to UDMA7:PIO5
[  669.877215] ata2: hard resetting port
[  670.755942] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  670.763916] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  670.763948]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  670.763983]  [<c0131470>] process_timeout+0x0/0x10
[  670.763993]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  670.764005]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  670.764022]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  670.764033]  [<c0138331>] run_workqueue+0x81/0x110
[  670.764040]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  670.764047]  [<c0138d30>] worker_thread+0x0/0x100
[  670.764050]  [<c0138dd0>] worker_thread+0xa0/0x100
[  670.764055]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  670.764061]  [<c0138d30>] worker_thread+0x0/0x100
[  670.764064]  [<c013bb12>] kthread+0x42/0x70
[  670.764067]  [<c013bad0>] kthread+0x0/0x70
[  670.764072]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  670.764081]  =======================
[  670.764464] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  671.267185] ata2: hard resetting port
[  672.145905] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  672.145923] ata2: EH pending after completion, repeating EH (cnt=2)
[  672.145934] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  672.860842] ata2: soft resetting port
[  673.016642] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  673.024607] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  673.024641]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  673.024677]  [<c0131470>] process_timeout+0x0/0x10
[  673.024687]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  673.024698]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  673.024715]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  673.024726]  [<c0138331>] run_workqueue+0x81/0x110
[  673.024732]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  673.024739]  [<c0138d30>] worker_thread+0x0/0x100
[  673.024743]  [<c0138dd0>] worker_thread+0xa0/0x100
[  673.024747]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  673.024754]  [<c0138d30>] worker_thread+0x0/0x100
[  673.024757]  [<c013bb12>] kthread+0x42/0x70
[  673.024760]  [<c013bad0>] kthread+0x0/0x70
[  673.024764]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  673.024826]  =======================
[  673.025216] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  673.527866] ata2: hard resetting port
[  674.406591] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  674.414578] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  674.414611]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  674.414646]  [<c0131470>] process_timeout+0x0/0x10
[  674.414655]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  674.414667]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  674.414684]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  674.414695]  [<c0138331>] run_workqueue+0x81/0x110
[  674.414702]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  674.414709]  [<c0138d30>] worker_thread+0x0/0x100
[  674.414712]  [<c0138dd0>] worker_thread+0xa0/0x100
[  674.414717]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  674.414723]  [<c0138d30>] worker_thread+0x0/0x100
[  674.414726]  [<c013bb12>] kthread+0x42/0x70
[  674.414730]  [<c013bad0>] kthread+0x0/0x70
[  674.414734]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  674.414743]  =======================
[  674.415128] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  674.415135] ata2.00: limiting speed to UDMA7:PIO5
[  674.917826] ata2: hard resetting port
[  675.796556] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  675.804541] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  675.804575]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  675.804611]  [<c0131470>] process_timeout+0x0/0x10
[  675.804621]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  675.804632]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  675.804649]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  675.804660]  [<c0138331>] run_workqueue+0x81/0x110
[  675.804667]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  675.804674]  [<c0138d30>] worker_thread+0x0/0x100
[  675.804678]  [<c0138dd0>] worker_thread+0xa0/0x100
[  675.804683]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  675.804689]  [<c0138d30>] worker_thread+0x0/0x100
[  675.804692]  [<c013bb12>] kthread+0x42/0x70
[  675.804695]  [<c013bad0>] kthread+0x0/0x70
[  675.804700]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  675.804708]  =======================
[  675.805093] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  676.307794] ata2: hard resetting port
[  677.186525] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  677.186541] ata2: EH pending after completion, repeating EH (cnt=1)
[  677.186552] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  677.901459] ata2: soft resetting port
[  678.057256] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  678.065232] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  678.065278]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  678.065318]  [<c0131470>] process_timeout+0x0/0x10
[  678.065328]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  678.065341]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  678.065357]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  678.065369]  [<c0138331>] run_workqueue+0x81/0x110
[  678.065376]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  678.065383]  [<c0138d30>] worker_thread+0x0/0x100
[  678.065387]  [<c0138dd0>] worker_thread+0xa0/0x100
[  678.065392]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  678.065398]  [<c0138d30>] worker_thread+0x0/0x100
[  678.065401]  [<c013bb12>] kthread+0x42/0x70
[  678.065404]  [<c013bad0>] kthread+0x0/0x70
[  678.065409]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  678.065418]  =======================
[  678.065806] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  678.568477] ata2: hard resetting port
[  679.447200] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  679.455177] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  679.455208]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  679.455244]  [<c0131470>] process_timeout+0x0/0x10
[  679.455253]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  679.455265]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  679.455282]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  679.455293]  [<c0138331>] run_workqueue+0x81/0x110
[  679.455300]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  679.455306]  [<c0138d30>] worker_thread+0x0/0x100
[  679.455310]  [<c0138dd0>] worker_thread+0xa0/0x100
[  679.455315]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  679.455321]  [<c0138d30>] worker_thread+0x0/0x100
[  679.455324]  [<c013bb12>] kthread+0x42/0x70
[  679.455327]  [<c013bad0>] kthread+0x0/0x70
[  679.455332]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  679.455341]  =======================
[  679.455724] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  679.455730] ata2.00: limiting speed to UDMA7:PIO5
[  679.958444] ata2: hard resetting port
[  680.837168] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  680.845137] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  680.845168]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  680.845204]  [<c0131470>] process_timeout+0x0/0x10
[  680.845214]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  680.845226]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  680.845242]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  680.845253]  [<c0138331>] run_workqueue+0x81/0x110
[  680.845260]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  680.845267]  [<c0138d30>] worker_thread+0x0/0x100
[  680.845271]  [<c0138dd0>] worker_thread+0xa0/0x100
[  680.845275]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  680.845282]  [<c0138d30>] worker_thread+0x0/0x100
[  680.845285]  [<c013bb12>] kthread+0x42/0x70
[  680.845288]  [<c013bad0>] kthread+0x0/0x70
[  680.845292]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  680.845301]  =======================
[  680.845685] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  681.348395] ata2: hard resetting port
[  682.227131] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  682.227148] ata2: EH pending after 5 tries, giving up
[  682.227152] ata2: EH complete
[  682.233394] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  682.233407] ata2: hard resetting port
[  683.109831] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  683.117824] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  683.117867]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  683.117905]  [<c0131470>] process_timeout+0x0/0x10
[  683.117915]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  683.117928]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  683.117944]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  683.117956]  [<c0138331>] run_workqueue+0x81/0x110
[  683.117963]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  683.117970]  [<c0138d30>] worker_thread+0x0/0x100
[  683.117974]  [<c0138dd0>] worker_thread+0xa0/0x100
[  683.117978]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  683.117984]  [<c0138d30>] worker_thread+0x0/0x100
[  683.117987]  [<c013bb12>] kthread+0x42/0x70
[  683.117991]  [<c013bad0>] kthread+0x0/0x70
[  683.117995]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  683.118004]  =======================
[  683.118392] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  683.621063] ata2: hard resetting port
[  684.499793] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  684.507765] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  684.507796]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  684.507831]  [<c0131470>] process_timeout+0x0/0x10
[  684.507841]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  684.507852]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  684.507869]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  684.507880]  [<c0138331>] run_workqueue+0x81/0x110
[  684.507887]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  684.507894]  [<c0138d30>] worker_thread+0x0/0x100
[  684.507898]  [<c0138dd0>] worker_thread+0xa0/0x100
[  684.507902]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  684.507909]  [<c0138d30>] worker_thread+0x0/0x100
[  684.507912]  [<c013bb12>] kthread+0x42/0x70
[  684.507915]  [<c013bad0>] kthread+0x0/0x70
[  684.507920]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  684.507928]  =======================
[  684.508311] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  684.508317] ata2.00: limiting speed to UDMA7:PIO5
[  685.011025] ata2: hard resetting port
[  685.889756] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  685.897726] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  685.897759]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  685.897794]  [<c0131470>] process_timeout+0x0/0x10
[  685.897804]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  685.897816]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  685.897832]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  685.897843]  [<c0138331>] run_workqueue+0x81/0x110
[  685.897850]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  685.897857]  [<c0138d30>] worker_thread+0x0/0x100
[  685.897861]  [<c0138dd0>] worker_thread+0xa0/0x100
[  685.897866]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  685.897872]  [<c0138d30>] worker_thread+0x0/0x100
[  685.897875]  [<c013bb12>] kthread+0x42/0x70
[  685.897878]  [<c013bad0>] kthread+0x0/0x70
[  685.897883]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  685.897892]  =======================
[  685.898275] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  686.401003] ata2: hard resetting port
[  687.279725] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  687.279745] ata2: EH pending after completion, repeating EH (cnt=4)
[  687.279756] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  687.994652] ata2: soft resetting port
[  688.150456] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  688.158434] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  688.158476]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  688.158515]  [<c0131470>] process_timeout+0x0/0x10
[  688.158526]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  688.158538]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  688.158555]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  688.158566]  [<c0138331>] run_workqueue+0x81/0x110
[  688.158573]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  688.158580]  [<c0138d30>] worker_thread+0x0/0x100
[  688.158583]  [<c0138dd0>] worker_thread+0xa0/0x100
[  688.158588]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  688.158594]  [<c0138d30>] worker_thread+0x0/0x100
[  688.158597]  [<c013bb12>] kthread+0x42/0x70
[  688.158601]  [<c013bad0>] kthread+0x0/0x70
[  688.158605]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  688.158614]  =======================
[  688.159001] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  688.661674] ata2: hard resetting port
[  689.540406] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  689.548382] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  689.548418]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  689.548453]  [<c0131470>] process_timeout+0x0/0x10
[  689.548463]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  689.548476]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  689.548492]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  689.548504]  [<c0138331>] run_workqueue+0x81/0x110
[  689.548510]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  689.548517]  [<c0138d30>] worker_thread+0x0/0x100
[  689.548521]  [<c0138dd0>] worker_thread+0xa0/0x100
[  689.548525]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  689.548532]  [<c0138d30>] worker_thread+0x0/0x100
[  689.548535]  [<c013bb12>] kthread+0x42/0x70
[  689.548538]  [<c013bad0>] kthread+0x0/0x70
[  689.548542]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  689.548551]  =======================
[  689.548939] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  689.548946] ata2.00: limiting speed to UDMA7:PIO5
[  690.051648] ata2: hard resetting port
[  690.930362] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  690.938341] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  690.938372]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  690.938408]  [<c0131470>] process_timeout+0x0/0x10
[  690.938417]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  690.938429]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  690.938445]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  690.938457]  [<c0138331>] run_workqueue+0x81/0x110
[  690.938463]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  690.938470]  [<c0138d30>] worker_thread+0x0/0x100
[  690.938474]  [<c0138dd0>] worker_thread+0xa0/0x100
[  690.938478]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  690.938485]  [<c0138d30>] worker_thread+0x0/0x100
[  690.938488]  [<c013bb12>] kthread+0x42/0x70
[  690.938491]  [<c013bad0>] kthread+0x0/0x70
[  690.938495]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  690.938504]  =======================
[  690.938886] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  691.441598] ata2: hard resetting port
[  692.320324] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  692.320342] ata2: EH pending after completion, repeating EH (cnt=3)
[  692.320352] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  693.035272] ata2: soft resetting port
[  693.191060] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  693.199038] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  693.199076]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  693.199112]  [<c0131470>] process_timeout+0x0/0x10
[  693.199122]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  693.199133]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  693.199150]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  693.199161]  [<c0138331>] run_workqueue+0x81/0x110
[  693.199168]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  693.199175]  [<c0138d30>] worker_thread+0x0/0x100
[  693.199179]  [<c0138dd0>] worker_thread+0xa0/0x100
[  693.199183]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  693.199190]  [<c0138d30>] worker_thread+0x0/0x100
[  693.199193]  [<c013bb12>] kthread+0x42/0x70
[  693.199196]  [<c013bad0>] kthread+0x0/0x70
[  693.199201]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  693.199209]  =======================
[  693.199596] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  693.702296] ata2: hard resetting port
[  694.581013] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  694.588984] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  694.589016]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  694.589052]  [<c0131470>] process_timeout+0x0/0x10
[  694.589061]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  694.589073]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  694.589089]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  694.589101]  [<c0138331>] run_workqueue+0x81/0x110
[  694.589107]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  694.589114]  [<c0138d30>] worker_thread+0x0/0x100
[  694.589118]  [<c0138dd0>] worker_thread+0xa0/0x100
[  694.589122]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  694.589129]  [<c0138d30>] worker_thread+0x0/0x100
[  694.589132]  [<c013bb12>] kthread+0x42/0x70
[  694.589135]  [<c013bad0>] kthread+0x0/0x70
[  694.589140]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  694.589149]  =======================
[  694.589531] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  694.589537] ata2.00: limiting speed to UDMA7:PIO5
[  695.092243] ata2: hard resetting port
[  695.970973] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  695.978947] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  695.978983]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  695.979020]  [<c0131470>] process_timeout+0x0/0x10
[  695.979030]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  695.979042]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  695.979059]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  695.979070]  [<c0138331>] run_workqueue+0x81/0x110
[  695.979076]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  695.979083]  [<c0138d30>] worker_thread+0x0/0x100
[  695.979087]  [<c0138dd0>] worker_thread+0xa0/0x100
[  695.979091]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  695.979098]  [<c0138d30>] worker_thread+0x0/0x100
[  695.979101]  [<c013bb12>] kthread+0x42/0x70
[  695.979104]  [<c013bad0>] kthread+0x0/0x70
[  695.979109]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  695.979118]  =======================
[  695.979502] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  696.482206] ata2: hard resetting port
[  697.360937] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  697.360958] ata2: EH pending after completion, repeating EH (cnt=2)
[  697.360969] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  698.075871] ata2: soft resetting port
[  698.231662] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  698.239636] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  698.239673]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  698.239708]  [<c0131470>] process_timeout+0x0/0x10
[  698.239718]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  698.239730]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  698.239747]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  698.239758]  [<c0138331>] run_workqueue+0x81/0x110
[  698.239764]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  698.239771]  [<c0138d30>] worker_thread+0x0/0x100
[  698.239775]  [<c0138dd0>] worker_thread+0xa0/0x100
[  698.239780]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  698.239786]  [<c0138d30>] worker_thread+0x0/0x100
[  698.239789]  [<c013bb12>] kthread+0x42/0x70
[  698.239792]  [<c013bad0>] kthread+0x0/0x70
[  698.239797]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  698.239806]  =======================
[  698.240190] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  698.742891] ata2: hard resetting port
[  699.621625] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  699.629614] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  699.629657]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  699.629695]  [<c0131470>] process_timeout+0x0/0x10
[  699.629706]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  699.629718]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  699.629735]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  699.629746]  [<c0138331>] run_workqueue+0x81/0x110
[  699.629753]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  699.629760]  [<c0138d30>] worker_thread+0x0/0x100
[  699.629764]  [<c0138dd0>] worker_thread+0xa0/0x100
[  699.629768]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  699.629775]  [<c0138d30>] worker_thread+0x0/0x100
[  699.629778]  [<c013bb12>] kthread+0x42/0x70
[  699.629781]  [<c013bad0>] kthread+0x0/0x70
[  699.629785]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  699.629795]  =======================
[  699.630183] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  699.630191] ata2.00: limiting speed to UDMA7:PIO5
[  700.132856] ata2: hard resetting port
[  701.011583] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  701.019555] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  701.019587]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  701.019622]  [<c0131470>] process_timeout+0x0/0x10
[  701.019632]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  701.019644]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  701.019661]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  701.019672]  [<c0138331>] run_workqueue+0x81/0x110
[  701.019679]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  701.019685]  [<c0138d30>] worker_thread+0x0/0x100
[  701.019689]  [<c0138dd0>] worker_thread+0xa0/0x100
[  701.019694]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  701.019700]  [<c0138d30>] worker_thread+0x0/0x100
[  701.019703]  [<c013bb12>] kthread+0x42/0x70
[  701.019706]  [<c013bad0>] kthread+0x0/0x70
[  701.019711]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  701.019719]  =======================
[  701.020102] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  701.522820] ata2: hard resetting port
[  702.401550] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  702.401569] ata2: EH pending after completion, repeating EH (cnt=1)
[  702.401580] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  703.116480] ata2: soft resetting port
[  703.272272] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  703.280240] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  703.280271]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  703.280306]  [<c0131470>] process_timeout+0x0/0x10
[  703.280316]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  703.280328]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  703.280344]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  703.280355]  [<c0138331>] run_workqueue+0x81/0x110
[  703.280362]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  703.280369]  [<c0138d30>] worker_thread+0x0/0x100
[  703.280373]  [<c0138dd0>] worker_thread+0xa0/0x100
[  703.280377]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  703.280384]  [<c0138d30>] worker_thread+0x0/0x100
[  703.280387]  [<c013bb12>] kthread+0x42/0x70
[  703.280390]  [<c013bad0>] kthread+0x0/0x70
[  703.280394]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  703.280403]  =======================
[  703.280787] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  703.783502] ata2: hard resetting port
[  704.662230] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  704.670208] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  704.670244]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  704.670280]  [<c0131470>] process_timeout+0x0/0x10
[  704.670290]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  704.670302]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  704.670318]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  704.670329]  [<c0138331>] run_workqueue+0x81/0x110
[  704.670336]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  704.670343]  [<c0138d30>] worker_thread+0x0/0x100
[  704.670347]  [<c0138dd0>] worker_thread+0xa0/0x100
[  704.670351]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  704.670357]  [<c0138d30>] worker_thread+0x0/0x100
[  704.670360]  [<c013bb12>] kthread+0x42/0x70
[  704.670363]  [<c013bad0>] kthread+0x0/0x70
[  704.670368]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  704.670377]  =======================
[  704.670762] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  704.670769] ata2.00: limiting speed to UDMA7:PIO5
[  705.173463] ata2: hard resetting port
[  706.052195] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  706.060182] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  706.060216]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  706.060251]  [<c0131470>] process_timeout+0x0/0x10
[  706.060261]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  706.060272]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  706.060289]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  706.060300]  [<c0138331>] run_workqueue+0x81/0x110
[  706.060307]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  706.060313]  [<c0138d30>] worker_thread+0x0/0x100
[  706.060317]  [<c0138dd0>] worker_thread+0xa0/0x100
[  706.060322]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  706.060328]  [<c0138d30>] worker_thread+0x0/0x100
[  706.060331]  [<c013bb12>] kthread+0x42/0x70
[  706.060334]  [<c013bad0>] kthread+0x0/0x70
[  706.060339]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  706.060348]  =======================
[  706.060735] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  706.563428] ata2: hard resetting port
[  707.442157] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  707.442177] ata2: EH pending after 5 tries, giving up
[  707.442181] ata2: EH complete
[  707.462056] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  707.462074] ata2: hard resetting port
[  708.336853] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  708.344816] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  708.344849]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  708.344885]  [<c0131470>] process_timeout+0x0/0x10
[  708.344895]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  708.344907]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  708.344924]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  708.344935]  [<c0138331>] run_workqueue+0x81/0x110
[  708.344941]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  708.344948]  [<c0138d30>] worker_thread+0x0/0x100
[  708.344952]  [<c0138dd0>] worker_thread+0xa0/0x100
[  708.344957]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  708.344963]  [<c0138d30>] worker_thread+0x0/0x100
[  708.344966]  [<c013bb12>] kthread+0x42/0x70
[  708.344969]  [<c013bad0>] kthread+0x0/0x70
[  708.344974]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  708.344982]  =======================
[  708.345366] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  708.848075] ata2: hard resetting port
[  709.726806] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  709.734777] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  709.734808]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  709.734843]  [<c0131470>] process_timeout+0x0/0x10
[  709.734853]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  709.734865]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  709.734882]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  709.734893]  [<c0138331>] run_workqueue+0x81/0x110
[  709.734900]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  709.734907]  [<c0138d30>] worker_thread+0x0/0x100
[  709.734911]  [<c0138dd0>] worker_thread+0xa0/0x100
[  709.734915]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  709.734922]  [<c0138d30>] worker_thread+0x0/0x100
[  709.734925]  [<c013bb12>] kthread+0x42/0x70
[  709.734928]  [<c013bad0>] kthread+0x0/0x70
[  709.734932]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  709.734941]  =======================
[  709.735324] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  709.735331] ata2.00: limiting speed to UDMA7:PIO5
[  710.238041] ata2: hard resetting port
[  711.116785] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  711.124739] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  711.124772]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  711.124807]  [<c0131470>] process_timeout+0x0/0x10
[  711.124817]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  711.124829]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  711.124845]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  711.124856]  [<c0138331>] run_workqueue+0x81/0x110
[  711.124863]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  711.124870]  [<c0138d30>] worker_thread+0x0/0x100
[  711.124874]  [<c0138dd0>] worker_thread+0xa0/0x100
[  711.124878]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  711.124885]  [<c0138d30>] worker_thread+0x0/0x100
[  711.124888]  [<c013bb12>] kthread+0x42/0x70
[  711.124891]  [<c013bad0>] kthread+0x0/0x70
[  711.124895]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  711.124904]  =======================
[  711.125286] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  711.628002] ata2: hard resetting port
[  712.506730] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  712.506750] ata2: EH pending after completion, repeating EH (cnt=4)
[  712.506760] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  713.221664] ata2: soft resetting port
[  713.377457] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  713.385424] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  713.385455]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  713.385491]  [<c0131470>] process_timeout+0x0/0x10
[  713.385501]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  713.385513]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  713.385529]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  713.385540]  [<c0138331>] run_workqueue+0x81/0x110
[  713.385547]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  713.385554]  [<c0138d30>] worker_thread+0x0/0x100
[  713.385558]  [<c0138dd0>] worker_thread+0xa0/0x100
[  713.385562]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  713.385569]  [<c0138d30>] worker_thread+0x0/0x100
[  713.385572]  [<c013bb12>] kthread+0x42/0x70
[  713.385575]  [<c013bad0>] kthread+0x0/0x70
[  713.385579]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  713.385588]  =======================
[  713.385972] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  713.888687] ata2: hard resetting port
[  714.767412] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  714.775392] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  714.775429]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  714.775465]  [<c0131470>] process_timeout+0x0/0x10
[  714.775475]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  714.775486]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  714.775503]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  714.775514]  [<c0138331>] run_workqueue+0x81/0x110
[  714.775521]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  714.775528]  [<c0138d30>] worker_thread+0x0/0x100
[  714.775532]  [<c0138dd0>] worker_thread+0xa0/0x100
[  714.775536]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  714.775543]  [<c0138d30>] worker_thread+0x0/0x100
[  714.775546]  [<c013bb12>] kthread+0x42/0x70
[  714.775549]  [<c013bad0>] kthread+0x0/0x70
[  714.775554]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  714.775563]  =======================
[  714.775947] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  714.775955] ata2.00: limiting speed to UDMA7:PIO5
[  715.278666] ata2: hard resetting port
[  716.157374] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  716.165355] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  716.165387]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  716.165423]  [<c0131470>] process_timeout+0x0/0x10
[  716.165433]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  716.165454]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  716.165470]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  716.165482]  [<c0138331>] run_workqueue+0x81/0x110
[  716.165488]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  716.165495]  [<c0138d30>] worker_thread+0x0/0x100
[  716.165499]  [<c0138dd0>] worker_thread+0xa0/0x100
[  716.165504]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  716.165510]  [<c0138d30>] worker_thread+0x0/0x100
[  716.165513]  [<c013bb12>] kthread+0x42/0x70
[  716.165516]  [<c013bad0>] kthread+0x0/0x70
[  716.165521]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  716.165530]  =======================
[  716.165913] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  716.668617] ata2: hard resetting port
[  717.547339] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  717.547358] ata2: EH pending after completion, repeating EH (cnt=3)
[  717.547369] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  718.262281] ata2: soft resetting port
[  718.418073] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  718.426047] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  718.426083]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  718.426119]  [<c0131470>] process_timeout+0x0/0x10
[  718.426129]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  718.426140]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  718.426157]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  718.426168]  [<c0138331>] run_workqueue+0x81/0x110
[  718.426175]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  718.426182]  [<c0138d30>] worker_thread+0x0/0x100
[  718.426186]  [<c0138dd0>] worker_thread+0xa0/0x100
[  718.426191]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  718.426197]  [<c0138d30>] worker_thread+0x0/0x100
[  718.426200]  [<c013bb12>] kthread+0x42/0x70
[  718.426204]  [<c013bad0>] kthread+0x0/0x70
[  718.426208]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  718.426217]  =======================
[  718.426633] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  718.929298] ata2: hard resetting port
[  719.808022] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  719.815996] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  719.816027]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  719.816063]  [<c0131470>] process_timeout+0x0/0x10
[  719.816073]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  719.816085]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  719.816101]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  719.816112]  [<c0138331>] run_workqueue+0x81/0x110
[  719.816119]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  719.816126]  [<c0138d30>] worker_thread+0x0/0x100
[  719.816130]  [<c0138dd0>] worker_thread+0xa0/0x100
[  719.816134]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  719.816140]  [<c0138d30>] worker_thread+0x0/0x100
[  719.816144]  [<c013bb12>] kthread+0x42/0x70
[  719.816147]  [<c013bad0>] kthread+0x0/0x70
[  719.816151]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  719.816160]  =======================
[  719.816545] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  719.816551] ata2.00: limiting speed to UDMA7:PIO5
[  720.319271] ata2: hard resetting port
[  721.197985] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  721.205958] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  721.205989]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  721.206025]  [<c0131470>] process_timeout+0x0/0x10
[  721.206035]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  721.206047]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  721.206063]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  721.206075]  [<c0138331>] run_workqueue+0x81/0x110
[  721.206082]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  721.206088]  [<c0138d30>] worker_thread+0x0/0x100
[  721.206092]  [<c0138dd0>] worker_thread+0xa0/0x100
[  721.206097]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  721.206103]  [<c0138d30>] worker_thread+0x0/0x100
[  721.206106]  [<c013bb12>] kthread+0x42/0x70
[  721.206109]  [<c013bad0>] kthread+0x0/0x70
[  721.206114]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  721.206123]  =======================
[  721.206505] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  721.709222] ata2: hard resetting port
[  722.587948] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  722.587967] ata2: EH pending after completion, repeating EH (cnt=2)
[  722.587978] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  723.302880] ata2: soft resetting port
[  723.458674] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  723.466644] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  723.466675]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  723.466711]  [<c0131470>] process_timeout+0x0/0x10
[  723.466721]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  723.466732]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  723.466749]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  723.466760]  [<c0138331>] run_workqueue+0x81/0x110
[  723.466767]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  723.466774]  [<c0138d30>] worker_thread+0x0/0x100
[  723.466778]  [<c0138dd0>] worker_thread+0xa0/0x100
[  723.466782]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  723.466789]  [<c0138d30>] worker_thread+0x0/0x100
[  723.466792]  [<c013bb12>] kthread+0x42/0x70
[  723.466795]  [<c013bad0>] kthread+0x0/0x70
[  723.466799]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  723.466808]  =======================
[  723.467193] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  723.969906] ata2: hard resetting port
[  724.848634] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  724.856606] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  724.856643]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  724.856681]  [<c0131470>] process_timeout+0x0/0x10
[  724.856691]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  724.856703]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  724.856720]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  724.856731]  [<c0138331>] run_workqueue+0x81/0x110
[  724.856738]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  724.856745]  [<c0138d30>] worker_thread+0x0/0x100
[  724.856749]  [<c0138dd0>] worker_thread+0xa0/0x100
[  724.856753]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  724.856760]  [<c0138d30>] worker_thread+0x0/0x100
[  724.856763]  [<c013bb12>] kthread+0x42/0x70
[  724.856766]  [<c013bad0>] kthread+0x0/0x70
[  724.856770]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  724.856779]  =======================
[  724.857162] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  724.857169] ata2.00: limiting speed to UDMA7:PIO5
[  725.359868] ata2: hard resetting port
[  726.238594] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  726.246576] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  726.246621]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  726.246660]  [<c0131470>] process_timeout+0x0/0x10
[  726.246670]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  726.246683]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  726.246699]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  726.246711]  [<c0138331>] run_workqueue+0x81/0x110
[  726.246718]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  726.246725]  [<c0138d30>] worker_thread+0x0/0x100
[  726.246729]  [<c0138dd0>] worker_thread+0xa0/0x100
[  726.246733]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  726.246740]  [<c0138d30>] worker_thread+0x0/0x100
[  726.246743]  [<c013bb12>] kthread+0x42/0x70
[  726.246746]  [<c013bad0>] kthread+0x0/0x70
[  726.246751]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  726.246760]  =======================
[  726.247147] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  726.749832] ata2: hard resetting port
[  727.628558] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  727.628578] ata2: EH pending after completion, repeating EH (cnt=1)
[  727.628588] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  728.343505] ata2: soft resetting port
[  728.499283] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  728.507253] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  728.507290]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  728.507327]  [<c0131470>] process_timeout+0x0/0x10
[  728.507337]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  728.507348]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  728.507365]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  728.507376]  [<c0138331>] run_workqueue+0x81/0x110
[  728.507383]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  728.507390]  [<c0138d30>] worker_thread+0x0/0x100
[  728.507394]  [<c0138dd0>] worker_thread+0xa0/0x100
[  728.507399]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  728.507405]  [<c0138d30>] worker_thread+0x0/0x100
[  728.507408]  [<c013bb12>] kthread+0x42/0x70
[  728.507411]  [<c013bad0>] kthread+0x0/0x70
[  728.507416]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  728.507425]  =======================
[  728.507810] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  729.010516] ata2: hard resetting port
[  729.889258] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  729.897215] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  729.897247]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  729.897283]  [<c0131470>] process_timeout+0x0/0x10
[  729.897293]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  729.897305]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  729.897321]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  729.897333]  [<c0138331>] run_workqueue+0x81/0x110
[  729.897339]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  729.897346]  [<c0138d30>] worker_thread+0x0/0x100
[  729.897350]  [<c0138dd0>] worker_thread+0xa0/0x100
[  729.897354]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  729.897361]  [<c0138d30>] worker_thread+0x0/0x100
[  729.897364]  [<c013bb12>] kthread+0x42/0x70
[  729.897367]  [<c013bad0>] kthread+0x0/0x70
[  729.897372]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  729.897381]  =======================
[  729.897764] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  729.897770] ata2.00: limiting speed to UDMA7:PIO5
[  730.400480] ata2: hard resetting port
[  731.279211] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  731.287183] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  731.287222]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  731.287260]  [<c0131470>] process_timeout+0x0/0x10
[  731.287270]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  731.287282]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  731.287299]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  731.287310]  [<c0138331>] run_workqueue+0x81/0x110
[  731.287317]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  731.287324]  [<c0138d30>] worker_thread+0x0/0x100
[  731.287327]  [<c0138dd0>] worker_thread+0xa0/0x100
[  731.287332]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  731.287338]  [<c0138d30>] worker_thread+0x0/0x100
[  731.287341]  [<c013bb12>] kthread+0x42/0x70
[  731.287345]  [<c013bad0>] kthread+0x0/0x70
[  731.287349]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  731.287358]  =======================
[  731.287741] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  731.790453] ata2: hard resetting port
[  732.669168] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  732.669187] ata2: EH pending after 5 tries, giving up
[  732.669191] ata2: EH complete
[  732.754758] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x2 frozen
[  732.754776] ata2: hard resetting port
[  733.631755] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  733.639732] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  733.639769]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  733.639805]  [<c0131470>] process_timeout+0x0/0x10
[  733.639814]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  733.639826]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  733.639843]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  733.639854]  [<c0138331>] run_workqueue+0x81/0x110
[  733.639861]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  733.639868]  [<c0138d30>] worker_thread+0x0/0x100
[  733.639872]  [<c0138dd0>] worker_thread+0xa0/0x100
[  733.639876]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  733.639883]  [<c0138d30>] worker_thread+0x0/0x100
[  733.639886]  [<c013bb12>] kthread+0x42/0x70
[  733.639889]  [<c013bad0>] kthread+0x0/0x70
[  733.639893]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  733.639902]  =======================
[  733.640288] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  734.142991] ata2: hard resetting port
[  735.021719] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  735.029690] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  735.029728]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  735.029766]  [<c0131470>] process_timeout+0x0/0x10
[  735.029776]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  735.029788]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  735.029804]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  735.029815]  [<c0138331>] run_workqueue+0x81/0x110
[  735.029822]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  735.029829]  [<c0138d30>] worker_thread+0x0/0x100
[  735.029833]  [<c0138dd0>] worker_thread+0xa0/0x100
[  735.029837]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  735.029843]  [<c0138d30>] worker_thread+0x0/0x100
[  735.029847]  [<c013bb12>] kthread+0x42/0x70
[  735.029850]  [<c013bad0>] kthread+0x0/0x70
[  735.029854]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  735.029863]  =======================
[  735.030245] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  735.030252] ata2.00: limiting speed to UDMA7:PIO5
[  735.532949] ata2: hard resetting port
[  736.411682] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  736.419652] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  736.419682]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  736.419718]  [<c0131470>] process_timeout+0x0/0x10
[  736.419728]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  736.419740]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  736.419756]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  736.419768]  [<c0138331>] run_workqueue+0x81/0x110
[  736.419774]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  736.419781]  [<c0138d30>] worker_thread+0x0/0x100
[  736.419785]  [<c0138dd0>] worker_thread+0xa0/0x100
[  736.419789]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  736.419796]  [<c0138d30>] worker_thread+0x0/0x100
[  736.419799]  [<c013bb12>] kthread+0x42/0x70
[  736.419802]  [<c013bad0>] kthread+0x0/0x70
[  736.419806]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  736.419815]  =======================
[  736.420199] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  736.922912] ata2: hard resetting port
[  737.801644] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  737.801665] ata2: EH pending after completion, repeating EH (cnt=4)
[  737.801675] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1
[  738.516574] ata2: soft resetting port
[  738.672368] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  738.680336] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  738.680369]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  738.680405]  [<c0131470>] process_timeout+0x0/0x10
[  738.680414]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  738.680426]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  738.680443]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  738.680454]  [<c0138331>] run_workqueue+0x81/0x110
[  738.680461]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  738.680468]  [<c0138d30>] worker_thread+0x0/0x100
[  738.680472]  [<c0138dd0>] worker_thread+0xa0/0x100
[  738.680476]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  738.680483]  [<c0138d30>] worker_thread+0x0/0x100
[  738.680486]  [<c013bb12>] kthread+0x42/0x70
[  738.680489]  [<c013bad0>] kthread+0x0/0x70
[  738.680494]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  738.680503]  =======================
[  738.680886] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  739.183600] ata2: hard resetting port
[  740.062329] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  740.070299] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  740.070337]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  740.070375]  [<c0131470>] process_timeout+0x0/0x10
[  740.070385]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  740.070397]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  740.070413]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  740.070425]  [<c0138331>] run_workqueue+0x81/0x110
[  740.070432]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  740.070439]  [<c0138d30>] worker_thread+0x0/0x100
[  740.070442]  [<c0138dd0>] worker_thread+0xa0/0x100
[  740.070447]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  740.070453]  [<c0138d30>] worker_thread+0x0/0x100
[  740.070456]  [<c013bb12>] kthread+0x42/0x70
[  740.070459]  [<c013bad0>] kthread+0x0/0x70
[  740.070464]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  740.070473]  =======================
[  740.070856] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  740.070863] ata2.00: limiting speed to UDMA7:PIO5
[  740.573559] ata2: hard resetting port
[  741.452289] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  741.460262] WARNING: at /build/buildd/linux-source-2.6.22-2.6.22/drivers/ata/libata-core.c:4801 ata_hsm_move()
[  741.460293]  [<f892b0fb>] ata_hsm_move+0x16b/0x740 [libata]
[  741.460328]  [<c0131470>] process_timeout+0x0/0x10
[  741.460338]  [<c02f2d57>] schedule_timeout+0x47/0xd0
[  741.460350]  [<f892f527>] ata_pio_task+0x27/0xf0 [libata]
[  741.460367]  [<f892f500>] ata_pio_task+0x0/0xf0 [libata]
[  741.460378]  [<c0138331>] run_workqueue+0x81/0x110
[  741.460384]  [<c013bf80>] prepare_to_wait+0x20/0x70
[  741.460391]  [<c0138d30>] worker_thread+0x0/0x100
[  741.460395]  [<c0138dd0>] worker_thread+0xa0/0x100
[  741.460400]  [<c013bdd0>] autoremove_wake_function+0x0/0x50
[  741.460406]  [<c0138d30>] worker_thread+0x0/0x100
[  741.460409]  [<c013bb12>] kthread+0x42/0x70
[  741.460412]  [<c013bad0>] kthread+0x0/0x70
[  741.460417]  [<c0105487>] kernel_thread_helper+0x7/0x10
[  741.460426]  =======================
[  741.460808] ata2.00: failed to IDENTIFY (I/O error, err_mask=0x100)
[  741.963525] ata2: hard resetting port
[  742.842251] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[  742.842271] ata2: EH pending after completion, repeating EH (cnt=3)
[  742.842281] ata2: exception Emask 0x10 SAct 0x0 SErr 0x0 action 0x1

---

### Post by EvilNed on 2007-11-09
Just tried adding irqpoll, acpi=off, and all_generic_ide to the kernel boot line. Same issue, the hard drive errors out again.

---

### Post by EvilNed on 2007-11-12
Bump.

---

