---
title: "Can't Install"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by RevShowStopper on 2012-02-09
I have an Acer Aspire 5733z-4851, with an Intel Pentium P6100 Processor.

I used to have Windows 7 installed, until the Windows files became corrupted and Windows would not boot, and I decided to install Ubuntu.

I am using a LiveCD to install Ubuntu 11.10, but when I get to the boot menu and select any of the options, it freezes and won't go any further. I tried using different solutions like removing "quiet splash --", and "acpi_osi=linux" and several others, but with the same result.  I can't even get it to boot live.

I am able to boot other Live Linux systems, like Knoppix and Backtrack, and do not understand why Ubuntu isn't working.

---

### Post by Bucky Ball on 2012-02-09
Maybe try the current long-term support release, 10.04 LTS, and see if that has the same result. You could work up from there (if you really need to).

Does 11.10 work ok from the LiveCD when you 'Try Ubuntu' from the initial options page?

---

### Post by RevShowStopper on 2012-02-09
When I select "Try Ubuntu", it freezes, and nothing happens, even when I hit F1, F2, etc.

I will try the other release, though, and see if it works.

---

### Post by MadBrozzeR on 2012-02-09
I have some similar problem.
Recently I've got laptop Dell Inspiron N7110 (i7, 6GB, geforce GT525M, Win7).
First I disassemble it, changed HDD, and installed Ubuntu 11.10 at new one. It was no problem.
But then, at the first day of use, laptop was out of battery power and powered off.
Next time when I tried to power it on it showed grub and froze after selecting normal boot.
And worse: LiveCD refuses to load itself, too. Just before starting GUI it freezes and CPU cooler begins to spin madly.
Tried on Ubuntu 11.10 and Xubuntu 8.10 LiveCDs.

Win7 works perfectly (but slow), but I don't want to live with it.
What can I try not to destroy my new laptop?

P.S. Sorry for my English.

---

### Post by Bucky Ball on 2012-02-09
> **MadBrozzeR said:**
> I have some similar problem.
Recently I've got laptop Dell Inspiron N7110 (i7, 6GB, geforce GT525M, Win7).
First I disassemble it, changed HDD, and installed Ubuntu 11.10 at new one. It was no problem.
But then, at the first day of use, laptop was out of battery power and powered off.
Next time when I tried to power it on it showed grub and froze after selecting normal boot.
And worse: LiveCD refuses to load itself, too. Just before starting GUI it freezes and CPU cooler begins to spin madly.
Tried on Ubuntu 11.10 and Xubuntu 8.10 LiveCDs.

Win7 works perfectly (but slow), but I don't want to live with it.
What can I try not to destroy my new laptop?

P.S. Sorry for my English.

Welcome MadBrozzeR!

Please post a new thread with a title describing your issues specifically and a detailed post. You will get more/more specific help for your issue. 

Crashing in on this thread makes it confusing for us to solve the OP's original problem. 

Post a link to the new thread back here if you like. ;)

---

### Post by RevShowStopper on 2012-02-10
I tried using the Ubuntu 10.04, and it worked, except that when I select any of the options, I get this error:

mounting /dev/loo0 on filesystem.squashfs failed: Input/output error
can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesysyem.squashfs

---

### Post by RevShowStopper on 2012-02-10
I tried on a USB, and get a similar error. It also says Failed command: READ FPDMA QUEUED

---

