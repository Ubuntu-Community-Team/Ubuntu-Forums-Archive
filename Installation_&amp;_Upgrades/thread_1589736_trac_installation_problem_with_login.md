---
title: "trac installation problem with login"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by darkzonedz on 2010-10-06
hi i installed trac but i have error with login. i am pressing the folow code otherwise i can not access login (i have a message that authenation is not ok)

so after this:
tracd -p 8021 --auth="environemt,/usr/local/trac/passwrods.txt,environemt" /usr/local/trac/environemt

i got this:

sudo tracd --port 8021 --auth="environemt,/usr/local/trac/passwrods.txt,a" /usr/local/trac/environemt
Warning: invalid digest line in /usr/local/trac/passwrods.txt: admin:nYpm3MCuAfvDs
Warning: found no users in realm: a

i am pressing to login i am adding my account but it can not accept it.

any ideas?

---

