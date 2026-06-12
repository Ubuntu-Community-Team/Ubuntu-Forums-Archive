---
title: "Please help me"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Jeyaganeshdj on 2009-11-15
hi,

 I have installed 9.10. The problem is most of the application is not opening. Movie Player, Rhythmbox music player and Ubuntu software center. I have already posted threads for this probs but not received any response. Please help me

---

### Post by rukiaEnix on 2009-11-15
Can you see the menus at the menus bar?

---

### Post by lisati on 2009-11-15
Please be patient: people have seen your other questions. Having more than one discussion active on the same problem can get confusing.

---

### Post by Jeyaganeshdj on 2009-11-15
I can see all the menu. Openoffice firefox are working when i click the apps from the menu

---

### Post by neonexus on 2009-11-15
I have the exact same problem with Ubuntu software center. I upgraded from 9.04 to 9.10, and now I have to use Synaptic to install/remove/upgrade software. I can't use the normal "Add / Remove" software option.... 

Every time I try to open the Ubuntu software center, it gives me the usual button on the 'task bar' that it's starting, but nothing ever loads. The button disappears after about 2 minutes, and I'm left being confused. 

I've ripped the internet apart looking for the answer to fix this problem. However, after everything I've tried reinstalling 'python', fully removing the 'software-center' and reinstalling... Everything... I'm going crazy here, someone please help me... Why is it that a new piece of software won't work for me? What do you need to figure this out?!

---

### Post by sandy8925 on 2009-11-15
Did you check if the CD had any errors before instaling ? Also, when you try to launch something does the hard disk light shine ?

---

### Post by Jeyaganeshdj on 2009-11-15
yeah i had checked the cd before installation and it was fine... the hard disk light glow when it was trying to start software center.

---

### Post by Jeyaganeshdj on 2009-11-15
Hi,

 Is there no solution to my problem.. should i revert back to windows for accessing this application???

---

### Post by phillw on 2009-11-15
> **Jeyaganeshdj said:**
> Hi,

 Is there no solution to my problem.. should i revert back to windows for accessing this application???

Try booting from the LiveCD, as LiveCD mode - it'll run slowly, but, what I want to see is if you can launch those applications from the CD

Phill.

---

### Post by phillw on 2009-11-15
You need to confirm the following ...

1) You checked the ISO file with md5  -->  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
2) You burned the CD at 4X speed, or slower
3) You checked the CD with md5, as in step 1

You may also consider cleaning your cd-drive with one of the cd/dvd drivecleaners. It really does sound like a file corruption somewhere to me.

Phill.

---

### Post by Jeyaganeshdj on 2009-11-15
Thanks Phill, I have checked the dowloaded iso files hash value and it is exactly the same as in the ubuntu hashes page. I have burned the cd at 4x speed but i have erased the cd after installation. so i am not in a position to check the hash value in the cd. what should i do next? once again thanks a lot...

---

### Post by Jeyaganeshdj on 2009-11-16
Hi,

 Please let me know if there is some kind of solution to my problem or only a re-installation is a solution. thanks a lot

---

### Post by Jeyaganeshdj on 2009-11-16
Please find the errors when i tried to run RhythmBox and Ubuntu Software center from terminal

_**RhythmBox**_

** (rhythmbox:2035): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:2035): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:2035): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault

_**Ubuntu Software center**_

Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    import pygtk
ImportError: No module named pygtk

---

