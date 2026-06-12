---
title: "Hard locks... but only when I'm at the library"
date: 2008-11-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Bou on 2008-11-24
Hi,

I'm having a REALLY weird problem with my Jaunty laptop. It seems to work just fine, but I get hard lockups when I use it in my local library.

It happens suddenly and, it seems, randomly. Suddenly the screen freezes, I can't move the cursor or even do ctrl+alt+backspace. I have to keep the power button pressed to shut it down.

It happens VERY often at the library (once every hour or so) but has never happened to me anywhere else, not once. Obviously, it only happens when I plug in the power cord.

Is there any way for me to find out what the problem is? Thanks.

---

### Post by mejy on 2008-11-24
Just a thought - I'd guess a problem like this would most likely be due to wireless networks?  Would it be practical for you to rmmod the kernel module for your wireless adapter and see if the hard locking still occurs?  Otherwise there's the kernel logs but I'd guess you've already checked them.  Otherwise I suppose it's a case of isolating factors which are likely to vary between the two locations (heat? power supply? etc)

---

### Post by ronacc on 2008-11-24
it only happens when you are on AC power ? I would suspect line transients of some sort . if you have a UPS you could take there and plug that into the ac power and then your power cord into that and if the locks did not occur you would know whwere the problem lies .

---

### Post by psyke83 on 2008-11-24
> **Bou said:**
> Hi,

I'm having a REALLY weird problem with my Jaunty laptop. It seems to work just fine, but I get hard lockups when I use it in my local library.

It happens suddenly and, it seems, randomly. Suddenly the screen freezes, I can't move the cursor or even do ctrl+alt+backspace. I have to keep the power button pressed to shut it down.

It happens VERY often at the library (once every hour or so) but has never happened to me anywhere else, not once. Obviously, it only happens when I plug in the power cord.

Is there any way for me to find out what the problem is? Thanks.

I've experienced this problem first-hand myself, so I can help you out. The problem in my case was actually a combination of a) the preservation chemicals (used to keep the books in good condition) interfering with the electronics in my laptop, and b) the noise from my laptop's fans causing a librarian to become irritated, and I believe their negative thoughts were somehow causing electrical interference.

Then again, maybe it's caused by a wireless network :P

I have a D-Link USB 802.11g card, and it causes complete lockups at random intervals when connected to a WPA2 network. If you have flaky drivers, even routine NetworkManager AP scans could cause a lockup. It's possible that the wireless router in the library is serving malformed AP responses that's confusing your driver, for example.

---

