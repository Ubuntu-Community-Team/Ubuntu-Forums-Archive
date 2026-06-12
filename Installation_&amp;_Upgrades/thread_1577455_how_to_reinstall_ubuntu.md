---
title: "how to reinstall ubuntu"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by thenetminder33 on 2010-09-18
I am having lots of problems with fresh install of ubuntu 10.04.1 LTS (dual boot with Win7) and would like to reinstall, however if i just insert the ubuntu CD and boot off of that, when i go to install it wants to create another partition that uses space from my partition for win7. How can i reinstall on my current ubuntu partition?

---

### Post by Rasa1111 on 2010-09-18
I just recently had to do something similar. 
Only i have a dual boot with Ubuntu 10.04, and Ubuntu 10.10.
I killed my 10.10 installation somehow,
so made a thread asking how to fix it, and uRock and wilee nilee hooked me up nicely!

Now , my first partition is untouched/unharmed, and I simply "cleared" the partition with 10.10, turned it back into an ext4, and reinstalled Ubuntu 10.10 back in the same place, and all works like magick again. 

 Here is the thread...[http://ubuntuforums.org/showthread.php?t=1576062](http://ubuntuforums.org/showthread.php?t=1576062)
as I feel it will be easier to follow that than to have me write it out for you. 
These guys know more what they are talking about. lol

 I can try to help with the small details, if you like though. 

 But the info in that thread should get you where you need to be. 

 good luck mate. <3

---

### Post by thenetminder33 on 2010-09-18
thanks for the reply
that thread is helpful but i still have several questions

what program/system app are you using to delete the partition there and also would i be able to delete the ubuntu partition from ubuntu (Im assuming i cant)
If i cant;
could i delete it using same program running from ubuntu live cd
or what program could i use in windows?

---

### Post by Rasa1111 on 2010-09-18
> **thenetminder33 said:**
> thanks for the reply
that thread is helpful but i still have several questions

what program/system app are you using to delete the partition there and also would i be able to delete the ubuntu partition from ubuntu (Im assuming i cant)
If i cant;
could i delete it using same program running from ubuntu live cd
or what program could i use in windows?

No problem, 

 What I was using to delete the partition, 
(or what was on it, rather), 
was the manual partitioner that comes with Ubuntu 10.10. on the LiveCD.  The CD also has GParted on it, and that can be used in the same way, but it turned out I didnt even need it. 

 As long as you are running from the CD,
you can manage all of the partitions. 

 So yes, you can definitely delete it from Ubuntu,
as long as you are using the CD. 
(not from a normal Ubuntu install though, no)

10.04, and 10.10 manual partitioners are essentially the same, 
they just look a little different (hardly). 

 When you put the CD in, you can choose "try without making any changes" or just "Install Ubuntu"..
 But either way, when the install dialog comes up,
it will ask whether you want to 
"erase and use the whole disk" (you DONT want that), lol
or "manually specify partition to install" on)

 I chose the "advanced" method, 
"manually specify where to install"

From there, you can simply highlight the partition you want to clear, choose to delete it, and once deleted, it will just be empty space. 

 Then I created the 'ext4' on the section of the hard drive that i just cleared, making it ready for a new install. 

 and reinstalled 10.10 back to the same place. 

and I was golden.  lol

 Please though, dont just take my words and use them,
its best to follow what uRock and wilee walked me through. 

 I had never done anything of the sort,
but all turned out perfect. :D

Sorry im not more help.

---

### Post by thenetminder33 on 2010-09-18
Thank you that answers all my questions, I will let you know how it goes

---

### Post by Rasa1111 on 2010-09-18
very good.
 most welcome.

 uRocks screenshots in that thread are really helpful to. 
and are what really got me comfortable enough to do it.  lol

 :)

 good luck bro, <3

---

### Post by thenetminder33 on 2010-09-18
thanks so much for the help, install was a great success

I used gparted from live cd and it was extremely simple.

I am extremely happy because all of my problems from before were solved

once again you and uRock, well.... rock:P

---

### Post by Rasa1111 on 2010-09-18
haha, awesome! 

So glad it went well! 
Very cool. 

 good job! 

yeah uRock does rock! 
and Thanks! lol  <3  :D

---

