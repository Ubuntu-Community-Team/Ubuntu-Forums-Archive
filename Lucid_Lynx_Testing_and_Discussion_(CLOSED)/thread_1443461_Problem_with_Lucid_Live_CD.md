---
title: "Problem with Lucid Live CD"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Rubi1200 on 2010-03-31
I have tried a number of times now to burn the latest Beta ISO (including using the lowest possible burn speeds) but every time I put the CD in the drive to test run it I get to the Ubuntu logo screen and then...nothing!
Anyone got some suggestions or advice because I would really like to test run the latest version before it goes live April 29.
Thanks in advance.

---

### Post by john newbuntu on 2010-03-31
Please check the md5sum of the iso and the CD first before proceeding.

---

### Post by plucky on 2010-03-31
> **Rubi1200 said:**
> I have tried a number of times now to burn the latest Beta ISO (including using the lowest possible burn speeds) but every time I put the CD in the drive to test run it I get to the Ubuntu logo screen and then...nothing!
Anyone got some suggestions or advice because I would really like to test run the latest version before it goes live April 29.
Thanks in advance.

At the logo press <enter> and the choice of language page should open.Select your language and then <enter> will take you the list of choices,one of which is to test CD.

Good Luck

---

### Post by Rubi1200 on 2010-03-31
md5 of the iso is 7ddbfbcfcc562bae2e160695ec820e39
not sure how to check for a cd; please advise
thanks

---

### Post by Rubi1200 on 2010-03-31
Thanks plucky, tried as you suggested and got as far as the screen where the little white dots turn red etc. Then it just froze up and went no further. Could this be a problem with restrictions on the computer (ssshhh I was trying it out at work)?
thanks

---

### Post by theozzlives on 2010-03-31
> **Rubi1200 said:**
> Thanks plucky, tried as you suggested and got as far as the screen where the little white dots turn red etc. Then it just froze up and went no further. Could this be a problem with restrictions on the computer (ssshhh I was trying it out at work)?
thanks

There shouldn't be restrictions on hardware, besides boot and BIOS password (permissions are at the OS level). However, I would strongly advise against installing Ubuntu on your work computer... could get you fired. Especially a Beta version.

---

### Post by lordskid on 2010-03-31
> **Rubi1200 said:**
> md5 of the iso is 7ddbfbcfcc562bae2e160695ec820e39
not sure how to check for a cd; please advise
thanks

you can open a terminal and browse to your cd drive. most probably /media/cdrom0

and do an md5sum

```

md5sum -c md5sum.txt

```

md5sum.txt should be in the root directory of your cd drive.

note that it will seem to hang after the first 3 files tested okay. try to wait for it mine completed in roughly 6 mins

---

### Post by Rubi1200 on 2010-03-31
Just to be clear; I am NOT trying to install anything at work, just wanted to test the latest beta as a LiveCD before considering a fresh install when it is released next month. However, BOTH at home and at work the process freezes and I would really like to know why that might be.
Thanks

---

### Post by Mark Phelps on 2010-03-31
Lucid is still in beta testing, thus beta-related questions should be posted to the proper forum: Development & Programming, Lucid Lynx Testing.

I will be asking the Mods to move this thread there.  Look there for future responses.

---

### Post by Rubi1200 on 2010-03-31
Thanks and sorry for not posting in the right forum.

---

