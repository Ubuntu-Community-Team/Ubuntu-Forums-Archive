---
title: "Preseed user creation in Ubiquity"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by wrix on 2011-03-27
Hello, I was trying to remaster Ubuntu Cd for mass-scale automated install, the only problem I'm having creating a regular account in Ubiquity. Please, can anyone provide the preseed option to create a user account in Ubiquity with a default password say, "123". Thanks.

---

### Post by Goldengate01 on 2011-03-29
Hi,

You should use a preseed file (located in preseed directory), look at the options:

d-i passwd/user-fullname string "Your user name like Peter Doe"
d-i passwd/username string "peter"
d-i passwd/user-password password 123

Good luck!


Francisco

---

