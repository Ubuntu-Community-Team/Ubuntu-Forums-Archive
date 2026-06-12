---
title: "ntfs-3g &amp; libntfs-3g16  backports????? do i or don't i??"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by ZeroHimself on 2008-02-07
ok, i am not a total newbie to linux, new to ubuntu, but i've had some debian expierence before...
in my software sources i have every box checked under ubuntu software
and under 3rd party i have added a few repositories
under Updates(probably the relevant place), i have

(x) important security updates (gutsy-security)
(x) recommended updates (gutsy-updates)
(  ) Pre-released updates (gutsy-proposed)
(x) Unsupported updates (gutsy- backports)

just today, my update manager informed me "You can install 2 updates".... upon reviewing them, they are "Backports" of ntfs-3g packages, and i am unsure that i want to "backport"-  i mean what if it breaks something i use (at all times, i am in the process of moving from windows)??

anyhow, it tells me 

libntfs-3g16
description.....
Version 1:1.1120-1ubuntu2~gutsy1 (size)

and

ntfs-3g
description...
From version 1:1.913-2ubuntu1 to 1:1.1120-1ubuntu2~gutsy1 (size)


the idea of backporting critical(at least to me) drivers, seems like a bad idea, and also, i have no way of knowing where the backports came from????(i don't know if this is an ubuntu update(or "DOWN"date), or if it is some other repositories outdated stuff???)

i had to enable the "backports" section for either winehq, or the avant-window-navigator.... not really sure, heck, i'm not even sure if i should keep it checked or not

Please help, knowledgable ones, i need guidance ;-) :confused:

---

### Post by Rocket2DMn on 2008-02-07
If you're worried, then don't get them and disable the backports repository - most of us don't use it.  The current ntfs-3g driver is stable, so there is no need to risk an unsupported update to it.

---

### Post by ZeroHimself on 2008-02-07
ok, that is kind of what i figured... but just for my own expereience, what exactly is the backport repository for?? why would i need it?

---

### Post by Rocket2DMn on 2008-02-07
When versions of Ubuntu are released, program versions tend not to change until the next release, they are "frozen" at a particular version.  However, newer versions can be released through the backports as time passes for those who want them.
Have a look here - [https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

