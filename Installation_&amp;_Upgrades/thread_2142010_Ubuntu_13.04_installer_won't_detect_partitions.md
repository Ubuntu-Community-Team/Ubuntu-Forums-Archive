---
title: "Ubuntu 13.04 installer won't detect partitions"
date: 2013-05-04
forum: Installation &amp; Upgrades
---

### Post by adrian2003 on 2013-05-04
Hi!

I am now trying to install ubuntu on my box without the annoying wubu installer...

Under the installation guide i came to the section where i could repartition my hdd, but it only showed one big unalocated partiotion. 

I suspect that it's a GPT HDD and that is the problem

Since I also want to dualboot with the current Windows installation, how do I proceed?

Thanks in advance for answers :)

---

### Post by 2F4U on 2013-05-04
I don't know your actual setup, so how many partitions do you actually have? GPT shouldn't be a problem and 13.04 should be able to detect and handle it. Since you have Windows installed, is there any space left where Ubuntu could be installed?

---

### Post by adrian2003 on 2013-05-04
There is a lot of space left for Ubuntu, and i have 3 partitions. I actually solved the problem by converting it to MBR, but then I faced another problem: GRUB... 

Managed to fix that though, so now I have a fully functional installation of Ubuntu 13.04 :)

---

