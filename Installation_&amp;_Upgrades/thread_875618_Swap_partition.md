---
title: "Swap partition"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2008-07-31
My friend is installing Ubuntu on his IBM A800 and he told me of interesting happening:  He did the clean install and decided to get rid of the gig of swap or whatever he head.  The A800 has a blazing 256MB of ram.  He did something to mess up the installation - what he did is not really my concern - but when he tried booting from the live cd the A800 was having difficulty, usually failing after extended waits.  Then, he somehow got a swap partition on the hard drive (again, how is not my concern right now) and the live cd booted perfectly and installed.

My question is, will the live cd be able to detect a swap partition on the hard drive and use it if necessary?  I didn't think that would make sense because you should be able to boot up a live cd without a hard drive and do whatever you can with the amount of memory you'd be allowed to play with.  I know it seems as if the live cd obviously DOES do this, but I just thought I'd ask for a definitive answer if anyone can give one and explain why.  Thanks!

---

### Post by overdrank on 2008-07-31
moved to Ibex testing :)

---

### Post by MaindotC on 2008-07-31
It's not really specific to Ibex, it's a general installation question.  If it will make you feel better I'll remove the word "Intrepid" from the post.

---

### Post by MaindotC on 2008-07-31
K I edited the original post, could you please move it back where people are actually viewing?

---

### Post by InfinityCircuit on 2008-07-31
Most livecds automatically probe if a swap partition exists and then enable it if it does exist.  This doesn't affect their ability to be used on machines that lack a hdd.

---

### Post by MaindotC on 2008-07-31
Thanks, Infinity.  Do you have any specific references or documentation I can visit to verify this information?

---

### Post by overdrank on 2008-07-31
I do apologize, as I understood you were asking about intrepid. 
Moved to installations :)

---

### Post by MaindotC on 2008-07-31
Ok I'm really sorry for nagging you like this but I initially posted this in "Installation".  Does this not qualify as an installation issue?

---

### Post by overdrank on 2008-07-31
Ok here it stays. I can not find the documentation that you want on swap but I do remember using the alternate cd on some low memory systems and I had to create a swap partition to complete the install. I am sure the live cd will use the ram for viewing but during the install it will look for a swap for the reasons I stated above. :)

---

### Post by Gina on 2008-07-31
As I recall Hardy (and Intrepid) need minimum of 384MB to install from Live CD.  The Alternate CD requires a lot less and is one reason for providing this alternative - it uses text mode rather than GUI to reduce resources needed to install.

---

### Post by MaindotC on 2008-07-31
> **overdrank said:**
> Ok here it stays.

Thanks, OD :)  and thank you for your reply Gina :)

---

### Post by arvevans on 2008-08-01
Open a terminal screen (the dreaded CLI - Command Line Interface) and enter "man mkswap".  Read this man page over by using your keyboard arrow keys to scroll up or down.  This should tell you what happens when a swap file is encountered by the live-CD or during an installation.

You asked for verification of an earlier post...the Linux manual page is it.
_._

---

### Post by MaindotC on 2008-08-01
Thanks, arvevans! Sometimes it's just a matter of knowing where to look for information :)

---

