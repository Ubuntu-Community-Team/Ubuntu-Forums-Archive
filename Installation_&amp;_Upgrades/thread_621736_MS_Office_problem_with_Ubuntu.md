---
title: "MS Office problem with Ubuntu"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by babek on 2007-11-24
Hi all!,

I have installed MS Office on Ubuntu 7,10.  But when i try to open word or other application, i get such message:

**Microsoft Office Word has not been installed for the current user. Please run the setup to install the application.**

But i already installed the application, but have troubles with it.

---

### Post by prodezigner on 2007-11-24
We need more specifics, like how you installed it, Wine, Crossover, etc.

I know some programs require you to be admin on the windows portion of windows boxes to install for all users. This could be the same instance.

---

### Post by mac-duff on 2007-11-24
Hi,
have u meanly found a solution for this problem?
I found this tut but the error still exist:
[http://wine-review.blogspot.com/2007/09/running-ms-office-2003-under-linux-with.html](http://wine-review.blogspot.com/2007/09/running-ms-office-2003-under-linux-with.html)

---

### Post by Elenion on 2007-12-18
I experienced the same problem istalling Office 2003 on Ubuntu Gutsy just using the Microsof installer and Wine 0.9.46.

Is it related to my version of Wine? In [this]("http://wine-review.blogspot.com/2007/09/running-ms-office-2003-under-linux-with.html") how to seems to work for Wine 0.9.37.

Then somebody also tried this trickery:

I got Office2003 to work on Wine 0.9.49 by doing this Tut but also editing the Regedit at:

HLM\Software\Microsoft\Office\11.0\Registration\

You will find a long Number Folder like this: {90023423-6000... Click on that and edit the SmartSourceDir to point to the Source of Office11 Folder which you installed from. I rip my Office to my Linux Box and made a Drive Mapping to point D:\ to home/user/office11 folder.

I'll try....:popcorn:

---

### Post by Elenion on 2007-12-19
I actually have found a solution.

The suggested downgrade to version 0.9.37 didn't worked for me. I tried to do it compiling wine from source, but it didn't worked. I also tried to upgrade to version 0.9.51 but it still didn't worked. 

What worked for me was to install the Office 2003 package in Wine version 0.9.51 from console using the following command:

```
wine SETUP.EXE ALLUSERS=2
```

As stated in the SETUP.HTM of the Office installation CD the above options install Office for all the users.:)

---

### Post by VO1HL on 2007-12-27
Has anyone else tried the ALLUSERS=2 solution?? I am trying to get MS Visio 2002 to work under Wine 0.9.46 with Ubuntu 7.10. I get the "User" issue. I have tried reinstalling a number of times all to no avail.

Any experience stories with the MS setup.exe switch solution would be appreciated.

73,
Larry

---

### Post by Orfintain on 2007-12-27
I've wine 9.46 

I'm getting user errors installing office 07 on gusty

I tried the users=2 and that didn't work

Dosn't work with wine 9.51 either

---

### Post by mac-duff on 2008-01-02
thx, with ALLUSERS=2 works for me perfectly. But what I ask myself now should be the value be 2 directly in the MSI???
Does somebody has MSI editor for Linux?

---

### Post by Orfintain on 2008-01-03
what office 03 or 07?

---

### Post by mac-duff on 2008-01-03
of course 2003 and thats only because its still impossible to have a good import to OO

---

### Post by Orfintain on 2008-01-03
we get 07 for free at school..

---

