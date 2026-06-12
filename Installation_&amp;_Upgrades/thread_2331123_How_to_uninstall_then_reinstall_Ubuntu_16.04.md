---
title: "How to uninstall then reinstall Ubuntu 16.04"
date: 2016-07-18
forum: Installation &amp; Upgrades
---

### Post by Franklin_J on 2016-07-18
(Newto Linux)  I purchased the Ubuntu 16.04 LTS desktop install/live 64bit DVD.  I installed it a week or so ago and have enjoyed itimmensely.  I prefer to work with Apache Open Office so followinginstructions from the 'Ask Ubunto' website I attempted to uninstallLibreOffice before installing Open Office with the following code.

```
sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove
```

Thenall hell busted loose. So many things have gone wrong with thecurrent Ubuntu installation that it's pointless to attempt to listthem all. 


Itseems I should backup my data— uninstall Ubuntu(if not wipe thepartition)— and reinstall it. Is it possible to just reinstall itfrom the the DVD overwriting the current— or is there anothersolution??? I really like the OS but I'm inexperienced.

---

### Post by yancek on 2016-07-18
> [FONT=arial narrow][SIZE=1] Is it possible to just reinstall itfrom the the DVD overwriting the current— or is there anothersolution??? I[/SIZE][/FONT]

There may be another solution such as repairing the damaged system.  Since you indicate you have numerous problems, it would probably be easier to reinstall.  Backup your data and  boot the DVD and simply install Ubuntu to the same partition on which it was previously installed.  Make sure you select to format the partition.  This will overwrite everything on the partition and do a new install so you need the backup first.

---

### Post by danbosse1 on 2016-07-18
If you can back up all your personal stuff on a cloud server. Its much easier and its always there no matter what happens.
[https://mega.nz/#sync!linux](https://mega.nz/#sync!linux) gives 50 GB of storage!

---

### Post by vasa1 on 2016-07-18
> **Franklin_J said:**
> ... I prefer to work with Apache Open Office so followinginstructions from the 'Ask Ubunto' website I attempted to uninstallLibreOffice before installing Open Office with the following code.

```
sudo apt-get remove --purge libreoffice*
sudo apt-get clean
sudo apt-get autoremove
```

Thenall hell busted loose. So many things have gone wrong with thecurrent Ubuntu installation that it's pointless to attempt to listthem all. 
...
In case you plan to continue using Ubuntu, I would suggest taking things slow. It's possible the first two commands you posted were harmless enough. It could be the third one, autoremove, that broke your system. Quite a few of us have run *sudo apt-get purge libreoffice** in the past without damaging our systems.

I suspect the autoremove effect in your case relates to "So many things have gone wrong with thecurrent Ubuntu installation".

As yancek suggests, a clean install would be best after verifying the integrity of the starting iso. You did mention **purchasing** it.

And then, please ask here before removing software! I'm sure people will guide you.

---

### Post by grahammechanical on 2016-07-18
Before running the autoremove command we should find out what it will remove. The second of these 2 commands will list any packages that were automatically installed and are no longer required and which will be removed by the autoremove command.

```
sudo apt update
sudo apt upgrade
```

I my guess is that purging Libreoffice also created some dependency issues resulting in some broken packages. Which then put those packages on the no longer required list. Running update/upgrade would identify any broken packages which can be fixed by

```
sudo apt install -f
```

Regards.

---

### Post by Franklin_J on 2016-07-19
Thank y'all for such prompt & useful responses,this surprised me!. (danbosse1, yancek, vasa1. I've decided to at least attempt to fix this installation one issue at a time and 'learn' in the process. Thanks vasa1 for your reference to 'posting guidelines', and your insights into the commandlines I used.

---

