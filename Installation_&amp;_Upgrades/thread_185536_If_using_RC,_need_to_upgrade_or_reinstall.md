---
title: "If using RC, need to upgrade? or reinstall?"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by RAV TUX on 2006-05-31
I have been using the RC do I still need to upgrade or reinstall?

---

### Post by Phlosten on 2006-05-31
You should not need to. Simply keeping up to date will be sufficient. Just run the update manager regurlarly, which by default should happen anyway from memory.

---

### Post by RAV TUX on 2006-05-31
[QUOTE=Phlosten]You should not need to. Simply keeping up to date will be sufficient. Just run the update manager regurlarly, which by default should happen anyway from memory.[/QUOTE]


Thanks for the excellent advise.






.

---

### Post by towsonu2003 on 2006-05-31
you may need a dist-upgrade in case they add something or else for the released version. 
sudo apt-get update
sudo apt-get dist-upgrade

once it is released and you do the dist-upgrade (and hence have the released version installed), than just 
sudo apt-get update
sudo apt-get upgrade

---

### Post by gatekeep on 2006-06-01
I've been using Dapper since the RC, did they add anything after that to the release? I mean, I know it wouldn't hurt to do a dist upgrade, but I'm just curoius to know, if that would be necessary.

---

### Post by towsonu2003 on 2006-06-01
[QUOTE=gatekeep]I've been using Dapper since the RC, did they add anything after that to the release? I mean, I know it wouldn't hurt to do a dist upgrade, but I'm just curoius to know, if that would be necessary.[/QUOTE]
I have dial up and thus answering your question would take me 30 minutes + total paralysis of web access (3MB data download by doing sudo apt-get update on dial up tends to be a torture) so I'm the last person to ask :)

You could do (if you have fast internet + RC)
sudo apt-get update
sudo apt-get -s upgrade
sudo apt-get -s dist-upgrade

and compare the output. Any difference in outputs means they did add (or remove?) something and the better thing is dist-upgrade. -s means "just **s**imulate the action, don't really do it".

---

### Post by FredB on 2006-06-01
[QUOTE=gatekeep]I've been using Dapper since the RC, did they add anything after that to the release? I mean, I know it wouldn't hurt to do a dist upgrade, but I'm just curoius to know, if that would be necessary.[/QUOTE]

Around 60 packages or so were upgraded : translations updated, graphics too. Just do the classical :

```
sudo apt-get update && sudo apt-get dist-upgrade

```

And don't forget to add dapper-updates repository ;)

---

### Post by RAV TUX on 2006-06-02
[quote=FredB]
And don't forget to add dapper-updates repository ;)[/quote]

ok so how do I do that?

---

