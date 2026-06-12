---
title: "Black Screen Crashes"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaco223 on 2010-03-30
I'm having an issue with Lucid crashing to a black screen, as if my monitor is turned off.
I logged on about 90 minutes ago, and it has crashed twice like this. Is this problem
related to video drivers? I'm using an iMac 24" LCD panel,  ATI Raedon HD 2400 XT
video. I'm currently using nouveau.

Edit. 3 black screen crashes in 2 and half hours. What was I doing when it crashed? surfing
the web with firefox.

---

### Post by zika on 2010-03-30
[http://ubuntuforums.org/showthread.php?t=1347430](http://ubuntuforums.org/showthread.php?t=1347430)
[http://ubuntuforums.org/showthread.php?t=1407214](http://ubuntuforums.org/showthread.php?t=1407214)

---

### Post by jaco223 on 2010-03-30
thanks for the provided links zika, I still need to sort them out to get a better understanding of what is causing the issue.

Jaco

---

### Post by zika on 2010-03-30
Good luck! I've been restling with that for (quite) some time. UMS is the (for now) only solution, for me... I hope You'll find the better solution and share it with us...

---

### Post by jaco223 on 2010-03-30
Bump

I've had at least 6 black screen crashes today! I don't understand what's going on.
I can't sort out from the other threads what's causing the problem, is it related to
video drivers? I'm using the ati opensource driver if that makes a difference.
Any suggestions or advice would be greatly appreciated.
How do you go about implementing UMS, it has worked for zika, but I don't know
how to do this.

Thanks,

Jaco

---

### Post by zika on 2010-03-31
> **jaco223 said:**
> Bump

I've had at least 6 black screen crashes today! I don't understand what's going on.
I can't sort out from the other threads what's causing the problem, is it related to
video drivers? I'm using the ati opensource driver if that makes a difference.
Any suggestions or advice would be greatly appreciated.
How do you go about implementing UMS, it has worked for zika, but I don't know
how to do this.

Thanks,

JacoJust add _nomodeset_ to Your kernel line in GRUB while boot-ing...

---

### Post by jaco223 on 2010-03-31
> **zika said:**
> Just add _nomodeset_ to Your kernel line in GRUB while boot-ing...

Zika thanks so much for your invaluable assistance, I edited GRUB, the boot screen
doesn't look as nice, but it's better than dealing with the black screen crashes. Hopefully
they will have this sorted out for rc, or I hope for the final release. Thanks again.

Jaco

Eidt. Zika I edited this line in GRUB: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
and on my first boot it looked like the boot screen was in a low graphics mode, and now when I
rebooted it was back to a normal graphics mode.

---

### Post by zika on 2010-03-31
> **jaco223 said:**
> Zika thanks so much for your invaluable assistance, I edited GRUB, the boot screen
doesn't look as nice, but it's better than dealing with the black screen crashes. Hopefully
they will have this sorted out for rc, or I hope for the final release. Thanks again.

Jaco

Eidt. Zika I edited this line in GRUB: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
and on my first boot it looked like the boot screen was in a low graphics mode, and now when I
rebooted it was back to a normal graphics mode.Did You do **sudo update-grub**? I did not quite get that from Your post... Sorry if You did.

---

### Post by jaco223 on 2010-03-31
> **zika said:**
> Did You do **sudo update-grub**? I did not quite get that from Your post... Sorry if You did.

Zika yes I did **sudo update-grub**, after that I rebooted. i used the computer for a couple
of hours this morning, had to run some errands. Started up again, so far no cashes. I'll
keep monitoring my situation and report back if I have any crashes. Thanks.

Jaco

---

### Post by jaco223 on 2010-04-01
Zika, I had to reinstall Lucid this morning because I installed kde, but  had problems with it, so I wiped
everything and jut finished reinstalling, but now I forget what file I  need to edit to add nomodeset.

Jaco

---

### Post by zika on 2010-04-01
> **jaco223 said:**
> Zika, I had to reinstall Lucid this morning because I installed kde, but  had problems with it, so I wiped
everything and jut finished reinstalling, but now I forget what file I  need to edit to add nomodeset.

Jaco```
gksu gedit /etc/default/grub
sudo update-grub
```
You might want to try it without nomodeset, I'm on KMS for several hours now...

---

### Post by jaco223 on 2010-04-01
> **zika said:**
> ```
gksu gedit /etc/default/grub
sudo update-grub
```You might want to try it without nomodeset, I'm on KMS for several hours now...

Zika thanks for the heads up, I'll wait and see what happens before adding nomodeset,
I just finished updating everything. Everything looks really good after the update.

Jaco

---

