---
title: "php5-gd"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by cynics on 2010-01-14
I've PHP5 installed on my server, and just recently I installed a new application that requires gd library.

understand that I can have gd library installed via apt-get install php5-gd command.

Question: do I need to remove php5 instance (which was installed together with apache2/mysql using tasksel command) prior to installing php5-gd?

Thank you!

---

### Post by Cheesemill on 2010-01-14
No. You need to keep your current PHP as php5-gd is just an add on module for it.

---

