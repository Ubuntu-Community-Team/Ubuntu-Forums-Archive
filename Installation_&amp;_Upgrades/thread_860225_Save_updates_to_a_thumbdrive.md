---
title: "Save updates to a thumbdrive?"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by aqk on 2008-07-15
I have a PC with Ubunto 8.04 on it, and currently there are about 130+ Meg of updates ready to download.
  Unfortunately there is only dial-up available in my locale.
I already seem to have downloaded 25+ meg of updates, and it is getting tiresome.
Is there any way I can go to a friend's house, where hispeed is available, and download the updates there onto a flashdrive?

 Oh yes.. he only has Windows (for now)....

  Thanx

---

### Post by Bablefish on 2008-07-15
One idea is bring your computer to your friend's house and use his connection (with his permission of course).

---

### Post by aqk on 2008-07-15
> **Bablefish said:**
> One idea is bring your computer to your friend's house and use his connection (with his permission of course).

Yes I had thought of that- he has wireless; all I have to do is drive into his driveway and supply the laptop with his WEP, but-
1. Ubuntu doesn't seem to like my laptop's Atheros wi-fi card.( I admit I havent tried it with 8.04 yet)
   - and -

2. **THE TRUTH:**  I actually have **three** PCs at home- 2 desktops and a laptop, two of which have Ubuntu, which I may install on the 3rd also.  If only the Update thing were easier.
  (Dont worry- I have a 3COM dialup router on my LAN!)

  Isn't there (or shouldn't there be) some sort of Ubuntu Multiple PC support, similar to MS' download-SP3 facility or MS' IEAK?

  Would be very handy!

---

### Post by aqk on 2008-07-21
I have three PCs, networked, all running Ubuntu 8.04.

How can I download updates ONCE, and then apply them to all three PCs?

Note:  I only have dialup at this location.

---

### Post by Potatoj316 on 2008-07-21
Yes you can download the files only once and use them for all your computers but it might be a pain.  You could use wget in the terminal (i dont really know how to) to retrieve the necessary packages from the repositories (you might want to write a shell script first) and save them on your computer and then transfer with a UFD or CD or external HD or however.  To get the files you could connect to his router using a cable, its faster and will probably work.

---

