---
title: "Root filesystem going to Read-only Mode frquently"
date: 2021-08-08
forum: Installation &amp; Upgrades
---

### Post by muralikris39 on 2021-08-08
I have been facing read-only filesystem error issue for past few weeks after my SMPS failure. I replaced SMPS with new one and system started to boot up. But quite frquently I am experiencing my primary hard disk partition /dev/sda1 goes to read-only mode for some unknown reasons. I was on Kubuntu 18.04 when i faced the issue.

I tried fsck ,e2fsck as resolution steps those worked temporarily to get into read-write mode. e2fsck or smarmontools does not reveal any bad blocks either. I am attaching report of boot repair summary of my grub configuration.[https://paste.ubuntu.com/p/jRTVMSSMkJ/](https://paste.ubuntu.com/p/jRTVMSSMkJ/)

But whenever i start fresh again (booting up the system after a while) i begin to experience same issue again and again. I somehow managed to upgrade to 20.04 LTS and did grub update also. But read-only issue seem to happen again afraid this issue going to get worse resulting in hard disk failure.

[FONT=monospace][COLOR=#54ff54]**murali@murali-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ dmesg | grep -i ext4 [/COLOR]
[    2.021017] [COLOR=#ff5454]**EXT4**[/COLOR][COLOR=#000000]-fs (sda1): mounted filesystem with ordered data mode. Opts: (null) [/COLOR]
[    5.087078] [COLOR=#ff5454]**EXT4**[/COLOR][COLOR=#000000]-fs (sda1): re-mounted. Opts: errors=remount-ro[/COLOR]


[FONT=monospace][COLOR=#54ff54]**murali@murali-kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /var/log/syslog | grep sda1 [/COLOR]
Aug  9 00:01:29 murali-kubuntu kernel: [    1.088521]  sda: [COLOR=#ff5454]**sda1**[/COLOR][COLOR=#000000] sda2 sda3 sda4 < sda5 s[/COLOR]
da6 > 
Aug  9 00:01:29 murali-kubuntu kernel: [    2.050626] EXT4-fs ([COLOR=#ff5454]**sda1**[/COLOR][COLOR=#000000]): mounted filesystem[/COLOR]
 with ordered data mode. Opts: (null) 
Aug  9 00:01:29 murali-kubuntu kernel: [    5.133534] EXT4-fs ([COLOR=#ff5454]**sda1**[/COLOR][COLOR=#000000]): re-mounted. Opts: [/COLOR]
errors=remount-ro

[FONT=monospace][FONT=monospace][COLOR=#000000]Aug  9 07:54:11 murali-kubuntu kernel: [    2.021017] EXT4-fs (sda1): mounted filesystem[/COLOR]
 with ordered data mode. Opts: (null) 
Aug  9 07:54:11 murali-kubuntu kernel: [    5.087078] EXT4-fs (sda1): re-mounted. Opts: 
errors=remount-ro 
Aug  9 07:54:11 murali-kubuntu kernel: [    5.436163] lp: driver loaded but no devices f
ound

Will share any more specific outputs for guidance on better troubleshooting
[/FONT]
[/FONT][/FONT][/FONT]

---

### Post by coffeecat on 2021-08-09
Dupicate of [https://ubuntuforums.org/showthread.php?t=2465698](https://ubuntuforums.org/showthread.php?t=2465698)

Please do not post duplicates. This causes confusion and dilutes community efoort. Thread closed.

---

