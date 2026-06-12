---
title: "extreme bug in partitioning (saucy salamander)"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by The musmula on 2013-10-21
I have encountered a serious bug in the partitioning code of ubuntu 13.10 and maybe elsewhere.

So what happened...
I have downloaded the new ubuntu 13.10 and installed it on my usb (with unetbootin, I know I should have used startup disk creator but it should not make a difference)
Eh, one info: I have had 4 primary partitions on my PC: one for winXP, one for ubuntu system files (/), one for my home folder and one for swap.
Since I had some bad expirience with upgrading from 12.10 to 13.04 (it took it 4h and I had CPU issues (the new installation was using only one core)) I decided to make a clean install wich would be totally safe since I have a seperated /home partition.
In the installation at the part where it asks me to decide do I want to run 13.10 alongside 13.04, erase, something else,... I have chosen "something else" and made sure that it would only format the old ubuntu system partition and install the new edition on it, but to LEAVE EVERYTHING ELSE AS IT IS!
That didnt happen,... After the install I`ve got stuck on the grub rescue so I made a new install this time I`ve chosen "reinstall ubuntu 13.10".
After that I was like, ok everything is fine, lets change the fstab so it uses the other partition as /home
It wiped my pc clean there was no other partition D:<

saucy salamander is as I see it not ready for release since I have encountered a graphical glitch a few seconds ago and it does not wanna boot without usb in port

---

### Post by oldfred on 2013-10-21
I am not sure I understand.
There is no d: in Linux?
You mount /home as part of your install, but when including it must not check format or else it will be erased.

The install or reinstall options I get are the same. Install alongside, erase drive, or Something else. I always use Something else and have not had any issues.

---

### Post by The musmula on 2013-10-23
You are right there is no d: in linux, there are UUID`s (a must-have for partitions) and labels (wich are not really required but usefull)

I havent checked my /home partition to be formated, I made 3 times sure that the partition shall "not be used" because I wanted to make it my /home after the install because it is safer for my data, but then again, it myght be a one in a milion bug, however I am now returning to ubuntu 12.04 LTS cuz it is LTS, and I wont have to make any risks like this one `till 2017

---

### Post by coldraven on 2013-10-23
> I made 3 times sure that the partition shall "not be used"
In the "Use as" field I think you should have put "/home" as well as unchecking the "Format?" box.

---

### Post by The musmula on 2013-10-23
As I already said I have unchecked it (actually it was unchecked by default) but I thought it might be risky to just set it to /home, cuz I had some expiriense in the earlier versions that it doesent let me check or uncheck the format checkboxes and that it sometimes leaves the checkbox unchecke for the partition that shall be used as "/"

And no I am not retarded, when operating with partitions my concentration is at 200%, I even turn off the music wich is ussually playing in my house.

I remember every step of the install (due to photographic memory) and I told everything relevant

---

### Post by coldraven on 2013-10-24
> I thought it might be risky to just set it to /home,
AFAIK if you don't do that then the partitioner will create another /home elsewhere.
The partitioner should give you a list of pending operations before proceeding to the next step. If they are wrong you can go back and correct them.
> And no I am not retarded,
No-one said that you were.

---

### Post by The musmula on 2013-10-24
alright, we could all cool down a bit, I am fully aware that it will create another /home folder, but that doesen`t bother me.
And there was no list of pending operations, seems suspicuos :-k

---

