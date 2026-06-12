---
title: "do-release-upgrade Problem?"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by tbohon on 2009-12-04
I'm running 9.04 Server edition and, following the news of the 9.10 Server edition release decided to do an in-place upgrade.

However, when I open a Terminal window and type in 

```
do-release-upgrade
```

I receive a message stating that there is "no new release".

Am I doing something wrong with this command?  I just did a whole slew of 'regular' upgrades to ensure 9.04 was current before the 9.10 move ... any chance I could have inadvertently done the release upgrade then?

Speaking of which, is there a command/way to find out exactly what version I'm currently running?

Thanks in advance.

Tom

---

### Post by phillw on 2009-12-04
> **tbohon said:**
> I'm running 9.04 Server edition and, following the news of the 9.10 Server edition release decided to do an in-place upgrade.

However, when I open a Terminal window and type in 

```
do-release-upgrade
```I receive a message stating that there is "no new release".

Am I doing something wrong with this command?  I just did a whole slew of 'regular' upgrades to ensure 9.04 was current before the 9.10 move ... any chance I could have inadvertently done the release upgrade then?

Speaking of which, is there a command/way to find out exactly what version I'm currently running?

Thanks in advance.

Tom
Hi

```
uname -a
```

will give you your kernel version - we can see if you're on 9.04 or 9.10 from that

I'm pretty sure, it has upgraded you - but if you post the output I'll double check for you.

Phill.

---

