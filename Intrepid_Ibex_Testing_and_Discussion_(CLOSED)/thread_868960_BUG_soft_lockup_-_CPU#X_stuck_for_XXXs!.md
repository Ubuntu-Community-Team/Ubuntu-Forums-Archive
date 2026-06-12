---
title: "BUG: soft lockup - CPU#X stuck for XXXs!"
date: 2008-07-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by klange on 2008-07-24
... and it happens quite often. I'm damn sure this is the same bug that existed in Hardy's kernel, which was supposed to be fixed.

On the visible side of the problem is this:
Whenever I leave my laptop idle for even a few seconds (sometimes when I just stopped moving the mouse), it will freeze. Now, the freeze itself isn't serious. Move the mouse, tap a key, whatever, and it's back up - however, it's annoying and it's killing my clock, which doesn't resync properly.

Now, I said I had this with Hardy, but I have two good reasons to post here in the Intrepid board:
1. This was (is) a major kernel bug that was supposed to be fixed and clearly wasn't.
2. I get log information with Intrepid that I never got with Hardy.

Now, with said logs, I only get them when I let the freeze continue for more than a minute, anything less and it goes unreported. Originally (that is, when I first had this bug), I thought it was a bug with the Intel wireless drivers (as my wifi would die at the same time). However, now I'm certain that it's the other way around (the kernel freeze is killing the wifi).


Specs:
Acer Aspire 5160 laptop, Core Duo (... "Centrino Duo") @1.73ghz, 1GB RAM, Intel 3945 wireless, running Intrepid Alpha 2 on the standard 2.6.26-4 kernel.

Symptom:
System repeatedly freezes until input is given.

---

### Post by olskar on 2008-07-24
I can assure you it was not fixed in Hardy, at least not for me :(

---

### Post by klange on 2008-07-24
> **olskar said:**
> I can assure you it was not fixed in Hardy, at least not for me :(
Indeed. I can't seem to find a specific cause for it, though. It's not memory/swapping, it's not ACPI, it's not wireless, touchpad, etc., I just know it doesn't happen on my desktop running Hardy, happened on my laptop on Hardy, still happens on Intrepid, was supposedly going to be fixed between the two (upstream), and also happens on openSUSE 11.0.

---

### Post by Nullack on 2008-07-25
We really need to start including bug numbers in these threads.

Whats the bug number?

---

