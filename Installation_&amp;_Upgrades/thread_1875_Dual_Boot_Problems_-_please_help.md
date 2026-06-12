---
title: "Dual Boot Problems - please help"
date: 2004-10-23
forum: Installation &amp; Upgrades
---

### Post by paul on 2004-10-23
I just instailled ubuntu on a computer that I had previously been dual booting between windows XP and Mandrake10.  I replaced the mandrake installation with ubuntu.  Things went well until I tried to boot into windows.   The choice of Windows XP was there on Grub but when I clicked on it the screen went blank and then the following appeared:

Booting 'Windows NT/2000/XP'

root (hd 0,0)
     File system is fat, partition type Oxc
Makeactive
Chaintoorder +1

The system then stalled and nothing more haopened.  I tired again and the same thing happened.

I had previously used Lilo to dual boot between win XP and mandrake and I did not remove it (not sure how to do that).  Could that be causing a problem?

The windows partition is the first one on the master hd so I thought 0, 0 was correct.

Does anyone have a suggestion.  From my quick test I like ubuntu and would like to be able to keep it and XP (need for some work programs and games) on the computer.

Thanks in advance.
P.S. I am not a linux expert but not a complete newbie as I have been running mandrake for about a year.

---

### Post by paul on 2004-10-23
I made a mistake in my previousb post.  The line was Chainloader +1 not chain to order

Paul

---

### Post by Seti on 2004-10-25
Try this then:

title Windows
rootnoverify (hd0,0)
chainloader +1
savedefault

see if that works for you.

---

### Post by demoncleanerd on 2004-10-25
Actually just got done fixing this problem and was about to write a thread on it.  Go Into your BIOS and change the addressing of your hard drives to LBA.  Windows should boot for you then.

---

