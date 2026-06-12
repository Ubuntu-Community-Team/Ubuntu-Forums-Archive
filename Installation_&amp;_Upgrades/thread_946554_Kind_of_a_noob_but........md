---
title: "Kind of a noob but......."
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by Ron from MD on 2008-10-13
......I always said if XP ever BSOD'ed me I'd switch to linux and here I am tweaking ubuntu on the desktop while using the laptop to check mail. The only problem I had installing 8.04.1 had to do with partitions on a system with 4 drives totalling one TB, three of the drives do noting more than hold data so I did not want ubuntu installed on them. Try as I might, I could not find anything clear telling me how to preserve the XP partition and what ubuntu needs created as a minimum to run using the manual partition.

So I cheated: power down and physically disconnect the 3 data drives (or however many you may have)leaving just the OS drive connected. Boot from the install CD, run install and use the guided partitioning on the OS drive. Once the install completes, after the first restart, power down again and reconnect the data drives. Simple and painless....now to install some software I use and take it out for a test drive.

---

### Post by aysiu on 2008-10-13
You need to shrink a partition and make room for and create a new partition just for Ubuntu. More details here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If you don't want to mess with partitioning, try Wubi:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by Ron from MD on 2008-10-14
> **aysiu said:**
> You need to shrink a partition and make room for and create a new partition just for Ubuntu. More details here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If you don't want to mess with partitioning, try Wubi:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Thanks aysiu, I did read the psychocats piece and it was of marginal help.  It did not explain at all what steps to perform during manual partitioning, nor could I find the information after searching for 2 hours, at least in a clear and concise form. I think you misunderstood my intent, I was giving a work around that at least hardware capable people can implement on large multi-drive systems. What I did was simply force the installer to only see one drive (the OS drive) and let it do the guided partitioning.

I have a small partition for XP since I plan to get away from it completely but still want the option for now. It's going to take me awhile to learn all the nomenclature and apps for ubuntu as well as find drivers/converters for some apps I use, until then XP has to stay available in a small way. My next thing to learn is how to get Thunderbird mail and address books from the XP side to the ubuntu side and get the ubuntu Thunderbird to see it......so far none of the methods I've found online work.

---

