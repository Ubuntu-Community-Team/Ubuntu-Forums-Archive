---
title: "GRUB 'no video mode activated ' on LUKS device (Ubu-Alternate)"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by Andreas Riedel on 2011-05-16
Hello Forum.

I've installed Ubuntu 11.04 alternate with encrypted partition.

Starting the system, grub prints "no videi mode activated". After a while, the system start normal, but I don't want this error message.

Reading some thread guess me, that grub will read some content, exspecially fonts, from the cryped partition.

Any idea, what's to do.

TIA
  Andreas

---

### Post by A.S. on 2011-05-17
Hello,

i've had the same problem after installing *Kubuntu 11.04* with encrypted harddrive.


My solution was make the file **/etc/grub.d/05_debian_theme** not executable with the command:

```
sudo chmod a-x /etc/grub.d/05_debian_theme
```

.

---

### Post by Andreas Riedel on 2011-05-19
Thanks.
Great.
You have done the job.

  Andreas

---

### Post by MAFoElffen on 2011-05-19
> **A.S. said:**
> Hello,

i've had the same problem after installing *Kubuntu 11.04* with encrypted harddrive.


My solution was make the file **/etc/grub.d/05_debian_theme** not executable with the command:

```
sudo chmod a-x /etc/grub.d/05_debian_theme
```.
Holy cow!!!  Even though this workaround fixes this problem for you 2, this "should" be reported as a bug to GNU, up at Savanah.  That way en this could get lokked at,  worked on and fixed upstream.

I see your workaround as disabling the debian theme section, which at least narrows down where the problem is coming from.

---

### Post by Andreas Riedel on 2011-05-20
But where should this be. You don't mean the Launchpad, do you?

---

### Post by tom.tom_j on 2011-09-09
> **A.S. said:**
> Hello,

i've had the same problem after installing *Kubuntu 11.04* with encrypted harddrive.


My solution was make the file **/etc/grub.d/05_debian_theme** not executable with the command:

```
sudo chmod a-x /etc/grub.d/05_debian_theme
```.


Hi All,

           Me too facing the exact problem as described by Andreas Riedel. I tried the above solution but doesn't seems to have any effect on the grub while starting. Any suggestions?????


Regards

---

### Post by kurci2 on 2012-05-20
after that you must execute
```
sudo update-grub
```

---

