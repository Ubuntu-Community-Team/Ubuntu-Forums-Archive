---
title: "Upgrades 404 not found [14.04]"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-30
hello i was using Ubuntu 13.10 and i was getting good updates with my server [which is in my city in my country]

but ever since i updated my Ubuntu [fresh install]
i am not getting full updates

i get these errors:

[http://bpaste.net/show/whiopl2dejHOrinJz6kb/](http://bpaste.net/show/whiopl2dejHOrinJz6kb/)

Please help and tell me how can i get fully updated?

My machine is: Lenovo B570e
HD 500GB
Intel core i3 2330M
2.1Ghz processor
Intel HD 3000 Graphics
4 GB RAM [64Bit machine]

---

### Post by grahammechanical on 2014-04-30
PPAs are Personal Package Archives. Individual developers set up a repository on a server to store their code. If the developer fails to provide a repository for 14.04 (trusty) then you will get those error messages.

Multiload Indicator is in the 14.04 software centre. Look for System Load Indicator. I installed Multiload Indicator on trusty tahr months before trusty tahr become 14.04 LTS. You should not need a PPA to install that software. Remove that PPA and install through the software centre. That will get rid of one of those error messages.

If we use a PPA to install software afterwards we should disable the PPA to prevent errors like this. Developers do not usually use PPAs to update there software. These errors will not prevent your installation from getting Ubuntu updates.

Regards.

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-30
thanks man! worked! [in a sense] there were 20's of ppa.launchpad.net links i removed all of them and now i am updated with no errors i just didn't have the concept of updates in Ubuntu. In windows i never update my OS xD

---

