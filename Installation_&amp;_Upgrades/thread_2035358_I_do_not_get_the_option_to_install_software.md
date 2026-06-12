---
title: "I do not get the option to install software"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by vigneshm247 on 2012-07-30
Hi I do not get the option to install software using the ubuntu software  manager. 

The screen shot is attached:

any help would be appreciated.


[IMG]http://ubuntuforums.org/attachment.php?attachmentid=221993&stc=1&d=1343666745[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=221994&stc=1&d=1343666745[/IMG]

---

### Post by mörgæs on 2012-07-30
What happens if you boot the computer and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

?

---

### Post by vigneshm247 on 2012-08-01
Hi Morges,
Thank you for replying. 
I tried to do what u said but the last command stops while executing 50% of updates, this happened many times. :confused:
So I just went ahead and reformatted the system.:)
Thanks, 
Vignesh.

---

### Post by mörgæs on 2012-08-01
It's not a bad solution. One can easily mess with a system to a degree where a reinstall is the best option. 

After doing it a few times you will be able to reinstall in less than half an hour.

---

