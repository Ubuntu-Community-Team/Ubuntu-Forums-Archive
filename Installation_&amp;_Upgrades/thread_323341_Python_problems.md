---
title: "Python problems"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by ceil on 2006-12-21
[IMG]http://www.nerblog.net/pkg.jpg[/IMG]

I attempted to install PyGlade and keep getting this error.  I try to downgrade Python and get a whole other slew of problems.  Please help ](*,)  The picture is me installing a dependency that also requires the same version of python.

---

### Post by po0f on 2006-12-22
ceil,

You shouldn't try to downgrade Python.  It will break your system most likely.

Are you using 6.06?  [python-glade2](http://packages.ubuntu.com/dapper/python/python-glade2) and [python-glade-1.2](http://packages.ubuntu.com/dapper/python/python-glade-1.2) are both in the repos.  Install them through apt-get/aptitude:
```
[FONT="Courier New"]$ sudo aptitude update && sudo aptitude install python-glade-1.2[/FONT]
```
Note that python-glade-1.2 resides in the universe repos.  You may have to enable them if you haven't already done so.

---

### Post by ceil on 2006-12-22
Thanks, but I do that and this happens.

> ceil@ceil-desktop:~$ sudo aptitude install python-glade-1.2
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  python-glade-1.2 python-gtk-1.2
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  python-glade-1.2: Depends: python (< 2.4) but 2.4.2-0ubuntu3 is installed.
  python-gtk-1.2: Depends: python (< 2.4) but 2.4.2-0ubuntu3 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
python-glade-1.2
python-gtk-1.2

I try and install glade2 and get this:

> ceil@ceil-desktop:~$ sudo aptitude install python-glade2
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  python2.4-glade2
The following NEW packages will be installed:
  python-glade2 python2.4-glade2
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/31.5kB of archives. After unpacking 164kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Media Change: Please insert the disc labeled 'Kubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807)' in the drive '/cdrom/' and press enter

aptitude: download_signal_log.cc:67: virtual bool download_signal_log::MediaChange(std::string, std::string): Assertion `rval != -1' failed.
Aborted

---

### Post by meng on 2006-12-22
Which version of Ubuntu are you using?
Did you enable the universe repositories?
How about "sudo aptitude remove ..." those packages and then reinstall them?

---

### Post by ceil on 2006-12-22
> **meng said:**
> Which version of Ubuntu are you using?
Did you enable the universe repositories?
How about "sudo aptitude remove ..." those packages and then reinstall them?

1.  Dapper Drake
2.  Yes
3.  Tried it

](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by meng on 2006-12-22
I suggest you disable the CD-ROM in your sources.list

---

### Post by ceil on 2006-12-22
How would I go about doing that? =x

---

### Post by meng on 2006-12-22
sudo nano /etc/apt/sources.list
(put a # in front of the line with the cd-rom in it, probably the top line or very near the top)
save

sudo aptitude update
sudo aptitude ... (etc)

---

### Post by ceil on 2006-12-22
Thanks a lot, it's working fine now :)

---

