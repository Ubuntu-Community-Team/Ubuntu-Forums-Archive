---
title: "Feisty Standby Broken, whats to do?"
date: 2007-05-06
forum: Installation &amp; Upgrades
---

### Post by petersra on 2007-05-06
OK, my thinkpad t23 / S3 video card and suspend to RAM worked on a Kubuntu Edgy.  However, after I upgraded to Feisty the suspend/resume results in a hung system.  

I have looked at a lot of posts and this appears to be a common problem.  The question is, what should I do.  Options are:

1.  Wait until a fix comes out
2.  Try to hack my way through countless remedies in hopes that I stumble on to a solution
3.  Try alternative approach aka uswsup

Suspend is a tricky complex process and I am not sure I understand all the steps that make it work.  So my ability to hack a solution is somewhat questionable.

---

### Post by rondackcpu on 2007-05-06
I'm having "suspend" issues with all my computers after the upgrade to Feisty.  All seemed to work correctly with Edgy.  They are: Dell E310,  may fail to resume, may fail to connect to modem, other times OK;  Dell Inspiron 5160, always fails to resume;  Dell Inspiron 5000e, may fail to suspend (resumes immediately).  Hope is that some update will fix the problem.

I enjoy playing with the configuration files and would try things, but I'm too much of a newbie to do this on my own.

Any help?

---

### Post by petersra on 2007-05-06
Actually, USWSUSP does not completely work.  It does come out of suspend to ram.  However, the wireless connection is broken.  Also, running the 2.6.20 generic kernel

---

### Post by petersra on 2007-06-20
Well, after several months of screwing around I finally reloaded Edby.  I tried everything on Feisty to get suspend/resume to work, including a clear Feisty install.  However, nothing could get me past the dead USP ports.  This regression is a good example of why linux is not ready for prime time.

---

