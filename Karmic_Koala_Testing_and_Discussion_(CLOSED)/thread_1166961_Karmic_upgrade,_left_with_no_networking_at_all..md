---
title: "Karmic upgrade, left with no networking at all."
date: 2009-05-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Mazza558 on 2009-05-22
See thread title. I have no networking (not even wired) after upgrading to karmic. nm-applet is running but says something along the lines of "no networking". Obviously this puts me in a tricky position, as I can't even upgrade/update to fix the problem.

Any ideas?

---

### Post by tacantara on 2009-05-22
I ran into the same issue when I installed Karmic (Kubuntu version) in a VB on my machine.  I'm not sure if I missed a setting during the installation, but I was able to fix the problem only after enabling the network applet.  Even after that, it took some doing because it didn't automatically discover my wi-fi card.  I essentially created a second network setting that insists that it is ethernet, but is connected to wi-fi.
 
Having said all that, are you using the Kubuntu or Ubuntu version of Karmic?

---

### Post by Mazza558 on 2009-05-22
> **tacantara said:**
> I ran into the same issue when I installed Karmic (Kubuntu version) in a VB on my machine.  I'm not sure if I missed a setting during the installation, but I was able to fix the problem only after enabling the network applet.  Even after that, it took some doing because it didn't automatically discover my wi-fi card.  I essentially created a second network setting that insists that it is ethernet, but is connected to wi-fi.
 
Having said all that, are you using the Kubuntu or Ubuntu version of Karmic?

Ubuntu.

---

### Post by hexsel on 2009-05-22
Same here, but I got a fresh install of Ubuntu from the daily build a few days ago.  I'm running on an HP DVX000 (6000? 9000?), and the Broadcom built-in wireless wasn't recognized, and didn't appear in the non-free hardware drivers list either (neither did the nvidia, btw).

We all share Internet, but it's located in another suite (townhouse, don't ask), so hardwired is not an option.  Not that I see any option that would even use it...

---

### Post by ranch hand on 2009-05-23
WOW, I have thought that Ubuntu loves this box and I guess I am right.

I am not using wireless but wired DSL just happens.

In fact, besides a little problem with Rhythmbox, 9.10 acts like a RC at worst.

---

### Post by Mazza558 on 2009-05-23
> **ranch hand said:**
> WOW, I have thought that Ubuntu loves this box and I guess I am right.

I am not using wireless but wired DSL just happens.

In fact, besides a little problem with Rhythmbox,** 9.10 acts like a RC at worst.**


That's because barely anything has changed yet since Jaunty ... apart from breakage of all of the networking...

---

### Post by Mazza558 on 2009-05-23
Just a notice - I have networking again since booting on an older kernel. I'd love to use the new one, but it's obviously not ready yet.

---

### Post by ranch hand on 2009-05-23
What kernal are you using?

---

### Post by robert.rankin.jr on 2009-05-23
> **Mazza558 said:**
> but it's obviously not ready yet.

Duh.

---

### Post by Mazza558 on 2009-05-23
I'm using the Jaunty kernel at the moment and networking works. When there's another kernel update I'll check.

---

### Post by ranch hand on 2009-05-23
HMMM, I am using the 2.6.30 kernal and have no problem with my wired DSL at all.

From lspci;
```

00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)

```

---

### Post by tad1073 on 2009-05-23
my wireless didn't work in 9.04 but works in 9.10, all be it kind of slow but it works.

> **Mazza558 said:**
> See thread title. I have no networking (not even wired) after upgrading to karmic. nm-applet is running but says something along the lines of "no networking". Obviously this puts me in a tricky position, as I can't even upgrade/update to fix the problem.

Any ideas?

Did you upgrade or did you do a clean install?

---

### Post by ranch hand on 2009-05-23
I should mention that not only is my ethernet card different but with this CPU array I can run on 32bit and that is what I am doing with 9.10.  I doubt that the kernal support is different than in 64 but it may be.

When alpha2 comes out (6-11) I will go with the 64bit.  Can't really say why I did it this way except every thing else on that HDD is 32.  I do like to play.

---

### Post by Mazza558 on 2009-05-24
> **ranch hand said:**
> HMMM, I am using the 2.6.30 kernal and have no problem with my wired DSL at all.

From lspci;
```

00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)

```

On the newer kernel, I saw all the networking adapters using lspci, but nm-applet refused to do anything.

> **tad1073 said:**
> my wireless didn't work in 9.04 but works in 9.10, all be it kind of slow but it works.



Did you upgrade or did you do a clean install?

Upgrade. Though the upgrade itself was from a pretty clean install of Jaunty.

---

