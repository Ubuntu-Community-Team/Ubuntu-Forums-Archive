---
title: "Help me fix hpet increased min_delta_ns errors"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by Blackie_Chan on 2011-08-14
I have a dual boot machine, having Ubuntu 9.10 and 11.04 installed. I usually use 9.10 because it's stable. 

I haven't been able to use 11.04 because of random hangups and freezes which frequently. Today in 11.04, I decided to use netconsole for troubleshooting the problem. What I discovered is that everytime it freezes, I see the following errors in the log:
```
[  416.641983] CE: hpet*  to 7500 nsec
[  416.641997] CE: hpet* increased min_delta_ns to 11250 nsec

```
where hpet* is ranges between hpet2 to hpet6.

How can I fix the problem so I never get the error anymore? Why is it that I never get the error when I run 9.10? 
increased min_delta_ns
Thanks in advance.

---

