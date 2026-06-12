---
title: "Partitioning with Separate Home"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by larry on 2006-08-31
Hello,
An easy question: when I install (X)(K)Ubuntu, I'd like to make a separate home partition, so that if anything goes wrong much later on and I need to re-install, then at least my data are safe.
However, I do not understand that much about filesystems and so on, so I wonder if there is any online tutorial explaining how to set up a separate home partition and how to re-install Ubuntu without spoiling your data.
Many thanks

Larry

---

### Post by pyros on 2006-08-31
[This]("http://www.psychocats.net/ubuntu/separatehome.html") should be of some help.

---

### Post by Titus A Duxass on 2006-08-31
Are you doing a fresh install or changing an installed system?

---

### Post by larry on 2006-08-31
I am more thinking about a fresh install: I should get soon a new laptop for my work and I'd like to set up the partitions properly this time.
Cheers

Larry

---

### Post by aysiu on 2006-08-31
> **larry said:**
> I wonder if there is any online tutorial explaining how to set up a separate home partition [http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) > and how to re-install Ubuntu without spoiling your data. [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by larry on 2006-09-01
Thanks for the links. Having in mind a fresh install, I mainly looked at
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)  .
However, this is the partition structure on my box (Xubuntu default):

/dev/hda1              36G  6.9G   27G  21% /
varrun                252M   64K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  120K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-26-386/volatile

Should I reproduce this structure? And how am I supposed to mount them?
Even better: where do I find something (without going into excrutiating detail) which can give me a hint at what is going on?
Cheers

Larry

---

