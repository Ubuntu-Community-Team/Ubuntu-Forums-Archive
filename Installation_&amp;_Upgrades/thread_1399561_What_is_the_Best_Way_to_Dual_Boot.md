---
title: "What is the Best Way to Dual Boot"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by ajt111 on 2010-02-05
I am currently running Windows Vista and am planning to upgrade to 7 in the near future.
I want to dual boot with Ubuntu 9.10.

The options I know of are:
1. Partition the drive and install Ubuntu
2. Use the windows installer (winbuntu - I think)

Can someone tell me which method they prefer and some pros and cons of each?

Which installation method would make it easier to remove one of the operating systems at a  later time?

When installing using winbuntu  does the ubnutu OS use any of the windows resources or disk?

---

### Post by wilee-nilee on 2010-02-05
What is your computer model? and do you want or have multiple hard drives?

---

### Post by raymondh on 2010-02-05
I prefer to have Ubuntu (or any OS) in its' (their) own partition rather than 'virtualized' as a windows file (WUBI).  That way, if one OS borks, you can still boot into the other..... as opposed to a WUBI install where if windows' crashes, so does your ubuntu until you get to fix windows.  

Let me attach a interview with A. Russo, the developer of WUBI.  Note his response in the second question.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

As for removing, I am a big fan of using gparted and have not had problems deleting/resizing/moving partitions.  Of course, a little research/reading will go long ways :)

Best,

Raymond

---

### Post by ajt111 on 2010-02-05
> **wilee-nilee said:**
> What is your computer model? and do you want or have multiple hard drives?

Toshiba Satellite A505

---

