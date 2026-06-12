---
title: "do-release-upgrade (i368 system - Gnome) 12.04 -&gt; 12.10"
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by amlost on 2013-03-20
Most likely, I might be posting this in the wrong section. If so please do excuse me as I barely ever ask for help, and I could not trace the exact same error I encountered. I am using Vaio which only has Ubuntu 12.04 (all pre-installed Microsoft is deleted).
I found indeed that the settings were only to report LTS upgrades, which I changed to all upgrades. After this I found that I was late in updating to 12.10
I did (after several failures of trying to get the upgrade) make sure that all 3rd party software was/is turned off.
However still I get an error "Application do-release-upgrade has closed unexpectedly" when clicking on the tab "more information" it only shows 'ExecutionPath' and underneath /usr/bin/do-release-upgrade.
Unfortunately after sending in this bug report, I have not been able to continue, as by clicking on continue all upgrade related parts shut down. I have thus not been able to retrace more error information, nor have I found a way to upgrade. 
I am curious as why the upgrade is so difficult, in comparison to what it used to be (been using since Heron Hardy, so a few years). Never had this kind of problem, and I am also nor a very technical person so I do not wish to change to another system as Ubuntu, unless it gets too complicated to solve this problem.


Amlost,

---

### Post by ibjsb4 on 2013-03-20
Do it in terminal and see what kind of errors you get.

```
sudo do-release-upgrade
```

---

### Post by amlost on 2013-03-26
Than I get the following report;

> 
root@myname-VPCEH3J1E:~# sudo do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1,198 kB]                                                  
Fetched 1,198 kB in 0s (0 B/s)                                                 
authenticate 'quantal.tar.gz' against 'quantal.tar.gz.gpg' 
extracting 'quantal.tar.gz'


Reading cache




A fatal error occurred 


Please report this as a bug and include the files 
/var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in 
your report. The upgrade has aborted. 
Your original sources.list was saved in 
/etc/apt/sources.list.distUpgrade. 


Traceback (most recent call last): 


File "/tmp/update-manager-PXY8hK/quantal", line 10, in <module> 
sys.exit(main()) 


File "/tmp/update-manager-PXY8hK/DistUpgrade/DistUpgradeMain.py", 
line 237, in main 
save_system_state(logdir) 


File "/tmp/update-manager-PXY8hK/DistUpgrade/DistUpgradeMain.py", 
line 130, in save_system_state 
scrub_sources=True) 


File "/tmp/update-manager-PXY8hK/DistUpgrade/apt_clone.py", line 148, 
in save_state 
self._write_state_sources_list(tar, scrub_sources) 


File "/tmp/update-manager-PXY8hK/DistUpgrade/apt_clone.py", line 235, 
in _write_state_sources_list 
"./etc/apt/sources.list.d/"+source) 


File "/tmp/update-manager-PXY8hK/DistUpgrade/apt_clone.py", line 239, 
in _add_file_to_tar_with_password_check 
with tempfile.NamedTemporaryFile(mode='w') as source_copy, 
open(sources, 'r') as f: 


IOError: [Errno 21] Is a directory: 
'/etc/apt/sources.list.d//eduke32' 




root@myname-VPCEH3J1E:~# 


---

### Post by schragge on 2013-03-26
It seems like */etc/apt/sources.list.d/eduke32* is a directory. There shouldn't be any directories under */etc/apt/sources.list.d/* Please post the output of
```
ls -l /etc/apt/sources.list.d/
```

---

### Post by amlost on 2013-05-13
After deleting all that was there, using MC, I got;

> 
root@xxx-VPCEH3J1E:~# root@xxx-VPCEH3J1E:~# ls -l /etc/apt/sources.list.d/
root@xxx-VPCEH3J1E:~#: command not found
root@xxx-VPCEH3J1E:~# total 28
The program 'total' is currently not installed.  You can install it by typing:
apt-get install radiance
root@xxx-VPCEH3J1E:~# drwxr-xr-x 2 root root 4096 Jul 31  2012 eduke32
drwxr-xr-x: command not found
root@xxx-VPCEH3J1E:~# -rw-r--r-- 1 root root   84 Mar 20 20:44 eduke32.list
-rw-r--r--: command not found
root@xxx-VPCEH3J1E:~# -rw-r--r-- 1 root root   84 Mar 20 20:44 eduke32.list.save
-rw-r--r--: command not found
root@xxx-VPCEH3J1E:~# -rw-r--r-- 1 root root  167 Mar 20 20:44 jitsi.list
-rw-r--r--: command not found
root@xxx-VPCEH3J1E:~# -rw-r--r-- 1 root root  165 Mar 20 20:44 jitsi.list.save
-rw-r--r--: command not found
root@xxx-VPCEH3J1E:~# -rw-r--r-- 1 root root  156 Mar 20 20:44 me-davidsansome-clementine-precise.list
-rw-r--r--: command not found
root@xxx-VPCEH3J1E:~# -rw-r--r-- 1 root root  156 Mar 20 20:44 me-davidsansome-clementine-precise.list.save
-rw-r--r--: command not found


---

### Post by amlost on 2013-05-13
Did an uninstall of Jitsi and Clementine. Through the software center.

---

### Post by schragge on 2013-05-13
Try ```
rm -r /etc/apt/sources.list.d/eduke32/
```

---

