---
title: "How do I setup TRIM on Samsung EVO 850 with 16.04 please?"
date: 2016-09-30
forum: Installation &amp; Upgrades
---

### Post by macbreak on 2016-09-30
Hello, fine people of Ubu!

How do I setup TRIM on Samsung EVO 850 with 16.04 please? I am a long time Linux user, and I just want a simple, concise and quick to implement tutorial on how one should activate TRIM on my SSD (non pro, consumer variant btw) without any fuss or fiddle? I am not averse to editing config files, but if it turns into a 70 step tutorial, forget it, hehe.

Thank you :) have a lovely evening!

---

### Post by QIII on 2016-09-30
Hello!

Just to be clear:  was Ubuntu installed on the SSD?

If so, no further action on your part is required.  A weekly cron job to do just that was automatically added at install time.

Would you like to have it occur more often?

---

### Post by macbreak on 2016-09-30
> **QIII said:**
> Hello!

Just to be clear:  was Ubuntu installed on the SSD?

If so, no further action on your part is required.  A weekly cron job to do just that was automatically added at install time.

Would you like to have it occur more often?

Hello, thanks for replying so swiftly.  

I've not yet installed it, but will be doing so later tonight. I don't know what the "normal" frequency is for TRIM (IE, I'd like to go with whatever Samsung Magician schedule is, if anyone knows that?) - what is the "normal" frequency, and how would deviating from it affect my system? Is one week "normal"? I just want my SSD to be transparent, as it should be in daily use. I'm accustomed to this kind of matter not needing intervention or consideration AT ALL, which is how one would expect it to be (as in Mac OS X or Windows.)

Anyone is more of an expert on TRIM than I am, I don't care to know about it beyond wanting my drive not to screw up.  Surely in this day and age this kind of issue shouldn't even be a user's consideration, one would hope!

Thank you.

---

### Post by QIII on 2016-09-30
I have moved my cron job for fstrim to daily and added some logging.  I don't know what might be called a "normal" schedule.

When you have installed Ubuntu, we can help you change the frequency of the job.

In this day and age, Linux does not make assumptions about how you want your machine to behave.  So you do have to make such considerations.  :)

---

### Post by macbreak on 2016-09-30
> **QIII said:**
> I have moved my cron job for fstrim to daily and added some logging.  I don't know what might be called a "normal" schedule.

When you have installed Ubuntu, we can help you change the frequency of the job.

In this day and age, Linux does not make assumptions about how you want your machine to behave.  So you do have to make such considerations.  :)

Yes, but I don't understand what the difference is or what it matters how often this (whatever it is) task, happens? As I do not know, I am unable to make an informed decision about which frequency is best. I appeal to your greater knowledge of this, thank you.

:)

---

### Post by ubfan1 on 2016-09-30
Your SSD isn't in an external USB enclosure, I hope, since TRIM doesn't work over USB.  eSATA connections to an enclosure will work fine with TRIM.

---

### Post by QIII on 2016-09-30
I think the weekly job might just be a good starting place.  I have a daily task because I run several virtual machines, break them, delete the virtual disks and restore them, etc.

But it's always fun to be introduced to what you can do with your machine.

---

### Post by macbreak on 2016-09-30
> **ubfan1 said:**
> Your SSD isn't in an external USB enclosure, I hope, since TRIM doesn't work over USB.  eSATA connections to an enclosure will work fine with TRIM.

Nope, that would be quite the waste of speed!  :P

> **QIII said:**
> I think the weekly job might just be a good starting place.  I have a daily task because I run several virtual machines, break them, delete the virtual disks and restore them, etc.

But it's always fun to be introduced to what you can do with your machine.

I'm a regular VM man myself, so I shall try weekly and see how it runs _(although how I could tell any difference is still beyond me as *"Mr SSD Uber N00b", ***LOL***)*_

I'll see how I get on, and do some more research. The reason for the thread was that I have been regularly Googling "Samsung EVO SSD Ubuntu Trim" and variations of that, over the last year, and I regularly saw reports of incompatibilities and/or problems, so I held off until I know what is going to pan out, in a predictable fashion. I can't stand uncertainty in tech, and if I think something isn't right it bugs me LIKE CRAZY, so I'd rather hold off until I am guaranteed that the EVO 850 would have no 16.04+ compat. issues, which you have reassured me of, now.



**{Addendum} **I've just had a peek at "Sandisk SSD Dashboard" (different machine) which has been running on my R61 for 9 months now with no problems at all, and it seems to have been set to a weekly TRIM schedule, although the setting above that which I have given a "?" question mark, confuses me somewhat - I do not see how it's different or why it is there?

[IMG]https://c2.staticflickr.com/6/5497/29405219194_4792820f9c_b.jpg[/IMG]

---

### Post by kurt18947 on 2016-09-30
Sammy needs to get with the program:P. I have an AMD Radeon (Rebadged OCZ VT180 IFIRC). OCZ's maintenance software is available as a .deb file, 32 or 64 bit.
Edit: Patriot SSDs also have Linux utilities.

---

### Post by macbreak on 2016-09-30
Well, that seemed to work... yeaaaaaahp.

[IMG]https://c2.staticflickr.com/6/5797/29740045060_bb9bd1a181_b.jpg[/IMG]

---

