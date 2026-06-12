---
title: "Installation Freezing"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by trirnoth on 2007-05-07
Installation Freeze.

I've read through multiple forums and tried just about everything I could think of ... so apologies if I am missing something obvious.

I've attempted to install both the 7.04 "Standard personal computer (x86 architecture, PentiumTM, CeleronTM, AthlonTM, SempronTM)" and the "64bit AMD and Intel computers" versions.

**Hardware:**
- ASUS A8V DELUXE Socket 939 VIA K8T800 Pro ATX AMD Motherboard
- OCZ Peroformance 1GB (2 x 512MB) 184-Pin DDR SDRAM DDR 433
- AMD Athlon 64 3500+ Newcastle 2.2GHz Socket 939 Processor
- NVIDIA 5200 FX Ultra

Almost every time (gotta be over twenty tries) this locks up when copying the files.
Initially I would install additional software along with the Nvidia drivers, but not after the first two times of this crashing.

**Things I have tried:**
- Used memtest without any errors.
- Upgraded the BIOS.
- Disabled all onboard devices.
- Removed all non-essential hardware (webcam, tvtuner, additional nic card, ...).
- Tried a different hard drive, power supply, and video card (nvidia 7600GS).
- passed kernel parameters (not always all at the same time) acpi=off noapic nosmp maxcpus=1 nolapic acpi=force irqpoll...

I opened a terminal before the installation in hopes of some sort of output. The one time this crashed but did not lock up, I was able to get the the output at the end of this post.
Can't say whether the this will be related to the freeze since this was the one time I could actually get output to copy.

I had been running FC3 successfully since it's release. Being time for an OS upgrade and thrilled with my Ubuntu Desktop at work, wanted this at home as well.

Apologies also for the length of this post and thanks for your time.
Let me know of any additional information required - I didn't want the initial post to be a book.

**OUTPUT:**
Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] Oops: 0002 [#1]

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] SMP 

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] CPU:    0

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] EIP:    0060:[radix_tree_insert+404/480]    Not tainted VLI

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] EFLAGS: 00010046   (2.6.20-15-generic #2)

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] EIP is at radix_tree_insert+0x194/0x1e0

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] eax: ffffffef   ebx: 00000000   ecx: 00000000   edx: e75be1bc

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] esi: 00000000   edi: 00000000   ebp: 00000000   esp: e1e5fd30

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] Process install.py (pid: 12214, ti=e1e5e000 task=e2e16a90 task.ti=e1e5e000)

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] Stack: 00000000 e75be1bc c179e980 00000000 e75be1b8 c179e980 00000000 c0157374 

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]        00000000 00000000 0838db8c 00000000 c015874d 000000d0 e75be1b8 00000003 

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]        00000001 e1e5fedc 00000001 c019756a dd011f00 f8e1f000 e75be114 c179e980 

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] Call Trace:

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [add_to_page_cache+84/160] add_to_page_cache+0x54/0xa0

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [generic_file_buffered_write+285/1744] generic_file_buffered_write+0x11d/0x6d0

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [__find_get_block+154/448] __find_get_block+0x9a/0x1c0

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [<f8e13269>] add_dirent_to_buf+0x129/0x2d0 [ext3]

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [current_fs_time+80/96] current_fs_time+0x50/0x60

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [__generic_file_aio_write_nolock+749/1552] __generic_file_aio_write_nolock+0x2ed/0x610

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [generic_file_aio_write+85/208] generic_file_aio_write+0x55/0xd0

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [file_read_actor+0/240] file_read_actor+0x0/0xf0

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [<f8e0d5c0>] ext3_file_write+0x30/0xc0 [ext3]

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [do_sync_write+213/288] do_sync_write+0xd5/0x120

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [autoremove_wake_function+0/80] autoremove_wake_function+0x0/0x50

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [do_mmap_pgoff+1348/1968] do_mmap_pgoff+0x544/0x7b0

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [vfs_write+190/400] vfs_write+0xbe/0x190

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [do_sync_write+0/288] do_sync_write+0x0/0x120

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [sys_write+65/112] sys_write+0x41/0x70

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  [sysenter_past_esp+105/169] sysenter_past_esp+0x69/0xa9

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000]  =======================

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] Code: ff ff 5b 5e 5f 5d c3 8b 44 24 04 e8 a7 f9 ff ff 85 c0 74 e6 85 ed 89 18 74 32 83 45 04 01 89 44 bd 10 e9 5f ff ff ff 8b 54 24 04 <83> 4c 24 08 01 8b 4c 24 08 8b 42 04 89 4a 08 a9 00 00 10 00 75 

Message from syslogd@ubuntu at Sun May  6 08:50:04 2007 ...
ubuntu kernel: [  458.204000] EIP: [radix_tree_insert+404/480] radix_tree_insert+0x194/0x1e0 SS:ESP 0068:e1e5fd30

---

### Post by trirnoth on 2007-05-18
For those here possibly looking for an answer, I believe I have found it.
At the very least I have been able to install and have a stable running system for nearly a week and counting.

I went to install Windows. I know, something I haven't had to do in a long long time for home consumption. But I figured that if this errored out, I would have more information to work off of.

It failed with irq_not_less_or_equal_to (or something like that, this was nearly a week ago). Narrowing this down to a fresh install, obviously not a driver issue, new software install, ... I found a forum where someone had a similar issue.

Ended up being my BIOS was set to Auto for overclocking. Something I never changed - there by default.
A sensor on the board maybe made this think to go full tilt? Regardless, setting this to actual values (no overclocking) I was able to install Ubuntu.

---

