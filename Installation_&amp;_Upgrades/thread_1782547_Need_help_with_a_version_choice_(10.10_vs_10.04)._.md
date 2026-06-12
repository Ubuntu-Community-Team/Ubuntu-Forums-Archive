---
title: "Need help with a version choice (10.10 vs 10.04). Any opinions appreciated."
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by nzjethro on 2011-06-14
Hi all. I'm an Ubuntu user for a couple of months now. I don't do anything overly heavy with Ubuntu, just surf the net with Chromium, write assignments for Uni with Libre Office, play around with GIMP, use Rhythmbox for music. I'm currently using 10.10 with XFCE, having tried 11.04 but found it not to my liking. XFCE is fantastic, it's the way for me. I'm wondering about changing release from 10.10 to 10.04 (for the LTS factor, given that this time next year Maverick won't be supported).

My question is, what do you guys recommend in this respect?

1) Should I switch to 10.04 or stay with 10.10?

2) Should I do a full install Ubuntu then add XFCE, or minimal install Ubuntu then add XFCE, or should I go with Xubuntu?

3) If I go Xubuntu or a minimal install, can I add GNOME or KDE later?

Thanks guys, any opinions or experiences are appreciated.

---

### Post by dabl on 2011-06-14
> **nzjethro said:**
> 

1) Should I switch to 10.04 or stay with 10.10?



The LTS factor?  What do you think that is going to do for you, in terms of daily usability of your computer?

If you can do everything you need to do with 10.10, then I recommend you leave it alone, as it is.

---

### Post by nzjethro on 2011-06-14
> **dabl said:**
> The LTS factor?  What do you think that is going to do for you, in terms of daily usability of your computer?


The only thing it would do would be that I could continue using it day to day up until April 2013, an extra year over Maverick. I imagino that's what LTS refers to right? I'm still new to Ubuntu, but doesn't the lack of LTS for 10.10 mean that packages will stop working with 10.10 in April 2012?  I'd prefer something a bit more long-term than that (only ~10 months away).

---

### Post by ezsit on 2011-06-14
You can continue using 10.10 for as long as you want to use it. The EOL just means you will not get updates, the software will continue to work just fine on its own.

---

### Post by nzjethro on 2011-06-14
> **ezsit said:**
> You can continue using 10.10 for as long as you want to use it. The EOL just means you will not get updates, the software will continue to work just fine on its own.

Cool, I was wondering about that. Wicked, so I'll still be able to install packages and stuff on 10.10 even when it is no longer "supported"?

---

### Post by BBQdave on 2011-06-14
10.10 is supported through April 2012.  Then, the next LTS (long term support) edition will be released.  Xubuntu 12.04 LTS (2012 April release) which will feature Xfce 4.8.

I am currently using Ubuntu 10.10 with the gnome 2 desktop.  In April 2012, I will try Ubuntu 12.04 LTS.  If it does not meet my needs, I will switch to Xubuntu 12.04 LTS.  Xfce 4.6 is good, and Xfce 4.8 continues a good desktop environment.

Too, LTS's are released every two years by Ubuntu, with three years of total support for desktop.

---

### Post by mörgæs on 2011-06-15
> **ezsit said:**
> You can continue using 10.10 for as long as you want to use it. The EOL just means you will not get updates, the software will continue to work just fine on its own.

Though it is possible, I will certainly not recommend this. End of life means that no security bug fixes are released.

---

### Post by ezsit on 2011-06-16
You can use any distribution long after it has stopped receiving security and bug fixes, especially if it is running smoothly and is stable for you, the lack of fixes will not really affect you. However, installing software after the supported time period is more difficult as the repositories are renamed after EOL. Usually , you would need to rename the repositories in your sources list to point to archived repositories instead of current repositories in order to keep installing software. However, if after a year and a half you do not already have all the software you will need is unlikely. Spend the supported life time of the release experimenting and then just before EOL hits, finalize your software setup, remaster the installation with remastersys, and you will have a great image with which to reinstall should you ever need it. Remastersys can be found at [www.remastersys.com](www.remastersys.com).

---

### Post by nzjethro on 2011-06-16
Wicked, thanks guys. Nice to know that even when Maverick runs out of support I'll still be able to "use" it. That's exactly what I wanted to hear.

---

### Post by mörgæs on 2011-06-17
Again, I am not pleased to see this advice given. You can use an obsolete release in the sense 'it runs', but not in the sense 'it is secure'.

There is a reason why people apply security fixes! 

It is plain logic. Ubuntu has its flaws like all other operative systems, and if they do not get fixed, they will get exploited.

---

### Post by Hedgehog1 on 2011-06-17
> **nzjethro said:**
> 
My question is, what do you guys recommend in this respect?

1) Should I switch to 10.04 or stay with 10.10?

2) Should I do a full install Ubuntu then add XFCE, or minimal install Ubuntu then add XFCE, or should I go with Xubuntu?

3) If I go Xubuntu or a minimal install, can I add GNOME or KDE later?

Thanks guys, any opinions or experiences are appreciated.

One of the beauties of Xubuntu is that it is streamlined and fast. If you want the best strengths of XFCE without any bloat, running an Xubuntu install give you that.  

However, any Linux distro (*ubuntu or otherwise) will greatly benefit from regular updates.  New kernels with ongoing improvements (we are using 3.0.0 right now in 11.10 testing), updating software with bug fixes, and security updates to keep you safe on the 'net are key to an enjoyable PC.

While **ezsit** advice will *function*, it is very like fixing a car using duct-tape.  Yes, with enough duct-tape it will keep running. But you can also get a new car every 6 months or 1 year or 2 years depending on your choice of release styles.  Why duct-tape when you can drive a new vehicle? For Free?!?!

If you want to minimize your distro upgrades, then moving to the next LTS make sense.

Be aware that over time you will become more comfortable doing a clean-install of the OS to 'freshen things up' and keep your performance up.

Finally, once you are on a release that is no longer supported, the forumn will ask you to get current before we can really help you; we can only keep so many variations in our heads at any one time.

Happy Ubuntu(ing)!

***The Hedge***

:KS

---

### Post by Bobhuber on 2011-06-18
> **mörgæs said:**
> Again, I am not pleased to see this advice given. You can use an obsolete release in the sense 'it runs', but not in the sense 'it is secure'.

There is a reason why people apply security fixes! 

It is plain logic. Ubuntu has its flaws like all other operative systems, and if they do not get fixed, they will get exploited.
Thats BS. I've been using Ubuntu since 9.04. The fixes usually arrive just before the release expires and are applied to the new release which is usually wrought with its own problems. 10.10 is one of the best releases to date,faster than 10.04 and just now getting extremely stable. It will be around for quite a while on my desktop. He could always install Natty and stare at a blank screen

---

### Post by nzjethro on 2011-06-18
> **Hedgehog1 said:**
> One of the beauties of Xubuntu is that it is streamlined and fast. If you want the best strengths of XFCE without any bloat, running an Xubuntu install give you that.  

However, any Linux distro (*ubuntu or otherwise) will greatly benefit from regular updates.  New kernels with ongoing improvements (we are using 3.0.0 right now in 11.10 testing), updating software with bug fixes, and security updates to keep you safe on the 'net are key to an enjoyable PC.

While **ezsit** advice will *function*, it is very like fixing a car using duct-tape.  Yes, with enough duct-tape it will keep running. But you can also get a new car every 6 months or 1 year or 2 years depending on your choice of release styles.  Why duct-tape when you can drive a new vehicle? For Free?!?!

If you want to minimize your distro upgrades, then moving to the next LTS make sense.

Be aware that over time you will become more comfortable doing a clean-install of the OS to 'freshen things up' and keep your performance up.

Finally, once you are on a release that is no longer supported, the forumn will ask you to get current before we can really help you; we can only keep so many variations in our heads at any one time.

Happy Ubuntu(ing)!

***The Hedge***

:KS

Thanks for that. The way I see it, 10.10 is supproted until the next LTS, and I'm very much enjoying 10.10 as it is, so I think I'll stay with 10.10 til 12.04. Thanks for the advice regarding Xubuntu vs Xfce on Ubuntu, I'll try a Xubuntu install when I do upgrade, already there are some minor things that annoy me about GNOME and Xfce co-existing.


> He could always install Natty and stare at a blank screen

Pass. I've tried Natty, and I like the concept, but it runs too slow on my old computer. Down the track I'll definitely try a Unity upgrade, but I think I'll need a hardware upgrade first. :P

---

### Post by Dutch70 on 2011-06-19
I know this thread is solved, but I just wanted to add that the longer you use any OS after it reaches EOL, the less secure it becomes. If you want to do this with you're computer, that's completely up to you, but advising someone else to do it with theirs when they're asking for help is just not right.

---

