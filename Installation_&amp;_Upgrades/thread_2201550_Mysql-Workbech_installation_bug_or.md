---
title: "Mysql-Workbech installation bug or ?"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by Sidmaker on 2014-01-24
Hi to everyone, 
i've faced with really weird behaviour of mysql-workbench. I don't know how i can explain it and where should i dig about my problem. 
So let me describe the problem:

Couple monthes ago i installed **mysql-server** and **mysql-workbench** using default commands:
**sudo apt-get install mysql-server**
and
**sudo apt-get install mysql-workbench**

Everything was OK, but i have not worked with **mysql-server** and **mysql-workbench** since my last time couple monthes ago. Now i came back and could not understand why **mysql-workbench** does work properly. 
Right now i have exact the same problems like described in [**this** **fancy**]("https://bugs.launchpad.net/ubuntu/+source/mysql-workbench/+bug/1108630") bug(Result Grid does not display query results). But what was most ununderstandable for me is: how is it possible? I had working environment before, than something happened and now it does not work.
I tried to reinstall both **mysql-server** and **mysq-workbench** but it didn't help me. Also i tried to install fresh version(even developers version) of **mysql-workbech** - stilll no luck. I still can't understand to who this bug related more to Ubuntu team or Mysql.

If somebody knows any kinds of crutch how to fix my problem i will appreciate that very much, because i didn't find solution.

Some info regarding my OS:
**lsb_release -a**

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

**uname -a**
Linux sidmaker 3.2.0-58-generic #88-Ubuntu SMP Tue Dec 3 17:37:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

---

