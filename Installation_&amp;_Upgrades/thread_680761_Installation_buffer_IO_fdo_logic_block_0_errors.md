---
title: "Installation buffer I/O fdo logic block 0 errors"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by DavidF579 on 2008-01-28
Still trying to get it to install.  I keep getting a "buffer I/O error on device fdo logic block zero"...there were two error messages ( [242.911479], and [280.936935] ) but I couldn't find them on the Ubuntu forums.  I also googled the error messages but didn't find them.

After I got the errors the install program still went through all the other checks which were okay and then there was just a tan screen...I let it sit for 2 hours since the program seemed to be accessing the CD Rom then shut it down and tried again.

I checked the CD for errors (using the ubuntu program on the CD) and also used my HDD diagnostics (my hard drive is a Western Digital 30 GB...WDC300EB) but everything checked out okay.

The only other thing I could think of is that I had installed an anti-rootkit program but I uninstalled it and I stll had the same problems.
  
Please help.  Thanks.

---

### Post by ajgreeny on 2008-01-28
Just a shot in the dark, but could it be anything to do with a floppy disk?
Perhaps the error message says "buffer I/O error on device fd[COLOR=Red]0[/COLOR] logic block zero" as in fd0(zero).
Even if that is the case, and as I say it is really a shot in the dark, I'm not sure what you can do about it other than disable the floppy, either in BIOS or by disconnecting it and trying again.

---

### Post by DavidF579 on 2008-01-28
Yes, it is fd0 as in zero.  I thought of that this morning and since I never use the FDD so I will try to disable it in Bios and retry.  But I'm not sure why the install program would "hang" even if it was the FDD.
Thanks for the tip.

---

