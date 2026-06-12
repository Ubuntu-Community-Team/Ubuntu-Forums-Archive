---
title: "[SOLVED] Update Manager logs"
date: 2008-12-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-12-07
Normally I download the latest updates via the command line. If I download via Update Manager is there a log file which I can look at in case of problems ?

---

### Post by ShirishAg75 on 2008-12-07
from what I know /var/log/apt has a term.log I am assuming that even if you use update-manager it will record stuff at term.log.

---

### Post by Kevbert on 2008-12-07
Thanks for that. It seems you have to view the file by using
```
sudo gedit /var/log/apt/term.log
```
as otherwise it will complain that I don't have permissions to open it!

---

### Post by ShirishAg75 on 2008-12-07
You can also do 

```
$ sudo cat /var/log/apt/term.log
```

and it will give the contents of the same on the terminal. One can grep (search) for some particular entry as well. An This is from Intrepid 

```

$ sudo cat /var/log/apt/term.log | grep linux
[sudo] password for shirish: 
Removing linux-generic ...
Preparing to replace linux-image-generic 2.6.27.7.11 (using .../linux-image-generic_2.6.27.10.13_i386.deb) ...
Unpacking replacement linux-image-generic ...
Setting up linux-image-generic (2.6.27.10.13) ...

```

---

### Post by autocrosser on 2008-12-07
Or  Menu>System>Administration>System Log & then File>Open>var>log>apt>term.log--That way whenever you want to look at the logs--they will be tracked by System Log

---

### Post by Kevbert on 2008-12-07
> **autocrosser said:**
> Or  Menu>System>Administration>System Log & then File>Open>var>log>apt>term.log--That way whenever you want to look at the logs--they will be tracked by System Log

Excellent idea. I've just tried this in 8.0.4.1 and get the attached screenshot:confused::confused::confused:

Just booted into Jaunty and it works fine there, so the option to add logs must have been introduced in Jaunty or Intrepid.

---

### Post by ShirishAg75 on 2008-12-07
That's a bug, I jut filed the same for ubuntu 8.10 as well [lpbug]_306021_[/lpbug] Kevbert if you want you can click on affects me too just above the bug and subscribe to the bug as well.

---

### Post by Kevbert on 2008-12-07
> **ShirishAg75 said:**
> That's a bug, I jut filed the same for ubuntu 8.10 as well [lpbug]_306021_[/lpbug] Kevbert if you want you can click on affects me too just above the bug and subscribe to the bug as well.

I'll add my two cents worth to the bug. Thanks.

Just found a similar problem a .gz file isn't a tar file...bug [[COLOR="Red"]306032[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/tar/+bug/306032")

---

### Post by ShirishAg75 on 2008-12-07
Kevbert, 
 dunno if tar is a good one for this . 

```

/var/log/apt$ sudo gzip -d term.log.1.gz

```

This one works. This one is used mainly for .tar files, for gzipped use gzip.

---

### Post by Kevbert on 2008-12-07
> **ShirishAg75 said:**
> Kevbert, 
 dunno if tar is a good one for this . 

```

/var/log/apt$ sudo gzip -d term.log.1.gz

```

This one works. This one is used mainly for .tar files, for gzipped use gzip.

Thanks again. That will resolve another post question. The bug report has been chucked out, my mistake of not reading between the lines on my crib sheet.

---

### Post by mavior on 2009-02-20
> **Kevbert said:**
> Normally I download the latest updates via the command line. If I download via Update Manager is there a log file which I can look at in case of problems ?

I would try with apt-log, here [http://mavior.eu/apt-log](http://mavior.eu/apt-log)

---

