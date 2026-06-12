---
title: "Can't boot into Windows"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by Leroy_Harrison_IV on 2015-11-17
When installing Ubuntu 14.04 I came to the section to erase my hard drive. I ddint see the option to dual boot. So i thought i had to click on lms box I thought I will able to choose the partition to dual boot Windows. But it went straight to the timezone question. I then hard reseted my laptop to boot back into Windows 10. Now Windows boot manger states selected boot device failed.
Please help.

---

### Post by Dreamer Fithp Apprentice on 2015-11-17
It's not absolutely clear to me what you did. Next time, when doing something like this, you might want to keep notes, so you can tell people EXACTLY what happened when. 
Anyway, boot some linux, even if only a live disk and check the output of:

```
 sudo parted -l
```

and

```
 df -h
```

What is supposed to be on the drive? Anything besides Windows and Ubuntu?

---

### Post by yancek on 2015-11-17
If you are using windows 10, you will be much better off using the manual install option which is called "Something Else" in Ubuntu.  Posting the requested output above will be a good first step and explain what you are referring to with this statement:  "So i thought i had to click on lms box"

If you aare using windows 10, you might also do some research on UEFI, you could just do a google of "dual boot windows ubuntu UEFI".

---

