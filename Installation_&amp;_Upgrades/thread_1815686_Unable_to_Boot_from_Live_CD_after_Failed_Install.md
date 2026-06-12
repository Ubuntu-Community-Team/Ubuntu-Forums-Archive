---
title: "Unable to Boot from Live CD after Failed Install"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by Abstruse on 2011-07-31
I inherited an "ancient" computer (AMD Athlon XP2000 1.66GHz with 896 MB RAM) and decided that the most current operating system to put on it that might actually do what I want it to is Ubuntu. I downloaded the 11.04 32 bit CD and everything goes great. Boots to the CD, select to install to the hard drive (not my computer so I don't care about data), and I'm surprised it asks me to do stuff while it's installing (I'm used to Windows where you sit around 20 minutes, then spend 10 minutes setting time zones and accounts).

Anyway, I get through the installation to the point of it asking me to set up an account, password, and computer name. I was distracted trying to come up with a name for the computer that fit my naming scheme, and by the time I was typing it in, the monitor suddenly lost signal. I know it was at the point of copying files, but not sure how much beyond that it was. I let it sit for about 15 minutes waiting to see if it'd come back on its own, but it didn't. I restarted with the CD in the drive thinking I could just boot off the CD again, repartition, reformat, and reinstall.

When I attempted to boot, I got this error message:

```
Kernal panic - not synching: Attempted to kill init!
Pid: 1, comm: run-init Not tainted 2.6.38-3-generic #42-Ubuntu
Call Trace:
 [KC1507054>] ? panic+0x5c70x157
 [KC10531e8>] ? forget_original_parent+0x1f8/0x200
 [KC10dbc0c>] ? perf_event_exit_task_context+0x2c/0x130
 [KC10b4582>] ? call_rcu_sched+0x12/0x20
 [KC1053203>] ? exit_notify+0x13/0x150
 [KC1053a50>] ? do_exit+0x180/0x350
 [KC1301430>] ? redirected_tty_write+0x0/0xa0
 [KC1053d38>] ? sys_exit+0x18/0x20
 [KC1509bf4>] ? syscall_call+0x7/0xb
panic occurred, switched back to text console
```(There were numbers in front, but I strained my eyes enough to see what I got. If it's important, I can retype them. They were all 155.something)

Everytime I reboot now, whether it's a reboot or a cold restart, I get the same errors. I tried booting without the CD and it's not recognizing the hard drive at all.

I'm burning the 10.04 CD to see if that works, but I'd really rather install right off. I haven't used Linux regularly in over a decade and I'm nervous enough as it is (which is why this is going on a computer I have no use for otherwise). If there's any further information you need, please let me know.

Update: Attempted to boot off of the 10.04 CD and it's freezing on the splash screen. When I drop down to the text to see what's going on, it looks like the same thing in slow motion: "Kernal panic - not syncing: Attempted to kill init!" Only this time, it takes 10 minutes or so rather than the previous 3-5 minutes for it to crash out. Also, after it does this, there's nothing I can do other than a warm or cold reboot as none of the keys do anything.

Update 2: Decided to try reformatting and installing Windows XP again then start over with ubuntu. First attempt to load the Windows installation CD failed, but the second time it worked. Going to let it have fun formatting for the next 30-45 minutes at this pace :/ Will update again if this still doesn't work or if anyone has any other suggestions.

---

