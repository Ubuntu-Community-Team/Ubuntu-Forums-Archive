---
title: "I need an example"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by RiotNrrd on 2005-03-20
OK, I had to reinstall Windows on my dual boot system, and Grub is now gone.

I'm trying to reinstall it, and I followed the instructions in the FAQ, but have gotten stuck on one point.

In using the Ubuntu installation disk to gain root access (so I can reinstall Grub), the FAQ tells me to type the following at one point:

```
mount <wherever your Ubuntu root device is> /Ubuntu
```

For a newbie to Linux like myself, the phrase between the angle-brackets is of no use at all.  I tried everything I could think of and it keeps telling me that there is no such file or directory.  I'm ready to pull my hair out.

My Windows install is on **hda1** (drive 1), and my Ubuntu install is on **hdb1** (a second harddrive).  I've tried typing **hdb1**.  I've also tried **(hd1,0)** - that doesn't work either.  **/dev/hdb1** doesn't work.  I think I tried a few others but can't think of them now.

Help!  I need to know what it's asking me to type!

---

### Post by Buffalo Soldier on 2005-03-20
Which FAQ are you refering to? Is this the one? [http://ubuntuguide.org/#gainrootinstallcd](http://ubuntuguide.org/#gainrootinstallcd)

Have you tried```
mount /dev/hdb1 /ubuntu/
```

EDIT: trying to figure this out too.

---

### Post by WW on 2005-03-20
Assuming you are following that instructions that Buffalo Soldier linked to...

Linux is case-sensitive.  The first command in step 6 of that FAQ is
```
# mkdir /ubuntu
``` which creates a directory called "/ubuntu" (not "/Ubuntu"). Try the command the way Buffalo Soldier showed it:
```
# mount /dev/hdb1 /ubuntu/
```

---

### Post by RiotNrrd on 2005-03-20
[QUOTE=WW]Assuming you are following that instructions that Buffalo Soldier linked to...

Linux is case-sensitive.  The first command in step 6 of that FAQ is
```
# mkdir /ubuntu
``` which creates a directory called "/ubuntu" (not "/Ubuntu"). Try the command the way Buffalo Soldier showed it:
```
# mount /dev/hdb1 /ubuntu/
```[/QUOTE]
 I appreciate the help, guys.

The case-sensitivity issue wasn't a factor except in my retyping above.

I finally solved the problem in the kludgiest way possible.  I installed the Ubuntu base files to a third partition, which as a side-effect installed grub, then used it to boot into my old (i.e., "good") Ubuntu installation and run grub-install (or whatever it was).  That repointed grub to the menu list on that installation.  Then I killed the new partition, and everything works fine.

The fact that Windows always wipes out grub, and that putting it back appears to be a major headache makes me think that the Ubuntu programmers might want to put an option on their install disk which just reads "Reinstall Grub".  I mean, this sort of thing must happen all the time.  This little option, in my imagination, would search your drive(s) for OS partitions, then ask which partition you want to link to.  If you've already got an Ubuntu installation, you just point at it and it'll link to the menu files that are already there.  Problem solved.

Oh, well.  We can dream, I guess...  :-)

---

