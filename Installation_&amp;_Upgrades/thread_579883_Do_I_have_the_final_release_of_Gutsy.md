---
title: "Do I have the final release of Gutsy?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by Posterus on 2007-10-18
I was wondering if someone could tell me how to check to see if I had the latest final release of Gutsy.  I have been running the Beta client and updated ragularly.  Is there a certain way I should upgrade? or does it upgrade automatically?

-Posterus

---

### Post by mattpker on 2007-10-18
No it just upgrades for you. As long as your running 7.10 (even beta) then you will be getting all the updates for it. So no your are no longer running beta if you did your updates.

---

### Post by FredB on 2007-10-18
> **Posterus said:**
> I was wondering if someone could tell me how to check to see if I had the latest final release of Gutsy.  I have been running the Beta client and updated ragularly.  Is there a certain way I should upgrade? or does it upgrade automatically?

-Posterus

If you updated your ubuntu, it is ok.

For info, here is how to verify simply. For my AMD64 installation, in console :

```
 cat /etc/issue.net ; uname -a
Ubuntu 7.10
Linux fredo-gutsy 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux
```

If you have something like this, your gutsy is a final one.

---

### Post by Posterus on 2007-10-18
Thank you guys, I appreciate your responses.

---

### Post by marf88 on 2007-10-18
Curious... this is my output

marf@desktop:~$ sudo uname -a
Linux desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux


No mention of 7.10

I installed Tribe 5 back in the day, but have run updates ever since. So I'm assuming (hoping) this is final.

---

### Post by bburg on 2007-10-19
> **marf88 said:**
> Curious... this is my output

marf@desktop:~$ sudo uname -a
Linux desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

No mention of 7.10

Type in your terminal window: cat /etc/issue.net

---

### Post by marf88 on 2007-10-19
Good?

> marf@desktop:~$ cat /etc/issue.net
Ubuntu 7.10

---

### Post by marf88 on 2007-10-19
perhaps you can take a look at my issue here please

[http://ubuntuforums.org/showthread.php?p=3569092](http://ubuntuforums.org/showthread.php?p=3569092)

---

