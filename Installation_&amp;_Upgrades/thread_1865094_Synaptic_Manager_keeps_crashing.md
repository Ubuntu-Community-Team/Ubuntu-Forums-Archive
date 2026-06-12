---
title: "Synaptic Manager keeps crashing"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by syed.rakib.al.hasan on 2011-10-19
my synaptic keeps crashing.
when i open it, it asks for sudo password.
i give the password.... then synaptic window flashes for less than a second and then goes away.

what's wrong?

after i faced the problem i uninstalled synaptic using apt-get.
i uninstalled....... cleaned...... removed...... auto-removed...... purged....... everything from apt-get.
Then i tried installing synaptic from scratch. Still no luck.

Help please! i just did a clean install of ubuntu11.10 yesterday.

UPDATE: I also removed ~/.synaptic folder........... no luck
UPDATE: Following is my terminal output
```
rakib@rakib-Vostro1510:~$ sudo synaptic
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
rakib@rakib-Vostro1510:~$
```

---

### Post by youngunix on 2011-10-19
did you try restarting after removing it?
if that doesn't work, install 11.04 and see if it works on that version. if it does, upgrade to 11.10 and hope it works.

---

### Post by drs305 on 2011-10-19
Take a look at this thread, starting with post #10. There are a couple of solutions that work for some users:
[http://ubuntuforums.org/showthread.php?t=1854470]("http://ubuntuforums.org/showthread.php?t=1854470")

The solution working most often deals with the Accessibility settings.

---

### Post by syed.rakib.al.hasan on 2011-10-19
> **drs305 said:**
> Take a look at this thread, starting with post #10. There are a couple of solutions that work for some users:
[http://ubuntuforums.org/showthread.php?t=1854470](http://ubuntuforums.org/showthread.php?t=1854470)

The solution working most often deals with the Accessibility settings.

What magic.... who figured that out? it worked for me...... thanks a lot for directing me [to this post]("http://ubuntuforums.org/showpost.php?p=11343209&postcount=10").

:guitar::popcorn:\\:D/\\:D/:popcorn::guitar:

---

### Post by syed.rakib.al.hasan on 2011-10-19
how do i mark this post as SOLVED ???

UPDATE: oh! Thread tools at the top of the thread had that option. :D

---

