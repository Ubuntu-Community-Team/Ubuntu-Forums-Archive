---
title: "[SOLVED] Go back to Gutsy without losing data"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by ResidentSuprhero on 2008-06-27
I'm ready to go back to Gutsy from Heron.  Is there any way to do that without having to do a clean install like the upgrade to Heron was?  I don't want to lose all of my data. Thanks.

---

### Post by ibutho on 2008-06-27
Is your /home on a separate partition? If so, then do a clean install, but don't format the partition with /home.

---

### Post by unutbu on 2008-06-27
If you don't have a separate home partition, here is how to make one: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by ResidentSuprhero on 2008-06-28
I'm about to create a separate home partition but I was wondering what size to make it.  Should I make it as large as possible?  Is there any way that I could make it too large?  Thanks for the replies so far.

---

### Post by unutbu on 2008-06-28
A linux distribution (not including a /home partition) can usually fit comfortably in 10GB.

I've read that swap space should equal twice your RAM, but I don't think this is a hard and fast rule. In fact, it seems rather ridiculous that the more RAM you have, the more swap you need. 

Since you are repartitioning, I think now is the best time to reserve an extra 10GB for a second operating system. Eventually you might get a hankering for reinstalling Heron, or Ibex, or some other operating system. By having an extra 10GB handy, you will be able to install the new operating system safely, without risking your current setup. If it works, you can start using that partition as your default boot...

The rest of the available hard drive space can happily go to your /home.

---

### Post by Redptc on 2008-06-28
Thanks Unutbu, that was a clear, precise comment that helped me even though I didn't ask the question. Your suggestion makes sense and I really appreciated the overall explanation. I will take up your partitioning suggestions.

Often, some of the help on offer is too cryptic to be of benefit unless you a 'qualified nerd'; not this time, you are a Guru!

---

### Post by ResidentSuprhero on 2008-06-29
Thanks for all of the help.  I somehow butchered it though.  I ended up simply creating another partition, installing Gutsy on it, copying my files from Hardy to Gutsy, and then deleting the Hardy partition to expand my Gutsy one.  I'll try to do the separate home partition again sometime.  It would have made my life much easier.

---

