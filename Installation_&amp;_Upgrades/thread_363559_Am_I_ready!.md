---
title: "Am I ready?!"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by Sicilianmandolin on 2007-02-17
How does this look? Do I have all the partitions I need? What about /boot, and why does it insist on saying that there's no root filesystem for mounting?

[http://img149.imageshack.us/img149/4217/screenshotjs7.png](http://img149.imageshack.us/img149/4217/screenshotjs7.png)

Thanks!

---

### Post by bigken on 2007-02-17
your root file partition should only have a forward slash (/)

---

### Post by bigken on 2007-02-17
select it from the drop down menu

---

### Post by Sicilianmandolin on 2007-02-17
I had tried that too, and it still says the same thing. :|

---

### Post by Sicilianmandolin on 2007-02-17
Also, there was some data written to those other two partitions (aside from the swap) because I had to use Partition Magic to do it... could this be causing the problem? Perhaps if I checked Reformat for all?

---

### Post by bigken on 2007-02-17
why dont you use the partition editor from the live disc

---

### Post by Sicilianmandolin on 2007-02-17
It wouldn't work. It kept saying there were errors even after I had ran CHKDSK so I just gave Partition Magic a go around and it worked.

---

### Post by bigken on 2007-02-17
you also need to check the boxes to format the partitions

---

### Post by bigken on 2007-02-17
are you duel booting with windows if you are you need to run defrag in windows a couple of times

---

### Post by Sicilianmandolin on 2007-02-17
Ok, I checked Reformat on all and it's still giving me the error:

[http://img70.imageshack.us/img70/9587/screenshot1jv4.png](http://img70.imageshack.us/img70/9587/screenshot1jv4.png)

---

### Post by Sicilianmandolin on 2007-02-17
I am dual booting and I defragged once with Diskdoctor...

---

### Post by bigken on 2007-02-17
download and the gparted liveCD to create your partitions its in my signature

---

### Post by Sicilianmandolin on 2007-02-17
> **bigken said:**
> download and the gparted liveCD to create your partitions its in my signature

Alright, so in other words, delete the partitions I made with Partition Magic and use GParted LiveCD to create the partitions instead?

---

### Post by bigken on 2007-02-17
ok I would run the windows defrag tool then delete the partitions you have created then use gparted liveCD to create your new partitions :)

---

### Post by bigken on 2007-02-17
> **Sicilianmandolin said:**
> Alright, so in other words, delete the partitions I made with Partition Magic and use GParted LiveCD to create the partitions instead?


yep you got it :)

ps how much ram do have in your pc

---

### Post by Sicilianmandolin on 2007-02-17
> **bigken said:**
> ok I would run the windows defrag tool then delete the partitions you have created then use gparted liveCD to create your new partitions :)

Lawl. Alright. Thanks... :|

---

### Post by bigken on 2007-02-17
keep us upto date with your progress 

and good luck ;)

---

### Post by Sicilianmandolin on 2007-02-17
Alright, I did as instructed and am still facing the same issue; the "No root file system" error. Here's how I have it configured:

[http://img186.imageshack.us/img186/5279/screenshothl7.png](http://img186.imageshack.us/img186/5279/screenshothl7.png)

[http://img201.imageshack.us/img201/241/screenshot1rt3.png](http://img201.imageshack.us/img201/241/screenshot1rt3.png)

(sda1 = recovery partition, sda2 = XP)

Well, I'm going to leave the system up while I sleep because I'm getting tired of having to wait 10-15 minutes for the installer to load every time I try this.

Thanks for your help...

---

### Post by Sicilianmandolin on 2007-02-17
For all of those with the same problem ("No root file system"), this link solved the problem:

[http://ubuntuforums.org/newreply.php?do=newreply&p=1700787](http://ubuntuforums.org/newreply.php?do=newreply&p=1700787)

---

### Post by bigken on 2007-02-18
if you look at it properly the only problem you had was you were formating
as ext2 insted of ext3 anyhow pleased your up and running :)

---

### Post by ubuntu27 on 2007-02-18
> **Sicilianmandolin said:**
> For all of those with the same problem ("No root file system"), this link solved the problem:

[http://ubuntuforums.org/newreply.php?do=newreply&p=1700787](http://ubuntuforums.org/newreply.php?do=newreply&p=1700787)

Were you able to solve the problem?

---

