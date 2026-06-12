---
title: "WUBI install hangs after /usr/sbin/cupsd"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by scottyscottscott on 2011-07-03
Hello, I am trying to install WUBI (Natty Narwhal) on my new HP7t, i7-2720qm, radeon graphics computer.

I successfully installed the initial windows part, then I rebooted it and selected Ubuntu, the Ubuntu screen came up and went through the text boot/install? process.  The process hangs after the line:

type=1400 audit(1309686869.557:9): apparmor="STATUS" operation="profile_load" name="usr/sbin/cupsd" pid=828 comm="apparmor_parser"

This also happened after I turned off the computer by pressing the power button, and selecting the recovery ubuntu boot selection.

I attached a rather blurry picture of the problem, it might be impossible to read though.

Thanks for your help!
Scott

---

### Post by Rubi1200 on 2011-07-03
Hi and welcome to the forums :-)

This is possibly a graphics issue. You can try the methods suggested here:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

I would start with nomodeset.

---

