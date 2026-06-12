---
title: "[SOLVED] Possible Broken Package : python-gnome2-extras"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by c1rcu17 on 2008-09-26
I am trying to install miro using their repository, 

```
http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu hardy/
```

and I am getting installation errors. It seems that miro has dependencies that are having problems being installed.
```
******@************:~$ sudo apt-get install miro
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  miro: Depends: libffi4 but it is not installable
        Depends: python-gnome2-extras (>= 2.14.0-2) but it is not going to be installed
E: Broken packages
```

Apparently libgdl-gnome-1-0 and python-gnome2-extras are broken packages. Or at least thats what I think is going on. I can manually install libffi4, but when I try to install python-gnome2-extras I get,

```
*****@*********:~$ sudo aptitude install python-gnome2-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  libgdl-gnome-1-0 
The following NEW packages will be installed:
  libgda3-3{a} libgda3-bin{a} libgda3-common{a} libgdl-1-0{a} libgdl-1-common{a} 
  python-gnome2-extras 
0 packages upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 112kB/1102kB of archives. After unpacking 9015kB will be used.
The following packages have unmet dependencies:
  libgdl-gnome-1-0: Depends: libgdl-1-common (= 0.7.11-1) but 2.24.0-1 is to be installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
libgdl-gnome-1-0 [Not Installed]
python-gnome2-extras [Not Installed]

Score is -9872

Accept this solution? [Y/n/q/?] 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
```

I have a feeling that these packages aren't installable because they aren't ready for II yet. Any ideas?

---

### Post by klange on 2008-09-26
libgdl-gnome-1-0 is the problem, not so much the python-gnome2-extras package.

---

### Post by dro0g on 2008-09-26
> **WindowsSucks said:**
> libgdl-gnome-1-0 is the problem, not so much the python-gnome2-extras package.

It's been fixed, just waiting on the builds at this point:
[https://bugs.launchpad.net/ubuntu/+source/gnome-python-extras/+bug/274398](https://bugs.launchpad.net/ubuntu/+source/gnome-python-extras/+bug/274398)

---

