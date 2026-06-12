---
title: "Dual Boot XP/Ubuntu - no option for guided partition"
date: 2007-07-31
forum: Installation &amp; Upgrades
---

### Post by MCrittenden on 2007-07-31
Have XP installed on a Dell 9300 80GB hard drive, 1GB RAM.

Booted Ubuntu via live CD, and it recognizes the accounts to import from windows, so I know it has found windows, but on the disk partition step it doesn't give me an option to do a guided partition. My only options are manual partition OR use the entire disk.

There's about 55GB free space on HDD, and I did a disk cleanup and a defrag before attempting install.  The windows defrag cut out about halfway through (blue screen of death, with error message telling me to uninstall any 3rd party defragmenters, had to restart computer) so I attempted again and same thing. I'm wondering if the reason Ubuntu can't partition is because the defrag didn't finish moving the data closer together?

Anyway I tried system rescue CD but GParted threw an error (I can rerun and find the error if that's helpful) when I tried to run it.

It seems like even if the defrag didn't do it's job, Ubuntu would still give me the option to to a guided partition and just not give me a lot of free space to work with.

Any ideas?  I'm not very familiar with command line utilities so that may be why GParted didn't work.

---

### Post by fazavon on 2007-07-31
I came across this, it is for new users.

[http://news.softpedia.com/news/Install-Ubuntu-from-Windows-in-3-Steps-Without-Using-a-CD-61304.shtml](http://news.softpedia.com/news/Install-Ubuntu-from-Windows-in-3-Steps-Without-Using-a-CD-61304.shtml)

I have ye to try it, mainly because I dont even own a machine that has Windows.

But it looks pretty easy to use.

//j

---

### Post by merlinus on 2007-07-31
A few suggestions:

Run chkdsk c: /f from windows.  You will have to reboot.  Then try defragging again, but first delete all temp files, etc. and backup vital data.

Before partitioning, set windows paging file to zero.  Write down the curent value so you can reset it after installing ubuntu.

Use gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It is graphical, and much better than the one on the live cd.

Good luck!

-merlin

---

### Post by MCrittenden on 2007-08-01
Thanks for the help...couple of new questions.

I ran chkdsk c: /f, rebooted, deleted temps and ran a backup, defragged again (once again it crashed).

Ran the GParted live CD...it was unable to resize the partition. Error message:

"Warning:  The software has detected that the disk has at least 128 bad sectors. This means physical damage to the disk caused by deterioration, manufacturing faults, or other reasons. Make a backup of the disk, and then run 'chkdsk /f /r', reboot TWICE, and then you can resize NTFS by additionally using the --bad--sectors option of ntfsresize"


I ran chkdsk /f /r, rebooted twice, got the same message.

Looks like ntfsresize can be run through GParted? Do I run it with the terminal window? Anyone know the syntax?

Thanks.

---

### Post by merlinus on 2007-08-01
With these kind of errors, I would advise replacing your hard drive.  You are risking loss of data and being unable to access your computer.

-merlin

---

