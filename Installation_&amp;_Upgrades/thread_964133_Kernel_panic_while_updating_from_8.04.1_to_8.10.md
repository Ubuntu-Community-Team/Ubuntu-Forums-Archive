---
title: "Kernel panic while updating from 8.04.1 to 8.10"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by Dumdideldum on 2008-10-30
I started an update from 8.04.1 to 8.10 using the alternate-cd and the script cdupgrade.
Everything went well, the updater gui fetched packages both from the CD and the WWW till it stuck during the package installation with a nasty kernel panic - that means a full lock up.

I am currently trying to get a basic working installation back using the old kernel 2.6.24 recovery options - 2.6.27 wont boot at all and I dont want to mess up my system anymore with the automatic repair from CD. I pinned to problem to the moment when it runs "Generating locales" which displays the error:

de_AT.UTF-8 Eek! page_mapcount(page) went negative !

and then a kernel crash log and the final message to reboot the system.


Any ideas?

thx

---

### Post by Dumdideldum on 2008-10-30
well, I have now kinda solved this nasty problem with some dirty file editing, namely /var/lib/locales/supported.d/de en and local.

Just put a comment # in front of all locales, despite my main one, de_AT.UTF_8 - that did the trick. I still would be very interested, what the problem was ...

---

### Post by Dumdideldum on 2008-10-30
.. and again a lockup while generating locales, different point of installation point. grrrr :(

Edit:
Finally, my system is booting up and is more or less usable, even gnome. Totally purging locales did the trick - but as I need locales, I am still trying to get it done, with no luck.

Here is the kernel output regarding locales:
```

Oct 31 02:32:51 amd64 kernel: [  395.934804] localedef[7998]: segfault at 0 ip 000000000043a20e sp 00007fffce59a718 error 4 in localedef[400000+49000]
Oct 31 02:32:51 amd64 kernel: [  395.945398] Eeek! page_mapcount(page) went negative! (-16777216)
Oct 31 02:32:51 amd64 kernel: [  395.945409]   page pfn = ce9e
Oct 31 02:32:51 amd64 kernel: [  395.945410]   page->flags = 100000000000068
Oct 31 02:32:51 amd64 kernel: [  395.945412]   page->count = 1
Oct 31 02:32:51 amd64 kernel: [  395.945413]   page->mapping = 00ff88002989fe01
Oct 31 02:32:51 amd64 kernel: [  395.945434]   vma->vm_ops = 0x0
Oct 31 02:32:51 amd64 kernel: [  395.945451] ------------[ cut here ]------------
Oct 31 02:32:51 amd64 kernel: [  395.945453] kernel BUG at /build/buildd/linux-2.6.27/mm/rmap.c:662!
Oct 31 02:32:51 amd64 kernel: [  395.945455] invalid opcode: 0000 [1] SMP 
Oct 31 02:32:51 amd64 kernel: [  395.945457] CPU 0 
Oct 31 02:32:51 amd64 kernel: [  395.945459] Modules linked in: binfmt_misc prism2_usb p80211 ppdev cpufreq_ondemand cpufreq_powersave cpufreq_conservative cpufreq_stats freq_table cpufreq_userspace pci_slot container video output sbs wmi sbshc battery ipv6 iptable_filter ip_tables x_tables dm_crypt crypto_blkcipher dm_mod ac it87 hwmon_vid sbp2 parport_pc lp parport pcspkr snd_hda_intel k8temp joydev usblp evdev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd soundcore i2c_nforce2 button snd_page_alloc i2c_core shpchp pci_hotplug ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg pata_acpi ata_generic usbhid hid ohci1394 ieee1394 pata_amd sata_nv skge forcedeth libata scsi_mod dock ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Oct 31 02:32:51 amd64 kernel: [  395.945508] Pid: 7998, comm: localedef Not tainted 2.6.27-7-generic #1
Oct 31 02:32:51 amd64 kernel: [  395.945510] RIP: 0010:[<ffffffff802ca891>]  [<ffffffff802ca891>] page_remove_rmap+0x121/0x130
Oct 31 02:32:51 amd64 kernel: [  395.945518] RSP: 0018:ffff88003783daf8  EFLAGS: 00010246
Oct 31 02:32:51 amd64 kernel: [  395.945519] RAX: 0000000000000000 RBX: ffffe2000033a780 RCX: 0000000000000000
Oct 31 02:32:51 amd64 kernel: [  395.945521] RDX: 00000000ffffffff RSI: 0000000000000046 RDI: 0000000000000246
Oct 31 02:32:51 amd64 kernel: [  395.945523] RBP: ffff88003783db08 R08: 0000000000000000 R09: 0000000000000006
Oct 31 02:32:51 amd64 kernel: [  395.945525] R10: ffff88003783d768 R11: ffff8800b783d877 R12: ffff88003d921c60
Oct 31 02:32:51 amd64 kernel: [  395.945527] R13: 00007fffc4670000 R14: ffff880032400380 R15: ffff88003783dca8
Oct 31 02:32:51 amd64 kernel: [  395.945530] FS:  00007fffc65766e0(0000) GS:ffffffff806e1a80(0000) knlGS:00000000f7338920
Oct 31 02:32:51 amd64 kernel: [  395.945532] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Oct 31 02:32:51 amd64 kernel: [  395.945534] CR2: 0000000000000000 CR3: 0000000016ddd000 CR4: 00000000000006e0
Oct 31 02:32:51 amd64 kernel: [  395.945536] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Oct 31 02:32:51 amd64 kernel: [  395.945538] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Oct 31 02:32:51 amd64 kernel: [  395.945541] Process localedef (pid: 7998, threadinfo ffff88003783c000, task ffff88003d9d1670)
Oct 31 02:32:51 amd64 kernel: [  395.945543] Stack:  ffffe2000033a780 ffff88000100f8a0 ffff88003783db98 ffffffff802beef2
Oct 31 02:32:51 amd64 kernel: [  395.945547]  0000000000000001 000000000000000c ffffe20000c90000 800000000ce9e067
Oct 31 02:32:51 amd64 kernel: [  395.945551]  ffffe20000c90010 00007fffc4800000 ffff88003d921c60 ffff88003c9416c0
Oct 31 02:32:51 amd64 kernel: [  395.945554] Call Trace:
Oct 31 02:32:51 amd64 kernel: [  395.945558]  [<ffffffff802beef2>] zap_pte_range+0x1f2/0x400
Oct 31 02:32:51 amd64 kernel: [  395.945561]  [<ffffffff802c015a>] unmap_page_range+0x2da/0x360
Oct 31 02:32:51 amd64 kernel: [  395.945565]  [<ffffffff802c09df>] unmap_vmas+0x17f/0x2b0
Oct 31 02:32:51 amd64 kernel: [  395.945568]  [<ffffffff802c4f65>] exit_mmap+0x95/0x120
Oct 31 02:32:51 amd64 kernel: [  395.945571]  [<ffffffff8024ca20>] mmput+0x40/0xe0
Oct 31 02:32:51 amd64 kernel: [  395.945574]  [<ffffffff8025114e>] exit_mm+0x11e/0x160
Oct 31 02:32:51 amd64 kernel: [  395.945580]  [<ffffffff80502446>] ? _spin_lock_irq+0x16/0x20
Oct 31 02:32:51 amd64 kernel: [  395.945582]  [<ffffffff8025319a>] do_exit+0x19a/0x410
Oct 31 02:32:51 amd64 kernel: [  395.945585]  [<ffffffff80253457>] do_group_exit+0x47/0xc0
Oct 31 02:32:51 amd64 kernel: [  395.945590]  [<ffffffff8025eaec>] get_signal_to_deliver+0x1ac/0x3a0
Oct 31 02:32:51 amd64 kernel: [  395.945593]  [<ffffffff80253e79>] ? set_normalized_timespec+0x9/0x90
Oct 31 02:32:51 amd64 kernel: [  395.945597]  [<ffffffff802124a5>] do_signal+0x75/0x200
Oct 31 02:32:51 amd64 kernel: [  395.945602]  [<ffffffff802461f3>] ? hrtick_start_fair+0x173/0x190
Oct 31 02:32:51 amd64 kernel: [  395.945605]  [<ffffffff805005b4>] ? thread_return+0x37/0x3c3
Oct 31 02:32:51 amd64 kernel: [  395.945608]  [<ffffffff802441ab>] ? finish_task_switch+0x2b/0xf0
Oct 31 02:32:51 amd64 kernel: [  395.945611]  [<ffffffff805005b4>] ? thread_return+0x37/0x3c3
Oct 31 02:32:51 amd64 kernel: [  395.945614]  [<ffffffff8021265d>] do_notify_resume+0x2d/0x50
Oct 31 02:32:51 amd64 kernel: [  395.945617]  [<ffffffff802130c4>] retint_signal+0x60/0xbc
Oct 31 02:32:51 amd64 kernel: [  395.945619] 
Oct 31 02:32:51 amd64 kernel: [  395.945620] 
Oct 31 02:32:51 amd64 kernel: [  395.945621] Code: e8 15 f9 ff ff 49 8b 84 24 90 00 00 00 48 85 c0 74 19 48 8b 40 20 48 85 c0 74 10 48 8b 70 58 48 c7 c7 00 50 5f 80 e8 ef f8 ff ff <0f> 0b eb fe 66 66 2e 0f 1f 84 00 00 00 00 00 55 48 89 e5 41 57 
Oct 31 02:32:51 amd64 kernel: [  395.945645] RIP  [<ffffffff802ca891>] page_remove_rmap+0x121/0x130
Oct 31 02:32:51 amd64 kernel: [  395.945647]  RSP <ffff88003783daf8>
Oct 31 02:32:51 amd64 kernel: [  395.945650] ---[ end trace 357ac21820ad3e45 ]---
Oct 31 02:32:51 amd64 kernel: [  395.945652] Fixing recursive fault but reboot is needed!

```

---

### Post by Dumdideldum on 2008-11-01
Update:
Seems like this is a kernel bug, not a bug in locales package ?

[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg582220.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg582220.html)

---

### Post by cdude on 2008-11-01
I have the same problem; even the the liveCD 8.10 boots with this kernel panic message.

EDIT: just an update, even openSUSE 11.1 Beta 3 fails to boot on my system - same error. I believe the bug is in the new kernel (2.6.27). My system is LG laptop ls50.

---

