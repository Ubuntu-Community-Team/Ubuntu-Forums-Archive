---
title: "Intrepid, Wifi and madwifi"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Romu on 2008-10-27
Hi all,
The Intrepid Ibex is the first Ubuntu working with a "out of the box" wifi on my Macbook Pro 2G (Core 2 Duo + ATI).

But (why there is always a "but"?), this is with a recent madwifi driver, and there is being a huge bandwith issue for a long time now.

Instead of having 10 mb, my internet connection is only at 1,5 mb :confused:

I would like to know if the issue is well know by the madwifi team?

I guess I have to compile and install an old madwifi to recover a correct connection speed.

---

### Post by Cifra on 2008-10-27
I'm just gonna ask here, so I don't have to make a new thread:

I have Intrepid installed on a Macbook2,1
Wifi's working out-of-the-box, WPA2
Sometimes the connection drops out and it's very unstable. If I disable teh security, it works well. People told me that I should switch to WPA1, but my router (belking54g) has only two options in the cpl: WPA1/2 & WPA2.

I could also try with WEP, but I don't know how to use it (seems complicated)

---

### Post by Romu on 2008-10-27
I used to install an old madwifi (from january or march 2007 I guess), I recompile it and everything works pretty well with a correct speed.

I'll create a ticket on madwifi regarding this speed issue.

---

### Post by cyberdork33 on 2008-10-27
> **Romu said:**
> I used to install an old madwifi (from january or march 2007 I guess), I recompile it and everything works pretty well with a correct speed.

I'll create a ticket on madwifi regarding this speed issue.
madwifi is "old code" the driver is being replaced by ath5k and ath9k. (Not that you should change if what you have is working...)

---

### Post by Cifra on 2008-10-27
> **Cifra said:**
> I'm just gonna ask here, so I don't have to make a new thread:

I have Intrepid installed on a Macbook2,1
Wifi's working out-of-the-box, WPA2
Sometimes the connection drops out and it's very unstable. If I disable teh security, it works well. People told me that I should switch to WPA1, but my router (belking54g) has only two options in the cpl: WPA1/2 & WPA2.

I could also try with WEP, but I don't know how to use it (seems complicated)

So, any clues anyone?

---

### Post by cyberdork33 on 2008-10-27
> **Cifra said:**
> So, any clues anyone?
There are a few discussions on this already, and I think it was determined to be a bug... Please don't hijack someone else's thread. I know you have similar hardware, but your question is really unrelated. You should also mention what driver is in use if you still need to open a new thread.

---

### Post by Romu on 2008-10-28
Thanks cyberdork, as you can see I didn't manage to give up Ubuntu to OSX, I just can't understand the logical behind this OS.

I've checked and you're right, the "out of the box" installed wifi driver is ath9k. But, the madwifi web site lists the ath5k to best suit the AR5008 of my late 2006 MacbookPro.

With the ath9k, the connection to my hotspot is well established, but NetworkManager manager displays a connection speed at 1 Mb/s and when I run some online bandwith test, I only get 1,5 Mb/s.

I don't know how I can switch from ath9k to ath5k to make some tests with this alternative. Can you give me some help?

Thanks in advance.

---

### Post by cyberdork33 on 2008-10-28
> **Romu said:**
> With the ath9k, the connection to my hotspot is well established, but NetworkManager manager displays a connection speed at 1 Mb/s and when I run some online bandwith test, I only get 1,5 Mb/s. That is a bug, and the speed is simply being reported incorrectly, but you are actually getting a higher speed.

> **Romu said:**
> I don't know how I can switch from ath9k to ath5k to make some tests with this alternative. Can you give me some help?

You can unload the current modules and load the one you want manually:
```
sudo modprobe -r ath5k ath9k
sudo modprobe ath5k
```

You can check all the modules loaded by using the command 'lsmod'

---

### Post by Romu on 2008-10-28
> **cyberdork33 said:**
> That is a bug, and the speed is simply being reported incorrectly, but you are actually getting a higher speed.


No, this is not just an incorrect information, when I test the connection, I can't go beyond 1,5 Mb, and I should really close to 10 Mb.

So, it may be a bug, but a real performance one. :) But as, this is not the correct driver, there is no need to create a ticket on madwifi, a ticket on Intrepid would be better.

Anyway, there is a huge performance issue with the madwifi for a long time now, more than one year. The performances are really very far from expactations.

> **cyberdork33 said:**
> You can unload the current modules and load the one you want manually:
```
sudo modprobe -r ath5k ath9k
sudo modprobe ath5k
```

You can check all the modules loaded by using the command 'lsmod'

That means ath5k is compiled and provided directly with Intrepid, I'll test this asap. Thanks.

---

### Post by cyberdork33 on 2008-10-28
> **Romu said:**
> Anyway, there is a huge performance issue with the madwifi for a long time now, more than one year. The performances are really very far from expactations.Probably because they stopped work on it about that long ago ;)

> **Romu said:**
> That means ath5k is compiled and provided directly with Intrepid, I'll test this asap. Thanks.That is correct.

How are you testing the speed? Have you tried the same test with an ethernet connection to see the difference?

---

### Post by Romu on 2008-10-29
Hi Cyberdork,
I still haven't found the time to make the test.

To answer your question, I google to find some Internet bandwith test and I run them, always 2 different to be sure.

And as already had the madwifi performance issue, I know my bandwith is normally around 10 Mb/s.

So, when these tests give my 1,5 MB/s that's because of a driver problem.

Another good test, in a more real situation is to try to watch TV on the computer, in the case of a bad driver it's unwatchable.

---

### Post by angel6700 on 2008-10-29
Hi,

you can try:

```
iwconfig ath0 rate 11MB

```

Good luck.

---

### Post by Romu on 2008-10-30
@angel6700: this makes the link usable, but not this the normal performances, anyway that's better, thanks for the tips.

@cyberdork33: ath5k not found on the system, so no, it is not provided by default. I'll switch back to madwifi.

---

