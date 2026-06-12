---
title: "Ubuntu Installation Help"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by raddmadd on 2007-10-25
Hello.  Sorry for the repetitiveness that this thread may hold, however I have searched a bit around the forum and Ubuntu documentation and I still am a bit confused.

I want to entirely install Ubuntu.  Now I am on an Ubuntu Feisty Fawn 7.04 live disc.  I would simply just click on the option to do an entire install in the installation program, however I was reading things that were talking about root files, and swap files, so it confused me a bit about partitioning.  Can someone tell me what is suggested when partitioning, that is how I should partition and how much space?

Also, if I later have to install Windows, I will be able to do this after I install Ubuntu, right?  I mean, will I be able to kill Ubuntu? (I don't want to, however it is my family's computer, and some of my programs are only compatible with Windows)

Also, I want to update to 7.10, what is the easiest way to do this during installation?

Thank you.

---

### Post by granz on 2007-10-25
It may be better to install Windows first, then when you get to the 'Partitioning ' stage of the Ubuntu install you can choose 'Manual'.
then shrink the Windows partition to leave room for Ubuntu (make sure to defrag windows first).
You can then chose to use entire amount of unused (forget the term) space, and it will set-up home and swap partitions automaticaly.
Or, you can set up seperate root (/), Home and swap partitions yourself.
I was advised (and used) 8GB for root, 1GB for swap and the balance for Home.
hope this helps in some way, I'm sure others will help out here  :-
If you want to boot into Windows by default, you will need to edit Boot/Grub/menu.lst file

---

### Post by oldos2er on 2007-10-25
If you want to use your entire hard disk for Ubuntu (I'm guessing that's what you mean by "entirely install"), you choose that option when the partitioning part of the installation comes up--it'll say something like "Guided--use entire hard disk." A swap partition will be created automatically. There's more info here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

 I don't understand what you mean by "kill" Ubuntu. You can simply install Windows on the same partition as Ubuntu--that would effectively "kill" it.

 I don't believe you can upgrade to Gutsy as part of the Feisty installation; but you can certainly do that once Feisty is fully installed.

 Hope this helps.

---

### Post by thanato5 on 2007-10-25
You probably want to keep windows and dual boot linux.  The easiest (safest?) way to do this is put linux on a second hard drive.  Otherwise, odds are you will have to shrink down the windows partition to make room for linux.  I'm not sure the best way to do that.  

As far as how big do you want partitions to be, well, it depends.  I believe your swap partition should be about twice as big as the amount of physical RAM.  The main partition you will have mapped to / should be more than a couple of gigs so you can install software and store data and what not.  mine's like 100 gig, but I use linux for everything.  I threw windoze away a long time ago, but then I'm the main user of this PC and the other people who want to use it can either live with my decision or buy their own @#$% computer.

---

### Post by raddmadd on 2007-10-25
Okay thanks for the replies all, you answered my questions :)

---

