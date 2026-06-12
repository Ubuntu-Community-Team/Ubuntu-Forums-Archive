---
title: "How to downgrade from lucid-proposed"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Kognit on 2011-04-30
Hi

I no longer want that my system is updated from pre-released updates(lucid proposed). About 50 packages are from lucid proposed and i want to downgrade them all. I know how to downgrade a package but i don't know how to downgrade all the packages at once (so that all 50 packages would be downgraded simultaneously).

Any suggestions?

thx for help

---

### Post by tonyhawz on 2011-06-16
I've never done it , but here you got some documentation 

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

---

### Post by Frogs Hair on 2011-06-16
I'm not quite sure if you have installed these packages or not . If not , open the update manager and remove the check from the boxes of the updates you don't want to receive . I would recommend that you install security updates. When the package manager is reloaded the updates should nolonger appearer . 

From the synaptic package manager > settings > preferences > distribution , you can select use the current version.

---

### Post by coffeecat on 2011-06-16
I believe the problem is not that the OP has upgraded to a newer version of Ubuntu, but that they enabled the proposed repository and may have install versions of packages which may or may not get into the regular repositories.

@Kognit, disable the proposed repository in Synaptic -> Setting -> Respositories -> updates tab. Close Synaptic, open a terminal and run:

```
sudo apt-get update
```Now try:

```
sudo apt-get upgrade
```What happens? Does it want to downgrade any packages? If not, you could try one or both of the following, but I really don't know whether they will do what you want:

```
sudo aptitude safe-upgrade
sudo apt-get dist-upgrade
```They both do intelligent handling of dependencies, so they *might* downgrade packages to their last released version. Contrary to popular belief, apt-get dist-upgrade does **not** do a distribution upgrade. See man apt-get for more details.

By the way, @tonyhawz, the first post dates from over six weeks ago. How did you find it?

---

