---
title: "Help me i have a problem and dont know what to do"
date: 2012-01-02
forum: Installation &amp; Upgrades
---

### Post by zccrx91 on 2012-01-02
I put in the disk and installed everything and restarted after i got everything setup and then when i was looking around it froze so i pushed the power button and when i went to turn it back on the screen came up and says. Please help me i don't know what i need to do. the computer is a laptop dell vostro 1000 if you need to know more i will find that out as well. I used a disk and it 10.04 lts. I am not sure what to do if there is a way to take ubuntu out and reinstall it? any help would be better than nothing......
 
[ 2.365393] [<c020cb87>] ? vfs_kern_mount+0x67/0x170
[ 2.365435] [<c0221553>] ? get_fs_type+0x33/0xb0
[ 2.365477] [<c020ccee>] ? do_kern_mount+0x3e/0xe0
[ 2.365518] [<c0224693>] ? do_mount+0x1c3/0x200
[ 2.365560] [<c022473b>] ? sys_mount+0x1c3/0x200
[ 2.365601] [<c01033ec>] ? syscall_call+0x7/0xb
[ 2.365641] Code: 00 55 89 e5 57 89 c7 56 53 e8 b3 f7 22 00 8b 5f 04 b8 ff ff
ff ff 8b 77 08 eb 1c 8b b6 00 00 00 00 8b 0c 85 40 1e 7a c0 8b 57 14 <8b> 14 0a 
89 d1 c1 f9 1f 01 d3 11 ce 8d 48 01 a1 cc af 59 c0 ba
[ 2.367093] EIP: [<c035daea>] ___percpu_counter_sum+0x2a/0x70 SS: ESP 0068:fa691
7d6c
[ 2.367093] CR2: 00000000017bd000
[ 2.367890] ---[ end trace d396b554d7987805
 
 
killed
mount: mounting /dev on /root/ dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on/root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
 
 
 
BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntull) built - in - shell (ash)
Enter 'help' for a list of built in commands.

---

