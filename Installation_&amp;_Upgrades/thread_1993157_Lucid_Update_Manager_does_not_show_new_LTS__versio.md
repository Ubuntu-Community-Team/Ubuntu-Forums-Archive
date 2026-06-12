---
title: "Lucid Update Manager does not show new LTS  version"
date: 2012-06-01
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2012-06-01
The title says it all. The Update Manager is set to show New LTS releases only, but does not show 12.04. 

I seem to recall this is known problem, but is there a way to fix it?

---

### Post by ajgreeny on 2012-06-01
You apparently need to wait until the 12.04.1 version comes in July(?) before that will automatically work for you.

You can still do it manually if you wish, but if I were you I would wait until you are asked by update-manager.

---

### Post by rsteinmetz70112 on 2012-06-01
Oddly, if I hit <Alt F2> and run "update-manager -d" it does prompt for 12.04. I tried editing the menu and adding the "-d" to the command but the behavior didn't change. Also if I set Update Manager to prompt for new releases it prompts for 10.10.

Something is off somewhere.

---

### Post by darkod on 2012-06-01
Nothing is off.

If you are running the previous LTS, and you have the option set to prompt you only for LTS releases, it doesn't prompt you for the next one until the .1 is released. In this case until 12.04.1 which is due in July.

You can "force" it with the -d option, that's why it shows 12.04 in that case.

You can wait until July when Update Manager will prompt you, or use the -d now.

Note that some issues seen in 12.04 might get fixed in 12.04.1.

---

### Post by rsteinmetz70112 on 2012-08-22
OK its now August and on one of my machines I am offered the option of upgrading to 12.04 LTS, by Update Manager.

It is running. 

> 2.6.32-42-386 #95-Ubuntu SMP Jul 25 16:28:45 UTC 2012 **i686** GNU/Linux

The other two are running 

> 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 08:03:28 UTC 2010 **x86_64** GNU/Linux

All have been updated recently with all recommended patches. None are showing any packages that were held back or pending.

Does this mean that the X86_64 kernel has not been updated to 12.04.1 yet?

---

### Post by darkod on 2012-08-22
I don't understand the question. They both show 2.6.32 which is 10.04. The kernel for 12.04 is 3.2.0.

---

### Post by rsteinmetz70112 on 2012-08-22
Update Manager is not showing an upgrade to 12.04 available on the x86_64 machines.

---

### Post by darkod on 2012-08-22
The official release is on 23rd so hold on for a day or two. Depending on time zone it might be even later.

---

### Post by rsteinmetz70112 on 2012-08-22
Thanks, I can wait. 

I want to try it on a couple of non production machines first and get used to it before I do my production machines.

---

### Post by rsteinmetz70112 on 2012-08-30
The option to upgrade to 12.04.1 is now should in Update manager on all machines.

---

