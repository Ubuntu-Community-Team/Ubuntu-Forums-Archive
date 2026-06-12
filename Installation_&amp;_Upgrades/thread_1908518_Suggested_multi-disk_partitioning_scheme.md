---
title: "Suggested multi-disk partitioning scheme?"
date: 2012-01-13
forum: Installation &amp; Upgrades
---

### Post by jmidgley on 2012-01-13
Hi

I'm sure this is a FAQ, but my searching mojo has failed me. If I'm settting up a new system which has 2 drives (a 250GB and a bigger one, maybe 1TB), what would be the suggested way of using the space? I've only set up single disk systems to date.

Any links/suggestions gratefully received.

Cheers
John

---

### Post by Basher101 on 2012-01-13
to give the most appropriate answer to your question, i must collect more information regarding your question.

Do you use Ubuntu only or do you have a Dualboot setup?

what exactly do you use the computer for ? (surfing, gaming..)

is there anything special you have in mind for this?


regards

---

### Post by Elfy on 2012-01-13
Personally I'd have one partition on the 1Tb drive, a smallish primary on the smaller drive - perhaps 50Gb, then on extended in the remainder of it in which I'd put swap, / and another smallish partition. Leaving some unallocated for a rainy day (or other distros to look at as and when)

But I would - becasue that's more or less what I have :)

---

### Post by jmidgley on 2012-01-13
> **Basher101 said:**
> to give the most appropriate answer to your question, i must collect more information regarding your question.

Do you use Ubuntu only or do you have a Dualboot setup?

what exactly do you use the computer for ? (surfing, gaming..)

is there anything special you have in mind for this?


regards

Yes, perhaps it was a bit vague. It's a little HP Proliant N40L. I run Ubuntu server (dual boot? ptooie!) and it runs an e-mail server, Slimserver, Twonkymedia, a bit of Apache, things like that. So I'm wondering if there's any merit in keeping different bits of the system on different partitions/spindles.

Regards
John

---

### Post by Learning Linux 2011 on 2012-01-13
You may want to put your /Home directory on a separate drive.  That way all of your data will be separate and you can play around with different OS's and not worry that your data is going to get screwed up.

You can also put the swap partition on a separate drive

---

### Post by Basher101 on 2012-01-13
well i could suggest you a setup if it were not a server. I have no experience with servers at all, not even how the data is managed with them so i will take my leave.

Good luck at finding your setup *bows*

---

### Post by darkod on 2012-01-13
> **jmidgley said:**
> Yes, perhaps it was a bit vague. It's a little HP Proliant N40L. I run Ubuntu server (dual boot? ptooie!) and it runs an e-mail server, Slimserver, Twonkymedia, a bit of Apache, things like that. So I'm wondering if there's any merit in keeping different bits of the system on different partitions/spindles.

Regards
John

For server, and for 2 disks (and maybe adding more later), you might wanna think about LVM. In fact the version used today is actually LVM2.

This link is quite old but it can start you off with the basics, that's the one I have at hand right now:
[http://www.tldp.org/HOWTO/LVM-HOWTO/whatislvm.html](http://www.tldp.org/HOWTO/LVM-HOWTO/whatislvm.html)

---

### Post by matza55 on 2012-01-14
> **darkod said:**
> For server, and for 2 disks (and maybe adding more later), you might wanna think about LVM. In fact the version used today is actually LVM2.

This link is quite old but it can start you off with the basics, that's the one I have at hand right now:
[http://www.tldp.org/HOWTO/LVM-HOWTO/whatislvm.html](http://www.tldp.org/HOWTO/LVM-HOWTO/whatislvm.html)

Interresting.

---

