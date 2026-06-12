---
title: "apt-get install mysecureshell"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by tmckeithan on 2012-01-26
I am trying to install mysecureshell. [http://mysecureshell.sourceforge.net/en/index.html](http://mysecureshell.sourceforge.net/en/index.html)
 
I have the package downloaded but I keep getting the following error when trying to install:
 
$ sudo apt-get install mysecureshell
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
mysecureshell: Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8.6 is to be installed
E: Broken packages
 
libssl0.9.8 is already installed. What do I need to go?
 
Thanks.

---

### Post by bluexrider on 2012-01-26
try forcing installation
```

sudo apt-get -f install mysecureshell
```

---

### Post by tmckeithan on 2012-01-26
Just tried that. Same result.

---

### Post by bluexrider on 2012-01-26
did you download the .DEB package, if so you should be able to install it by 'right clicking'

I did not see a compatibility list for anything other than this one distribution:


Ubuntu 10.10 
[LIST]
[*][Host 32bit]("http://mysecureshell.free.fr/repository/index.php/ubuntu/pool/main/m/mysecureshell/mysecureshell_1.25_i386.deb")
[*][Host 64bit]("http://mysecureshell.free.fr/repository/index.php/ubuntu/pool/main/m/mysecureshell/mysecureshell_1.25_amd64.deb")
[/LIST]

---

### Post by JRV on 2012-01-26
try:
```

sudo dpkg -i /FULL/PATH/TO/FILENAME.deb

```

---

### Post by tmckeithan on 2012-01-26
Thanks for the replies, but i'm still getting dependency problems.
 
$ sudo dpkg -i mysecureshell_1.25_i386.deb 
Selecting previously deselected package mysecureshell.
(Reading database ... 51339 files and directories currently installed.)
Unpacking mysecureshell (from mysecureshell_1.25_i386.deb) ...
dpkg: dependency problems prevent configuration of mysecureshell:
 mysecureshell depends on libssl0.9.8 (>= 0.9.8m-1); however:
  Version of libssl0.9.8 on system is 0.9.8k-7ubuntu8.6.
dpkg: error processing mysecureshell (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Errors were encountered while processing:
 mysecureshell

---

### Post by Old_Grey_Wolf on 2012-01-26
Have you tried adding the PPA to sources.list? Instructions for Ubuntu at [http://mysecureshell.sourceforge.net/en/installpak.html#question2](http://mysecureshell.sourceforge.net/en/installpak.html#question2).

---

### Post by bluexrider on 2012-01-26
> **Old_Gray_Wolf said:**
> Have you tried adding the PPA to sources.list? Instructions for Ubuntu at [http://mysecureshell.sourceforge.net/en/installpak.html#question2](http://mysecureshell.sourceforge.net/en/installpak.html#question2).


I think the OP has that. Has downloaded the package but had an install problem with dependencies.  

The thing I would recommend would be to run this:
```

sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```If you have a problem along this line with a broken package the first thing to try is, as root;
     Code:
     ```
dpkg --configure -a
```

---

### Post by Old_Grey_Wolf on 2012-01-27
I searched for the error and found a few recent posts on other forums; however, no solutions were provided yet. It could be a temporary problem with the PPA.

---

### Post by tmckeithan on 2012-01-27
thanks. just tried and had same results. i just saw this post on the mysecureshell forum. i also have ubuntu 10.04.3 LTS.
 
[http://mysecureshell.free.fr/forum/viewtopic.php?id=259](http://mysecureshell.free.fr/forum/viewtopic.php?id=259)
 
going to try from source code.
 
thanks to all. wish me luck.

---

### Post by tmckeithan on 2012-01-27
downloading the source and compiling did the trick.

---

### Post by bluexrider on 2012-01-31
Glad you got things handled. Please mark this
(SOLVED)

---

