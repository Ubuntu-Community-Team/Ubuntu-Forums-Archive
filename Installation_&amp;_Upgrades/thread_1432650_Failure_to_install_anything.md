---
title: "Failure to install anything"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by Cosmos42 on 2010-03-18
So when I tried to install some software, every software program would get to 50% and then crash.

Then, when I tried to update, I got this: 

(Reading database ... dpkg: unrecoverable fatal error, aborting:
unable to open files list file for package 'empathy': input/output error
E: subprocess user/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:


The only other issue I've been having lately is that when I attempt to open My Documents or the Desktop by clicking on them, nothing happens.

---

### Post by UCSBGauchosRock on 2010-03-18
I'm not sure but you could have broken packages. Try running the following command in a terminal

sudo dpkg --configure -a

---

### Post by tomsoms on 2010-03-18
Did you recently install the dpkg-dev update?

---

### Post by Cosmos42 on 2010-03-18
Thanks, that seemed to get things installing again.  I was hoping that the same issue that caused the install problem would be the issue causing my display problem, but no such luck.  Clicking open My Documents and Desktop still does nothing.  The mouse will just have the activity icon for a bit, and then nothing.

Any ideas?

---

### Post by UCSBGauchosRock on 2010-03-18
I was thinking on it and possibly try opening the folders like My Computer, Documents, Music... etc by using Disk Usage Analyzer and then right clicking on the folder you want to open and selecting open folder.

---

### Post by Cosmos42 on 2010-03-18
Hmm my computer doesn't give me the option of opening anything from Disk Usage Analyzer it seems...

---

### Post by Megafag on 2010-03-18
> **Cosmos42 said:**
> Hmm my computer doesn't give me the option of opening anything from Disk Usage Analyzer it seems...

Can you open terminal?

Try 

```
nautilus ~/
```

---

### Post by Cosmos42 on 2010-03-21
When I do that, I get this:

(nautilus:4921): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Segmentation fault

---

### Post by UCSBGauchosRock on 2010-03-25
Possibly try to open nautilus from a root environment. Open Terminal and type in "gksudo nautilus". Go to File System, Home, and Your User Name...

---

