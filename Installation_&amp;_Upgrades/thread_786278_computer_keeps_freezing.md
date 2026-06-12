---
title: "computer keeps freezing"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by HunkieChan on 2008-05-08
i dont know what's wrong with my hardy heron. it keeps freezing.. please can anyone help me

ps. im a noob

---

### Post by sstusick on 2008-05-08
Downgrade to Gutsy 7.10... that's what I did.

---

### Post by HunkieChan on 2008-05-08
for some reason .. gutsy doesnt work on my pc (hp)

---

### Post by Bubba64 on 2008-05-08
This is a problem that the answer to has not been found. On my desktop I have no problems but it has a 1.7 gig hard drive but only 256 of ram. On my laptop which has only 700Mhz on the hard drive and 256 on ram I have occasional freezes which are totally random. I see people with very robust setups having this problem, I think though that it is a small problem overall but a big problem to anybody personally.

---

### Post by dlridings on 2008-05-08
> **HunkieChan said:**
> i dont know what's wrong with my hardy heron. it keeps freezing.. please can anyone help me

ps. im a noob

That sounds like the way my computer was behaving until I quit using Firefox 3beta5 (the version of Firefox that comes along with 8.04).

You can install the older version of Firefox (it's called firefox-2 in the repository) and use it without having to unintall Firefox 3beta5. Just don't use the latter. Maybe a bug fix will come along some day.

---

### Post by HunkieChan on 2008-05-08
> **dlridings said:**
> That sounds like the way my computer was behaving until I quit using Firefox 3beta5 (the version of Firefox that comes along with 8.04).

You can install the older version of Firefox (it's called firefox-2 in the repository) and use it without having to unintall Firefox 3beta5. Just don't use the latter. Maybe a bug fix will come along some day.

i actually thought firefox was causing the problem. but then i uninstalled it and installed firefox 2 but it still happens.. firefox occasionally crashes too.. but one thing i noticed is that whenever firefox is running my computer freezes.. i dont know why firefox might be causing this problem.. but thats just my observation. i guess there is no real solution to this problem.. but i hate this freezes.. grr

---

### Post by dlridings on 2008-05-08
> **HunkieChan said:**
> i actually thought firefox was causing the problem. but then i uninstalled it and installed firefox 2 but it still happens.. firefox occasionally crashes too.. but one thing i noticed is that whenever firefox is running my computer freezes.. i dont know why firefox might be causing this problem.. but thats just my observation. i guess there is no real solution to this problem.. but i hate this freezes.. grr

I can understand your frustration.

If I were you, I'd simply dump 8.04 and install 7.10.

Ubuntu is a really fine system and I'm sure 8.04 will eventually be ok too. But right off hand I can't think of one single reason to use 8.04 instead of a perfectly fine 7.10.

It could be that some of the multimedia stuff works better out of the box (actually worse on my machine). But I lost control over volume when I went from 7.10 to 8.04, so I'm not sure even that attempt at positive thinking is valid :-)

Really, 7.10 is a great system. You might want to use it until 8.04 is ready for prime time.

---

### Post by HunkieChan on 2008-05-08
> **dlridings said:**
> I can understand your frustration.

If I were you, I'd simply dump 8.04 and install 7.10.

Ubuntu is a really fine system and I'm sure 8.04 will eventually be ok too. But right off hand I can't think of one single reason to use 8.04 instead of a perfectly fine 7.10.

It could be that some of the multimedia stuff works better out of the box (actually worse on my machine). But I lost control over volume when I went from 7.10 to 8.04, so I'm not sure even that attempt at positive thinking is valid :-)

Really, 7.10 is a great system. You might want to use it until 8.04 is ready for prime time.

but the problem is , 7.10 doesnt work on my system for some reason. i have tried countless time with countless cds,it never worked. i was stuck with 7.04 for last 6 months or so and couldn't wait for hardy but uh, it dissapointed me. i guess i just have to wait . thanks anyway guys

---

### Post by dumbo on 2008-05-08
If the computer freezes, but you can hear the hard disk whirling away/thrashing then it's likely this rather showstopping bug:

[https://bugzilla.mozilla.org/show_bug.cgi?id=402469](https://bugzilla.mozilla.org/show_bug.cgi?id=402469)

Basically whenever firefox3b5 syncs the list of 'evil sites' (every 30 minutes), it can cause your computer to do a large amount of CPU/disk work.

This is believed 'fixed' in the nightlies, and should be in rc1 which is due to appear imminently...

---

With 8.04 I also have a (rare) firefox crash, and a very common pidgin hang :(.  Hopefully these things will get ironed out as time goes by...

---

### Post by HunkieChan on 2008-05-09
i just realized that even when firefox isn't running, ubuntu freezes. ugh. does this happen to alotta users ?

---

