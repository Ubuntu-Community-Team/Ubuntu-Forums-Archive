---
title: "My boot times are quite bad..."
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-06-19
How can I improve it down to Karmic goals?

---

### Post by douham on 2009-06-19
Starks, mine are shocking to. the progess indicator hangs at 10% for about 20s.

[ATTACH]118290[/ATTACH]

---

### Post by plun on 2009-06-20
I noticed seg faults within my kern.log

Also a 10s break before udev is initiated.

Apparently Scott J Remnant is working with this but more basics such as Grub2 and so on must be ready first.

---

### Post by taavikko on 2009-06-20
This looks pretty awful too: 15s
Will do an clean install in a few days...

Hmm, where the attachment.. Ah finally it uploaded it...

---

### Post by plun on 2009-06-20
We will also have a new kernel with several fixes.

[https://lists.ubuntu.com/archives/karmic-changes/2009-June/002937.html](https://lists.ubuntu.com/archives/karmic-changes/2009-June/002937.html)

I don't think a reinstall will help....


EDIT  My bootchart...

Note "the sleep" in the beginning

[[img]http://www.ubuntu-pics.de/thumb/16787/plun_laptop_karmic_20090620_1_pv0bu3.png[/img]](http://www.ubuntu-pics.de/bild/16787/plun_laptop_karmic_20090620_1_pv0bu3.png)

---

### Post by douham on 2009-06-20
> **plun said:**
> We will also have a new kernel with several fixes.

[https://lists.ubuntu.com/archives/karmic-changes/2009-June/002937.html](https://lists.ubuntu.com/archives/karmic-changes/2009-June/002937.html)

I don't think a reinstall will help....

[[img]http://www.ubuntu-pics.de/thumb/16787/plun_laptop_karmic_20090620_1_pv0bu3.png[/img]](http://www.ubuntu-pics.de/bild/16787/plun_laptop_karmic_20090620_1_pv0bu3.png)

No, a reinstall won't help. I tried that a litle while ago and hanging boot still with clean install

---

### Post by MacUntu on 2009-06-20
Yes, seems to be a bit slower than with Jaunty atm, but nothing to worry... ;)

---

### Post by NCLI on 2009-06-20
It's still in Alpha guys, it's not even feature complete ;)

Let's wait for the beta before we start to worry. :popcorn:

---

### Post by ronacc on 2009-06-20
alphas are for finding problems so they can be fixed before beta or rc .
I've got a huge sleep for one instance of devkit-disks-pa and my kern log keeps complaining about an IO error on my non-existant floppy . commented fd0 out of fstab no help .

---

### Post by douham on 2009-06-25
Hi

Is everyone's boot speed still pretty bad. I'm up to kernel:2.6.30-10.12
compared to the O.P's.

---

### Post by MacUntu on 2009-07-03
Hm, anyone knows how to get rid of that 'exe'-part at the beginning?

[IMG]http://img.xrmb2.net/images/434206.png[/IMG]

Sometimes it's so short bootchart doesn't draw it, sometimes it's up to about four seconds long. I'm not using hibernation and the swap UUID is right in all places.

---

### Post by tjeremiah on 2009-07-03
mines has been slow since upgrading from 8.04 to 8.10. Is it because I used Wubi?

---

