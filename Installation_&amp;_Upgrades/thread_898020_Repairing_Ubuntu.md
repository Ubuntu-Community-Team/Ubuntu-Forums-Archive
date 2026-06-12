---
title: "Repairing Ubuntu"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by AuToFiRE on 2008-08-22
Hello, I was wondering if there is an automated way to repair Ubuntu, i have to boot in failsafe gnome because main gnome keeps locking up and i dont know why. Im currently up-to-date on all updates and running hardy

---

### Post by Diabolis on 2008-08-22
Do you get an error message? What does it say or what do you mean by locking up?

---

### Post by Cheesehead on 2008-08-22
Can you post copies of recent /var/log/syslog and /var/log/dmesg where the lockups occur?

Can you reproduce the lockup by any combinations of apps or actions?
Do you remember when it started locking up?
Was there a time when it *didn't* lockup for a longer-than-usual period?

Is your system a personal one or a server, used *primarily* for school/office apps, programming, or gaming?

Is it a stock 8.04 install, or is it heavily customized?

---

### Post by AuToFiRE on 2008-08-23
just the normal syslog/dmesg or one/all of the 7 .gz ones?

what i mean by locking up, it completely locks up, no messages, nothing, just complete freeze that requires hard reset
it is not modified in anyway, it is stock GNOME personal

It doesnt matter if there are apps running or not it will just eventually lock up after a couple minutes to several days(no idea how or why), a lot of the time its within the first 5 minutes even if its just sitting
the usual programs i run are as follows:
Firefox
Amsn

---

### Post by Diabolis on 2008-08-23
I had this behavior in my laptop and the first time happened because the CD-RW unit was not tightly connected, the second time happened because my hard drive had a scratch therefore a small section of it couldn't be read and the whole system froze whenever it tried to read that area. Both hardware problems occurred because I dropped the computer by accident. Could this be the case?

When its locked, can you go to a tty?
*you go to the first tty by pressing **<Ctrl><Alt>F1**. F1 to F6 are command line terminals, F7 is graphical mode.*

---

### Post by cariboo on 2008-08-23
Create a new user and see if it still locks up, If it doesn't just transfer your important files from your home directory to the new user and then try repairing the problem.

Jim

---

