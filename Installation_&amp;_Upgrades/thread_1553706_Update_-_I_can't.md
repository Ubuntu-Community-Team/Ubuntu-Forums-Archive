---
title: "Update - I can't"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by kosenrufu on 2010-08-15
Can anyone help me with this problem?:confused: My Update Manager says that I have new updates. I click on U M and then click on install updates. I am then asked to enter password. I do this and it seems as if the computer is doing something and then ... nothing. What am I doing wrong?

---

### Post by snowpine on 2010-08-15
Welcome to the forums! You can get more detailed messages if you go to Applications, Accessories, Terminal and use the following commands. Copy & paste the output here so we can see what's going on.

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Paul Wotherwell on 2010-08-18
I had exactly this problem, which was fixed by running the terminal commands. 

I think I had been using the wrong password, which just produces a silent abort of Update Manager, instead of my normal account login password.

---

