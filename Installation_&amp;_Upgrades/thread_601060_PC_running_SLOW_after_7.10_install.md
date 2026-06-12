---
title: "PC running SLOW after 7.10 install"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by hodad on 2007-11-02
I just installed 7.10 fresh last week on my AMD64 machine. I also installed a newer, larger hard drive, and installed 7.10 onto it. I can still access the older drive, and have transferred my older files onto the newer drive.

Everything works fine, but it runs VERY SLOW! All applications run slowly, not just startup. Internet has slowed to a crawl as well.

A few more details:
Running System Monitor shows no unusual activity (cpu and memory running about 30% when I start Open Office, and less when idle).
I suspect it has something to do with the second drive, but I can disconnect the second (smaller) drive connector, and the pc boots up just fine, albeit still slow.

Is there some process that is eating up cpu time that doesn't show on the system monitor? Do I need to eliminate the second drive (I'd like to keep it to backup files onto,however).  Can I eliminate some backup process that may be eating up processor time?  Is the kernal searching in two places (drives) for the same thing?

Very frustrating problem, and none of the other posts I've searched seem to apply...

Thanks

---

### Post by Pumalite on 2007-11-02
What are your specs?

---

### Post by hodad on 2007-11-02
AMD Athlon 64 processor
MSI K8N Neo2 mthbd (about 3 yrs old)
Seagate 226 GB SATA drive (the new drive)
WD Caviar 80 GB drive

---

### Post by Pumalite on 2007-11-03
Memory?. Graphics?.

---

### Post by hodad on 2007-11-03
512 MB PC-3200 DDRAM
VGA Card: ASUS Radeon R9200SE/T/128M TV R
Logitech cordless keyboard/mouse MX Duo
CPU: AMD 64 3400+ Athlon 64 939
HD (old) WD 80 GB WD800JD
HD (new) Seagate ST3250620AS

---

### Post by Pumalite on 2007-11-03
Your specs are fine. Run TestDisk on your drives:[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
[http://en.wikipedia.org/wiki/TestDisk](http://en.wikipedia.org/wiki/TestDisk)

---

### Post by hodad on 2007-11-03
Thanks for your replies...

I downloaded and extracted "testdisk_static" , and then clicked on the "blue gear "icon, but nothing happened.  Tried running it in terminal "sudo testdisk_static", but got "command not found".

How do I run it?  Can't  find answer in documentation.

---

### Post by Pumalite on 2007-11-03
[http://www.google.com/search?hl=en&q=TestDisk+User%27s+Guide&btnG=Google+Search](http://www.google.com/search?hl=en&q=TestDisk+User%27s+Guide&btnG=Google+Search)

---

