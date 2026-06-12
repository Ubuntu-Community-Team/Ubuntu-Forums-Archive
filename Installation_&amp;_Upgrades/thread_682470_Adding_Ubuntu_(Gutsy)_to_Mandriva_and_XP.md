---
title: "Adding Ubuntu (Gutsy) to Mandriva and XP"
date: 2008-01-30
forum: Installation &amp; Upgrades
---

### Post by coverup1128 on 2008-01-30
As the subject says, I would like to install Ubuntu 7.10 on a ThinkPad T61, which already dualboots Windows XP and Mandriva 2008 Free. I have a free partition of about 20Gb to host Ubuntu stuff but would like Ubuntu and Mandriva share /home, which is on a separate partition, and swap (4Gb, should be plenty).

1. I presume this kind of install should not be a problem, but would like to have some detailed instructions. In particular, how will Ubuntu handle MBR which already has Mandriva and XP  boot infos?

2. Is it Okay to share homedirs between the two distros? What will happen to config files in my home dir if I boot Ubuntu after Mandriva (or the way around)? 

3. I would like to be able to suspend to disk. Will shared swap cause any problems? 

4. The idea is to switch to Ubuntu sometime later, after I will sort out all issues to my satisfaction. For the moment, booting from Gutsy LiveCD gives me about 2.5 hours of battery time vs over 3 hours in Mandriva and 4-4.5 hours in XP. This is the major reason for keeping Mandriva. Nonetheless, what will I need to do to remove Mandriva? Just wiping it off the harddrive will leave a 10Gb  empty partition  in the middle of the harddrive. How can I reclaim this space by moving Gutsy to that partition? 

Too many questions... but hope I will get an answer. Thanks.

---

### Post by zvacet on 2008-01-30
I don´t think it is good idea to share home dir between different distros.Because they are different and they share home may finish with strange bihavior.Of course you spend much energy with Gutsy because you are runing it from CD.I belive it is slower as well.You can easy Put Gutsyon top on Mandriva.During install when you come to partition stage choose manual way and select partition where Mandriva is and delete it.On that free space install Gutsy.before you do anything of these I just say backup your files.I think you will need new home so if you have something there you want to keep back it up.

---

### Post by coverup1128 on 2008-01-30
The point about sharing home is taken. But mandriva will have to stay for a while until I get comfortable with Ubuntu - I need the laptop for work :)

About Ubuntu being more power hungry... I believe one reason for mandriva being more power savvy because it runs a special kernel for laptops, with all power saving features compiled as modules or into the kernel. Gutsy boots some kind of generic kernel off the CD. What will I end up with if I install off this CD? Is there a special kernel for laptops? Will it be installed from the CD, or will I have to upgrade later to this special kernel?

---

### Post by coverup1128 on 2008-01-30
Bump.

Only question 2 has been answered. Anyone?

---

### Post by zvacet on 2008-01-31
I belive I answered two of your questions,but never mind.You should not have problem with MBR.Maybe Ubuntu will be first on your grub list and if you don´t like it you can change it.For suspend I don´t know.

---

### Post by coverup1128 on 2008-01-31
Thanks. Appreciate your replies.

Does anybody here has an experience with removing a Linux distro from a tripple boot system? I presume this should involve reinstalling  grub into the MBR, but will I be able to move Ubuntu's /  directories from one physical partition to another? 

Also, are ext3 partitions resizable? It looks like I will have to split /home into two, one for mandriva and another for Ubuntu.

---

### Post by zvacet on 2008-01-31
Download [Gparted](http://gparted.sourceforge.net/) and with it you can resize(and more) partitions.What exactly you are planing to do?

---

### Post by coverup1128 on 2008-01-31
> **zvacet said:**
> Download [Gparted](http://gparted.sourceforge.net/) and with it you can resize(and more) partitions.What exactly you are planing to do?

1. I will need to split /home into /home_Mandriva, /home_Ubuntu and /home_myfiles. The latter will have to be visible to both mandriva and Ubuntu.

2. Eventually, when I will be ready to remove Mandriva, I will need to rationalize the diskspace. Having empty partitions in the middle of the harddrive is a waist of resources, so I will have to move Ubuntu in order to reclaim the disk space.

3. Will I need to use separate /swap partitions for Mandriva and Ubuntu?

4. An unrelated question but I am still not certain: Will Ubuntu install a laptop kernel (like mandriva does) or is it a "one size fits all" type kernel?   

Thanks for your patience.

---

### Post by zvacet on 2008-02-01
1. I think there is no problem with that,but maybe someone will correct me if I´m wrong.
2.If you decide to remove mandiva someday you can add that free space to your files partition(I belive that one will be large)
3.it will be installed by default(I know that because I don´t have laptop and I have it installed)** laptop-mode-tools.**

---

