---
title: "the 9.10's problem!"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by fanglinyong on 2009-10-03
hello, everybody:
   when i upgrade my stystem from 9.04 to 9.10, and when i restart  my pc, i found that i can't getinto x server!  and when i ls /home ,i found that my /home dir is empty!
so ,can you help to solve this problem ?

---

### Post by yeats on 2009-10-03
9.10 is still in beta and is not recommended for production use.  Which is to say that, unfortunately, it is expected to break :-).

You may want to back up your data and reinstall Jaunty.

---

### Post by akakingess on 2009-10-03
I think fanglinyong is saying that the home folder being gone means all data is gone, which would not be good. Please tell us you did a backup of your personal data before upgrading?!?!?!

---

### Post by yeats on 2009-10-03
> I think fanglinyong is saying that the home folder being gone means all data is gone, which would not be good.

fanglinyong, was this an upgrade done from within 9.04, or did you burn a 9.10 CD and install from there?  If you upgraded from within 9.04, that should not have affected your data (even if things like X aren't working).  If you upgraded from a CD, that's a different story...

---

### Post by akakingess on 2009-10-03
> **chrissharp123 said:**
> fanglinyong, was this an upgrade done from within 9.04, or did you burn a 9.10 CD and install from there?  If you upgraded from within 9.04, that should not have affected your data (even if things like X aren't working).  If you upgraded from a CD, that's a different story...

chrissharp123, I wasn't trying to contradict you in any way, just trying to see if we could get some clarification from the OP. It sounds to me like the OP did an install via CD and that the home directory was created anew, now, whether we can recover anything for them, that's a whole 'nother issue;)

---

### Post by fanglinyong on 2009-10-03
ok, thanks everyone's reply!
first ,i upgrade my system to ver9.10 by the internate! and after i reboot my pc, i found that the system said "sorry, your x-sever din't work!"and then the system go into text-module! and after i loggin, i found that the /home/fanglinyong didn't exist! eventhouth the "root" directory is also  not exist,too!

---

### Post by tomchiverton on 2009-10-03
Did you have /home on a different disk partition ? If so, maybe /etc/fstab is mucked up...

---

### Post by yeats on 2009-10-03
> **fanglinyong said:**
> ok, thanks everyone's reply!
first ,i upgrade my system to ver9.10 by the internate! and after i reboot my pc, i found that the system said "sorry, your x-sever din't work!"and then the system go into text-module! and after i loggin, i found that the /home/fanglinyong didn't exist! eventhouth the "root" directory is also  not exist,too!

fanglinyong:  Can you post here the output of these commands?:

```
ls /
ls /home
cat /etc/fstab
```


> chrissharp123, I wasn't trying to contradict you in any way, just trying to see if we could get some clarification from the OP. It sounds to me like the OP did an install via CD and that the home directory was created anew, now, whether we can recover anything for them, that's a whole 'nother issue

No problem :-)  I didn't take you the wrong way.

---

### Post by fanglinyong on 2009-10-03
ok&#65292;now ,i can't get into system,now 
when i exec the code ls,it displayed all the files for example :etc, boot , home and so on!
when i exce the code ls /home, it displayed nothing!
when i download the 9.10's cd, and boot from cd ,and i found that my home file exist! and all my files exist! but without the livecd, i cant say my home dir, and can't get into system--the x-server!

---

### Post by yeats on 2009-10-03
Okay, using the live CD, offload your files to an external medium, like a USB drive.  Then burn a 9.04 CD and reinstall.

---

### Post by fanglinyong on 2009-10-03
> 
Okay, using the live CD, offload your files to an external medium, like a USB drive. Then burn a 9.04 CD and reinstall.

ok, is there anyway to solve this problem? i din't want to reinstall my system!

---

### Post by arpanaut on 2009-10-03
Have you tried booting into recovery mode and selecting the "xfix" option?

---

### Post by tomchiverton on 2009-10-04
We really need to see the /etc/fstab from your normal system, and the output of 'mount' when using the LiveCD.
You probably just need to correct/add a line in that file. You shouldn't need to reinstall from scratch.

---

### Post by fanglinyong on 2009-10-04
ok&#65292; thanks everyones's help!my problem had been solved!i recoveryed my system by backup files! 
thanks everyone!

---

