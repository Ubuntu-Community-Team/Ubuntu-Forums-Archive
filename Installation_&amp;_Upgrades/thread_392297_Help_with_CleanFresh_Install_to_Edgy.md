---
title: "Help with Clean/Fresh Install to Edgy"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by NewJack on 2007-03-24
I am a Ubuntu beginner (3 weeks) and wasn't sure whether to post this here or in the Beginner's section.  I have searched around a bit, but didn't find a direct answer.

I have read that you can do a clean install to a new Ubuntu version without changing any of your personal settings.  I have my partitions set up the following way:

Windows
/Home - Shared Data
/
Swap

Now, I downloaded Edgy and burned it to disk.  My question is, how do I perform a clean install from the LiveCD?  How do I start the process from the LiveCD?  I am assuming that I am pointing the installation to the / partition, or am I wrong?  Thanks in advance!!!

P.S.- I know Feisty is coming out soon, but wanted to learn how to do this anyway. :) 

Joe

---

### Post by bulldog on 2007-03-24
You can boot your edgy live cd and go through the steps till the partitioner.
Choose manual partitioning and mount your / as / :)  and set it to format.
Mount your swap as swap and set it to format.
Now comes the tricky part,mount your /home as /home but **don't set it to format**

The problem could be you have programs installed which aren't in the official repo's.
This can generate errors because they can't be upgraded.
The best way to avoid this,is by removing that kind of programs out of your /home folder and place them back when you have your sources.list up to date and reinstall them manually.

---

### Post by NewJack on 2007-03-24
Thanks for the quick reply.  Much appreciated!!!  This should be stickied in the Beginners Section IMHO.

---

