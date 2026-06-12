---
title: "Problems installing aMSN"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by RichardSpence on 2008-10-04
Hey... first time using Ubuntu and having problems setting up aMSN. Could someone please provide a step by step guide? Will be greatly appreciated.

---

### Post by Partyboi2 on 2008-10-04
open a terminal (Applications>Accessories>Terminal and install with
```
sudo apt-get install amsn
``` Or go to add/remove (Applications>Add/Remove and search for amsn and install. Then when it has been installed you can launch it from Applications>Internet>amsn.

---

### Post by SuperSonic4 on 2008-10-04
The Repos version doesn't work, M$ changed the server and the repo is yet to be updated as far as I know (0.97.2 is the latest version)

After doing the above:

```
sudo apt-get remove amsn
``` (but don't do autoremove)

Get the latest version of aMSN here: [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php) (click the second one, for tcl/tk 8.5). When that downloads (say to the desktop) type in the terminal

If you're lazy you should be able to get the package file directly by typing into a terminal: ```
wget -c 'http://prdownloads.sourceforge.net/amsn/amsn-0.97.2-1.tcl85.x86.package'
```

```
cd ~/Desktop
```
```
chmod +x amsn-0.97.2-1.tcl85.x86.package
```
```
./amsn-0.97.2-1.tcl85.x86.package
```

first code removes the repo version of amsn but not its dependencies
second code takes you to the desktop
third makes the package file executable
fourth executes it.

---

### Post by Sef on 2008-10-04
> The Repos version doesn't work, M$ changed the server and the repo is yet to be updated as far as I know (0.97.2 is the latest version)

That is not correct.  I have it (0.972) and it works.

---

### Post by stanz on 2008-10-06
too?> **Sef said:**
> That is not correct.  I have it (0.972) and it works.

 Would you please pass on which server your connecting

---

### Post by Sef on 2008-10-06
> too?     Quote:
                                                                      Originally Posted by **Sef**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=5908127#post5908127")                 
                 *That is not correct.  I have it (0.972) and it works.*
                                 
 Would you please pass on which server your connecting From Preferences > Connection:  Uses port 1863 - direct connection to the internet.  

Intrepid Ibex is my Ubuntu version.

RichardSpence: What Ubuntu version do you have?

---

