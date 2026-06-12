---
title: "Going nuts trying to get a live cd to work."
date: 2013-01-14
forum: Installation &amp; Upgrades
---

### Post by hortstu on 2013-01-14
I've been up all night trying to get a live cd of 12 to work.  I've burned them to 

CDRW
DVDRW
and DVDR

I've tried acquiring ubuntu and kubuntu from different sources.  12.04 and 12.10. I have a 10.04 live cd that my computer's been booting from w/o a problem. They seem to burn fine. I've used brasero, the default program in 10.04 and roxio in windows. 

I'm at a loss.  I don't know what to do next.  

I'm hoping for suggestions.
Thanks.

---

### Post by adityamagadi on 2013-01-14
why dont u try burning the image on to a pendrive?

---

### Post by hortstu on 2013-01-14
> **adityamagadi said:**
> why dont u try burning the image on to a pendrive?
 
I'm running ubuntu/kubuntu on an old, but updated laptop.  I believe it is pre 2004 so pen drive boots don't work. At least I don't think they do. 

Thanks for the suggestion though.

---

### Post by Elfy on 2013-01-14
It might help to actually say what issue you have running them ;)

All we know is you're going nuts :p

---

### Post by hortstu on 2013-01-14
The issue is that instead of booting from the live cd/dvd the computer notices there's a disk in the drive flashes a cursor on the black screen while it checks to see if it can boot from it, then decides it can't and boots from hard drive. I've tried f12 and selected cd/dvd for a one time boot just in case, and it still boots from the internal hard drive.

Thanks for asking the right questions. Sorry I wasn't clear.

---

### Post by Elfy on 2013-01-14
If it was me I'd check I'm burning as an image - from that description it would _seem_ to be not. 

I'd check that the cd boots on another machine if possible.

Sometimes I have seen people have issues burning to RW discs.

---

### Post by coldraven on 2013-01-14
I have never had much success with Brassero I use K3b instead.
Make sure that in whatever program you use to select the "Burn Image" option.
In K3b select "More Actions" from the blue panel in the lower window then choose "Burn Image".

---

### Post by hortstu on 2013-01-14
> **coldraven said:**
> I have never had much success with Brassero I use K3b instead.
Make sure that in whatever program you use to select the "Burn Image" option.
In K3b select "More Actions" from the blue panel in the lower window then choose "Burn Image".

Thanks.  I'll give that a try.

---

### Post by hortstu on 2013-01-14
> **coldraven said:**
> I have never had much success with Brassero I use K3b instead.
Make sure that in whatever program you use to select the "Burn Image" option.
In K3b select "More Actions" from the blue panel in the lower window then choose "Burn Image".

Yeah It's been a few years since I had to make a live cd so it's very possible that I'm screwing it up.  Hopefully K3b can help me do it right.

---

### Post by oldfred on 2013-01-14
Is system so old that it does not support PAE. Only Lubuntu & Xubuntu now have kernels that work with those very old systems.

       [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)

            [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae

---

### Post by hortstu on 2013-01-14
Thanks.  k3b seemed to do the trick.  I've made some working live CDs.

> **oldfred said:**
> Is system so old that it does not support PAE. Only Lubuntu & Xubuntu now have kernels that work with those very old systems.

I'm not sure.  I'm working on a Dell Inspiron 6000.  I'm not into gaming or anything so it does everything I need.  As long as there is a decent supported linux OS that works with it that is.

---

