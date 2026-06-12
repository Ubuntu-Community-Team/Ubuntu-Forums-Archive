---
title: "Errors- &quot;Can not run the upgrade&quot;  from 12.04 LTS to 14.04 LTS"
date: 2017-02-09
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2017-02-09
I'm trying to upgrade from 12.04 LTS to 14.04 LTS.

Using Update manager the following error appears;


[B]Can not run the upgrade

This usually is caused by a system where /tmp is mounted noexec. Please remount without noexec and run the upgrade again.[/B]


How can I fix this?

Thanks

---

### Post by PDA1 on 2017-02-09
Solved-

sudo mount -o remount,exec /tmp

---

### Post by Autodave on 2017-02-09
Sorry, but I have no answer for that. I do have a question though: why 14.04 and not 16.04?

I have always had much better results with saving/backing up my files and wiping the HD and installing the newest long term release (16.04 as of now).

---

### Post by PDA1 on 2017-02-09
> **Autodave said:**
> Sorry, but I have no answer for that. I do have a question though: why 14.04 and not 16.04?

I have always had much better results with saving/backing up my files and wiping the HD and installing the newest long term release (16.04 as of now).

Autodave,

I had been looking for advice of which release to upgrade to but many of
those things are a matter of opinion.  Upgrade from 12.04 to 14.04 is
what I've understood to be the correct process. Whether I upgrade to
Ubuntu "55.01" (meaning- any Ubuntu version) matters not to me- I just
don't want any data destroyed and want to have all of my existing
programs working properly.

My computer is rather old (like me) and I don't want of need the
fanciest or newest release. The Unity theme (or whatever it's called)
isn't want I want to use and I only want the typical looking desktop
with the bar at the bottom with a few program icons on it- just like 10.04.

I've already wasted 7 hours or so and plenty of DVDs trying to get a
working Live version of Debian but to no success. No, I don't want more
advice about moving to Debian- if Debian can't provide me with a working
LiveCd/DVD the first or third time I download and burn it then it's a
flop and waste of time.

I like Ubuntu- but not that Unity thing. I'm computer user and not a
programmer and have no interest in being one.

But, why do I want to upgrade? Because Ubuntu says you're not going to
get any updates or other stuff past a certain date. I don't want to
upgrade but the "security" stuff they're always talking about is a
concern and probably necessary.

The catch is they "say" upgrading is easy (advertisers always lie). The
reality is it could break your system and wreck everything. Back up
important data is smart but will it copy over and be useful once the
upgrade as happened? I highly doubt it. It's all fine and nice to back
up the entire Home folder but aren't there other folders that programs
are dependent upon in folders other than Home?

Any suggestions are welcomed by those who have been successful in the
process.

---

### Post by Impavidus on 2017-02-09
I've done many upgrades and all of them worked. Other people have been less happy. What works best is having a clean system – no third-party applications, no proprietary drivers, no leftovers from things you shouldn't have done.

The more classical interface had been replaced by unity already in version 12.04 (in 11.04 in fact), so I assume you've been using it for a while. But if you want to return to a more classical interface, you can try Xubuntu or Ubuntu Mate. They will be lighter on your hardware too. Note that their LTS releases have a shorter support period than regular Ubuntu, so you'll have to use 16.04 (and a clean install). Indeed, you can't upgrade from 12.04 to 16.04 directly.

---

### Post by PDA1 on 2017-02-09
> **Impavidus said:**
> I've done many upgrades and all of them worked. Other people have been less happy. What works best is having a clean system – no third-party applications, no proprietary drivers, no leftovers from things you shouldn't have done.

The more classical interface had been replaced by unity already in version 12.04 (in 11.04 in fact), so I assume you've been using it for a while. But if you want to return to a more classical interface, you can try Xubuntu or Ubuntu Mate. They will be lighter on your hardware too. Note that their LTS releases have a shorter support period than regular Ubuntu, so you'll have to use 16.04 (and a clean install). Indeed, you can't upgrade from 12.04 to 16.04 directly.

I've used Unity for about 30 minutes over the past several years.  it's not for me.

So a clean install is what most people suggest? 

'Don't feel like buying another SSD to install but maybe that would be the best approach?  And certainly don't want to buy a new computer.  

Well, this gives me something to think about.  Oh well, that's progress!

Thanks for the ideas.

I'd put my name here but can't remember what fake name I've been using?

How about "Robert"?  That sounds like a good one.

---

