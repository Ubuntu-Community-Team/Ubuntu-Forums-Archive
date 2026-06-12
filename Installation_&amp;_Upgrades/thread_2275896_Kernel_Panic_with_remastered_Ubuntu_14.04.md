---
title: "Kernel Panic with remastered Ubuntu 14.04"
date: 2015-04-29
forum: Installation &amp; Upgrades
---

### Post by Manjukiran_S on 2015-04-29
I see a kernel panic when I try to boot up certain systems using a remastered LiveUSB. The same LiveUSB works (boot/install) on some other PCs.
I have created the ISO file from which I am building the LiveUSB using remastersys (Backup option).
The ISO file is based on Ubuntu 14.04 LTS.
Remastering the ISO file is done inside a VirtualBox Guest Ubuntu 14.04 (Host machine is Mint 17)

I have attached a screenshot of the kernel panic, but I think it is not of much use.
Kernel panic - not syncing: Attempted to kill init! exitcode = 0x00000100

[FONT=courier new]CPU: 1 PID: 1Comm: run-init Not tainted 3.16.0.34-generic #47~14.04.1-Ubuntu
Hardware name: Dell Inc. Vostro 3900 /OT1D10       , BIOS A06 08/19/2014
00000000 00000000 f146df34 c168d22a c1990400 f146dfS4 c1687536 c187cd20
c1b0ac80 f146df40 c1990400 f7163a40 f14c8000 f146dfa4 c105ecbf c157d0b4
00000100 c118edb4 00000001 00000001 00000000 f0273e48 f02ad224 f0273e40
Call Trace:
[<c168d22a>] dump_stack+0x41/0x52
[<c1687536>] panic+0x87/0x1a5
[<c105ecbf>] do_exit+0x8df/0x8e0
[<c118edb4>] ? vfs_write+0x144/0x1d0
[<c105ecf6>] SyS_exit+0x16/0x20
[<c1694709>] sysca11_ca11+0x7/0x7
Kernel Offset: 0x0 frum 0xc1000 (relocation rnge: 0xc000000-0xf7ffdfff)
drm_kms_helper: panic occurred, switching back to text console[/FONT]


Since the LiveDVD (LiveUSB) works on some systems and does not work on others, I suspect a hardware setting. I am thinking of varying the Enable PAE/NX, Enable VT-x/AMD-V, Enable Nested Paging settings in the Ubuntu VirtualMachine setting before remastering, as I read somewhere. Is it going to help. What is the approach I should follow.
[ATTACH=CONFIG]261634[/ATTACH]

---

