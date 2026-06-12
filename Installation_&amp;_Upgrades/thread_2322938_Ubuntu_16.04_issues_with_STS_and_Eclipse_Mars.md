---
title: "Ubuntu 16.04 issues with STS and Eclipse Mars"
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by razvan11 on 2016-05-01
Hi,

  Just installed 16.04 LTS Desktop, than on top STS (Spring Tool Suite 3.7.3) and it takes a lot of time for each action. If I try to import maven projects it hangs. Then I tried Eclipse Mars, smae thing. This was working with 15.
  Can you please check? Thanks!

Best Regards,
Razvan

---

### Post by Mike_Summers on 2016-05-03
I'm having the same issue, STS 3.7.3 was fine on 14.04 LTS but hangs doing most anything on 16.04 LTS.

What version of Java are you using? I'm using
[FONT=courier new]java version "1.8.0_91"[/FONT]
[FONT=courier new]Java(TM) SE Runtime Environment (build 1.8.0_91-b14)[/FONT]
[FONT=courier new]Java HotSpot(TM) 64-Bit Server VM (build 25.91-b14, mixed mode)[/FONT]

---

### Post by razvan11 on 2016-05-03
Hi Mike,

  I use the default openJDK. I reverted to ubuntu 15.10 and STS 3.7.1 (java version "1.7.0_95"OpenJDK Runtime Environment (IcedTea 2.6.4) (7u95-2.6.4-0ubuntu0.15.10.2)
OpenJDK 64-Bit Server VM (build 24.95-b01, mixed mode)) since I couldn't fix 16.04. Also tried this here on 15.10 doesn't work with STS 3.7.3 so most likely won't do it on the 16 also. ([https://stackoverflow.com/questions/36822242/eclipse-doesnt-work-with-ubuntu-16-04](https://stackoverflow.com/questions/36822242/eclipse-doesnt-work-with-ubuntu-16-04))

 Best Regards

---

### Post by Mike_Summers on 2016-05-03
Interesting.

I just installed Mars.2 from the installer into /opt, then used the Marketplace to install STS, and modified eclipse.ini with
> 
--launcher.GTK_version
2

[FONT=arial]And everything works as it should. Your link to Stack Overflow did the trick.[/FONT]

---

