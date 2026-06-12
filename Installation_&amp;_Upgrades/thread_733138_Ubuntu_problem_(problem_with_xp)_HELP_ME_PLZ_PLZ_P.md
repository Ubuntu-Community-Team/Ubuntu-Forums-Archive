---
title: "Ubuntu problem (problem with xp) HELP ME PLZ PLZ PLZ PLZ"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by stuartlulu on 2008-03-23
**_HHHHHeeeeellllllllllppppppppp meeeeeeeeeeeeeeee_**

[SIZE="4"]I have stupidly installed ubuntu os over my xp partition and now xp is gone. My computer inst powerful enough to insttall vista on so i was wondering if it was possible to put in a xp disk and install xp normally

So basicallly i have ubuntu installed only. if ii put in the xp disk, will it come up with the xp screen and install xp. reason y i am asking is because i dont have my laptop with me at the moment.

pllz help other wise im screwed.

Btw my computer had 1gb of ram (2 x 512mb) and came which vista preinstalled but since both ram modules  broke i have only 128mb which is crap but it does the job.

help me with my prblem as i need to do coursework for school

Stuart[/SIZE]

---

### Post by Pumalite on 2008-03-23
I would love to help you but can't read your message in my monitor. I suggest you eliminate the red and use normal fonts.

---

### Post by buntu_Geek on 2008-03-23
Yeah.... XP installation screen will appear....but for it you have to change the boot order with CD-ROM as the first boot option....

---

### Post by stuartlulu on 2008-03-23
it wont let me change the boot order

---

### Post by buntu_Geek on 2008-03-23
You have to go into the bios menu... and change the boot order...
there will options to change the boot order.... for sure

---

### Post by Pumalite on 2008-03-23
Consult your motherboard Manual to see how to access BIOS. Most common is 'Del' after POST

---

### Post by fela on 2008-03-23
If you install XP i think GRUB won't recognize it, so what I'd do (or what i wouldn't do, as i don't touch windoz) would be to reinstall windoze over ubuntu, then install ubuntu in a seperate partition.

---

### Post by stuartlulu on 2008-03-23
well i did what i said wat i wouldnt do and i restoresed the laptop (SLOW AS F**K) and i now cant install x on a seperate partition

---

### Post by uDanimal on 2008-03-23
Yup, just boot the windows cd and install xp from scratch.  THEN install ubuntu again and make sure you select ANOTHER partition for ubuntu.  I think it is technically possible to install xp after ubuntu and keep both, but its not very easy, and it would be far simpler to just reinstall xp and ubuntu.

---

### Post by Pumalite on 2008-03-23
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete everything in your hard drive. Make 2 'New' partitions: the 1st (at the beginning of the drive), formatted ntfs. The second (at the end) formatted ext3. Now boot your XP CD and install it in the 1st partition. Then proceed to install Ubuntu in the second partition.

---

### Post by stuartlulu on 2008-03-23
the thing is it wont let me install xp

---

### Post by Pumalite on 2008-03-23
Read my previous post.

---

### Post by uDanimal on 2008-03-23
I would imagine you would have to tell the installer to resize and use the free space on the windows partition.  The recovery disk usually just wipes all partitions and puts it back the way the factory did it.

---

