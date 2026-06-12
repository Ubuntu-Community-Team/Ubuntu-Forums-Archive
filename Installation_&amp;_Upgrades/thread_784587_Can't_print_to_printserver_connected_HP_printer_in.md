---
title: "Can't print to printserver connected HP printer in ubuntu 8.04 (that works in 7.10)"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by adonet on 2008-05-06
I'm not able to print to my HP Laserjet 4000 printer when I use Ubuntu 8.04 (Hardy). When I use Ubuntu 7.10 (Gutsy) on the same PC (another partition with dual boot) it all works fine. I installed the printer on the same way. Re-installing the printer doesn't help. Removing hplip and CUPS and re-installing these packages does't help.

When I try to print anything the printopdrachtbeheerder (screen where I see the printing commands) sometimes accepts the printcommand, and sometimes it doesn't. After a while it asks me If the printer is connected or not.

When in a console I give this command: sudo hp-check -r
it gives one error and one warning:

There are no CUPS printer queues found

and

Checking SIP version...
error: SIP not installed or version not found.

Checking for CUPS...
Status: taakplanner is actief
Version: 1.3.7
error_log is set to level: warn

I cant find a way to add any CUPS printer Queue and SIP is not in my repositories. 


I can ping the printserver. It has a valid IP nr  (192.168.2.10) and replies. I can login to the printserver and find all the communication methods are turned on.

I tried:   socket://192.168.2.10:9100 as printer port. Does't work (though it works in Gutsy (7.10)
I tried  ipp://192.168.2.10/printers/1   Doesn't work
I tried lpd://192.168.2.10   Doesn't work

The printer cannot be browsed for (it couldn't in 7.10 Gutsy too) 

I tried tot install hplip 2.8.4 from the HP website without any result. The HP device manager that comes with it doesn't see the connected printer.

What can I do apart from downgrading to Ubuntu 7.10 ?

Any help or suggestions would be very nice.

Jeroen

---

### Post by Fernando Negro on 2008-05-09
Could it be [_this_]("http://ubuntuforums.org/showthread.php?t=661752") problem?

In hardy my HP printer was not detected anymore also, and after I added ",[my username]" in the "scanner:x:105:hplip" line in the /etc/group file it solved the problem.

(scanner:x:105:hplip -> scanner:x:105:hplip**,username**)

(:x = two dots (":") and an "x", not an angry face as it is automatically converted)

---

### Post by adonet on 2008-05-09
Thanks, but no, my username was already in that group. My printer is NOT a USb printer. Its a parallel HP Laserjet 4000 printer connected to a sitecom printserver. The printserver is connected to my router with a fixed IP address. If I ping this IP nr, I receive nice answers. So the printserver is connected
In Gutsy I use printerpoort



```
socket://192.168.2.10:9100
```

and it works. In Hardy it doesn't.



```
sudo hp-setup
```

doesn't see my printer and I can't print.

Does anyone have another idea?

Thanks

---

