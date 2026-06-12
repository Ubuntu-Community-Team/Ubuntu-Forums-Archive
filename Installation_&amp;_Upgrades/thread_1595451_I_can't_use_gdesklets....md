---
title: "I can't use gdesklets..."
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Sampady on 2010-10-13
hi

i installed ubuntu 10.10 (i removed my 10.04 and then do this!)and now i cant use gdesklet


i installed it via terminal but i can't open that and it crash , i removed and install it for 3 times and now i completly removed that

what should i do?

is there anything which can be as good as gdesklet?(i dont want googels gadet!)

thx a milion!

---

### Post by Sampady on 2010-10-14
any one who can help me????

---

### Post by tsaowang on 2010-10-14
Hi,

Did you try screenlets ?

---

### Post by Sampady on 2010-10-14
thx 
i am using screenlets now..

---

### Post by sectorq on 2010-11-10
i found solution for this problem.


 in file /usr/lib/gdesklets/utils/ErrorFormatter.py
 Original:
def _new_imp(name, globs = {}, locls = {}, fromlist = []):
 Change to:
def _new_imp(name, globs = {}, locls = {}, fromlist = [], test = []):

---

### Post by ranjith19 on 2010-11-24
[http://ubuntuforums.org/showthread.php?p=10156439#post10156439](http://ubuntuforums.org/showthread.php?p=10156439#post10156439) has the solution

---

