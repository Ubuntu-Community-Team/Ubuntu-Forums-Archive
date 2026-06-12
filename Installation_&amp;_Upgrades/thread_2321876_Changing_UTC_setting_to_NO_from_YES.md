---
title: "Changing UTC setting to NO from YES"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by Blix775 on 2016-04-25
I have a desktop that has two  hard drives, one for windows and one for linux. Normally windows adds 4 hours to the time if Ubuntu has been booted previously and I found out that the solution to that problem was to open a file with super user privileges and then chaning the option UTC from yes to no. Here is the command I used to use:

gksu gedit /etc/default/rcS

To my surprise, the UTC Option is no longer there. I would like to know what I have to do now to fix this. Thanks in advanced.

I am using Ubuntu 16.04 64 bits.

---

### Post by $yl9pAR%t on 2016-04-25
To check your settings:

```
timedatectl
```

To change RTC in local TZ:

```
timedatectl set-local-rtc 1
```

More info here:

[http://manpages.ubuntu.com/manpages/xenial/man1/timedatectl.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/timedatectl.1.html)

My working settings:

```

Network time on: yes
NTP synchronized: yes
 RTC in local TZ: yes
```

---

### Post by Blix775 on 2016-04-25
So that is the new term for UTC? I just changed it and I will let you know if it worked after I restart a couple of times.

---

### Post by Blix775 on 2016-04-26
It worked perfectly. Thanks a lot.

---

### Post by $yl9pAR%t on 2016-04-26
Fine it works. I am just not sure what will happen in the autumn (when DST will change), but I hope as long as NTP is active it should be OK.

---

