---
title: "Printer error after upgrade to 8.10"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by guillot1 on 2008-11-13
I have upgrated from Hardy to Intrepid and cannot use printer anymore. Printer is Samsung ML-2510. I get a 'cups-missing-filter' message. When I look in System->Administration->Printing, I see

Printer State: Stopped - Filter "rastertospl2" for printer "ML-2510_Series" not available: No such file or directory

Any clue what to do ?

---

### Post by c0rd3l1a on 2008-11-20
Did you ever get this figured out? I'm having the same problem.

---

### Post by buffybot5 on 2008-12-05
Don't know if this helps: 
I had the same problem with my Samsung ML-2510 when I switched to Intrepid.  I went to System---> Administration-----> Printing and deleted the printer and disconnected the printer.  Then I reconnected it and added a new printer. It automatically found the drivers needed. It prints just fine now.  Good luck!

---

### Post by Decoy on 2009-01-21
Yeah, this really helps!

---

### Post by vixmusic01 on 2009-03-23
Hi this probably would have fixed my problem but * tried this first and I think I need to reset something*

I read a bug report that seemed to apply ==

I should just stay out of terminal . . . How do I get it out of complain mode?

victoria@u-live:~$ sudo aa-complain cupsd
Setting /etc/apparmor.d/usr.sbin.cupsd to complain mode.
victoria@u-live:~$ 

Thanks for the help.

Victoria

---

### Post by ginjer on 2009-03-31
I had the same problem after upgrading to 8.10 with a Samsung 1710.  I removed the printer from the Printer administrator, unplugged the printer.  Plugged it back in and magic happened. Happily printing again.

---

