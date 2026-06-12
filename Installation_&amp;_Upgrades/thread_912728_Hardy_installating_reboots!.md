---
title: "Hardy installating reboots!"
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by rakan_dr on 2008-09-07
hi guys, i'm trying to install Hardy on my Desktop. When i choose the installation choice and it starts loading the system, after a while it reboots!!! It doesn't even reach the desktop!

I tried another CDs, i tried also xubuntu but i got the same result. I also tried to boot as Live, but it also reboots while it loads the system.

what should i do??

PC spec:
CPU: P4 3.2GHz.
RAM: 512MB DDRI 400mhz.
Mobo: asus ....

Thanks.

---

### Post by rakan_dr on 2008-09-07
I also did a memtest but i got no probs.

---

### Post by Sef on 2008-09-07
Run 'Check Disk for Errors', and see what the results say.  (Instead of installing, go down the list of options.)

---

### Post by rakan_dr on 2008-09-08
How can i do the Check Disk for Errors????

By the way, i can install windows xp without any problems

---

### Post by weboide on 2008-09-08
Try installing using an alternate CD, see if it works.

---

### Post by rakan_dr on 2008-09-08
i did that!! I mentioned that in my first post.

---

### Post by rakan_dr on 2008-09-08
is alternate CD == another CD??? or the alternate is something else???

---

### Post by Kevbert on 2008-09-08
Ubuntu alternate CD is a text based installer (as opposed to a GUI installer).  The CD check is a menu option when you boot from the CD.
When you downloaded the ISO file, did you perform a [[COLOR="Red"]hash check[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") ?  Also you need to burn the CD at the slowest speed available to minimize errors.
Another thing to do is a memory check via the CD boot menu.  It's possible to have faulty memory and still run windows (though you may get the occasional random crash).

---

### Post by rakan_dr on 2008-09-08
> **Kevbert said:**
> Ubuntu alternate CD is a text based installer (as opposed to a GUI installer).  The CD check is a menu option when you boot from the CD.
When you downloaded the ISO file, did you perform a [[COLOR="Red"]hash check[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") ?  Also you need to burn the CD at the slowest speed available to minimize errors.
Another thing to do is a memory check via the CD boot menu.  It's possible to have faulty memory and still run windows (though you may get the occasional random crash).

I did everthing you mentioned, except the HASH Check. I installed Ubuntu from these CDs on plenty of desktops.

---

### Post by Kevbert on 2008-09-08
Is the CD drive a SATA drive ?  I've had a rebooting problem, but it reboots whenever I put any DVD in the drive.  Sounds like you've done all the obvious checks and if CD only fails in one of many drives it must be a hardware (compatibilty ?) problem.  What make/model drive is it ?

---

### Post by rakan_dr on 2008-09-08
> **Kevbert said:**
> Is the CD drive a SATA drive ?  I've had a rebooting problem, but it reboots whenever I put any DVD in the drive.  Sounds like you've done all the obvious checks and if CD only fails in one of many drives it must be a hardware (compatibilty ?) problem.  What make/model drive is it ?

no it's IDE. Actually yeah, i think it's hardware compatibility problem, but i don't think it's from the DVD drive.
What should i do??

Please don't tell me that i have to uninstall the hardware and try piece after piece!! I will install Win XP if this is the only solution!!!! I don't have time for this.

---

### Post by rakan_dr on 2008-09-09
Has anybody faced such a situation??

---

### Post by Kevbert on 2008-09-10
What's the drive manufacturer, model, revision ?
You can get the info with
```
lshw
```
in terminal

---

