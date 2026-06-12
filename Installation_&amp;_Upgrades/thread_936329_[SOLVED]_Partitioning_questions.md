---
title: "[SOLVED] Partitioning questions"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by 09buntu on 2008-10-02
Hi! I would like to switch to Ubuntu when 8.10 is released.

Is it possible to make it an encrypted LVM install and use different "partitions" or whatever it's called in LVM for root and home so that root can be easily reinstalled without interfering with home? Would there be any problems with the encryption thing? And is it possible to put all that after the first partition on disk (windows, for games)?

Would this be a reasonable setup or is good old-style partitioning better suited for this purpose? 

Thanks

---

### Post by Herman on 2008-10-02
[Encrypted Ubuntu 8.04 - Step-by-step installation tutorial with screenshots!]("http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml")

You will need to use the Ubuntu 'Alternate' CD (also called the 'text mode installer'.

I have one encrypted installation, but mine's in a second hard disk, I just let the installer automatically partition the entire disk. It made itself a separate /boot partition, I think that would be necessary for an encrypted / (root).
I'm not sure about an encrypted /home too, I haven't tried that. Probably that's possible, would be worth a try anyway, if you like having a separate /home, (personally, I don't believe in it). You should be able to use the partitioning menu in the 'Alternate' CD's installer to partition the hard disk however you like, select manual partitioning.
See my first sig link if you want to see some illustrations of how the text mode installer works.

Regards, Herman :D

---

### Post by 09buntu on 2008-10-03
Thank you very much for the link (and answer). Seems pretty straightforward. 
Thanks again.

---

### Post by kruisa7 on 2008-10-03
Here is a link that I think will show you exactly what you want, using LVM and encrypted everything except root.  It is very secure and may be over kill, but it is also flexible allowing you to resize logical partitions and even add / delete logical partitions.

[http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html](http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html)

---

### Post by 09buntu on 2008-10-05
> **kruisa7 said:**
> Here is a link that I think will show you exactly what you want, using LVM and encrypted everything except root.  It is very secure and may be over kill, but it is also flexible allowing you to resize logical partitions and even add / delete logical partitions.

[http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html](http://www.iki.fi/kuparine/comp/ubuntu/en/cryptolvm.html)

Very interesting! Thanks!

---

