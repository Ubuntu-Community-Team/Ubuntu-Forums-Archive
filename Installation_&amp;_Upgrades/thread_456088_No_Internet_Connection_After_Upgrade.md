---
title: "No Internet Connection After Upgrade"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by morpheus55 on 2007-05-27
Hi all


  I just reinstalled 6.06lts after 7.04 failed dismally. Good install and 132 updates, but now I don't have an internet connection. I have had three weeks of frustration with these systems, can somebody do a step by step guide for me as I don't understand the code stuff very well. Thanks.:D

---

### Post by mejohnsn on 2007-05-27
I know three weeks of frustration is hard to document in a single post, but please tell us at least a little more about what went wrong. For example, when you say you have no network, did this happen before, or after reverting from Feisty Fawn back to Dapper Drake? If 'before', then what were those 'upgrades' you referred to? How did you do them without network? What network hardware do you have? Does Ubuntu report the existence of your network hardware correctly in /etc/network/interfaces?

---

### Post by morpheus55 on 2007-05-28
Yes , well I run 2 hdd's , xp and linux. For 3 weeks I have been trying several types of linux but to no avail. 
they just don't work.There is always something wrong with them. Last night i installed 6.06 again and it did the 132 updates as per normal, but now it won't connect to the net. I don't know where to find this "/ect" stuff . I have looked everywhere. There must be something I am not doing, but I thought Linux was supposed to be simple. Perhaps its me. I don't even know how to remove the grub loader from xp so I can start again. Any clues??:)

---

### Post by morpheus55 on 2007-05-28
Don't worry about the 6.06, I found open suse and installed it. Works fine.Thanks anyway.

---

### Post by mejohnsn on 2007-05-30
It sounds like you are up and running with SUSE Linux. Good for you.

For future reference, the reason you are having trouble finding the '/ect stuff' could just be your mis-spelling. The correct spelling is '/etc', not '/ect'; it is the standard abbreviation for "Et cetera". And you should be able to find it using either a Terminal window or the Nautilus File Manager.

Also, for help debugging network problems, one of the best first steps is to give us the output of "sudo ifconfig", so that we can see what network devices -- if any -- the system was able to find. The contents of the file /etc/networks/interfaces is also very helpful.

---

