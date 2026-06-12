---
title: "apt-get upgrade: Which type of update does? (security, recommended, not published,..)"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by antoniorueda2013 on 2013-04-25
Hello, I´m introducing in this new exciting world of Ubuntu and I would want to ask something that I have in mind and don´t find an answer: If I use update manager, I can choose between security, recomended, not published or not supported updates, but If I use the apt-get upgrade tool, which type of update does? Maybe there is some configuration file that is changed when I change Update Manager`s options and both do the same update? 

Thank you very much!!

---

### Post by fantab on 2013-04-25
Yes. Its called 'sources.list'. It is located at /etc/apt/sources.list. Yes, 'apt-get upgrade' and upgrade from Update-Manager use the same settings.

'apt-get upgrade does the same job as update manager, except apt-get upgrade is more manual.

---

### Post by pfeiffep on 2013-04-25
> **antoniorueda2013 said:**
> Hello, I´m introducing in this new exciting world of Ubuntu and I would want to ask something that I have in mind and don´t find an answer: If I use update manager, I can choose between security, recomended, not published or not supported updates, but If I use the apt-get upgrade tool, which type of update does? Maybe there is some configuration file that is changed when I change Update Manager`s options and both do the same update? 

Thank you very much!!

Welcome to the world of freedom computing!

```
sudo apt-get update
```synchronizes the latest available software listings to your computer. It doesn't install anything, that's what upgrade does! (all apt-get commands should be run with sudo) 

Complete explanation is available by typing in a terminal window ```
man apt-get
``` 

[Wikipedia]("http://en.wikipedia.org/wiki/Advanced_Packaging_Tool") has some more info.

Synaptic Package Manager is an excellent GUI front end for apt-get that is available in the software center.

---

### Post by snowpine on 2013-04-25
If you are new to Ubuntu then I recommend you apply all recommended updates (the default setting, not changing any configs or checking/unchecking any boxes). This will get you the latest bug fixes and security patches for the software you already have installed (and nothing more).

Either run the Update Manager with the default settings, or if you prefer the terminal:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Your choice; the methods produce identical results. :)

---

### Post by antoniorueda2013 on 2013-04-27
Thanks you guys! I´m not used to be answered so soon! Actually, I have verified that after cheking the las two ones (not published, not supported), /etc/apt/sources.list has been added with two more lines:

*precise-proposed restricted main multiverse universe*
*precise-backports restricted main multiverse universe*

I have now another question, I have added some ppa´s with add-apt-repository commands. These ppas appear in Ubuntu´s software center -> software origin-> another software, but they don´t appear in /etc/apt/sources.list , so , is there another file with those repositories?

Thank you again, See you!

---

### Post by pfeiffep on 2013-04-27
Did you execute apt-get update after installing ppa's?

---

### Post by snowpine on 2013-04-27
I do not recommend "proposed" repo for non-developers. According to [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu) (lots of good info on that page) the propsed repo is described as:

> The testing area for updates. This repository is recommended only to those interested in helping to test updates and provide feedback.

As far as where PPA's are configured, look in the folder /etc/apt/sources.list.d/ and you should see a .list file for each of your PPA's.

---

### Post by antoniorueda2013 on 2013-04-29
Pfeiffep: Yes I did, and yes SnowPine, there are there. Thank you guys!

---

### Post by Cheesemill on 2013-04-29
> **antoniorueda2013 said:**
> I have now another question, I have added some ppa´s with add-apt-repository commands. These ppas appear in Ubuntu´s software center -> software origin-> another software, but they don´t appear in /etc/apt/sources.list , so , is there another file with those repositories?

All of the files in the /etc/apt/sources.list.d/ directory get looked at as well, this is where PPA's get added when you use the add-apt-repository command.

---

### Post by antoniorueda2013 on 2013-05-01
Thanks Cheesemill! Since I´m begginer, I´m trying to understand  how it works. I have another question: When you add the ppa´s, the system advises when are updates of this repositories available? I mean, in the way the updater manager does, or this is only for official repositories? I view it from a programmer point of view, can he advise his users that there is an update available?
More I study and learn more I like Ubuntu/Linux world! it´s fascinating!
Thank you all!

---

