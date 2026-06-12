---
title: "I did a stupid thing"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by erkker on 2007-01-24
Okay I set up a Ubuntu 6.06 / WinXP dual boot box and everything ran fine.

I setup the inital account for my father and then I got the box as my own.  So I decided to setup a second account which I did, but neglected to give my new self all the admin permissions.  Then I deleted the original account.

So when I booted up into the new account I got a nasty surprise:  I have no write permissions anywhere.  I did sudo into etc/sudoers and gave the new account permission under the %admin section (thanks to the forum) but the problem persists.

can it be saved?

-E

---

### Post by hscottyh on 2007-01-24
Yes, but I think you'll have to use a live cd. I actually did that once, but it was a year and a half ago. I don't remember the exact details, but it was fairly easy. 

I'll look around and see if I can find a howto. Anyone know off the top of there head?

---

### Post by wpshooter on 2007-01-24
Seems like to me I saw this question addressed before and it involved a fix thru recovery mode boot.  But I don't remember the details.

---

### Post by hscottyh on 2007-01-24
This should help:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

I was wrong, no cd needed.

---

