---
title: "Triple boot Ubuntu Backtrack and windows 7"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by tanush on 2010-09-08
Guys,
Im really copping up with linux and have learned quite much in linux field and now i tried triple booting Ubuntu,Backtrack and windows 7. 

I have installed ubuntu through wubi but can install seperately also

How should i proceed?
Can someone please help?

I have been scared of grub and i wanna overcome it. 

plz help guys....

---

### Post by uRock on 2010-09-08
You are wanting to remove the wubi and install to a partition and install Back|Track or you already have BT installed?

What is your current partitioning scheme?

---

### Post by tanush on 2010-09-08
I tried installing all 3 but dont knw how to configure..

what i did was

i installed 7
then ubuntu using wubi

and then backtrack..

now i cant log in into windows 7 and there is no grub entry for backtrack :(

---

### Post by mohansathish on 2010-09-08
Just try updating the grub.
Goto terminal and type sudo update-grub.
I think that will list backtrack

---

### Post by uRock on 2010-09-08
Tanush, Did the updating of grub fix the problem?

---

### Post by mohansathish on 2010-09-08
Our kind request Is, If you get your problem solved, please do inform us so that we will be much more happy to hear that

---

### Post by tanush on 2010-09-08
sorry for the late reply..

I didnt touch the grub.

I have installed the operating systems only.

And I cannot boot into windows.

I could boot only till boot splash screen.

---

### Post by mohansathish on 2010-09-08
I think installing grub alone will solve your problem. The reason is that the BOOT.INI file in windows might malfunction. so, Installing grub will help you. Install it by using Live CD and Internet. 

Good luck

---

### Post by tanush on 2010-09-09
Alrite This is what happened now..


I updated the grub but no use..


I see 4 entries named Ubuntu but two of them opens up backtrack and other 2 hangs.


Windows 7 is working perfectly... BT is working perfectly but I cannot boot into ubuntu....


update grub was completed successfully but nothing has changed...

what should i do now ?

---

### Post by tanush on 2010-09-09
plz see the pic attached

the highlighted entry does not work..

---

### Post by Mark Phelps on 2010-09-09
> **mohansathish said:**
> I think installing grub alone will solve your problem. The reason is that the BOOT.INI file in windows might malfunction. so, Installing grub will help you. Install it by using Live CD and Internet. 

Good luck

Been a while since I checked, but AFAIK, Wubi installs do not use GRUB; instead, they use something known as GRUB4DOS -- because they install it to an NTFS partition.  So, telling the OP to install GRUB is not only wasting their time, it's possibly damaging their system.

As to boot.ini -- good grief folks!  That hasn't been used since Vista came out YEARS ago. If you're going to offer MS Windows advice, then at least take the time to research the problem.

---

### Post by uRock on 2010-09-09
Mark, the OP should have grub via the Back|Track install.:D

---

### Post by tanush on 2010-09-11
> **mohansathish said:**
> Just try updating the grub.
Goto terminal and type sudo update-grub.
I think that will list backtrack

This worked..

but i had to install ubuntu again without using wubi..

thnx a ton...

---

### Post by uRock on 2010-09-11
I bet ubuntu will run even better for you now. It may take some initial tweaking, but it will be good.

---

### Post by mohansathish on 2010-09-11
Rock and roll with separate install tanush ;)

---

