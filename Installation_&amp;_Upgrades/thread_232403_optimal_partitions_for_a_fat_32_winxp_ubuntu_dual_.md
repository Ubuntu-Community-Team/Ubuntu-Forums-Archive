---
title: "optimal partitions for a fat 32 winxp ubuntu dual boot system"
date: 2006-08-08
forum: Installation &amp; Upgrades
---

### Post by SkippyJames on 2006-08-08
I am trying to install the ubuntu and i chose manually partition although i dont know much about it. i have 100 gb of fat 32 harddisk. Does anyone know an optimal partitioning. 

Thanks for your help

---

### Post by loserboy on 2006-08-08
theres a howto somewhere that shows optimal partitioning, anyway this is basically what it shows... forgive the ugliness it took about half a second

this is how my setup at work is, with everything but the win partition as a extended partition, swap being about double the amount of your ram and of course just make your ubuntu the size that you feel like you need.

you could add more empty fat32 partitions in between the swap and ubuntu if you wanted since linux can read/write to fat32 and keep those as backups


Edit: about the extra fat32 backup partitions, people say you can put them wherever you want and they haven't noticed a speed dif.

---

### Post by Jagot on 2006-08-08
It all depends what you want to do with it.  Have a read of this:

[http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html)

---

### Post by loserboy on 2006-08-08
lol oh there it is haha  ok please don't look at my pic now

---

### Post by SkippyJames on 2006-08-08
sorry i couldn't wait and i let ubuntu make the partition itself and now i am up and running. :)

Thanks for your help.

---

### Post by loserboy on 2006-08-08
oh well that works too, only bad thing about that is it cuts quite a bit into your windows partition... but hey hopefully you'll stop using windows soon

---

