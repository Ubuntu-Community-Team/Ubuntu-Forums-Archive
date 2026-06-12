---
title: "How I can upgrade to the last Dapper Drake version?"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by Davigetto on 2006-11-21
Hello, I have Dapper Drake 6.06, and i want to upgrade to the last version of Dapper Drake to see if they can solve some bugs that i have found. I have read about 6.06.1....

How I can upgrade my ubuntu to the last version and upgrades of Dapper Drake? I don't still want to use Edgy Eft because i have tested it and have too much bugs for me.

Thank you. Greetings

---

### Post by louieb on 2006-11-21
If you have been keeping up with the updates you should be there.
to check.
```
lou@gameu:~$ lsb_release -a
```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper
lou@gameu:~$

Description field should show 6.06.1.

If not then 
```
 sudo aptitude update
 sudo aptitude dist-upgrade

```

---

### Post by Davigetto on 2006-11-21
Really Thank you man, you have solved my problem.

Greetings

---

