---
title: "Trusty upgrade process stalled by lots of questions"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by spookybathtub on 2015-01-26
I have a headless server running Precise, which I'm upgrading to Trusty.  I'm upgrading over SSH using screen.  It's taking all day, because occasionally there is a conflict with some configuration file, and it asks whether I'd like to keep my custom version or use the new updated version.  I understand this question is necessary, but I think this is a bad way of doing it.  Is there some way to have the install finish, unattended, and then ask all the questions all at once?

---

### Post by nerdtron on 2015-01-26
I wouldn't even recommend this type of upgrade. In-place upgrades could be hit-or-miss depending on your hardware and your software config you may end up with an unusable server. Have you even tested this type of upgrade before?

** Test before you leap **

---

### Post by ian-weisser on 2015-01-26
> **spookybathtub said:**
>   I understand this question is necessary, but I think this is a bad way of doing it.  Is there some way to have the install finish, unattended, and then ask all the questions all at once?

It's a very good way for the machine. Humans find it understandably inconvenient.

It's good for the machine because it doesn't leave a bunch of packages in an inconsistent or half-installed state. Apt's (fairly simple) logic is necessarily conservative, since one ever-present alternative is a thoroughly broken system. 

You are essentially asking for apt to keep a queue of half-installed packages...which then block other depending packages from installing. I see potential there for a cascade into quite serious consequences under some conditions. "Hey, I forgot to answer a few stupid questions and rebooted instead, but my upgraded system wouldn't boot at all." Not waters I want to swim in.
I think perhaps you are overestimating how smart the system is.

In one sense, you *can* get the machine to not ask the questions at all...by throwing your customizations away during a reinstall, as Nerdtron suggested.

---

### Post by spookybathtub on 2015-01-26
nerdtron, you were right. I did end up with an unusable server. Rather than tracking down the problems, I'm just going to clean install the whole thing. After running for 4 years, it's about time anyway. Note: this is not a critical server; it just runs some household tasks.

---

