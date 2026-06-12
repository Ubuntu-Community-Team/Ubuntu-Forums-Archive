---
title: "Luckybackup Ubuntu 22.10 - Broken Pipe"
date: 2022-10-22
forum: Installation &amp; Upgrades
---

### Post by rudolf-kunzli on 2022-10-22
I just upgrade to Ubuntu 22.10 and almost everything went fine.
Except LuckyBackup that produces the following error message:

---
 [COLOR=#ff00ff]Removing old snapshots and logfiles of task: [/COLOR][COLOR=#ff00ff]backup rudolf[/COLOR]
=====================================

 

 Removed all older snapshots data
 

 Removing /home/rudolf/.luckyBackup/snaps/Ubuntu-backup rudolf-20221021234656.changes.log
 

 Removing /home/rudolf/.luckyBackup/logs/Ubuntu-backup rudolf-20221021234656.log
 =====================================
[COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]backup rudolf[/COLOR][COLOR=#ff00ff], starting[/COLOR]
Source : [COLOR=#0000ff]/home/rudolf[/COLOR]
Destination : [COLOR=#0000ff]/media/rudolf/Backup RK/home/[/COLOR] 
 building file list ... 
  0 files...
  100 files...
 
 ---snip---

 [COLOR=#ff0000]E[/COLOR][COLOR=#ff0000]RROR: rejecting excluded file-list name: rudolf/.luckybackup-snaphots rsync error: protocol incompatibility (code 2) at flist.c(994) [Receiver=3.2.5] [/COLOR]
  2800 files...

--- snip
 
 [COLOR=#ff0000]r[/COLOR][COLOR=#ff0000]sync: [sender] write error: Broken pipe (32) [/COLOR]
 .
 [COLOR=#00ffff]    -----| Backing-up profile, logfiles and snapshot data -> Ok |-----[/COLOR]
[COLOR=#ff00ff]execution of task : [/COLOR][COLOR=#ff00ff]backup rudolf[/COLOR][COLOR=#ff00ff], finished[/COLOR] 
=====================================

This worked perfectly before the upgrade...
It's produced on all 3 systems upgrade to 22.10

Any idea ?

---

### Post by rudolf-kunzli on 2022-10-24
You may close this thread. 
I don't think I'll get an answer here...

---

### Post by maglin2 on 2022-10-24
I believe you need to add  --trust-sender to the command.
It's an rsync issue that is fixed in 3.2.7 - if I find the link I'll add it.
Update
[https://sourceforge.net/p/luckybackup/discussion/873564/thread/0b74b43ac3/](https://sourceforge.net/p/luckybackup/discussion/873564/thread/0b74b43ac3/)
Though I think that perhaps only addresses the protocol error, not the broken pipe error.

---

### Post by rudolf-kunzli on 2022-10-24
> **maglin2 said:**
> I believe you need to add  --trust-sender to the command.
It's an rsync issue that is fixed in 3.2.7 - if I find the link I'll add it.
Update
[https://sourceforge.net/p/luckybackup/discussion/873564/thread/0b74b43ac3/](https://sourceforge.net/p/luckybackup/discussion/873564/thread/0b74b43ac3/)
Though I think that perhaps only addresses the protocol error, not the broken pipe error.

Thanks, I guess I'll wait for the updated rsync !
I'll using Grync meanwhile. At least this one works but has lesser options in excluding files...

---

### Post by maglin2 on 2022-10-24
> **rudolf-kunzli said:**
> Thanks, I guess I'll wait for the updated rsync !
I'll using Grync meanwhile. At least this one works but has lesser options in excluding files...

I have no idea when that will be. Maybe 23.04? I don't normally run anything but LTS, so I don't know if fixes (other than security) are rolled out during interim releases?
The --trusted-sender workaround described by Loukas seems to work for me.

---

### Post by rudolf-kunzli on 2022-10-24
> **maglin2 said:**
> I have no idea when that will be. Maybe 23.04? I don't normally run anything but LTS, so I don't know if fixes (other than security) are rolled out during interim releases?
The --trusted-sender workaround described by Loukas seems to work for me.

Okay!
I just had to look for the place to add **--trust-sender **but I found it in "Command Options".
Everything runs now finally !
Great - I appreciate your support !

---

