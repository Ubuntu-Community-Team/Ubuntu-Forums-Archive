---
title: "[SOLVED] Cannot open theme file@@@ToBeReplacedByDesktopBase&amp;amp;&amp;amp;&amp;amp;"
date: 2008-07-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by caryb on 2008-07-14
As the abstract title says, when I log on after updates today I get the above message & then dropped to shell. Any thoughts or has anyone seen this?

BTW O/S is Intrepid (no surprises there) DE is Kubuntu/KDE4


Cary

---

### Post by caryb on 2008-07-14
I just had a play & if I boot to terminal as root & type startx it will boot to KDE as root with no problems. I wonder if there is a permissions thing happening there? I also renamed my .kde4 folder to .kde4old & restarted but this didn't work. I guess I should have worked that out when it doesn't get that far as it is at the kdm level that it trips up.


Cary

---

### Post by caryb on 2008-07-15
Was pointed to a fix on the Kubuntu forum for this:guitar:

The post to the fix is here [http://ubuntuforums.org/showpost.php?p=3515501&postcount=32]("http://ubuntuforums.org/showpost.php?p=3515501&postcount=32")


Cary

---

### Post by xebian on 2008-07-15
> **caryb said:**
> Was pointed to a fix on the Kubuntu forum for this:guitar:

The post to the fix is here [http://ubuntuforums.org/showpost.php?p=3515501&postcount=32]("http://ubuntuforums.org/showpost.php?p=3515501&postcount=32")


Cary
That's the thing with Kubuntu.  Seems no one is checking if packages will break users DE unuseable for even such basic install/upgrade.  Seems to me they are more on to meeting schedules instead of quality release.  The release notes for RC1 said '.. still compiling..'.  If it's not complete, then don't release it yet.  Otherwise, unmet dependencies, will break things.  Not very good for Kubuntu's reputation.

---

### Post by xebian on 2008-07-15
> **caryb said:**
> Was pointed to a fix on the Kubuntu forum for this:guitar:

The post to the fix is here [http://ubuntuforums.org/showpost.php?p=3515501&postcount=32]("http://ubuntuforums.org/showpost.php?p=3515501&postcount=32")


Cary

Checked the post, but this was posted in Oct 2007, and it refers to KDE3 not KDE4.  :confused:

---

### Post by MoridinBG on 2008-07-15
As you have noticed you can log on with startx. But it is no necessary to do it as root. In contrast to 8.04 here normal users can start X too. So you just have to login in the console with your normal user, startx, then go to SystemSettings and disable theming for the login manager. The KDM works again.

---

### Post by caryb on 2008-07-15
If you change the kde3 for kde4 the rest is the same.


Cary

---

