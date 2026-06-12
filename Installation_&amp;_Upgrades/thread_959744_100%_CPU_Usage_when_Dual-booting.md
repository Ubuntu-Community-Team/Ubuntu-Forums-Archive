---
title: "100% CPU Usage when Dual-booting"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by techlover on 2008-10-26
So I've just started dual-booting with Windows xp on C drive and Ubuntu 8.0.4 on D drive on my laptop.

I happen to realize that my CPU fan spins more vigorously now when I'm running xp.  I checked the CPU usage and it is always at 100% even after I've turned off all/most non-windows applications.  For now, I've temporary reduced my CPU speed to prevent any overheating issues.

Any idea how to solve the CPU usage problem or is it just a norm for dual-booting?

Thanks.

---

### Post by loell on 2008-10-26
strange, dual booting shouldhave no effect on your cpu usage.

have you check what process(es) that occupies the cpu in  XP?

---

### Post by techlover on 2008-10-26
It seems monitor.exe is taking up all the CPU.  BTW i don't know if this would help in the diagnosis, but I'm using an acer and after dual-booting, I've to manually end "erecovery.exe" whenever I restart/shutdown windows.

---

### Post by loell on 2008-10-26
if i'm not mistaken monitor.exe is the Task manager itself? and its giving the high cpu usage? ;)  


yeah, upon googling **"erecovery.exe"** is an acer utility , can you try reinstalling it? if you still need it. or better yet just uninstall it.

---

### Post by Shazaam on 2008-10-26
Is your Ubuntu install a WUBI install in Windows? You might need more RAM (memory).

---

### Post by ukera on 2008-10-26
hmm try deleting Windows XP fully.  i'm 100% sure that will solve it :P

---

### Post by loell on 2008-10-26
> **ukera said:**
> hmm try deleting Windows XP fully.  i'm 100% sure that will solve it :P

no sarcasm please :)

---

### Post by techlover on 2008-10-26
I think I figured it out.  Monitor.exe is not a windows program.  It's Acer's and has something to do with erecovery.  Anyway, all I have to do is to disable it and I should be good.

Just to put up the link for people who might encounter the same problem in future:
[http://nerd.steveferson.com/2007/06/28/stop-monitorexe-hogging-cpu/](http://nerd.steveferson.com/2007/06/28/stop-monitorexe-hogging-cpu/)

---

