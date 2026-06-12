---
title: "Just upgraded to Karmic Koala and have major problems"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by joni8.10 on 2010-03-23
Just upgraded to 9.10 and now get a warning that my HD has many bad sectors (realocated sector count). Also, cannot open my master cd-rw, and cannot play anything on tvtime.

Everything was working OK before the upgrade. 

Not impressed with linux anymore.

---

### Post by coffeecat on 2010-03-23
Did you want any help? Because people tend to be put off from offering help if they read negative comments such as: 

> **joni8.10 said:**
> Not impressed with linux anymore.

---

### Post by stevepaul on 2010-03-23
@coffeecat

> **coffeecat said:**
> Did you want any help? Because people tend to be put off from offering help if they read negative comments such as:

Not exactly a helpful response (from someone with your experience), I'm guessing the Guy was just a little bit frustrated and was looking for someone to provide a sensible comment...

Have to be honest I'm not particularly impressed myself having had a question here that I would have expected at least a response to ...

---

### Post by coffeecat on 2010-03-23
@stevepaul, perhaps I could have expressed myself better, but the point I was trying to make was that negative comments like the OP's suggest that the poster has already given up and is just blowing off steam. This is certainly the impression it gives and it does put people off from offering help. People don't want to waste their time helping someone who doesn't really want help.

I have several times made the mistake of offering (sometimes quite detailed) help to an OP who has ended their post with something like, "I'm seriously thinking of going back to Windows" or similar to this OP's, and finding that not only does the OP not post again, but their profile reveals that they haven't even bothered to log in to the forum since making the post. In such circumstances I feel that my goodwill has been abused.

Actually, if you think about it, my post was helpful.

I am unrepentant.

---

### Post by prodigy_ on 2010-03-23
> Just upgraded to 9.10 and now get a warning that my HD has many bad sectors (realocated sector count).
Possibly a false positive due to [this bug in libatasmart](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/438136?comments=all). Might as well be a genuine warning, so I'd double check SMART data with some other software.

---

### Post by nindrianto on 2010-03-23
Hi i am a newbie. How we upgrade ubuntu version...now i am using ubuntu 9.04, and wanna upgrade to the latest version. Should I download all packages? It need a long time because of size. Or could I upgrade any parts only? thanks.

---

### Post by stevepaul on 2010-03-23
@coffeecat

I totally understand your frustrations, I had exactly the same frustrations over at the Google Chrome Help forum ...

@nindrianto

I had the very same issue ...

The solution is really quite easy ...

You need first to burn a 9.10 Alternate ISO (i386 or AMD depending on your actual 9.04 install) ...

Boot into Ubuntu ...

When you're up and running insert your 9.10 ISO disc ...

You will get an option to Upgrade ...

Start the Upgrade ...

Enjoy ;)

---

### Post by rifter on 2010-03-23
> **coffeecat said:**
> @stevepaul, perhaps I could have expressed myself better, but the point I was trying to make was that negative comments like the OP's suggest that the poster has already given up and is just blowing off steam. This is certainly the impression it gives and it does put people off from offering help. People don't want to waste their time helping someone who doesn't really want help.

I have several times made the mistake of offering (sometimes quite detailed) help to an OP who has ended their post with something like, "I'm seriously thinking of going back to Windows" or similar to this OP's, and finding that not only does the OP not post again, but their profile reveals that they haven't even bothered to log in to the forum since making the post. In such circumstances I feel that my goodwill has been abused.

Actually, if you think about it, my post was helpful.

I am unrepentant.

     I agree that it was helpful, and probably well-deserved.  You might feel better if you realize that your helpful replies do not actually go to waste even if the OP never reads or replies, because people do read the forums looking for information.
     In this case, though there's not much to go on.  The bug link was a sensible reply as well.

---

### Post by coffeecat on 2010-03-23
> **rifter said:**
> I agree that it was helpful, and probably well-deserved.

Well-deserved? :) Actually, I meant my original post kindly - I wasn't trying to be down on the OP - although I could have worded it better. I can understand the OP's frustration - I've had more than my share of teeth-grinding moments myself.

---

### Post by joni8.10 on 2010-03-28
I have reinstalled ubuntu 6.10 and am very pleased with the results!

No more warnings about iminent HD failure, etc. and everything is running alot faster too. 

I wonder what happened with 9.10? In any case, I'm not going there again!

---

### Post by JustinR on 2010-03-28
> **joni8.10 said:**
> I have reinstalled ubuntu 6.10 and am very pleased with the results!

No more warnings about iminent HD failure, etc. and everything is running alot faster too. 

I wonder what happened with 9.10? In any case, I'm not going there again!

Correct me if I'm wrong,
but a new disk utility (now part of the gnome utilities package) called Palimpsest Disk Utility, starts a daemon on bootup that monitors your hard drives, among other things.

To turn it off go to System > Preferences > Startup Applications, and then delete the program called, "Disk Notificiations".

Personally, I think its neat that it does that - I've never had problems with it though.

Take care, -JustinR

---

### Post by Gnusboy on 2010-03-28
> **coffeecat said:**
> @stevepaul, perhaps I could have expressed myself better, but the point I was trying to make was that negative comments like the OP's suggest that the poster has already given up and is just blowing off steam. This is certainly the impression it gives and it does put people off from offering help. People don't want to waste their time helping someone who doesn't really want help.

I have several times made the mistake of offering (sometimes quite detailed) help to an OP who has ended their post with something like, "I'm seriously thinking of going back to Windows" or similar to this OP's, and finding that not only does the OP not post again, but their profile reveals that they haven't even bothered to log in to the forum since making the post. In such circumstances I feel that my goodwill has been abused.

Actually, if you think about it, my post was helpful.

I am unrepentant.

"I am unrepentant"

Yes, you are. It is because of jerks like you that newbies give up on Linux.
I have been trying to solve many Karmic problems for nearly a month, but I don't usually post here, because of snotty people like you.
So, continue being unrepentant.

---

### Post by stevepaul on 2010-03-28
@Gnusboy

I have to say I'm more than a little disappointed at the response to what I thought would be a fairly straight forward answer ...

Either it exists and I just can't find it or it has been removed (a reason would be nice) ...

Being an avid user of Chrome on the Dev channel I'm used to features disappearing from one release to the next, but I would have thought that something as fundamental as this would have someone cast a little light on the subject ...

You mentioned that you no longer post here, so where do you ask your questions and do you get any response ?

I have had Ubuntu installed for 5 days now and asked 2 questions on this forum, neither of which I've got an answer to ...

It really doesn't bode well for the future if I've got some real technical issues that I need to get sorted ...

God help me if I was to ask how to implement Proxomitron in Ubuntu ;-)

---

