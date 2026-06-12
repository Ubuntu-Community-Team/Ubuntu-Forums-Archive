---
title: "Lucid and BIOS Clock???"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ken0069 on 2010-04-10
Installed Lucid 10.04 on a multiboot system the other day and now I notice that every time I go back and boot Windows XP the clock is off by 4 hours?  Yes the proper time zone is set and yes I've double checked it in both Windows and Lucid?  It seems that the clock in Lucid may be set to see UTC time and there is NO provision to select anything different at install like it is in 9.10.  
 
Anyone have a fix for this?
 
Thanks,
 
Ken

---

### Post by undecim on 2010-04-10
This should help: [https://help.ubuntu.com/community/UbuntuTime#Multiple%20Boot%20Systems%20Time%20Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple%20Boot%20Systems%20Time%20Conflicts)

You can either make Windows use UTC or make Ubuntu use local time to solve the problem.

---

### Post by clhsharky on 2010-04-10
HI ken0069

Lucid has its own section, its still in testing.
Please report a bug, if something didn't work right.

Lucid Lynx Testing and Discussion
[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)


Sharky

---

### Post by gmargo on 2010-04-10
It may be an improper setting in the **/etc/default/rcS** file.  Open that file and look for the **UTC=**{yes|no} line, and toggle the value, and reboot.  See if that fixes it.

---

### Post by ken0069 on 2010-04-10
Will do, and thanks guys.
 
Ken

---

