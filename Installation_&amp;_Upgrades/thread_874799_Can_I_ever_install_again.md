---
title: "Can I ever install again?"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by PCessna on 2008-07-30
I installed LimeWire, Latest from LimeWire.com, I accidentally logged out, and nothing will install, even system stuff now. It just says its lock, and it cant lock or cant unlock.

System asked for these commands along the way:

```
sudo dpkg --configure -a
```
```
apt-get -f install

```

When trying to install:
```

paul@paul-desktop:~$ sudo apt-get install avant-window-navigator
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


```
When system updates try to install:
A red (-) icon comes up in top right corner in system try "An error occrued, Please run Package manager from right-click menu or apt-get in terminal to see what is wrong. The error message was: ;Error : BrokenCount > 0' This usally means that your installed packages have unment dependencies 

When typing apt-get
```
paul@paul-desktop:~$ apt get
The program 'apt' can be found in the following packages:
 * sun-java6-jdk
 * sun-java5-jdk
 * openjdk-6-jdk
Try: sudo apt-get install <selected package>
bash: apt: command not found
paul@paul-desktop:~$ 
```


Please help.

---

### Post by randomnote1 on 2008-07-30
> paul@paul-desktop:~$ apt get

for apt-get, it looks like you fat fingered the command

> paul@paul-desktop:~$ sudo apt-get install avant-window-navigator
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

do an

ls /var/lib/dpkg/lock

if the lock file is there, remove that and try running apt-get again

rm /var/lib/dpkg/lock

---

### Post by PCessna on 2008-07-30
> **randomnote1 said:**
> for apt-get, it looks like you fat fingered the command



do an

ls /var/lib/dpkg/lock

if the lock file is there, remove that and try running apt-get again

rm /var/lib/dpkg/lock
```
paul@paul-desktop:~$ ls /var/lib/dkpg/lock
ls: cannot access /var/lib/dkpg/lock: No such file or directory
paul@paul-desktop:~$ ls /var/lib/dpkg/lock
/var/lib/dpkg/lock
paul@paul-desktop:~$ rm /var/lib/dpkg/lock
rm: remove write-protected regular empty file `/var/lib/dpkg/lock'? ^[[A^[[A^[[A
paul@paul-desktop:~$ sudo apt-get install avant-window-navigator
[sudo] password for paul: 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
paul@paul-desktop:~$ 
```

---

### Post by randomnote1 on 2008-07-30
that's the issue...the lock file is still there.  You'll probably need to be sudo to remove the lock file

sudo rm /var/lib/dpkg/lock

if that doesn't work I would recommend rebooting.

---

### Post by PCessna on 2008-07-30
> **randomnote1 said:**
> that's the issue...the lock file is still there.  You'll probably need to be sudo to remove the lock file

```
sudo rm /var/lib/dpkg/lock

if that doesn't work I would recommend rebooting.
paul@paul-desktop:~$ sudo rm /var/lib/dpkg/lock
paul@paul-desktop:~$ sudo apt-get install avant-window-navigator
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
paul@paul-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
paul@paul-desktop:~$ sudo dpkg --configure -a
paul@paul-desktop:~$ sudo apt-get install avant-window-navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  awn-manager libawn0 sun-java6-bin sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-fonts sun-java6-plugin ia32-sun-java6-plugin
  ttf-wqy-zenhei
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  avant-window-navigator awn-manager libawn0
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
paul@paul-desktop:~$ 
```

Now rebooting..

---

### Post by SunnyRabbiera on 2008-07-30
Yeh I have seen issues like this when apps hang when installing...
I had to reboot too to resolve it.

---

### Post by PCessna on 2008-07-30
> **SunnyRabbiera said:**
> Yeh I have seen issues like this when apps hang when installing...
I had to reboot too to resolve it.

Won't work, Sun Java is interfering with my system, and I cannot install anything without sun java asking me to agree to terms and locking up.. I want it out! I WANT TO INSTALL PROGRAMS.. Lord, Can anyone please help this D:.. Right after installer to avant starts working

Package configuration
```

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-bin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; 2.  License Grant. Subject to the terms and conditions of this            &#8593; 
 &#9474;     Agreement, as well as the restrictions and exceptions set forth in    &#9618; 
 &#9474;     the Software README file, Sun grants you a non-exclusive,             &#9646; 
 &#9474;     non-transferable, royalty-free limited license to reproduce and use   &#9618; 
 &#9474;     the Software internally, complete and unmodified, for the sole        &#9618; 
 &#9474;     purposes of running Programs and designing, developing and testing    &#9618; 
 &#9474;     Programs.  Sun also grants you a non-exclusive, non-transferable,     &#9618; 
 &#9474;     royalty-free limited license to reproduce and distribute the          &#9618; 
 &#9474;     Software, directly or indirectly through your licensees,              &#9618; 
 &#9474;     distributors, resellers, or OEMs, electronically or in physical       &#9618; 
 &#9474;     form or pre-installed with your Operating System on a general         &#9618; 
 &#9474;     purpose desktop computer or server, provided that: (a) the Software   &#9618; 
 &#9474;     and any proprietary legends or notices are complete and unmodified;   &#9618; 
 &#9474;     (b) the Software is distributed with your Operating System, and       &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               



```
Out of nowhere, Omg, What do I do?

and now it's all locked(same locks you said a reboot would fix)! What do I do?

---

### Post by PCessna on 2008-07-30
Now I get this
```
paul@paul-desktop:~$ sudo apt-get install avant-window-navigator
[sudo] password for paul: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
paul@paul-desktop:~$ 
```

Please help..................................................:mad:

When system updates a run, now
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

```
paul@paul-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
paul@paul-desktop:~$ sudo dpkg --configure -a
paul@paul-desktop:~$ 
paul@paul-desktop:~$ 

```
```
paul@paul-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
paul@paul-desktop:~$ sudo dpkg --configure -a
paul@paul-desktop:~$ 
paul@paul-desktop:~$ sudo apt-get install avant-window-navigator
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  awn-manager libawn0 sun-java6-bin sun-java6-jre
Suggested packages:
  binfmt-support sun-java6-fonts sun-java6-plugin ia32-sun-java6-plugin
  ttf-wqy-zenhei
Recommended packages:
  gsfonts-x11
The following NEW packages will be installed:
  avant-window-navigator awn-manager libawn0
The following packages will be upgraded:
  sun-java6-bin sun-java6-jre
2 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/30.7MB of archives.
After this operation, 88.5MB of additional disk space will be used.
Do you want to continue [Y/n]?
```
I need to know how to uninstall java sun. 
Then it seems that will return my system to normal.

Edit 5: System finally budged and installed java fine. now attempting to install avant

Edit 6: finally works :D
Thank you all for help, Now changing topic to SOLVED

---

### Post by randomnote1 on 2008-07-30
Excellent - glad it turned out to be relatively simple!

---

### Post by iacobus on 2008-08-03
!?  What do you mean your system "budged"?  I'm having the exact same problem, and there's been no "budge"ing about it.  How did you get the license agreement screen to go away?

.:iacobus:.


EDIT: aha! [http://ubuntuforums.org/showthread.php?t=416496](http://ubuntuforums.org/showthread.php?t=416496)   --- it's shift+tab!

---

### Post by colobix on 2008-08-03
OK so does anyone know how to solve this problem now? cox I do not.
I wish the ubuntu team could come up with a solution that makes problems like this easy to get rid of in the future. Like a way to delete files already in use or to restore the system to prev installed program or something like that.

---

