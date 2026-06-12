---
title: "upgrade ubuntu 10.04 to 12.04"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by chitragurung on 2012-05-18
I have dell inspiron mini machine with ubuntu 10.04 is that possible to upgrade to 12.04 ?

---

### Post by darkod on 2012-05-18
If you go into Software Sources, in the Updates tab, check the setting for upgrades (new version). Usually it would say Long Term releases.

That will make the Update Manager prompt you to upgrade to 12.04.1 once it's released in July.

When you are running the previous LTS (10.04), the update manager offers the upgrade to the next LTS only after the first .1 is released.

It's better to wait for some basic bugs to be solved in .1 anyway.

If you don't want to wait, you can start the update manager with the -d option and it should offer you upgrade to 12.04. You can do that in terminal with:
sudo update-manager -d

In any case, it's best to make a cd of 12.04 first and try it in live mode to check if there are any issues with your machine. Because if they are, and you don't test, after doing the upgrade it might not work straight away.

---

