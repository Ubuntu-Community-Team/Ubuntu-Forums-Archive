---
title: "Upgrade aborts"
date: 2009-06-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by artsci2 on 2009-06-28
I'm getting messages that a partial upgrade is possible and then a meassage that pakcages are not downloadable at the point of 78 of 100+ files downloaded. Update manager then aborts the upgrade.

The system seems to work fine at its current state but just will not upgrade.

Should I just download the daily and do a fresh install or is there some other info I could report?

64bit Karmic Kernel 2.6.30-9generic
AMD 7750 3Ghz, 4Gb ram (3.8reported)
Sapphire HD 4550 single monitor 1920x1200
Gigabyte MA78GM-US2

---

### Post by psyke83 on 2009-06-28
Edit: removed this reply due to strange double-post, sorry.

---

### Post by psyke83 on 2009-06-28
The missing packages mean that your repository information needs to be updated (or a regional mirror is missing some files). Update your repository lists:

```
$ sudo apt-get update
```

Next point: **never** perform a Partial Upgrade **unless** you're sure that packages are supposed to be removed! I cannot emphasize this enough.

Run:
```
$ sudo aptitude safe-upgrade
```

This will upgrade as many packages as possible without removing anything.

You should not upgrade the remaining packages that are held back until you have verified they are safe to be removed. You must check the changelogs to verify. You can find them here: [https://lists.ubuntu.com/archives/karmic-changes/](https://lists.ubuntu.com/archives/karmic-changes/)

---

### Post by artsci2 on 2009-06-28
EDIT: This message below was written before my 3rd re-boot. On the third try the data drive appeared again and it was accessible this time. I was hoping to take a screenshot of the error message. I did change the boot disk priority in the bios on this boot so I would not need to keep pressing F12 to select the boot drive. Drives: WD 200GB PATA for 64bit ubuntu, Segate 250Gb Sata for 9.04, and a second Segate 250Gb data HD. THe OS were installed separately by disconnecting other drives during installation of each os.

> **psyke83 said:**
> ... Update your repository lists:

```
$ sudo apt-get update
```

Next point: **never** perform a Partial Upgrade.....

Run:
```
$ sudo aptitude safe-upgrade
```

-

OK the repository update seemed to work with no error messages and the safe upgrade too. Now however My data disk (second hard drive) is listed in "places" untill I click on it to open. An error message instantly appears about device bus time out. after that the data disk does not appear in the "places" menue. When I reboot the computer the data disck is in the "places menue again but dissapears after trying to open.

---

### Post by psyke83 on 2009-06-29
> **artsci2 said:**
> EDIT: This message below was written before my 3rd re-boot. On the third try the data drive appeared again and it was accessible this time. I was hoping to take a screenshot of the error message. I did change the boot disk priority in the bios on this boot so I would not need to keep pressing F12 to select the boot drive. Drives: WD 200GB PATA for 64bit ubuntu, Segate 250Gb Sata for 9.04, and a second Segate 250Gb data HD. THe OS were installed separately by disconnecting other drives during installation of each os.



OK the repository update seemed to work with no error messages and the safe upgrade too. Now however My data disk (second hard drive) is listed in "places" untill I click on it to open. An error message instantly appears about device bus time out. after that the data disk does not appear in the "places" menue. When I reboot the computer the data disck is in the "places menue again but dissapears after trying to open.

You will avoid a lot of headaches by browsing and/or searching the development forum before posting issues. This has been [discussed]("http://ubuntuforums.org/showthread.php?t=1198041") [several]("http://ubuntuforums.org/showthread.php?t=1198112") [times]("http://ubuntuforums.org/showthread.php?t=1198870").

---

### Post by artsci2 on 2009-06-29
> **psyke83 said:**
> You will avoid a lot of headaches by browsing and/or searching the development forum before posting issues. This has been [discussed]("http://ubuntuforums.org/showthread.php?t=1198041") [several]("http://ubuntuforums.org/showthread.php?t=1198112") [times]("http://ubuntuforums.org/showthread.php?t=1198870").

You are right but in this case I was following your lead and reporting back the results that came from the actions you suggested. 

Those suggestions worked and I thank you for them, and for mentioning the threads related to the disk acces problem.

Regarding the "sudo apt-get" and "sudo apttitude safe-upgrade": Is it good practice to do this before any updates on testing the next-best systems?

---

### Post by muglikar on 2009-06-29
Hello brother,
                    I have turned to Linux hoping it will solve my problem that my hard drive which is receiving a msg regarding my USB Hard Disk "This device cannot start. (Code 10)"

I have chosen Ubuntu due to recoomendation by a frnd and his advocacy that Ubuntu has huge support and that he has not faced any prob whatsoever whne he used Ubuntu.

I think the problem is because I reinstallled XP sp2, which in turn I did because the HD was running well on my Dell Laptop but its not working on my Desktop...

Another prob is that scrolling on my desktop CRT monitor has suddenly become discrete after I reinstalled XP sp2...

I cant change my Monitor's refresh rate...Earlier I could change it from 60 Hz to 85Hz...

DO U THINK UBUNTU WILL SOLVE THESE PROBLEMS FOR ME?

---

