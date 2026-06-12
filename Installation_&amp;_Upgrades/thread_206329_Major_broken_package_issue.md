---
title: "Major broken package issue"
date: 2006-06-29
forum: Installation &amp; Upgrades
---

### Post by Karbonik on 2006-06-29
which is blocking anything else from being updated, installed, or removed, via any method I can think of short of manually editing databases...

After originlly trying to install via dpkg it sticks, and has unmet dependencies, which I tried to acquire via Adept and also by apt-get, which didn't work.

First I get this:

karbonik@Biosolar-laptop:~$ sudo apt-get install gpar2
Reading package lists... Done
Building dependency tree... Done
E: The package gpar2 needs to be reinstalled, but I can't find an archive for it.


So I attempt  reinstall...

karbonik@Biosolar-laptop:~/downloads$ sudo dpkg -i gpar2_0.3-1_i386.deb
Selecting previously deselected package gpar2.
(Reading database ... 86778 files and directories currently installed.)
Preparing to replace gpar2 0.3-1 (using gpar2_0.3-1_i386.deb) ...
Unpacking replacement gpar2 ...
***
* Updating MIME database in /usr/share/mime...
Wrote 498 strings at 20 - 2988
Wrote aliases at 2988 - 2b34
Wrote parents at 2b34 - 3578
Wrote literal globs at 3578 - 35d4
Wrote suffix globs at 35d4 - 6b0c
Wrote full globs at 6b0c - 6b38
Wrote magic at 6b38 - c1dc
Wrote namespace list at c1dc - c204
***
/var/lib/dpkg/info/gpar2.postrm: line 25: update-desktop-database: command not found
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
***
* Updating MIME database in /usr/share/mime...
Wrote 498 strings at 20 - 2988
Wrote aliases at 2988 - 2b34
Wrote parents at 2b34 - 3578
Wrote literal globs at 3578 - 35d4
Wrote suffix globs at 35d4 - 6b0c
Wrote full globs at 6b0c - 6b38
Wrote magic at 6b38 - c1dc
Wrote namespace list at c1dc - c204
***
/var/lib/dpkg/tmp.ci/postrm: line 25: update-desktop-database: command not found
dpkg: error processing gpar2_0.3-1_i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
***
* Updating MIME database in /usr/share/mime...
Wrote 496 strings at 20 - 2958
Wrote aliases at 2958 - 2b04
Wrote parents at 2b04 - 3548
Wrote literal globs at 3548 - 35a4
Wrote suffix globs at 35a4 - 6adc
Wrote full globs at 6adc - 6b00
Wrote magic at 6b00 - c1a4
Wrote namespace list at c1a4 - c1cc
***
/var/lib/dpkg/tmp.ci/postrm: line 25: update-desktop-database: command not found
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gpar2_0.3-1_i386.deb



Okay....
let's try a remove...

karbonik@Biosolar-laptop:~/downloads$ sudo dpkg -P gpar2
dpkg: error processing gpar2 (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 gpar2


That's funny - the reinstall didn't work the first time, but I try it again to no avail...


karbonik@Biosolar-laptop:~/downloads$ sudo dpkg -i gpar2_0.3-1_i386.deb
Selecting previously deselected package gpar2.
(Reading database ...
dpkg: serious warning: files list file for package `gpar2' missing, assuming package has no files currently installed.
86749 files and directories currently installed.)
Preparing to replace gpar2 0.3-1 (using gpar2_0.3-1_i386.deb) ...
Unpacking replacement gpar2 ...
dpkg: dependency problems prevent configuration of gpar2:
 gpar2 depends on libgtkmm-2.4-1c2 | libgtkmm-2.4-1c2a; however:
  Package libgtkmm-2.4-1c2 is not installed.
  Package libgtkmm-2.4-1c2a is not installed.
 gpar2 depends on gnome-desktop-data; however:
  Package gnome-desktop-data is not installed.
dpkg: error processing gpar2 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gpar2



Okey doke.  Mayb it didn't like my manual reinstall.  Let's try something that should meet the dependencies automagically...

karbonik@Biosolar-laptop:~/downloads$ sudo apt-get install gpar2
Reading package lists... Done
Building dependency tree... Done
gpar2 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gpar2: Depends: libgtkmm-2.4-1c2 but it is not installable or
                  libgtkmm-2.4-1c2a but it is not going to be installed
         Depends: gnome-desktop-data but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Just to be on the safe side, maybe I need to update...

karbonik@Biosolar-laptop:~/downloads$ sudo apt-get update

...and try again...

karbonik@Biosolar-laptop:~/downloads$ sudo apt-get remove gpar2
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  gpar2
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 201kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 86748 files and directories currently installed.)
Removing gpar2 ...
***
* Updating MIME database in /usr/share/mime...
Wrote 496 strings at 20 - 2958
Wrote aliases at 2958 - 2b04
Wrote parents at 2b04 - 3548
Wrote literal globs at 3548 - 35a4
Wrote suffix globs at 35a4 - 6adc
Wrote full globs at 6adc - 6b00
Wrote magic at 6b00 - c1a4
Wrote namespace list at c1a4 - c1cc
***
/var/lib/dpkg/info/gpar2.postrm: line 25: update-desktop-database: command not found
dpkg: error processing gpar2 (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 gpar2
E: Sub-process /usr/bin/dpkg returned an error code (1)


Now although I'm fresh enough on this Linux distro install to be able to format the drive and reinstall from scratch without too much time wasted, I'd really love to know exactly WTF is going on in case this happens again, as it apparently easily does...  

Any ideas?

---

### Post by Rumor on 2006-07-03
A friend of mine had this same issue. He fixed it with ```
/var/lib/dpkg/info$ sudo rm gpar2.*
```

---

### Post by Karbonik on 2006-07-07
Cool, thanks.

I wound up reformatting and reinstalling anyway (didn't like the partition scheme) but I'm going to try it again.  If it happens, I'll definitely try that before resorting to a partition-image backup restore.

---

### Post by Karbonik on 2006-07-07
Just reinstalled the Gpar2 package.

This time it went with no problems, possibly because this last OS install I also added Gnome (to test it out and see how I like it) which apparently adds the necessary libgtkmm packages already, so the only thing to add for Gpar2 was the library first, and then the Gpar2.

Hope this helps someone else out down the road.

---

### Post by Kramon on 2007-02-18
I can confirm that Karbonik's fix works :)

---

