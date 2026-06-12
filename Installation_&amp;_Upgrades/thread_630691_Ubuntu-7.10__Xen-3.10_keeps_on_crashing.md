---
title: "Ubuntu-7.10 / Xen-3.10 keeps on crashing"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by PascalNobus on 2007-12-03
I'm trying to get configure a Xen-3.1 on Ubuntu 7.10 for days now, but it keeps crashing.
Everytime I try to make a domU my kernel panics.


I got errors like this:
kernel: [  263.314870] Bad page state in process 'makedev.postins'
kernel: [  263.314872] page:c18d32c0 flags:0x00000000 mapping:00000000 mapcount:0 count:0
kernel: [  263.314876] Trying to fix it up, but a reboot is needed
kernel: [  263.314878] Backtrace:
kernel: [  263.315532]  [bad_page+99/160] bad_page+0x63/0xa0
kernel: [  263.315592]  [destroy_compound_page+126/160] destroy_compound_page+0x7e/0xa0
kernel: [  263.315672]  [__free_pages_ok+964/976] __free_pages_ok+0x3c4/0x3d0
kernel: [  263.315701]  [mod_zone_page_state+61/144] mod_zone_page_state+0x3d/0x90
kernel: [  263.315738]  [pgd_free+179/288] pgd_free+0xb3/0x120
kernel: [  263.315745]  [kmem_cache_free+133/240] kmem_cache_free+0x85/0xf0
kernel: [  263.315751]  [pgd_free+179/288] pgd_free+0xb3/0x120
kernel: [  263.315784]  [pgd_free+179/288] pgd_free+0xb3/0x120
kernel: [  263.315797]  [__mmdrop+18/48] __mmdrop+0x12/0x30
kernel: [  263.315851]  [do_exit+289/2128] do_exit+0x121/0x850
kernel: [  263.315892]  [do_group_exit+38/144] do_group_exit+0x26/0x90
kernel: [  263.315925]  [syscall_call+7/11] syscall_call+0x7/0xb
kernel: [  263.315937]  [wait_for_completion_interruptible+304/336] wait_for_completion_interruptible+0x130/0x150
kernel: [  263.315950]  =======================
kernel: [  263.321312] Bad page state in process 'syslogd'
kernel: [  263.321315] page:c18d32e0 flags:0x00024000 mapping:00000000 mapcount:0 count:1048832
kernel: [  263.321319] Trying to fix it up, but a reboot is needed

kernel: [  956.980739] BUG: unable to handle kernel paging request at virtual address 012988d7
kernel: [  956.980843]  printing eip:
kernel: [  956.980878] c0176a14
kernel: [  956.980884] 0d661000 -> *pde = 00000000:36adc001
kernel: [  956.980924] 08adc000 -> *pme = 00000000:00000000
kernel: [  956.980965] Oops: 0000 [#1]
kernel: [  956.981001] SMP 
kernel: [  956.981053] Modules linked in: bridge ipv6 parport_pc lp parport loop af_packet shpchp pci_hotplug iTCO_wdt iTCO_vendor_support evdev ext3 jbd mbcache sg sd_mod ata_generic e1000 ata_piix libata scsi_mod uhci_hcd ehci_hcd usbcore raid10 raid456 xor raid1 raid0 multipath linear md_mod fuse apparmor commoncap
kernel: [  956.981541] CPU:    0
kernel: [  956.981542] EIP:    0061:[kmem_cache_zalloc+100/272]    Not tainted VLI
kernel: [  956.981543] EFLAGS: 00210006   (2.6.22-14-xen #1)
kernel: [  956.981648] EIP is at kmem_cache_zalloc+0x64/0x110
kernel: [  956.981686] eax: 0000c16f   ebx: 0126831b   ecx: 00000000   edx: c16deda0



I tried with images and LVM, but the same things happen.
Last time I followed the guide at
[http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories)


I changed the memory-cards (so that can't be the problem)
The disk's are in software raid, not giving 1 error. (so no disk problem)

The server is a Supermicro PDSMI+, with Dual Intel P4
2x SATA-disk in software Raid-1.


Is this a hardware incompatable problem?
Or am I just being stupid?

---

### Post by madman100 on 2007-12-03
hi m8 ? will   Xen  work on 7.10 with out a raid i tried it on 7.4 and it was crashing then 
thanks 
:confused:

---

### Post by PascalNobus on 2007-12-07
Solved the problem.
Seems like Hypertreading doesn't work with all the Motherboards.
After switching it off I got no more crashes.

---

### Post by cableroy on 2008-01-06
> **PascalNobus said:**
> Solved the problem.
Seems like Hypertreading doesn't work with all the Motherboards.
After switching it off I got no more crashes.

Hi

Did you see if your memory memory got used? i have a problem that the memory usage increases  while transfer files to the domU, when i stop the transfer the memory usage stops, but do not decrease, when i continue to transfer its starts again to its no more memory left and the domU dies. I can't figure out whats causing it... i think the same apply for dom0 so kernel bug?

---

