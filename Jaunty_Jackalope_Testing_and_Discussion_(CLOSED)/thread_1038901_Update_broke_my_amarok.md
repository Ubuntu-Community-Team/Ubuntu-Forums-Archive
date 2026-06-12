---
title: "Update broke my amarok"
date: 2009-01-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2009-01-14
In this update I saw amarok-common and amarok was uninstalled.  After reboot amarok was still gone (thought amarok-common was replacing that) and I cannot install amarok again.

```

amarok:
  Depends: amarok-common (=2:2.0.1.1-0ubuntu2) but 2:2.0.1.1-0ubuntu3 is to be installed
 Recommends: kdemultimedia-kio-plugins but it is not going to be installed

```

---

### Post by Vorian on 2009-01-14
What arch are you running?

Also, there was a mysql transition which affects any new installation of amarok
[https://bugs.edge.launchpad.net/ubuntu/+source/amarok/+bug/316957](https://bugs.edge.launchpad.net/ubuntu/+source/amarok/+bug/316957)

We should have a new revision out soon

---

### Post by LordVeovis on 2009-01-14
> **Vorian said:**
> What arch are you running?

Also, there was a mysql transition which affects any new installation of amarok
[https://bugs.edge.launchpad.net/ubuntu/+source/amarok/+bug/316957](https://bugs.edge.launchpad.net/ubuntu/+source/amarok/+bug/316957)

We should have a new revision out soon

I am running Ubuntu Jaunty alpha2 x86_64

---

### Post by Vorian on 2009-01-14
> **LordVeovis said:**
> I am running Ubuntu Jaunty alpha2 x86_64Hopefully we'll have a fix by the end of the day.

---

### Post by LordVeovis on 2009-01-14
THANKS!!! I missed not having that last night, I had to use Rhythmbox

---

### Post by LordVeovis on 2009-01-15
Still have problems.  Now they are with mysql
```

@ubuntu:~$ sudo aptitude install amarok
Reading package lists... Done                    
Building dependency tree                         
Reading state information... Done                
Reading extended state information               
Initializing package states... Done              
Writing extended state information... Done       
The following packages will be REMOVED:          
  amarok-mysql-data{u}                           
The following partially installed packages will be configured:
  amarok mysql-server-5.1                                     
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2458kB will be freed.      
Do you want to continue? [Y/n/?] y                                     
Writing extended state information... Done                             
(Reading database ... 170671 files and directories currently installed.)
Removing amarok-mysql-data ...                                          
Setting up mysql-server-5.1 (5.1.30-2ubuntu3) ...                       
 * Stopping MySQL database server mysqld                                                                   [ OK ] 
 * Starting MySQL database server mysqld                                                                   [fail] 
invoke-rc.d: initscript mysql, action "start" failed.                                                             
dpkg: error processing mysql-server-5.1 (--configure):                                                            
 subprocess post-installation script returned error exit status 1                                                 
dpkg: dependency problems prevent configuration of amarok:                                                        
 amarok depends on mysql-server-5.1 (>= 5.1.30-2ubuntu3); however:                                                
  Package mysql-server-5.1 is not configured yet.                                                                 
dpkg: error processing amarok (--configure):                                                                      
 dependency problems - leaving unconfigured                                                                       
No apport report written because the error message indicates its a followup error from a previous failure.        
                                                                                                          Errors were encountered while processing:                                                                                 
 mysql-server-5.1                                                                                                 
 amarok                                                                                                           
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                           
A package failed to install.  Trying to recover:                                                                  
Setting up mysql-server-5.1 (5.1.30-2ubuntu3) ...                                                                 
 * Stopping MySQL database server mysqld                                                                   [ OK ] 
 * Starting MySQL database server mysqld                                                                   [fail] 
invoke-rc.d: initscript mysql, action "start" failed.                                                             
dpkg: error processing mysql-server-5.1 (--configure):                                                            
 subprocess post-installation script returned error exit status 1                                                 
dpkg: dependency problems prevent configuration of amarok:                                                        
 amarok depends on mysql-server-5.1 (>= 5.1.30-2ubuntu3); however:                                                
  Package mysql-server-5.1 is not configured yet.                                                                 
dpkg: error processing amarok (--configure):                                                                      
 dependency problems - leaving unconfigured                                                                       
Errors were encountered while processing:                                                                         
 mysql-server-5.1                                                                                                 
 amarok                                                                                                           
Reading package lists... Done                                                                                     
Building dependency tree                                                                                          
Reading state information... Done                                                                                 
Reading extended state information                                                                                
Initializing package states... Done                                                                               
Writing extended state information... Done

```

---

### Post by LordVeovis on 2009-01-16
Ok, I fixed the mysql problem and I installed amarok, but I cannot run it.  It will crash immediately after.

---

### Post by LordVeovis on 2009-01-16
restarted again and it worked this time...

---

### Post by super.rad on 2009-01-21
how did you fix it as I'm still having the same problems?

---

### Post by inportb on 2009-01-22
You might want to have a look at launchpad.

---

