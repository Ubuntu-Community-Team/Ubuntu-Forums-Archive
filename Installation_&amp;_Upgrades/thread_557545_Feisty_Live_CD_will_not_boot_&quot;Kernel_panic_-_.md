---
title: "Feisty Live CD will not boot &quot;Kernel panic - sync error&quot;"
date: 2007-09-22
forum: Installation &amp; Upgrades
---

### Post by DeclanMcErlane on 2007-09-22
I'm having problems installing my feisty live CD on to an old RM connect computer that i nicked from school (they were going in the skip soon so I thought why not...). Aimed on using it as a torrent box and using my main computer only when I needed to do work but the old computer keeps coming up with the error "kernel panic - sync error: deleting idle tasks"(?) or something to that effect. Any ideas on what the problem could be? I can post a more detailed error report if needed.

---

### Post by Pumalite on 2007-09-22
Post specs

---

### Post by DeclanMcErlane on 2007-09-24
[   67.677132]  [<c012af50>] current_fs_time+0x50/0x60
[   67.677255]  [<c0158fed>] __generic_file_aio_write_nolock+0x2ed/0x610
[   67.677382]  [<c0159365>] generic_file_aio_write+0x55/0xd0
[   67.677506]  [<c0176355>] do_stnc_write+0xd5/0x120
[   67.677623]  [<c013adf0>] autoremove_wake_function+0x0/0x50
[   67.677744]  [<c0176c9e>] vfs_write+0xbe/0x190
[   67.677858]  [<c0176280>] do_sync_write+0x0/0x120
[   67.677974]  [<c0177421>] sys_write+0x41/0x70
[   67.678087]  [<c03dd3ea>] do_copy+0x8a/0xc0
[   67.678205]  [<c03daa6c>] write_buffer+0x1c/0x30
[   67.678321]  [<c03dab0e>] flush_window+0x7e/0xd0
[   67.678436]  [<c03db0b4>] inflate_codes+0x554/0x5b0
[   67.678555]  [<c03dc081>] inflate_dynamic+0x521/0x760
[   67.678694]  [<c03dcbde>] unpack_to_rootfs+0x7ae/0x960
[   67.678814]  [<c03dcddc>] early_populate_rootfs+0x4c/0x60
[   67.678933]  [<c03d77ea>] start_kernel+0x35e/0x420
[   67.679050]  [<c03d7230>] unknown_bootoption+0x0/0x250
[   67.679167]  =================
[   67.679237] Code: 2c 07 00 00 90 0f b3 8b 5c 01 00 00 b6 00 64 42 c0 09 c2 03
14 8d 00 fc 3c c0 c7 42 04 01 00 00 00 03 04 0d 00 fc 3c c0 89 30 90 <0f> ab 0f
5c 01 00 00 8b 47 24 05 00 00 00 40ff 15 90 53 3a c0
[   67.681781]  EIP:  [<c02ac5dd>] __sched_font_start+0x29d/0xa90 SS:ISP 0060:c03d
35ec
[   67.681965] <0> kernel panic - not syncing: Attempted to kill the idle task!
[   67.68.2009]

That should be all correct I think

---

### Post by Pumalite on 2007-09-24
I need your processor, memory, graphics, how many drives, etc.

---

### Post by DeclanMcErlane on 2007-09-25
This is not a normal computer. It's like a computer for logging on to a specific network that used to be in my school but that network is not used anymore. It will show the Windows 98 loading image then an RM Connect logon window. That is the reason I wanted to get the Live CD to boot which in turn would allow me to do a complete format of the HDD. How can I view the specs of the computer if I am unable to boot th Live CD or access the main Windows 98 desktop?

---

### Post by Pumalite on 2007-09-25
Catch-22

---

### Post by weedeatr on 2007-09-25
Try a mini iso wich is like 8mb
it worked on my crappy laptop and runs like a bomb now

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Officer Dibble on 2007-09-25
The simplest way I can think of to just wipe a drive without the use of the CD drive would be to get a floppy disk that boots to DOS, and copy onto that disk a program called Delpart.exe

Boot off the floppy, type delpart and then the rest of the menus are self explanatory. Fdisk would do the same but is a little more laborious.

---

### Post by weedeatr on 2007-09-25
> **DeclanMcErlane said:**
> This is not a normal computer. It's like a computer for logging on to a specific network that used to be in my school but that network is not used anymore. It will show the Windows 98 loading image then an RM Connect logon window. That is the reason I wanted to get the Live CD to boot which in turn would allow me to do a complete format of the HDD. How can I view the specs of the computer if I am unable to boot th Live CD or access the main Windows 98 desktop?
Use a windows cd at first.

---

