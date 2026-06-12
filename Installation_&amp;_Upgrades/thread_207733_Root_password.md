---
title: "Root password"
date: 2006-07-02
forum: Installation &amp; Upgrades
---

### Post by AlliumPorrum on 2006-07-02
Hi!

What might be the default password for the root- level user after Ubuntu installation?? I tried to use the same password that I gave for the default user during the installation, but that's not it :-s

---

### Post by cacharreo on 2006-07-02
On Ubuntu there is not root account. You should use the ***sudo*** before the command you want to run like root

---

### Post by beausimon on 2006-07-02
There is a root account. If you really want you can go to system-> users and groups  to change the password of root.

---

### Post by karl0318 on 2006-07-02
When I installed Ubuntu 6.06 I saw no opportunity to create a password for the root account, only for my user account (which is sufficient for installing Linux updates). If I go into the System Users menu, how do I setup a password for the root? Is there a default root password? Thank you.

---

### Post by karl0318 on 2006-07-02
I was able to create my own password for the Root Account by going into System and User Accounts from the top menu and clicked on "Show All Users" and then clicked on Properties for root. I can now go to the Konsole and enter the su command and it takes the new root password I just created.

To those who answered to my question from earlier - thank you!

[Although, as I am new to this forum, I haven't figured out how to access your replies yet!]

---

### Post by rcarring on 2006-07-02
Root privileges require the first user created on installation to use their own password. If you do recovery mode it will log you in as root automatically.

Hmmm, isn't that a security hole?

---

### Post by aysiu on 2006-07-02
[QUOTE=rcarring]Root privileges require the first user created on installation to use their own password. If you do recovery mode it will log you in as root automatically.

Hmmm, isn't that a security hole?[/QUOTE] No, not really. Anyone who has physical access to your computer (the ability to reboot it) can pretty much get root access pretty easily--either by booting a live CD, resetting the BIOS, or just physically removing the hard drive.

---

### Post by jdkullmann on 2006-07-02
[QUOTE=AlliumPorrum]Hi!

What might be the default password for the root- level user after Ubuntu installation?? I tried to use the same password that I gave for the default user during the installation, but that's not it :-s[/QUOTE]

I believe you can also boot into single-user mode and then set the root password from there

---

