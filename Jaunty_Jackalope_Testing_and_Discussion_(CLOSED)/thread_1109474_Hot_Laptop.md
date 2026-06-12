---
title: "Hot Laptop"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mempho on 2009-03-28
Loaded the Jaunty Beta yesterday and now I notice that my T42 Thinkpad is running at full speed all the time with the fan always on, temperature always around 160F. With Intrepid the CPU would slow down when idle and the laptop stayed wonderfully cool, much cooler than with XP. Anybody else noticing this?

---

### Post by tjeremiah on 2009-03-28
hmm, i notice this too. How does one check the temp in ubuntu?

---

### Post by Nullack on 2009-03-28
Why dont you try some diagnosis using top / system monitor / htop and the power utilities so you can have some visibility as to what is going on.

---

### Post by ktp on 2009-03-28
> **tjeremiah said:**
> hmm, i notice this too. How does one check the temp in ubuntu?

See following:

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

[http://ubuntuforums.org/showthread.php?p=6365702](http://ubuntuforums.org/showthread.php?p=6365702)

---

### Post by Mempho on 2009-03-28
Hmm, poking around a bit I noticed that powernowd was not installed in Jaunty but was present in Intrepid. I installed it thru Synaptic and that fixed *this* problem -- but maybe introduced some others? It looks like powernowd was intentionally omitted from Jaunty and is a low priority fix. Maybe it messes with Suspend and/or Hibernate?

---

### Post by tjeremiah on 2009-03-28
> **Mempho said:**
> Hmm, poking around a bit I noticed that powernowd was not installed in Jaunty but was present in Intrepid. I installed it thru Synaptic and that fixed *this* problem -- but maybe introduced some others? It looks like powernowd was intentionally omitted from Jaunty and is a low priority fix. Maybe it messes with Suspend and/or Hibernate?

I just installed powernowd, reset, and it doesnt miss with suspend or hibernate.

---

### Post by Mempho on 2009-03-28
Thanks, tjeremiah. Hibernate is broken for me anyway in Jaunty, seems a common problem, so I wouldn't know.

I'll see if I can find out why they're holding powernowd out of Jaunty. At least things are cooler now, 106F at 600 mhz, although the fan is still running. And I don't feel like I'm in danger of frying my whatucallit off.

BTW I'm monitoring all this thru conky with the following lines:

Frequency:        $alignr$freq mhz
Temperature:    $alignr$acpitempf F
Fan speed:        $alignr$ibm_fan

---

### Post by mamamia88 on 2009-03-28
i wouldn't worry too much about it i'm pretty sure thats about average.  even when i boot mine up it's around that and it's been to about 200 no problems

---

