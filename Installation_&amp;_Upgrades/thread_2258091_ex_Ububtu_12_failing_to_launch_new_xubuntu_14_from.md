---
title: "ex Ububtu 12 failing to launch new xubuntu 14 from USB"
date: 2014-12-24
forum: Installation &amp; Upgrades
---

### Post by T_S_O_P on 2014-12-24
I have a Fujitsu Amilo, originally with Vista. About 3 years ago I started using Ubuntu from memory stick, before eventually overwritung Vista, which was rubbish.

I kept getting power failings not long after and along with a change around in the house, stored the Amilo until now. Wanted to put xubuntu or ubuntu on the maching and prepared a USB loader. Whether i run xubuntu from USB or install xubuntu, the instilation fails. I get the following code:

[    0.864518] Kernel panic – not syncing: VFS; Unable to mount root on unknown-block(2,0)
[    0.864585] CPU: 0 PID: 1 Comm: swapper/0 Not tainted 3.13.0-32-generic #57Ubuntu
[    0.864647] Hardware name: FUJITSU SIEMENS Amilo Desktop PI3745A/MS-7504VP-PV, BIOS V3.0V 04/10/2009
[    0.864710] 00000000 00000000 f3091ec4 c1650cd3 f3091f10 f3091ee4 c164be0c cl82d0b4
[    0.865201] c1aabc80 a01f32c2 f3091f10 00008001 f3387000 f3091f40 c19b4f86 cl81be40
[    0.865691] f3091f19 f3091f10 fffffffa 00000000 f338713b 00000000 f485e0e0 fffffffa
[    0.866181] Call Trace: 
[    0.866244] [<c1650cd3>] dump_stack+0x41/0x52
[    0.866306] [<c164be0c>] panic+0x87/0x181
[    0.866367] [<c19b4f86>] mount_block_root+0x1e2/0x254
[    0.866427] [<c19b5171>] mount_root+0x5b/0x61
[    0.866487] [<c19b52c5>] prepare_namespace+0x14e/0x192
[    0.866548] [<c19b4cd0>] kernel_init_freeable+0x1d9/0x1e6
[    0.866609] [<c19b4524>] ? do_early_param+0x78/0x78
[    0.866669] [<c1647060>] kernel_init+0x10/0x100
[    0.866730] [<c165ef37>] ret_from_kernel_thread+0x1b/0x28
[    0.866791] [<c1647050>] ? rest_init+0x70/0x70

can anyone help?

---

### Post by mörgæs on 2014-12-25
Does the USB stick boot in another computer?

---

