---
title: "Upgrade 14.04.1 kernel to 14.04.5"
date: 2019-09-19
forum: Installation &amp; Upgrades
---

### Post by littlezero on 2019-09-19
I have kernel version 14.04.1 and I would like to upgrade to the latest supported kernel listed at 14.04.5 without a fresh install. I have followed the update procedure from here:
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

But after running the command, and using uname -a it still says I am on 14.04.1.

Is there not a way to update the Kernel? Does it keep the same # but update all the packages to be equivalent to 14.04.5?

---

### Post by CatKiller on 2019-09-19
14.04 is no longer supported. Its repositories will have, or will have shortly, moved somewhere else.

If you want to be up to date you'll need to move to either 16.04 or 18.04, which are still supported.

---

### Post by deadflowr on 2019-09-19
You install 16.04.1 since 14.04 is now unsupported,
unless you've subscribed to Ubuntu Advantage. (Ubuntu's Paid extended support service)

---

### Post by littlezero on 2019-09-19
Right, I understand that it went end of life. It is just a system for work that they would like to keep on 14 if possible. Is it safe to assume if I ran the update process in that page I linked above, those are the most up-to-date updates I am going to be able to find?

---

### Post by deadflowr on 2019-09-19
No.
Those updates are all old and out of date already.
As posted only updates for 14.04 come through a special repository for users who have signed up for the paid Ubuntu Advantage service.
[https://ubuntu.com/esm]("https://ubuntu.com/esm")

---

### Post by littlezero on 2019-09-19
Thank you, that answers my questions.

---

