---
title: "Separate partition for /home not created during &quot;auto&quot; installation?"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by KillrBuckeye on 2006-06-19
Hi, I just installed Ubuntu 6.06 on a spare machine, and I used the option to "delete entire hard disk" during the installation instead of the "manually edit partition table" option.  I was surprised to find that the auto installer didn't create a separate disk partition for /home.  Is this the norm???  I thought it was generally accepted that it is best to keep /home on a separate partition, so why wouldn't this be performed during an "auto" installation?

---

### Post by aysiu on 2006-06-19
This is the norm. The auto installation is simplistic. That's the way it's always been.

[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html) may help you.

---

### Post by KillrBuckeye on 2006-06-19
Okay, thanks for the info!  I'll probably just go ahead and reinstall with manual partition creation since I haven't done anything with this new install yet.

---

### Post by az on 2006-06-19
[QUOTE=KillrBuckeye] Is this the norm???  I thought it was generally accepted that it is best to keep /home on a separate partition, so why wouldn't this be performed during an "auto" installation?[/QUOTE]
It is not the norm.  All-on-one-partition is best for most people, in general.  You tend to not run out of disk space that way.

---

### Post by az on 2006-06-19
Seperate partition for home PRO and CON

Pro:

-simple backup of data when reinstalling

Con:

-You need to know your needs before you partition, otherwise you may run out of space on either your / or your home partition.
-The installation is more complicated since the user would have to learn what a home patition is in order to install.
-Config files for apllications may not always work properly with different versions of the same app.


Since there are more elegant ways of backing up your data (that don't run the risk of you blowing away the wrong partition when you reinstall) and a seperate partition for home is not required for your box to run properly, the all-on-one is the default partitioning scheme.

You can make one if you like using the installer.  It is not hard.

---

### Post by KillrBuckeye on 2006-06-19
Good points.  However, I can think of another important "Pro" for having a separate partition:  data on /home remains safe when the OS gets screwed up due to user error or 3rd party application.  Maybe this is more applicable to Windows :) , but those of us who tinker a lot and like to overclock are at a high risk for filesystem corruption or a broken OS. :D

---

### Post by aysiu on 2006-06-19
My advice--get a live CD like Knoppix. Then, it doesn't matter how badly your installation gets screwed up; you'll still be able to save your files.

Now if your partition table gets corrupted, that's another story, but a separate /home partition might not save you from that anyway.

---

### Post by az on 2006-06-19
[QUOTE=KillrBuckeye]data on /home remains safe when the OS gets screwed up due to user error or 3rd party application.  [/QUOTE]

Not really.  There are no applications tha you could install that deal with the filesystem directly.  The kernel does.  And why would it screw up your / and not your home partition?

The same goes for a windows partitioning too or something like that.  As well as for hardware failure.

[QUOTE=KillrBuckeye]
Maybe this is more applicable to Windows :) , but those of us who tinker a lot and like to overclock are at a high risk for filesystem corruption or a broken OS. :D[/QUOTE]

You run equal risk of borking your home partition, too, no?

---

### Post by KillrBuckeye on 2006-06-19
I've had 3rd party applications or malware that screw up an installation of Windows to the point where it's easiest to just revert to a previous image of the partition.  If one keeps his/her data and documents on the OS partition, all changes and additions since the last image was made will be wiped out.  For this reason I have the "My Documents" folder and as much program data as possible mapped to a separate partition from Windows.  It makes restoring the OS a snap.  I'm not experienced enough with Linux to know if the same risks are present.

---

