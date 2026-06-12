---
title: "E: Couldn't find package?"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by timka1 on 2006-08-15
Probably a really dumb question but what does the message

E: Couldn't find package [xxxx]

mean?

I keep getting this when trying to find How tos

In particular when I did the following:

sudo apt-get install ruby1.8 ruby1.8-dev irb

It found the "ruby1.8" "ruby1.8-dev" but not "irb"

How do I get the missing package? For that matter where are the ones that are found? Complete newbie I'm afraid...

---

### Post by meng on 2006-08-15
Most likely you get this error when the required package is not in the repositories you have enabled. In order to enable extra repositories, you can follow this guide if you don't already know:
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

(irb is in universe, while ruby(dev) is in standard repos)

---

### Post by timka1 on 2006-08-16
Thanks for the clear answer!

Seems to me that when someone mentions an installation they should also specify the repository in which they reside...

---

