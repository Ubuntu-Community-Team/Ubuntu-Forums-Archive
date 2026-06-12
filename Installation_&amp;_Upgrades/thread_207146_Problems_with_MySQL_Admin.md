---
title: "Problems with MySQL Admin"
date: 2006-07-01
forum: Installation &amp; Upgrades
---

### Post by spyke01 on 2006-07-01
hi guys, im having a wierd problem with MySQL Admin, i can login to localhost and use everything but user admin. whenever i click on it, it freezes completely theres [another thread](http://ubuntuforums.org/showthread.php?t=194661&highlight=mysql+admin+freezes) with a guy having the same problem, so i know its not the first time anyones seen it.

anyone got some ideas?

---

### Post by MonkeyNet on 2006-07-01
Having the same issues as yourself. Had a hunt around and it appears that this bug was reported on the MySQL website on the 13th of Feb and still no resolve for it yet.

Details of the bug can be found [here]("http://bugs.mysql.com/bug.php?id=17352").

If someone else has managed to resolve this issue, please let me know

---

### Post by spyke01 on 2006-07-01
i found a workaround that works sometimes, if you go to all of the menus but user administration, then click view -> user administration, that it will let you in, its a hassle but it works for me, what about you?

---

### Post by MonkeyNet on 2006-07-01
[QUOTE=spyke01]i found a workaround that works sometimes, if you go to all of the menus but user administration, then click view -> user administration, that it will let you in, its a hassle but it works for me, what about you?[/QUOTE]

Interesting workaround, however, didn't work for me :(

Will stick to using phpmyadmin for now. But will keep my eye out for solution

---

### Post by MonkeyNet on 2006-07-01
Hey spyke,

Also found a bug report on Launchpad for Ubuntu

[Link]("https://launchpad.net/distros/ubuntu/+source/mysql-admin/+bug/29802")

Within that page there is also another link to the MySql bug website.

It appears there is a patch which I am going to try today and see if it works.

Will let you know how I go.

Cheers

---

### Post by claypole on 2006-08-02
This works for me (from link above, thanks!)

At the terminal:

export DEBUG_DONT_SPAWN_FETCHES=1;mysql-admin

---

