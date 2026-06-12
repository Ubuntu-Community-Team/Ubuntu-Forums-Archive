---
title: "Stuck @ disk partition step...."
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by korax123 on 2007-05-01
Ok I was installing Ubuntu on my free computer...
PIII 800mhz 256mb ram

It was installing fine then stopped @ 41% for 30min I got inpatiant and reset the computer.  Now when you go to install it it gets stuck at the partition step.   Goes to 100% then it won't bring the option to select the partition type it just sits there.

---

### Post by raja on 2007-05-01
With 256 MB of RAM, it might be better to use the text-based installer. Things must be slow with the live CD.

---

### Post by korax123 on 2007-05-01
So if i would have left it longer it might have  gone through?

---

### Post by korax123 on 2007-05-01
Ok now it comes up with a program error when it gets to the disk partition portion of the install.  ANd i have 512 ram in the machine now.

---

### Post by raja on 2007-05-02
You can try gparted. It can be burnt as a live cd.

---

### Post by Topsiho on 2007-05-02
I have found that preparing the install by first doing the partitioning with the Live CD of Gparted makes things much easier. The graphical install program of Ubuntu also uses Gparted but that version is older or it is clipped, anyway it is not as good as that on the most recent Live CD of Gparted.

It is also usually much easier to do one job that requires some attention at a time then to combine such jobs, such as doing the partitioning during the install.

My two pennies :)

Topsiho

---

### Post by korax123 on 2007-05-02
Ok i figured it out.  I download version 6 last night and thismorning and it wouldn't even boot into the OS.

So i plugged in a newer CD drive.  The one in it was a 16x DVD drive.  Well that was the problem I put Version 7 in the  CD drive (old burner) and it booted and installed everything just fine.

I messed around with it for about 15min before going to work.  I love it so far but it does run a little slow on the 800mhz machine even though there is 512 ram in it.

---

### Post by Topsiho on 2007-05-03
Glad it works now. 512 MiB RAM is quite enough, more is better though. 800MHz is a little slow. But if your expectations are not towering high you should be able to enjoy your new Ubuntu Linux with this computer.

One thing: you write about the versions 6 and 7, which is a little bit confusing. There are the versions 6.04 and 6.10, and 7.04. Version 7.10 will be released in October this year.

6.10 means release date is year 2006, month 10

Sorry for correcting you, I have been a teacher in my previous life :), so I have this problem :lolflag: 

Topsiho

---

