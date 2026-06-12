---
title: "Edgy Can't remove havp module using synaptic"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by mmarinho on 2006-11-15
No mater what I do I cannot remove havp. It was installed using synaptic but now I can't remove it. Even from the shell. Always get the same error:

E: havp: subprocess pre-removal script returned error exit status 1

Also see attached screen shot with the output of the synaptic uninstall.

-Manny

---

### Post by ToulCit on 2006-12-06
i get the exact same error ...
and i have tried the command chown too , and multiple package managers , but i didn't try aptitude yet.

---

### Post by ToulCit on 2006-12-06
no luck there ..

---

### Post by ToulCit on 2006-12-07
i only got this error :

"toulcit@toulcit-desktop:~$ sudo su
root@toulcit-desktop:/home/toulcit# apt-get remove havp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  havp
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  havp
0 upgraded, 0 newly installed, 1 to remove and 26 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 811kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 96293 files and directories currently installed.)
Removing havp ...
Stopping havp: invoke-rc.d: initscript havp, action "stop" failed.
dpkg: error processing havp (--remove):
 subprocess pre-removal script returned error exit status 1
Starting havp: Starting HAVP Version: 0.79
Could not open lock testfile /var/run/havp/havp-yeRizb: No such file or directory
Maybe you need to: chown havp /var/run/havp
Exiting..
Exiting..
invoke-rc.d: initscript havp, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 havp
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@toulcit-desktop:/home/toulcit# "

I hope there is someone to help me , because now thanks to this error i can't install or delete things naymore using synaptic , or dpkg or whatever.

---

### Post by bapoumba on 2006-12-07
> **ToulCit said:**
> 
Could not open lock testfile /var/run/havp/havp-yeRizb: No such file or directory
Maybe you need to: chown havp /var/run/havp


Hi, both errors look the same about that file. Just a guess ;)

---

### Post by orionsbelt on 2007-02-22
i had the same problem, which i fixed using instructions from [here]("http://www.ubuntuforums.org/showthread.php?p=2194342#post2194342") (make sure you read all the way through, because some things got changed along the way).

hope this helps!

also, if you're having trouble removing clamav (the antivirus application which depends upon hvap), then you can follow instructions [here]("http://www.getautomatix.com/forum/lofiversion/index.php?t695.html").  i just don't know how to get it working again.  someone said that it's been fixed, but it doesn't seem like it has to me.

---

### Post by vadania on 2007-05-07
I had this problem too!
The link from **orionsbelt** was very helpful.

It seems that one has to sudo create the dir */var/run/havp* and the file */etc/init.d/havp* and fill the file with someting (blank or space). I also did some *sudo chown havp /var/run/havp* and *sudo chgrp havp /var/run/havp*, not sure if this is really needed.

After this I guess one can use any package management program to remove havp - they all call dpkg, which actually does all the work.

---

