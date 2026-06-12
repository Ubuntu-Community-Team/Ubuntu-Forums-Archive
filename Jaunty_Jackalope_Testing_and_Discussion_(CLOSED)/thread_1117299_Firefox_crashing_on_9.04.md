---
title: "Firefox crashing on 9.04"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by leonardo_neo on 2009-04-05
Hi all,

Today I did a fresh install of Ubuntu 9.04 beta, with ext4 formatting.

Before I was using 8.10, so I didn't have any hardware issues.

In Ubuntu 9.04, when I click the firefox, it opens the default page, but when I try to open some other URL, it simply closes. This happens with every page I try to browse. Anyone having similar problem? 

I am using windows to post this problem. Can someone recommend me to install some other browser in 9.04, so that I can boot in Ubuntu till the time I find the fix for firefox??

Thanks :)

---

### Post by Gramps on 2009-04-05
I had the same problem when I did an install off a CD then I did a sudo apt-get update then sudo apt-get dist-upgrade and the problem disappeared. The 1st command will get a list of the latest packages, the 2nd will install the latest updates for 9.0.4

If that doesn't help, you can use epiphany from the repositories. If you need a full features browser you could then download Opera

---

### Post by leonardo_neo on 2009-04-05
> **Gramps said:**
> I had the same problem when I did an install off a CD then I did a sudo apt-get update then sudo apt-get dist-upgrade and the problem disappeared. The 1st command will get a list of the latest packages, the 2nd will install the latest updates for 9.0.4

If that doesn't help, you can use epiphany from the repositories. If you need a full features browser you could then download Opera

Thanks buddy, your solution worked for me too. :)

But before posting my question in forum, I tried to resolve the issue on my own by complete uninstallation and reinstallation, because of that the dist-upgrade command was not helping in the previous install. So I did install ubuntu again, and the fist thing after installation I did was the update and dist-upgrade, and now firefox is working good. 

Thanks again :)

---

### Post by mamamia88 on 2009-04-05
+1 for epiphany much faster than firefox and hasn't crashed on me yet

---

### Post by psyke83 on 2009-04-06
> **mamamia88 said:**
> +1 for epiphany much faster than firefox and hasn't crashed on me yet

That's a workaround, not a solution ;).

To the OP, I realize that you've resolved the issue, but is it possible that your disk (or home partition) was 100% full? I recently noticed Firefox crashing immediately, and that was the cause.

---

### Post by leonardo_neo on 2009-04-06
> **psyke83 said:**
> That's a workaround, not a solution ;).

To the OP, I realize that you've resolved the issue, but is it possible that your disk (or home partition) was 100% full? I recently noticed Firefox crashing immediately, and that was the cause.

I afraid that was not the case....Though I have old comp, with 40 Gb hard disk and dual boot, still I keep 10 Gb for Ubuntu installation. So even after installation, my home partition had around 4 Gb space left.

---

### Post by psyke83 on 2009-04-06
> **leonardo_neo said:**
> I afraid that was not the case....Though I have old comp, with 40 Gb hard disk and dual boot, still I keep 10 Gb for Ubuntu installation. So even after installation, my home partition had around 4 Gb space left.

Alright. In future, you can launch "firefox" from a terminal to see any debug output. Your profile may have been corrupted; moving or deleting the ~/.mozilla directory would have forced the creation of a new profile to help you identify the problem.

---

### Post by JK3mp on 2009-04-06
Hmmm..doubt the low disk space problem then. 2nd the above post as far as getting a more specific error towards figuring out the problem.

---

