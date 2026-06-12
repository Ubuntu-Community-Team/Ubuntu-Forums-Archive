---
title: "root password"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by dlw on 2012-10-31
When installing Ubuntu I entered a password.
Whenever prompted for this password it works.
However, when I enter 'su' then the password, it does not work.
Went into rescue mode and did 'passwd' entered the password twice and got a 'token' error. Tried a few different passwords with the same result.

Any help appreciated.

dlw

---

### Post by uhgreen on 2012-10-31
sudo su
then enter user password.

Should work.

---

### Post by sisco311 on 2012-10-31
By default, the root account password is locked. Use sudo instead of su. 

Please check out [uhelp]community/RootSudo[/uhelp]

---

### Post by Karlchen on 2012-10-31
Hello, dlw.

This article explains everything you might wish to know about root account and root password on Ubuntu:  [**RootSudo**](https://help.ubuntu.com/community/RootSudo)

Kind regards,
Karl

---

### Post by Abhinav Kumar on 2012-11-01
+1 for posts of sisco311 and Karlchen:)
A good explaination is also available at [here]("http://www.howtogeek.com/111479/htg-explains-whats-the-difference-between-sudo-su/")

---

### Post by dlw on 2012-11-01
Got it!!!
Thank you.

dlw

---

