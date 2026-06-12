---
title: "ndiswrapper not working"
date: 2009-01-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by lance bermudez on 2009-01-20
I was told to move here could some one please check out my pervise post here
[http://ubuntuforums.org/showthread.php?p=6586343&posted=1#post6586343](http://ubuntuforums.org/showthread.php?p=6586343&posted=1#post6586343)

---

### Post by Slug71 on 2009-01-20
Do you not have the restricted driver in System-Admin-Hardware Drivers?

---

### Post by lance bermudez on 2009-01-20
i have the restricted driver in System-Admin-Hardware Drivers link but their is no driver in it. It is blank. I moved from 2.6.27 with kernel check or what ever the program is called from sourceforge.net.

---

### Post by Slug71 on 2009-01-20
> **lance bermudez said:**
> i have the restricted driver in System-Admin-Hardware Drivers link but their is no driver in it. It is blank. I moved from 2.6.27 with kernel check or what ever the program is called from sourceforge.net.

This doesnt really make sense? You have the driver there but its blank?

---

### Post by Ayuthia on 2009-01-20
Since you compiled your own driver, you will not have the wl driver and you will not be able to use ndiswrapper from the repositories.  However, ndiswrapper 1.53 will not compile in 2.6.28 without a patch.  You might try grabbing the ndiswrapper source from SVN.  I think that they have that version working.  Here is the link:
[http://sourceforge.net/svn/?group_id=93482](http://sourceforge.net/svn/?group_id=93482)

You will need to install subversion so that you can grab the source.

---

### Post by LordVeovis on 2009-01-21
ndiswrapper worked out of the box with my laptop.  Why did it not for you?  All I had to do was get the windows driver for my nic and install it if I remember correctly.

---

