---
title: "Installation failed on BOTH computers"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by duanra on 2008-04-26
(Copy of a thread in the Wubi forum, but since I don't know if it's Wubi or Ubuntu related)

Hi,

Being a 20 year student, I simply wanted to try and install Ubuntu 8.04 on one of my computers (desktop or laptop) with Wubi.

I first tried on my desktop, and the installation failed just before the end (something like 88% or just a little bit more).

I pass you the details (uninstall, reinstall, fail,...).
Then I tried on my laptop and....... exactly the same error and at the same point.
So this time I came to think : it can't be my hardware, it must be a bug in the software (either Wubi or Ubuntu).

And here I am, with no Ubuntu installed on any computer

But last time, I saved the installation logs (see attached file).
I hope you can do something with them, because I frankly can't...


Thank you.
Duanra

---

### Post by pbpersson on 2008-04-26
What version of Ubuntu were you installing?  I Googled the error at the end of your log files and read a conversation between some developers - they were saying it was a bug in Ubiquity in how it was partitioning your hard drive for the installation.

This was a bug (#123984) in Feisty and Gutsy, they thought the issue had been resolved in Hardy.

If you do more research into this and discover it is a partitioning problem, I wonder what would happen if you deleted all the partitions on the drive before Ubuntu reads it?

---

### Post by duanra on 2008-04-26
I was TRYING :( to install Ubuntu 8.04 (Hardy Heron) with Wubi 8.04.

As for the partitions, I would be surprised if it were the cause of the problem, because I have only 1 partition on my desktop ( C: ). And since the 2 failures look much the same...

Well, thank you for your quick answer anyway !

Duanra

---

### Post by duanra on 2008-04-26
It LOOKS like it's a Wubi-related bug, due to an accuentuated letter in the French "Windows WP **_É_**dition familiale".

But please keep an eye if somebody find an alternative to this problem.

Thanks.
Duanra

---

