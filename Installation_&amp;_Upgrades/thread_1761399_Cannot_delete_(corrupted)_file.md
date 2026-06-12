---
title: "Cannot delete (corrupted) file"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by Ub11 on 2011-05-18
Problem:  Cannot delete file  

System:  Ubuntu 11.04 with KDE desktop

Symptoms:

When I try to start Synaptic, I get 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Running the requested command in terminal, I get 

ubuntu@ubuntu:/var/lib/dpkg/updates$ sudo dpkg --configure -a
dpkg: error: failed to open package info file `/var/lib/dpkg/updates/0001' for reading: No such file or directory

ubuntu@ubuntu:/var/lib/dpkg/updates$ ls -l
total 4
-rw-r--r-- 0 root root 835 2011-05-16 21:51 0001

ubuntu@ubuntu:/var/lib/dpkg/updates$ sudo rm 0001
rm: cannot remove `0001': No such file or directory

ubuntu@ubuntu:/var/lib/dpkg/updates$ file 0001
0001: regular file, no read permission
ubuntu@ubuntu:/var/lib/dpkg/updates$ sudo chmod a+r 0001
ubuntu@ubuntu:/var/lib/dpkg/updates$ ls -l
total 4
-rw-r--r-- 0 root root 835 2011-05-16 21:51 0001
ubuntu@ubuntu:/var/lib/dpkg/updates$ file 0001
0001: regular file, no read permission

ubuntu@ubuntu:/var/lib/dpkg/updates$ sudo rm 0001
rm: cannot remove `0001': No such file or directory


Please help to delete the problem:     /var/lib/dpkg/updates/0001

Also tried to move, copy and rename the file and also to delete the updates folder with rmdir.
Also tried   rm -i *   but it seems there is only the one file in the folder.
The only strange result is the  "total 4" when I run the ls -l command: What does this mean? 

Please help, I am on the verge of a re-install.

---

### Post by jerrrys on 2011-05-18
have you tried
**sudo apt-get update**
**[B]sudo apt-get upgrade**[/B]

---

### Post by Ub11 on 2011-05-18
> **jerrrys said:**
> have you tried
**sudo apt-get update**
**[B]sudo apt-get upgrade**[/B]

We have solved the problem based on advice from user fabricator4 in another thread on deleting files:


If you want the nautilus file manager method press <alt><F2>  and type in the box "gksu nautilus".  This will open the file manager  with root privileges.  This is dangerous, do NOT mess up, and do not  leave it open longer than necessary, and do not forget.  I suggest you  change the background to bright red as soon as you open it to remind  yourself:
Edit->Backgrounds and emblems-> then click the "colors" button  then drag "fire truck red" to the background of the file manager.  Now,  whenever you open file manage with root privileges it will be bright red  to remind you not to mess up and to close the file manager as soon as  you are finished with it.


Nautilus could not delete the file 0001, but it managed to delete the  updates  folder with file 0001 and anything else that might have been in there.

Afterwards, I just re-created the  updates  folder with the mkdir command.

Thanks to jerrys for his advice.

---

