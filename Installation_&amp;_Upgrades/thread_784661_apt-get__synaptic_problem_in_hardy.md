---
title: "apt-get / synaptic problem in hardy"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by rbprogrammer on 2008-05-06
so i installed hardy and updated all the necessary packages.  now i am in the process of installing the extra packages that i use.  one of them is keytouch.  when i installed it through synaptic, it just shutdown.  not the computer, just synaptic.  now i am unable to install anything.

when i do:
```

$ gksudo synaptic

```
the window pops up then closes.

then when i go command line, i get this:
```

$ sudo apt-get install keytouch
Reading package lists... Done
Segmentation faulty tree... 50%

```

how can i fix this?  any help is greatly appreciated.

---

### Post by ztirffritz on 2008-05-06
I've been getting all kinds of segmentation faults too.  I've found that sometimes I can recover by doing any or all of these:
sudo dpkg --configure -a
sudo apt-get autoclean
sudo apt-get udpate

---

### Post by rbprogrammer on 2008-05-06
> **ztirffritz said:**
> 
...
sudo apt-get update

thats what i was looking for.  for some reason sudo apt-get autoclean did not work at first, but the update one fixed it.... thanks

---

### Post by bengar on 2008-05-07
I am having that problem too right now. I was using the shell to install HTOP and this message appear.

> bengar@bengar-desktop:~$ sudo apt-get install htop
Reading package lists... Done
Segmentation faulty tree... 91%
bengar@bengar-desktop:~$ sudo apt-get install htop
Reading package lists... Done
Segmentation faulty tree... 96%


I did used autoclean and update commands and still with the same problem. All started when OS did an update.

---

### Post by mrcorey on 2008-05-07
Is [This]("http://ubuntuforums.org/showpost.php?p=4831175&postcount=2") the solution?

---

### Post by bengar on 2008-05-08
Okay after a lot of update commands the system look like stabilized. All the time that I run>  sudo apt-get update it stop in 56% in this line > Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg
Then continue with the rest of the update without problem.

---

