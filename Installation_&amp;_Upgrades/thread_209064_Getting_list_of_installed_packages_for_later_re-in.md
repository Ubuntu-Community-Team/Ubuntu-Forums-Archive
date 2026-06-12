---
title: "Getting list of installed packages for later re-installation"
date: 2006-07-04
forum: Installation &amp; Upgrades
---

### Post by A.Skwar on 2006-07-04
Hello!

To (maybe) fix my problems with Dapper, I'd like to reinstall Dapper. After finishing the installation, I'd like to re-install all the now missing packages and remove the unneeded packages, so that I'll have all the packages installed, that I've now got installed. What's the best way to do this?

To get a list of the installed packages, I wanted to do:

```
dpkg -l | awk '{print $2}' > ListOfInstalledPackages.txt
```

And to later reinstall those packages, I tought about:

```
apt-get install `cat ListOfInstalledPackage.txt`
```

Will this work? Will this install all those packages that are missing from the new installation? How about removing the unneeded packages - will they be removed? Because of the "install" command, I "suspect" not :)

How would I go about this?

Thanks,

Alexander

---

### Post by aysiu on 2006-07-04
This is a little more ghetto, but I know this works.

1. ```
dpkg -l > installedpackages.txt
```
2. Open OpenOffice Calc.
3. Open *installedpackages.txt* as a delimited text file.
4. Get rid of extraneous columns.
5. Copy and paste the relevant columns into another text file in Gedit.
6. Find/replace the carriage returns for spaces. Highlight. Copy. Control-H.
7. Add this in front of the list of packages: ```
#!/bin/bash
sudo aptitude update
sudo aptitude install package1 package2 package3 package4 etc.
```
8. Save the text file as installpackages.sh

After you reinstall, make sure you have all the repositories you need and then ```
chmod +x installpackages.sh
./installpackages.sh
```

Then after you get the install just the way you want, I'd recommend using PartImage to back it up so you won't have to reinstall again:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by mister_p_1998 on 2006-07-04
[QUOTE=aysiu]This is a little more ghetto, but I know this works.

1. ```
dpkg -l > installedpackages.txt
```
2. Open OpenOffice Calc.
3. Open *installedpackages.txt* as a delimited text file.
4. Get rid of extraneous columns.

and which are the extraneous columns?

---

### Post by aysiu on 2006-07-04
The extraneous ones are the ones with the package versions and  descriptions and such.

You want only the *names* of the packages.

---

### Post by delfick on 2007-02-23
thnx for the howto aysiu :D
(i was trying to do this, but couldn't find anything that would do it for me, until i somehow found this thread :D)

it's a bit confusing to try and figure out how to open as a delimited text file....but once you know how to, it's easy....

To open as a delimited text file, just choose Text CSV as the file type (like in the attached screenshot)

and then when the dialog comes up, choose "fixed width" and manually choose where each column goes (just do it so the package names have their own column (another screenshot attached)

and so you end up with a single column for all the package names :D (last screenshot)

:D

---

### Post by dannyboy79 on 2007-02-23
how do you do step 6? could some1 explain? so once I copy column 1 with all the package names and paste them into a new gedit file, what will it look like then, can you do a screen shot again? thanx for any help

---

### Post by aysiu on 2007-02-23
Apparently [someone has an easier way to do this](http://www.ubuntuforums.org/showthread.php?p=1069593#post1069593). It may be worth checking out.

---

### Post by delfick on 2007-02-23
> **aysiu said:**
> Apparently [someone has an easier way to do this](http://www.ubuntuforums.org/showthread.php?p=1069593#post1069593). It may be worth checking out.

wow :D much easier :D :D

(for dannyboy79, to find carriage returns, search for "\n" (without quotation marks) :D)

---

