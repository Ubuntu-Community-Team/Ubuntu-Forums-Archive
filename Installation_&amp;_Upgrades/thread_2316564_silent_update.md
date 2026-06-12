---
title: "silent update"
date: 2016-03-09
forum: Installation &amp; Upgrades
---

### Post by Patrick_Pigmans on 2016-03-09
Hello all, i have been at this for a couple of days now and i still cant get it to work, i have a script, in it stands

```
apt-get -qq update
apt-get -qq upgrade
apt-get -qq dist-uppgrade
```

but after apt-get -qq update (update wont show any output which is what i want) all the outputs of upgrade and dist-upgrade show, i want both of them to run silent, is this even possible?

---

### Post by QDR06VV9 on 2016-03-09
Hi Patrick_Pigmans
Iam not sure really what you are asking here but maybe this will shed some light.. The qq flag is for [B]-qq No output except for errors..
[/B]See man apt-get[B]
For Example:
[/B]> apt-get update -qq > /dev/null apt-get -qq -y install apache2 > /dev/null

If you're absolutely sure you're not going to make your system catch on fire, you could always sudo apt-get upgrade -qq --force-yes > /dev/null. [B]-qq implies -y
More Info Here: [/B][http://serverfault.com/questions/644180/what-does-qq-argument-for-apt-get-mean](http://serverfault.com/questions/644180/what-does-qq-argument-for-apt-get-mean)
If you are wanting Automatic Updates and Dist-Upgrades...That can be done with script and I can show you one with or without a text out-put to show what was installed..
If Not Kindly just disregard.

---

### Post by Patrick_Pigmans on 2016-03-10
Thanks for your reply but i want the end user in this case to see the error if an error comes up

---

