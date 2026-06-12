---
title: "problem with gcc compiler"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by alwar.sumit on 2008-01-19
hi all!
i've installed ubuntu gusty frm a DVD. GCC compiler for 'C' is already installed but when i compile a 'C' program then a error occured:

sumit@sam:~$ gcc sumit.c
sumit.c:1:19: error: stdio.h: No such file or directory
sumit.c: In function ‘main’:
sumit.c:4: warning: incompatible implicit declaration of built-in function ‘printf’
sumit.c:3: warning: return type of ‘main’ is not ‘int’

what should i do to overcome this problem.

---

### Post by lian1238 on 2008-01-19
Try this:
```
sudo apt-get install build-essential

```

---

### Post by Partyboi2 on 2008-01-19
Try installing  build-essential
```
sudo aptitude install build-essential
```

---

### Post by Partyboi2 on 2008-01-19
Beaten to the post :lolflag:

---

### Post by alwar.sumit on 2008-01-19
thanks for ur help but when i tried this command i get hte following:

sumit@sam:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  emacs22-common emacsen-common libartsc0 
The following NEW packages will be automatically installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch 
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch 
0 packages upgraded, 8 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B/7934kB of archives. After unpacking 26.9MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 90769 files and directories currently installed.)
Removing emacs22-common ...
Removing emacsen-common ...
emacsen-common: Handling removal of emacsen flavor emacs
Removing libartsc0 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
E: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb: Hash Sum mismatch
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done 

i'm not getting what i've to do........plz help

---

### Post by Partyboi2 on 2008-01-19
Go to software sources (System>Admin>Software Sources)
on the 2nd tab (3rd party) untick the cdrom  and on the first tab make sure all the boxes are ticked except source code
then close and try again
 
Edit: from what is displayed above build-essential is installed so try gcc again, unticking the cd rom will stop the fail to fetch message
sudo apt-get install <package> installs packages (programs) from the ubuntu repo's

---

### Post by alwar.sumit on 2008-01-19
the problem persists..............in the software sources (2nd tab)(third party software)
there are only two websites which are marked. there is no cdrom option to tick OR untick...

---

### Post by alwar.sumit on 2008-01-19
there is a option in first tab with option of cdrom........i have un ticked it..........after that the following output is coming :

sumit@sam:~$ sudo aptitude install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "build-essential"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
sumit@sam:~$ 

the problem persists.............

---

### Post by Partyboi2 on 2008-01-19
Sorry for Gusty the cd rom it might be on the first tab, I can't remember

---

### Post by alwar.sumit on 2008-01-19
but the problem remains........please help me.........how can i install gcc compiler for 'C'

---

### Post by lian1238 on 2008-01-19
I think, all you need to do is install build-essential.
But somehow, you've unticked a software source. Go back to Software Sources. Then make sure you've checked All the sources under Downloadable from the internet. Close it. When it asks you to Reload, do it. Now try to install build-essential again.

Edit: leave "source code" as it is.

---

