---
title: "problem : Sorry, Ubuntu 16.04 has experienced an internal error"
date: 2018-01-09
forum: Installation &amp; Upgrades
---

### Post by sajadshiraz on 2018-01-09
hi
i did update ubuntu
after update my ubuntu has error
[COLOR=#000000][FONT=&quot]Sorry, Ubuntu 16.04 has experienced an internal error
please help me 
[/FONT][/COLOR]

---

### Post by cruzer001 on 2018-01-10
And you can still get into your system, right?

If so, open a terminal and enter:

```
sudo dpkg --configure -a && sudo apt -f install
```

And post back here if you get any errors.

Also run:

```
sudo rm /var/crash/*
```

and reboot

If you still get the popup, you need to post the report.

---

### Post by sajadshiraz on 2018-01-10
i have error after enter code
error is :
sajad@sajad:~$ sudo dpkg --configure -a
sudo: unable to resolve host sajad

---

### Post by cruzer001 on 2018-01-10
```
sudo: unable to resolve host sajad
``` 

I am not sure how this happen, here is a link to some fixes.

[https://ubuntuforums.org/showthread.php?t=1754106](https://ubuntuforums.org/showthread.php?t=1754106)

Please read and post back with any questions.

Also, if your not comfortable with using the command line.  Please backup your personal files/folders first.  Worst case would be a system reinstall if something goes further wrong.

---

