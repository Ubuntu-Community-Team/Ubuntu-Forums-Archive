---
title: "Am I using the right repositories???"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by willix on 2008-01-08
Hy 

Could someone please tell me if the url in my source.list file (further down) are still active? 
I've refreshed synaptic yet it still tells me the latest version of thunderbird is 1.5 (eventhough 2 is out), that gnucash is currently 2.0 although I believe it to be 2.2, and so on...

I'm running Ubuntu edgy and these repositories are obvisously edgy based. Are they being kept up to date eventhough daper and gutsy have been released? If not can I use a daper or gutsy repository eventhough I'm running edgy or do I need to upgrade the whole system first?

thanks

----------

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) edgy non-free

---

### Post by PmDematagoda on 2008-01-08
If you wish to upgrade the system properly, then it is recommended that you use the official method of upgrading without resorting to methods such as adding incompatible repositories which can damage the entire system. Your system is kept up-to-date as the repositories get updated, this will continue until Edgy's support ends(If it has not occurred already).

---

### Post by erginemr on 2008-01-08
Hello,

Yes, your repository list is correct. However, don't expect to have the latest versions of the software while running Edgy Eft. All you can count on under Edgy is backports.

I was also an Edgy user up until recently. and although I loved Edgy, it also pissed me off not to be able to install and run the latest versions of Linux software (under the pretext of incompatible libraries). So, I had to do a fresh install of Gutsy.

You can do a gradual upgrade with Edgy -> Feisty -> Gutsy, but odds are that there will be side effects. The best path to follow, IMHO, is to back up what you can from your /home and /etc folders and do a fresh install.

(P.S. For Thunderbird, you have the option of installing version-2 from Mozilla web page.)

---

### Post by erginemr on 2008-01-08
> **PmDematagoda said:**
> If you wish to upgrade the system properly, then it is recommended that you use the official method of upgrading without resorting to methods such as adding incompatible repositories which can damage the entire system. Your system is kept up-to-date as the repositories get updated, this will continue until Edgy's support ends(If it has not occurred already).

+1 to that. I had tried this once (by replacing Edgy with Feisty) and ended up with an unusable system having fonts replaced by rectangles. So, that is not a solution.

---

