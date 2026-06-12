---
title: "Clean install?"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by hvymtlsteve on 2007-06-22
Hi guys.. I have 6.06 but would like to give 7.04 a try. 
I tried to upgrade to 6.10 using the gksu "update-manager -c" but no dice on that, it gives me some "Unable to calculate upgrade" thing:

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.


So I'm thinking I should just go ahead and clean install 7.04 (I don't have many files on this machine that I need to keep, so I got everything backed up real quick). 
How should I go about this-- boot from CD or format my HD?
And.. uh, how do I do either of these? I know how to do all this in windows but I'm still kind of new to Linux so I don't know what I'm doing here. 

Any help appreciated... cheers,

Steve

---

### Post by merlinus on 2007-06-22
This may help:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

-merlin

---

### Post by yabbadabbadont on 2007-06-22
If you don't dual boot with windows, just boot the feisty install cd and install it that same way that you did dapper.  If you do dual boot, you'll need to take the manual partitioning option and then select your existing ubuntu partitions to be used for the install.  That is, mark your existing root to be root, home as home, boot as boot, swap as swap, etc.  (you probably don't have that many)  Be sure to tell it to reformat them.  From then on, the install should go just as it did with dapper.

---

### Post by hvymtlsteve on 2007-06-22
Yup, thanks-- all I had to do was hop into the BIOS setup, boot from CD, and let 'er rip. I'm already in 7.04. 

A nice new thing-- my onboard sound works now (didn't work in 6.06)! 
Complete with some high-pitched squeal.. we'll have to see what the deal is with that..Everything else (wireless, display, etc.) has worked right off the bat too. We'll see how we do with Xilinx software,  next .

Thanks for answering my retard question, I'm an idiot *rolls eyes at self*

---

### Post by yabbadabbadont on 2007-06-22
I've said it before and I'll say it again.  If you don't know the answer, then it isn't a stupid question.  (unless you are just asking to be a jerk ;))  :D

---

