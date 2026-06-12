---
title: "how to install james(The Apache Java Enterprise Mail Server )"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by jinjh on 2006-06-26
Is there anybody know how to install The Apache Java Enterprise Mail Server with **apt-get install**  command.  I run apt-cache search james,but can't find The Apache Java Enterprise Mail Server package. 
     any suggestions is welcome. thanks a lot.

---

### Post by jinjh on 2006-06-26
[QUOTE=jinjh]Is there anybody know how to install The Apache Java Enterprise Mail Server with **apt-get install**  command.  I run apt-cache search james,but can't find The Apache Java Enterprise Mail Server package. 
     any suggestions is welcome. thanks a lot.[/QUOTE]


Help! Please!

---

### Post by smeel on 2007-03-30
I also want to install the Apache James Mail Server. Any ideas. I come across this post through Google.

Can it be done via apt-get? If not how can it be done??

Thank you

Jason Smith

---

### Post by carcophan on 2008-06-01
it can be done quite easily. I did it on Debian Etch, so it shouldn't be much different on ubuntu. Just download the package from the Apache James site and follow the instructions. Works brilliantly.
Only problem is that I can't get a proper init script working. I used the skeleton in /etc/init.d and linked them with update-rc.d but when I reboot my system, it wont start. executing the script: "/etc/init.d/phoenix start" does exactly what you would expect and so does the "stop" parameter. The S and K Links all seem to be in the right rc directories but they just wont automatically start when my server reboots.
:(:confused:

---

### Post by PmDematagoda on 2008-06-01
> **carcophan said:**
> it can be done quite easily. I did it on Debian Etch, so it shouldn't be much different on ubuntu. Just download the package from the Apache James site and follow the instructions. Works brilliantly.
Only problem is that I can't get a proper init script working. I used the skeleton in /etc/init.d and linked them with update-rc.d but when I reboot my system, it wont start. executing the script: "/etc/init.d/phoenix start" does exactly what you would expect and so does the "stop" parameter. The S and K Links all seem to be in the right rc directories but they just wont automatically start when my server reboots.
:(:confused:

Please know that you are replying to a thread that is more than an year old and that the people who started the thread may have long gone or they may have already solved their problems.

This thread is closed.

---

