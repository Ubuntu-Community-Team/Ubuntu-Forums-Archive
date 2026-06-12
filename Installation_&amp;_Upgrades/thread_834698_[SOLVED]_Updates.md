---
title: "[SOLVED] Updates"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by RMD94 on 2008-06-19
Hii

My problem is:
I can't install updates.... i get an error while trying to install the updates 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I didn't log into Ubuntu for almost a month and i have upto 121 updates. The Last time i logged into Ubuntu i had installed VirtualBox and i think i am having problems cuz i installed Virtual Box...

Please Help Me!!
- Rajas

---

### Post by wormser on 2008-06-19
Run the command

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

---

### Post by RMD94 on 2008-06-19
I am getting something 

Unable to find a precompiled module for the current kernel!              
                                                                           
Without a suitable kernel module you will never be able to start VMs. It  
is strongly recommended to compile a kernel module now. The kernel        
headers and the tools to build kernel modules (gcc, make, binutils, ...)  
are required. However, in case a suitable kernel module already exists   
at another place you might want to override the default position by       
setting KDIR=<full_path_to_vboxdrv_module> in /etc/default/virtualbox.    
The compilation can also be done later by executing                       
                                                                          
   /etc/init.d/vboxdrv setup                                                
                                                                          
as root.  

plz help me!!

---

### Post by wormser on 2008-06-19
> **RMD94 said:**
> dpkg: requested operation requires superuser privilege

That error is saying you are not an admin.  You need to run the command with a user that is an admin.  Then enter in that user's password.

---

### Post by avtolle on 2008-06-19
> **RMD94 said:**
> I forgot to tell u guys that i have already tried that b4 but it gives me an error:

dpkg: requested operation requires superuser privilege

plz hep me!!!!
```
sudo dpkg --configure -a
```as suggested earlier.

---

