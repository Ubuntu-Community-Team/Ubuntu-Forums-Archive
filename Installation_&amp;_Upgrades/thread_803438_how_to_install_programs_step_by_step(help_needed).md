---
title: "how to install programs step by step(help needed)"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by tbones94589 on 2008-05-22
I'm a rather new user of Ubuntu altogether, I'm having problems installing programs following the terminal instructions listed on the install pages given. If anyone can plz help me I would greatly appreciate the time you take assisting me..... Thank you all for looking, Tony.:confused:

---

### Post by Peter09 on 2008-05-22
In Linux most programs can be installed through synaptic. If you are a beginner I suggest do it this way for a while.

Following the menues,
System->Administration->Synaptic Package Manager

When this opens you will see a big list of applications. Just tick the box for the one you want and the Apply.

The rest is automatic.

Also, for a limited range of programs its simpler to go to Applications->Add/Remove

PC

---

### Post by ajgreeny on 2008-05-22
I agree with Peter09, but it is so easy to use the terminal once you know what you want to install so don't put it away as a possibility just yet.

There are two main terminal apps to use, apt-get and aptitude, both of which use the same back-end as synaptic.  Synaptic is easier to use at the start to search for applications, but if you know you want to install for example abiword, the word processor, you type in the terminal ```
sudo apt-get abiword
```or ```
sudo aptitude abiword
```and follow the prompts for password (which won't show on screen at all) and then accept with a "Y" for yes.

I hope that helps.

---

### Post by tbones94589 on 2008-05-22
Thank you guys....You guys are very helpful, I'm hoping that I don't have to worry bout to much more from now on but I did need the initial bump to help me get moving....lol greatly appreciate you taking time to help a newbie..... Tony.

oh btw....you guys rock!!! thx again.:guitar:

---

### Post by Herman on 2008-05-22
:) Here are two links on the subject, _[How to install *ANYTHING* in Ubuntu!]("http://monkeyblog.org/ubuntu/installing/")_ and, Community Docs: [Software Management]("https://help.ubuntu.com/community/SoftwareManagement"). :)

---

