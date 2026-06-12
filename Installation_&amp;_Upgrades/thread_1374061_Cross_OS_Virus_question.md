---
title: "Cross OS Virus question"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by JoeBlotnik on 2010-01-06
I'm going to install a dual boot Ubuntu/Winxp on a PC. I need Ubuntu because  I occasionally visit Russian sites, and as you know, they are notorious for viruses. I want to learn to use Ubuntu and possibly switch completely in the future. 

I have one question. Is is likely that someone could send a windows virus to my windows OS THRU my Ubuntu browser? I realize Ubuntu itself is fairly safe, but am concerned about having the Win OS infected thru the Ubuntu brower. 

Appreciate your help. 

JoeB

---

### Post by mocoloco on 2010-01-06
No.  It's not *completely* impossible but it's very very unlikely.

---

### Post by doas777 on 2010-01-06
it is highly improbable, especially in the case you mention. far more likely, you would accidentally download a trojan via ubu, and then try to open it in windows (at which point you are p0wned).

if you are worried about someone managing to break FF such that they can interact with the underlying system, then look into apparmor and selinux. they both apply policies to applications ensuring that the app can only access the resources that the policy explicitly states they can. I have heard that there is a preconfigured FF apparmor profile in the repos (finally).

---

### Post by cpplinux on 2010-01-06
Do not mount your Windows partition in Ubuntu. Use ext3/4 for Ubuntu, Then the two systems are separated and not sharing file.

---

