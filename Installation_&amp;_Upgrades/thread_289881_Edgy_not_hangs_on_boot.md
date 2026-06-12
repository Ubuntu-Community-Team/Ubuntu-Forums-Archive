---
title: "Edgy not hangs on boot"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by b0ertje on 2006-10-31
Hi everybody!

I installed a clean version of edgy today on my Dell x200 Laptop. Unfortunately edgy is unable to boot. I get a kernel-oops from a modprobe after which the system is unable to recover correctly:

[17179595.212000] ISDN subsystem Rev: 1.1.2.3/1.1.2.3/1.1.2.2/1.1.2.3/1.1.2.2/1.1.2.2 loaded
[17179595.312000] HiSax: Linux Driver for passive ISDN cards
[17179595.312000] HiSax: Version 3.5 (module)
[17179595.312000] HiSax: Layer1 Revision 2.46.2.5
[17179595.312000] HiSax: Layer2 Revision 2.30.2.4
[17179595.312000] HiSax: TeiMgr Revision 2.20.2.3
[17179595.312000] HiSax: Layer3 Revision 2.22.2.3
[17179595.312000] HiSax: LinkLayer Revision 2.59.2.4
[17179595.320000] avma1_cs: testing i/o 0x140-0x147
[17179595.360000] avma1_cs: checking at i/o 0x140, irq 3
[17179595.360000] BUG: unable to handle kernel paging request at virtual address e82f5000
[17179595.360000]  printing eip:
[17179595.360000] e82f5000
[17179595.360000] *pde = 1ffeb067
[17179595.360000] Oops: 0000 [#1]
[17179595.360000] SMP 
[17179595.360000] Modules linked in: avma1_cs hisax crc_ccitt isdn slhc pcmcia joydev tsdev 3c59x mii yenta_socket rsrc_nonstatic pcmcia_core hw_random floppy snd_intel8x0 snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss shpchp pci_hotplug intel_agp agpgart evdev psmouse serio_raw snd_pcm snd_timer snd soundcore snd_page_alloc ext3 jbd ohci1394 ieee1394 uhci_hcd usbcore ide_generic ide_disk piix generic thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[17179595.360000] CPU:    0
[17179595.360000] EIP:    0060:[<e82f5000>]    Not tainted VLI
[17179595.360000] EFLAGS: 00010282   (2.6.17-10-generic #2) 
[17179595.360000] EIP is at 0xe82f5000
[17179595.360000] eax: 00000000   ebx: 00000000   ecx: e4451e2c   edx: e4451b8c
[17179595.360000] esi: e4451b8c   edi: e4451e2c   ebp: e441ebe0   esp: e4451b7c
[17179595.360000] ds: 007b   es: 007b   ss: 0068
[17179595.360000] Process modprobe (pid: 2906, threadinfo=e4450000 task=e687aa90)
[17179595.360000] Stack: e8409529 e8482480 e845d9d7 e4e5be00 61536948 e4410078 e441ebe0 c0122e9b 
[17179595.360000]        e4e5be00 e810251e e441ebe3 e810236d e81024b0 00000140 00000003 00000000 
[17179595.360000]        00010101 41000401 49000009 0007a120 00000041 00000000 0007a120 dffbd3c0 
[17179595.360000] Call Trace:
[17179595.360000]  <e8409529> hisax_init_pcmcia+0x89/0xd0 [hisax]  <c0122e9b> printk+0x1b/0x20
[17179595.360000]  <e810236d> avma1cs_probe+0x29d/0x3b0 [avma1_cs]  <c01d3d40> generic_make_request+0x150/0x200
[17179595.360000]  <e818c580> ext3_get_block+0x0/0x100 [ext3]  <c025a95b> ide_build_sglist+0x2b/0xd0
[17179595.360000]  <c012bb70> lock_timer_base+0x20/0x50  <c012bca7> __mod_timer+0xa7/0xd0
[17179595.360000]  <c01e0542> __next_cpu+0x12/0x20  <c011b22d> find_busiest_group+0xcd/0x2f0
[17179595.360000]  <c02d8dad> schedule+0x41d/0xcc0  <c011b8e7> activate_task+0x67/0xb0
[17179595.360000]  <c011aca4> __activate_task+0x14/0x30  <c011ba7e> try_to_wake_up+0x6e/0x3d0
[17179595.360000]  <c02d8dad> schedule+0x41d/0xcc0  <e830c6dc> pcmcia_device_probe+0x6c/0x120 [pcmcia]
[17179595.360000]  <c0245f44> driver_probe_device+0x44/0xc0  <c011d497> __cond_resched+0x17/0x30
[17179595.360000]  <c02460c2> __driver_attach+0x82/0x90  <c02458bb> bus_for_each_dev+0x3b/0x60
[17179595.360000]  <c0245e86> driver_attach+0x16/0x20  <c0246040> __driver_attach+0x0/0x90
[17179595.360000]  <c024552c> bus_add_driver+0x8c/0x140  <c02462f1> driver_register+0x41/0xa0
[17179595.360000]  <c013cda8> sys_init_module+0x148/0x19c0  <e830d000> pcmcia_request_irq+0x0/0x240 [pcmcia]
[17179595.360000]  <c0102fbb> sysenter_past_esp+0x54/0x79 
[17179595.360000] Code:  Bad EIP value.
[17179595.360000] EIP: [<e82f5000>] 0xe82f5000 SS:ESP 0068:e4451b7c
[17179595.360000]  <6>NET: Registered protocol family 17
[17179598.072000] NET: Registered protocol family 10
[17179598.072000] lo: Disabled Privacy Extensions
[17179598.072000] IPv6 over IPv4 tunneling driver
[17179608.660000] eth0: no IPv6 routers present

At this point the system hangs. So I guess modprobing some isdn-module (i don't use that) crashes the system. If I do a ctrl-alt-del now I get dumped into a shell which is pretty unuseable but at least I have basic networking and was able to cat the dmesg output to another machine.

Does anybody have an idea about that?

---

### Post by b0ertje on 2006-10-31
Update:

I booted the rescue system and added those lines to /etc/modprobe.d/blacklist

blacklist hisax
blacklist avma1_cs

Now the system boots. But I think this is a pretty serious bug!

---

