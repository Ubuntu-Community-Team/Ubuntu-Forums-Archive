---
title: "Run it as root?"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by mobarobber on 2012-03-23
Hi
I'm trying to install aircrack on my system but here's whats happening:

yash@ubuntu:~$ sudo -l
[sudo] password for yash: 
Matching Defaults entries for yash on this host:
    env_reset

User yash may run the following commands on this host:
    (ALL) ALL
yash@ubuntu:~$ airmon-ng start wlan1
Run it as root
yash@ubuntu:~$ 


Can someone tell a noobie how to fix the problem here?:confused::confused:

---

### Post by sisco311 on 2012-03-23
Welcome to the forums, mobarobber!

In order to start a root shell, you have to run **sudo -i**.  
The last letter is a lowercase I (/a&#618;/), NOT an L (ell or /&#603;l/).

Also please check out: [uhelp]community/RootSudo[/uhelp]

---

### Post by cariboo on 2012-03-23
We don't support this type of activity here. You would be better off asking your question on the[ BackTrack forums]("http://www.backtrack-linux.org/forums/forum.php"). Thread closed.

---

