---
title: "Installation fails on Dell R250 hardware  NX (Execute Disable protection): active err"
date: 2022-08-09
forum: Installation &amp; Upgrades
---

### Post by shodan182 on 2022-08-09
Installation of both 22.04 and 20.04 fails , when checking the logs I see

NX (Execute Disable) protection: active
/var/crash/160048410.4564482079.install_fail.crash

This typically happens after settings up the NIC and sometimes after setting up a local user.

I'm a newbie to Ubuntu installs on physical hardware but have done it virtually without this issue cropping up.

---

### Post by ubfan1 on 2022-08-09
Did you use official sources for the ubuntu install ISO?   Did you ever check your memory?  That bit probably should stay active, but really don't have any experience with what threats it is counteracting.

---

### Post by shodan182 on 2022-08-09
I think i'm focusing on the wrong thing as that error is just the bottom of the page for the /var/crash log.

I have the crash log available to review (was able to use ssh/winscp to get the logs)  Where am I able to post that for someone to assist me in combing through it for more information?

---

