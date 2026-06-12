---
title: "Could not opn Lock file?"
date: 2016-12-18
forum: Installation &amp; Upgrades
---

### Post by mazzam15 on 2016-12-18
Hello everyone,

I've recently purchased a new desktop computer for the coding and computer programming courses i'm going to take online, ive decided to use vim as my IDE and in the process of downloading my vim stuffs I came across this error message after trying to install the "apt-get install python-pip"

"
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
"

i am new to the ubuntu comunity 

thanks in advance mates

---

### Post by wildmanne39 on 2016-12-18
The command is sudo apt-get install package name, after you enter the command it will ask for your user password, type the password it will not show it as you type so when you are done hit enter.

The sudo command gives you root temporarily, I believe 15 minutes is the limit.

---

### Post by mazzam15 on 2016-12-18
thanks, it works perfectly

---

### Post by wildmanne39 on 2016-12-18
Please use thread tools at the top of the page to mark the thread solved.
Thanks

---

