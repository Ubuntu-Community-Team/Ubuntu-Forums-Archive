---
title: "Installion issues and ACPI"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by tweekage1 on 2008-05-19
I know this topic is ALL OVER THE INTERNET, but I cant seem to find the answer to my specific question.

My motherboards BIOS date is 1998. So the installation wont start normally.
I can not upgrade the BIOS, because the latest BIOS update is only 1999.

I have tried using;
acpi=force
acpi=off
acpi=off apm=on

Yet, when I use any of the above, the installation does not start, instead it boots into Ubuntu(a bash shell) off the CD.

I just can not get the installation to start???

Any ideas?

---

### Post by tweekage1 on 2008-05-19
bump

---

### Post by Pumalite on 2008-05-19
Post your specs.

---

### Post by tweekage1 on 2008-05-19
Motherboard is an MSI MS-5184. Full specs found at [http://global.msi.com.tw/index.php?func=proddesc&maincat_no=1&cat2_no=&cat3_no=&prod_no=330](http://global.msi.com.tw/index.php?func=proddesc&maincat_no=1&cat2_no=&cat3_no=&prod_no=330)

The CPU is a K6 500mhz processor.

It has 128mbs of sdram.

It is all being ran of an AT powersupply, as the motherboard is AT

Does this help?

---

### Post by mrtomservo on 2008-05-19
On an old 450mhz Celeron I had to use the following:
> noapic noirqdebug irqpoll
inserted where you tried the acpi= commands.

---

### Post by tweekage1 on 2008-05-19
mrtomservo - this did not work.

---

### Post by Pumalite on 2008-05-20
With that RAM you cannot boot a Live CD. Ubuntu 8.04 is too heavy for you. Go with Xubuntu Alternate CD.

---

### Post by tweekage1 on 2008-05-20
pumalite, ill download, try, and let you know of the result.

I am really disappointed to hear someone tell me "linux needs more memory". linux used to be one of the most robust operating systems. you could run it on a 286 with 2 mbs of ram... now you need as much as windows... has ubuntu lost its way... :(

---

### Post by Pumalite on 2008-05-20
Xubuntu can run on 64 MB of RAM.

---

