---
title: "update manager gives error"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by Saqib Amin on 2011-07-02
anyone please help. i am new to ubuntu.
when i open update manager i get an error, i have attached the screenshot of the error.

---

### Post by dino99 on 2011-07-02
try again, or into a terminal: sudo apt-get update

---

### Post by Rubi1200 on 2011-07-02
Hi and welcome to the forums Saqib Amin :)

If the suggestions  by dino99 don't work, then try this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by Saqib Amin on 2011-07-03
thanks Rubi1200 ur code worked.
can you tell me what the first line mean and what it did?

---

### Post by Rubi1200 on 2011-07-03
The first command removes corrupt package lists, the second command refreshes and updates it again.

Glad this worked for you :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

