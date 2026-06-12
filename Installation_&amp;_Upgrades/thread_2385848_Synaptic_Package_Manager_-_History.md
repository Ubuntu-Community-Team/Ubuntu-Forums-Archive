---
title: "Synaptic Package Manager - History"
date: 2018-02-25
forum: Installation &amp; Upgrades
---

### Post by electrosteam on 2018-02-25
Running Lubuntu on an old Dell laptop, starting with 17.04 in September 2017 and now 17.10 with 4.13.0-36-generic.

The History in Synaptic Package Manager shows nil entries for November, January and February.
The last December entry was on the 28th, gkrellm.

I have upgraded every notification since the original install.

Any suggestions on where to find the missing history ?
Is gkrellm a possible cause ?

John

---

### Post by #&amp;thj^% on 2018-02-25
Only software packages installed using the Synaptic Package Manager are displayed on the History dialog box. If you installed other software using other methods, such as the Ubuntu Software Center, they are not listed here.
```
cat /var/log/dpkg.log | grep “\ install\ “
``` 
command is probably the best way of viewing a list of installed packages, because only “install” entries in the log file are displayed. If you need to view installed packages that are older than those available in the dpkg.log file, simply replace the dpkg.log filename in the cat command with other dpkg log filenames you find using the
```
ls –l /var/log/dpkg* 
```
command.

---

### Post by vasa1 on 2018-02-25
I like```
grep "status installed" /var/log/dpkg.log
```for the most recent and```
zgrep "status installed" /var/log/dpkg.log*
```for all (subject to logrotate). Of course, this won't list packages which have been removed subsequently.

---

### Post by electrosteam on 2018-02-26
Thanks guys, you have got me thinking correctly again, it can be hard at 73 y.
John

---

### Post by mörgæs on 2018-02-26
Good, please mark the thread solved.

---

