---
title: "Removing hibernate and uswsusp"
date: 2010-12-09
forum: Installation &amp; Upgrades
---

### Post by h9uest on 2010-12-09
Hi, guys:

I installed hibernate by ```
sudo apt-get install hibernate
```. And it breaks the first time I use it. When I try to resume the system, it is just stuck there for at least 10 minutes with the ventilation fan spinning at maximum, after showing something like "successful resume" etc. That forced me to restart the computer and obviously there's a bug. So I remove it. The next time I restart my system, there's the following message:
"resume: libgcrypt version: 1.4.4"

Although I can still enter the system, I'm quite uncomfortable with this message since it shows up every time. So I also removed uswsusp.

Now everything returns to normal, and I'm happy.
But my question is, since I previously used hibernate, and the computer put everything into an img file for resume and stored it somewhere on the disk. I guess the img file hasn't been deleted and that's why I continue to see "resume: libgcrypt version: 1.4.4". Probably the computer detects some file and tries to resume using it, but fails, so it then restart a new session. 

Is it correct? and how can I find the file and delete it manually? When I run hibernate, I think I saw a message showing where the file is stored, but I don't remember where it was. Any ideas are appreciated.

---

### Post by nijibug on 2011-02-05
Bumping this thread because I'm having similar issues.

---

### Post by rvboutin on 2011-03-29
Hi,
Same issue for me, I installed hibernate to try to solve a problem of a laptop not able to resume after suspend or hibernate. Now boot time is slightly longer due to this command: resume: libgcrypt 1.4.5
I have removed hibernate as it did not solve the problem at all, but resume: libgcrypt 1.4.5 still appear...
very annoying indeed.
Any solution guys?
Cheers,
Rv

---

### Post by matt_symes on 2011-03-29
Hi

Open a terminal and type

```
swapon -s
```

Post the results back here.  It will tell us where your swap file is. 

Did you rebuild your initramfs after uninstalling hibernate ? Maybe there is a reference to it there.

Kind regards

---

