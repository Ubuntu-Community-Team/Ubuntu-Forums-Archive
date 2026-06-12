---
title: "update duplication"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by hg21 on 2012-01-24
I just had a notification to update.  Among the many things said to have been downloaded and installed was  linux-image-3.0.0-15-generic.  This was already on my system for several days.  I suspect there were other duplications.

At the end of the installation Apper reported "You have no updates. Verified 34!!! day ago" (my !!!).

Usually this message is less than 1 day.   Maybe the update notification system is not reading my /var/lib/dpkg/info/ directory correctly. 


How/what should I check please?

---

### Post by raja.genupula on 2012-01-24
check your system date once and second one is try with a restart. Let us know what you got .

---

### Post by hg21 on 2012-01-24
> **raja.genupula said:**
> check your system date once and second one is try with a restart. Let us know what you got .

Thanks for reply.

How do you mean by check system date?

I did:

$ date         and got 

Tue Jan 24 15:29:35 GMT 2012
Is that what you mean.

Before restart I got


$ uname -a

Linux hg21-sda1 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I'll restart now and come back and edit to add new info

I now get:

$ uname -a

Linux hg21-sda1 3.0.0-15-generic #26-Ubuntu SMP Fri Jan 20 17:23:00 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

#25 has changed to #26 so I guess I was wrong and it's not just a duplication.

I/m still puzzled by the 34 days.

---

### Post by ilia_avramov on 2012-01-25
same problem! For then third time it installs same updates. Finally I updated my system manually by sudo apt-get update & sudo apt-get upgrade. (Kubuntu 11.10)

---

### Post by raja.genupula on 2012-01-25
> **hg21 said:**
> Thanks for reply.

How do you mean by check system date?

I did:

$ date         and got 

Tue Jan 24 15:29:35 GMT 2012
Is that what you mean.

Before restart I got


$ uname -a

Linux hg21-sda1 3.0.0-15-generic #25-Ubuntu SMP **Mon Jan 2 17:44:42** UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I'll restart now and come back and edit to add new info

I now get:

$ uname -a

Linux hg21-sda1 3.0.0-15-generic #26-Ubuntu SMP** Fri Jan 20 17:23:00** UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

#25 has changed to #26 so I guess I was wrong and it's not just a duplication.

I/m still puzzled by the 34 days.

18 days difference already here .

---

### Post by raja.genupula on 2012-01-25
> **ilia_avramov said:**
> same problem! For then third time it installs same updates. Finally I updated my system manually by sudo apt-get update & sudo apt-get upgrade. (Kubuntu 11.10)

sometimes it will happen if synchronization problem with hard ware clock i think . I hope better to maintain the system clock  synchronization with NTP servers . 

[https://help.ubuntu.com/community/UbuntuTime](https://help.ubuntu.com/community/UbuntuTime)

---

