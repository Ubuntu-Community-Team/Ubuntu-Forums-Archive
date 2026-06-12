---
title: "apt-get update problems?"
date: 2010-08-07
forum: Installation &amp; Upgrades
---

### Post by cooltuyul on 2010-08-07
alright, so every time i run this command i get this thrown at my face

```
W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz  404  Not Found [IP: 212.72.53.130 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Ugh. 

what could possibly be wrong?

thanks

---

### Post by Elfy on 2010-08-07
An old or out of date or just not availabel at the moment repo I would guess.

Check in either /etc/apt/sources.list for it or it might be in a list in /etc/apt/sources.list.d

---

### Post by cooltuyul on 2010-08-07
well, it happens every time i run sudo apt-get update

also, what exactly am i supposed to be looking for in etc/apt/sources.list.d?

---

### Post by akester on 2010-08-07
You could find that line (download.skype.com...) and delete it.

Rather than using the repos to get skype, download it [here.]("http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/post-download/")

Hope this helps

---

### Post by ak4allz on 2010-08-07
> **cooltuyul said:**
> well, it happens every time i run sudo apt-get update

also, what exactly am i supposed to be looking for in etc/apt/sources.list.d?

maybe the CLI interface won't good enough for you. I think you should open the software sources under the Administration menu, go to the other software tab and untick the line that have the url.

[IMG]http://img14.imageshack.us/img14/9569/unticksomething.png[/IMG]
I hope this would help.

---

### Post by cooltuyul on 2010-08-07
splendid, i dont get that message any more. however im curious, will disabling this repo prevent my computer from downloading some software?

---

### Post by ak4allz on 2010-08-08
if you disable the repo, you will not get any application provided by the repo. As example, you have a repo in your software sources providing an application known as "Frantz Antivirus". If you disable that repo, you cannot fetch that application. 

Easy, right? So, don't disable the main repo or installed repo, cause they always providing new updates. If you disable that, you will no longer can fetch the updates.

---

### Post by cooltuyul on 2010-08-09
cool thanks

---

