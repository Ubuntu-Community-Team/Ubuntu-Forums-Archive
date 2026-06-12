---
title: "Upgrade from 13.10 to 14.04 LTS"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-17
As every one knows, finally Ubuntu 14.04 L.T.S. has been released, therefore, i wanted to upgrade my Saucy Salamander to Trusty Tahr.I have Ubuntu 13.10 backup.tar.bz2 which contains all folders of my root directory including /home/user.I have Ubuntu 14.04 L.T.S. , if i fresh install Ubuntu 14.04 LTS and restore my backup [complete backup of every folder in the root directory] then will i be messing up 13.10 with 14.04 LTS ? i guess myself, yes!If yes, then which folders i should backup of my current Ubuntu 13.10 so that i may cover up all necessary folders which contain backup of my all software.If no, then why 13.10 will not be messing 14.04 LTS.[P.S. I don't want to install manually all software again from zero.]Any help would be appreciated. Thank you!

---

### Post by 23dornot23d on 2014-04-17
I use Timeshift ..... it may be worth a look at ........

A Timeshift backup - just of your old system ( should you need a snapshot - only you can say )
only records the system though ..... so go through your home folders and put onto a separate partition
anything else like photos videos and documents etc .......

Just ensure you have plenty of space on a partition to keep the backup - often I have noticed it needs 3 gig more than it
reports back ........ which can make things awkward if you have little room .......
 ..... also it only works from a graphical environment ....... so you have to be sure you can get to a gui to do the restore should you need it.
[URL="http://www.teejeetech.in/p/timeshift.html"]


http://www.teejeetech.in/p/timeshift.html[/URL]

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-17
> **23dornot23d said:**
> I use Timeshift ..... it may be worth a look at ........A Timeshift backup - just of your old system ( should you need a snapshot - only you can say )only records the system though ..... so go through your home folders and put onto a separate partitionanything else like photos videos and documents etc .......[http://www.teejeetech.in/p/timeshift.html](http://www.teejeetech.in/p/timeshift.html)that's cool, software i would like to test it in 14.04 [ when i will get to install it hehe :p ]but for the time being, my problem is not backing up but restoring everything on a new version of Ubuntu. . .I don't see how timeshift is gonna help me in the problem! by the way , thanks for you help! :)

---

### Post by monkeybrain20122 on 2014-04-17
That is not how you do it. Instead of backing up the software you create a list of what are installed and then reinstall from the list.
[https://answers.launchpad.net/ubuntu/+question/230034](https://answers.launchpad.net/ubuntu/+question/230034)

This however will not keep your settings. So you need to copy the .conf files from your backup. This would be a lot easier had you made a seperate /home partition. That way when you reinstall you can use the same /home

---

### Post by Ubi_one_2014 on 2014-04-17
i just started update-manager to upgrade to 14.04

1Gb of upgrades is availble
i minutes i am upgraded.. for free....:KS

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-17
that's one way of doing it, thanks! any further suggestions? i mean i am not as willing to re-download and re-install all of software which i safely assume that is gonna take long time & i don't have that much time either. In my locale, electricity has enough issues so may be during installation if my router gets off and all working will be messed up and i don't wanna do that to me!

---

### Post by Muhammad_Ahmad_Mujtaba on 2014-04-17
> **Ubi_one_2014 said:**
> i just started update-manager to upgrade to 14.041Gb of upgrades is availblei minutes i am upgraded.. for free....:KShehe Linux has always been free [that's the best thing about it after being opensource hehe :p].P.S. i have a scheme which is time as same as you suggested, I would upgrade via terminal and there are only two possible cases:1. If all went well that will be superb but i have read over forums that upgrade isn't good most of times so fresh installation is recommended.2. If all went messy or some of the process, i would have backup and image of 13.10 . I would re-install 13.10 and restore my backup and wait for the GOD call when i will be called to update my PC [hehe :p just kidding, i just meant, when i'll find a suitable thread or answer to my good problem xD ]

---

