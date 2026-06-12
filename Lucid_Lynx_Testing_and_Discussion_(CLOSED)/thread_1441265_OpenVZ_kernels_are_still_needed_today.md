---
title: "OpenVZ kernels are still needed today"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by narcisgarcia on 2010-03-28
[I]As discussed in this forum thread:
[http://ubuntuforums.org/showthread.php?t=1382823](http://ubuntuforums.org/showthread.php?t=1382823)
And asked for me in this other one:
[http://ubuntuforums.org/showthread.php?t=1341845](http://ubuntuforums.org/showthread.php?t=1341845)[/I]

Ubuntu 8.04 (Hardy Heron) included linux-openvz support, that is a great virtualization patch for the Linux kernel, because makes possible to create containers with GNU systems inside with hardware native performance. The OpenVZ packages in Ubuntu repositories made Ubuntu a good choice for server administrators, but has become a trap for the future.

Next Ubuntu versions (8.10 9.04 and 9.10) didn't include linux-openvz kernels, and this made suspect that would appear again with the next LTS release, as the last one. But the news this autumn were that LXC (Linux Containers) is going to replace the role for Ubuntu Servers.

Oh no! Some work to migrate virtual servers! Well, let's go to learn about LXC and walk to the solid future of the containers. **But with Ubuntu we are now locked in a trap:**

Some users (server administrators) are testing the last Ubuntu 10.04 beta releases, and doesn't give way to make a container (virtual server sharing resources and at native speed) for a production environment: not with OpenVZ, nor with LXC.
OpenVZ seems to be left by Ubuntu packagers, and LXC is definitely not ready for production.

And I quote *cdufour* words:
> LXC is definitely not ready for production. The lack of proper documentation is one proof of it, among others. Dropping support of a stable, efficient, well-documented virtualization solution for a new unreliable, unproven, poorly documented one, in a LTS release, without providing a path for a smooth migration (like having the two solutions co-exist for a time), is a poor choice of strategy. That not being said against LXC, which holds great promises for when it will be mature

There isn't anything bad for Lucid Lynx to include support both to LXC and OpenVZ kernels, to ease a good migration.

---

### Post by narcisgarcia on 2010-03-29
See [http://community.livejournal.com/openvz/30998.html](http://community.livejournal.com/openvz/30998.html) . A pity there has not been just a few more weeks. Maybe OpenVZ could have made it into Lucid

---

### Post by narcisgarcia on 2010-03-29
I see this is the only way to solve the problem, but needs a good promotion work from users and developers:

[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)

---

### Post by NCLI on 2010-03-29
Yep, you need to submit a request for a freeze-exception. If you make your case well, you should be able to get it through. However, once again, posting in the forums will not change anything ;)

---

### Post by JedMeister on 2010-03-29
Yes that looks like the go. I don't have time at the moment but I will endevour to log a Feature Freeze Exception 'Bug' tonight (if someone doesn't beat me to it). If someone else gets it done before me, then perhaps a link to the bug can be posted here so others who are interested can subscribe too.

Good work narcisgarcia on your work on this issue so far!

---

### Post by narcisgarcia on 2010-03-30
JedMeister, thanks for the help, if you write here a link to the Feature Freeze Exception petition, me and other interested  people can subscribe.

---

### Post by JedMeister on 2010-03-30
I'm sorry narcisgarcia but I think we're just too late. :frown:

The kernel & beta freezes occurred 20 days ago. Obviously beta1 is out now, with beta2 freeze tomorrow. Ubuntu kernel-team were approached by one of the OpenVZ devs just prior to the freeze and turned him down (see [here]("https://lists.ubuntu.com/archives/kernel-team/2010-March/009276.html") and [here]("https://lists.ubuntu.com/archives/kernel-team/2010-March/009277.html")). I really don't think we have time to do the level of testing they require to make a good enough case for a late inclusion. Especially how late in the process it is already.

It's really unfortunate that we didn't mobalise sooner as I think we would've been able to make a damn fine case for a freeze exception. Looks like we may need to look to alternative ways of accessing OpenVZ in 10.04 (perhaps a PPA?). Or maybe I'll just stick with 8.04 with a view to migrate to Debian Squeeze when its released.

---

### Post by narcisgarcia on 2010-03-30
Debian 5 (Lenny) has already OpenVZ kernels in the repository.
With this kind and size of problems, I'm not seeing a great future to Ubuntu servers, while Debian looks more serious and technically well supported.

This kind of things are which makes people to divide to the "easy" ubuntu or the "strong" Debian. Of course, some serious and professional system administrators change to Debian.
I'm thinking about if this will be my case.

LXC has become a trap, because of it's not ready.

---

