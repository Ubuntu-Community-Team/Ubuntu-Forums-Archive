---
title: "Why is ?? not upgraded"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-14
Is there a way to find out why a package is not being upgraded (in general?)

In this particular case konsole is 'not upgraded' on a sudo apt-get upgrade

---

### Post by ShirishAg75 on 2009-01-14
LordVevois, 
 That usually happens due to dependancy resolution meaning of the dependent packages also need an upgrade and they are not upgraded .. yet. 

What I would suggest is you try 

```
 sudo aptitude safe-upgrade 
```

and 

```
 sudo aptitude full-upgrade 
```

The full-upgrade would show what packages need to be upgraded in order to konsole to be upgraded without an issue.

---

### Post by LordVeovis on 2009-01-14
```

sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  konsole
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 843kB of archives. After unpacking 4096B will be used.
The following packages have unmet dependencies:
  konsole: Depends: kdebase-runtime (>= 4:4.1.96) but 4:4.1.85-0ubuntu2 is installed.
The following actions will resolve these dependencies:

Remove the following packages:
konsole

Score is 119

Accept this solution? [Y/n/q/?]
```

So why does it want me to remove konsole?  Does this mean that kdebase-runtime needs upgraded first? and how would I know when that ould be done? (this is my first alpha) :P

---

### Post by ShirishAg75 on 2009-01-14
you would just need to be patient. As you rightly observed, kde-base runtime needs to be upgraded to 4:4.1.96 or higher for konsole to be upgraded. So my suggestion is for you to sit tight and just do safe-upgrades . At some point kdebase-runtime would get upgraded again and then you would be able to upgrade to the newer konsole.

---

