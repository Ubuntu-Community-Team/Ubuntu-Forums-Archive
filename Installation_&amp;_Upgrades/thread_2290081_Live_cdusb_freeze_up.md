---
title: "Live cd/usb freeze up"
date: 2015-08-09
forum: Installation &amp; Upgrades
---

### Post by michael14 on 2015-08-09
when i am on live usb yesterday the system froze up making me have to force a shutdown.. this has happened twice but not in a row it happened days apart. What could have caused it you think and would it happen once i get it installed?

---

### Post by VMC on 2015-08-09
Did it freeze upon booting or during live usage?

Need your hardware info. Might try using 'nomodeset' for the kernel booting.

---

### Post by michael14 on 2015-08-09
> **VMC said:**
> Did it freeze upon booting or during live usage?

Need your hardware info. Might try using 'nomodeset' for the kernel booting.

It didn't freeze up during boot. Booting up was so fast it happened during live usage after like i guess 2 or 3 hours of using it.
I'm windows 8.1 right now, and all my specs are on [http://speccy.piriform.com/results/1vExsVZ00tU8NcDQrtSsdpC](http://speccy.piriform.com/results/1vExsVZ00tU8NcDQrtSsdpC) I just used speccy to publish a snapshot of the info.

---

### Post by michael14 on 2015-08-09
do you think it would happen once installed?

---

### Post by NathanRodriguez on 2015-08-09
Hard to say, see if you can reproduce the freeze to determine the application causing it.

---

### Post by michael14 on 2015-08-09
> **NathanRodriguez said:**
> Hard to say, see if you can reproduce the freeze to determine the application causing it.

I was mostly using google chrome and HexChat on the live preview.. i didn't have the security fixes installed on the live preview.

---

### Post by VMC on 2015-08-09
Check the log files. using file manager open either/or "/var/log/syslog", "/var/log/kern.log". They are rather lengthy files. Look for the date it failed and search for any unusual error messages.

---

