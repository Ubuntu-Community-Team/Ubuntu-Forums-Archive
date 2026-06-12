---
title: "phpmyadmin missing file in Gutsy"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by tai133 on 2007-10-20
After upgrading to Gutsy, phpMyAdmin runs, allows logins and shows installed databases, but when picking a database to manage the left frame goes blank except for the message:

"The requested URL /phpmyadmin/left.php was not found on this server."

I have done a "complete removal" and reinstall in Synaptic but still get the same result.

Worked fine in Feisty.

---

### Post by tai133 on 2007-10-24
Solution was to do an apt-get update. The file 'left.php' is replaced with 'navigation.php' and everything works.

---

### Post by Linuturk on 2007-11-05
I had to clear my browser cache after upgrading from feisty to gutsy.

---

