---
title: "Incomplete installation of linux-image-2.6.35-24-generic-pae (2.6.35-24.42)"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2010-12-20
I have just run the latest updates to 10.10. It includes  a kernel upgrade. My upgrade manager has frozen. What should I do?

Unfortunately I can not copy the Applying changes details. It had got as far as generating grub.cfg and then stopped.

---

### Post by sikander3786 on 2010-12-20
You can continue wait. Or if it has stuck there for a long period of time and you don't have any hopes, quit it. Logout and then log back in. Make sure you DON'T reboot under any circumstances.

Then from Applications > Accessories > Terminal:

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

Please post the complete output of all those commands and wrap them using proper code tags # from post menu.

---

### Post by Robbyx on 2010-12-20
For some time now I have not been able to use the GUI to close down, sleep, hybernate, or log out. Nothing happens although occasionally it does work if I have not been using the machine for long.

Currently I cannot logout using the panel widget. Do you know the command line that does the same thing?

---

### Post by sikander3786 on 2010-12-20
Ctrl + Alt + Del to bring up the dialog box for options ?

---

### Post by Robbyx on 2010-12-20
> **sikander3786 said:**
> Ctrl + Alt + Del to bring up the dialog box for options ?

Yes but it has no option to logout.

---

### Post by sikander3786 on 2010-12-20
Try Ctrl + Alt + F1

```
sudo service gdm stop
```

```
sudo service gdm start
```

---

### Post by Robbyx on 2010-12-20
When I logged in again there was a message:

System start required on login. It seemed to indicate from the messages that the kernel update had worked. I have not restarted it. 

Here are the results of your command line information requests:

```
rob@robin:~$ sudo apt-get install -f
[sudo] password for rob: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rob@robin:~$ 

```

```
rob@robin:~$ sudo dpkg --configure -a
dpkg: status database area is locked by another process

```

```
rob@robin:~$ sudo apt-get update && sudo apt-get upgrade
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by sikander3786 on 2010-12-20
The lock is there which should have disappeared with the logout/login. Anyhow, try these and post the outputs please.

```
sudo rm /var/lib/apt/lists/lock
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Robbyx on 2010-12-20
```
rob@robin:~$ sudo rm /var/lib/apt/lists/lock
[sudo] password for rob: 
rob@robin:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://archive.canonical.com maverick Release.gpg
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Hit http://gb.archive.ubuntu.com maverick Release.gpg                          
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB       
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]          
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB    
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB.UTF-8
Hit http://archive.canonical.com maverick Release                              
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB.UTF-8 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB.UTF-8
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB.UTF-8
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB.UTF-8
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB.UTF-8
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB.UTF-8
Get:2 http://dl.google.com testing Release.gpg [189B]                          
Ign http://ppa.launchpad.net/andrewsomething/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/andrewsomething/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/andrewsomething/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB   
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB.UTF-8
Hit http://packages.medibuntu.org maverick Release.gpg                         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Ign http://ppa.launchpad.net/shutter/ppa/ubuntu/ maverick/main Translation-en  
Ign http://ppa.launchpad.net/shutter/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/shutter/ppa/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/arzajac/ppa/ubuntu/ maverick/main Translation-en  
Ign http://ppa.launchpad.net/arzajac/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/arzajac/ppa/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://winff.org maverick Release.gpg                                      
Ign http://winff.org/ubuntu/ maverick/universe Translation-en                  
Get:3 http://gb.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB.UTF-8
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB.UTF-8
Ign http://dl.google.com/linux/deb/ testing/non-free Translation-en            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/pj-assis/ppa/ubuntu/ maverick/main Translation-en 
Ign http://ppa.launchpad.net/pj-assis/ppa/ubuntu/ maverick/main Translation-en_GB
Get:4 http://security.ubuntu.com maverick-security Release [27.2kB]            
Ign http://dl.google.com/linux/deb/ testing/non-free Translation-en_GB         
Hit http://repo.wuala.com stable Release.gpg                                   
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB.UTF-8
Ign http://winff.org/ubuntu/ maverick/universe Translation-en_GB               
Ign http://winff.org/ubuntu/ maverick/universe Translation-en_GB.UTF-8         
Hit http://winff.org maverick Release                                          
Ign http://dl.google.com/linux/deb/ testing/non-free Translation-en_GB.UTF-8   
Ign http://ppa.launchpad.net/pj-assis/ppa/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/amsn-daily/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/amsn-daily/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/amsn-daily/ppa/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://archive.canonical.com maverick/partner Sources                      
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB.UTF-8
Hit http://gb.archive.ubuntu.com maverick Release                              
Get:5 http://gb.archive.ubuntu.com maverick-updates Release [31.4kB]           
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/cavedon/ppa/ubuntu/ lucid/main Translation-en     
Ign http://packages.medibuntu.org/ maverick/free Translation-en                
Get:6 http://dl.google.com stable Release.gpg [189B]                           
Ign http://ppa.launchpad.net/cavedon/ppa/ubuntu/ lucid/main Translation-en_GB  
Ign http://ppa.launchpad.net/cavedon/ppa/ubuntu/ lucid/main Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://winff.org maverick/universe i386 Packages                           
Hit http://archive.canonical.com maverick/partner i386 Packages                
Ign http://ppa.launchpad.net/dtl131/ppa/ubuntu/ maverick/main Translation-en   
Ign http://ppa.launchpad.net/dtl131/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/dtl131/ppa/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://ppa.launchpad.net/rvm/libs/ubuntu/ karmic/main Translation-en       
Ign http://ppa.launchpad.net/rvm/libs/ubuntu/ karmic/main Translation-en_GB    
Get:7 http://security.ubuntu.com maverick-security/multiverse i386 Packages [1,655B]
Ign http://ppa.launchpad.net/rvm/libs/ubuntu/ karmic/main Translation-en_GB.UTF-8
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en             
Ign http://repo.wuala.com/ stable/main Translation-en                          
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_GB          
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_GB
Hit http://download.virtualbox.org maverick Release.gpg                        
Ign http://dl.google.com/linux/deb/ stable/non-free Translation-en_GB.UTF-8    
Ign http://packages.medibuntu.org/ maverick/free Translation-en_GB             
Hit http://gb.archive.ubuntu.com maverick/multiverse i386 Packages             
Hit http://gb.archive.ubuntu.com maverick/universe i386 Packages               
Hit http://gb.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://gb.archive.ubuntu.com maverick/restricted i386 Packages             
Get:8 http://security.ubuntu.com maverick-security/universe i386 Packages [21.4kB]
Get:9 http://dl.google.com testing Release [2,513B]                            
Ign http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/ maverick/main Translation-en_GB.UTF-8
Ign http://repo.wuala.com/ stable/main Translation-en_GB                       
Ign http://repo.wuala.com/ stable/main Translation-en_GB.UTF-8                 
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/rawstudio/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/rawstudio/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/rawstudio/ppa/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/ maverick/main Translation-en
Get:10 http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,522B]
Get:11 http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages [68.1kB]
Get:12 http://security.ubuntu.com maverick-security/main i386 Packages [54.2kB]
Ign http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/tldm217/tahutek.net/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net maverick Release.gpg                              
Get:13 http://dl.google.com stable Release [2,544B]                            
Hit http://repo.wuala.com stable Release                                       
Get:14 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en_GB
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en_GB.UTF-8
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_GB.UTF-8
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_GB
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ maverick/main Translation-en_GB.UTF-8
Ign http://packages.medibuntu.org/ maverick/free Translation-en_GB.UTF-8       
Get:15 http://dl.google.com testing/non-free i386 Packages [793B]              
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net maverick Release                                  
Get:16 http://gb.archive.ubuntu.com maverick-updates/main i386 Packages [187kB]
Hit http://ppa.launchpad.net karmic Release                                    
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://repo.wuala.com stable/main i386 Packages                            
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Get:17 http://dl.google.com stable/non-free i386 Packages [1,010B]             
Hit http://ppa.launchpad.net maverick/main Sources                             
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en            
Ign http://repo.wuala.com stable/main i386 Packages                            
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://download.virtualbox.org maverick Release                            
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net lucid/main i386 Packages                          
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://repo.wuala.com stable/main i386 Packages                            
Hit http://ppa.launchpad.net karmic/main i386 Packages                         
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main i386 Packages                     
Hit http://ppa.launchpad.net maverick/main Sources                           
Hit http://ppa.launchpad.net maverick/main i386 Packages                     
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_GB         
Hit http://ppa.launchpad.net maverick/main i386 Packages                     
Ign http://packages.medibuntu.org/ maverick/non-free Translation-en_GB.UTF-8   
Get:18 http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Hit http://download.virtualbox.org maverick/non-free i386 Packages             
Hit http://packages.medibuntu.org maverick Release                             
Hit http://packages.medibuntu.org maverick/non-free i386 Packages              
Hit http://packages.medibuntu.org maverick/free i386 Packages
Fetched 402kB in 0s (429kB/s)
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rob@robin:~$ 

```

---

### Post by sikander3786 on 2010-12-20
```
sudo rm /var/lib/dpkg/lock
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

If those commands don't return an error, it means that there are no problems with the Linux image on your PC.

---

### Post by Robbyx on 2010-12-20
```
rob@robin:~$ sudo rm /var/lib/dpkg/lock
rob@robin:~$ sudo apt-get install -f
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
rob@robin:~$ sudo dpkg --configure -a
Setting up linux-libc-dev (2.6.35-1024.42) ...
Setting up acroread (9.4.1-1maverick1) ...
No LSB modules are available.
No LSB modules are available.
Setting up linux-image-2.6.35-24-generic-pae (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic-pae
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic-pae /boot/vmlinuz-2.6.35-24-generic-pae
 * dkms: running auto installation service for kernel 2.6.35-24-generic-pae                                                                                     
 *       vboxhost (3.2.12)...                                            [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic-pae /boot/vmlinuz-2.6.35-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic-pae /boot/vmlinuz-2.6.35-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-24-generic-pae /boot/vmlinuz-2.6.35-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-24-generic-pae /boot/vmlinuz-2.6.35-24-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-24-generic-pae /boot/vmlinuz-2.6.35-24-generic-pae
Generating grub.cfg ...

```

It does not go further than this point and hangs. Same as with the original attempt at the update.

---

### Post by sikander3786 on 2010-12-20
How much RAM has your PC got actually? If less than 3 GB, PAE Kernel installation might fail I think.

---

### Post by Robbyx on 2010-12-20
> **sikander3786 said:**
> How much RAM has your PC got actually? If less than 3 GB, PAE Kernel installation might fail I think.

System monitor says memory is 3.9gib with linux kernel 2.6.35-23-generic-pae.

---

### Post by sikander3786 on 2010-12-21
> **Robbyx said:**
> System monitor says memory is 3.9gib with linux kernel 2.6.35-23-generic-pae.
Ok. So what is happening now? Is it still stuck at generating Grub.cfg? Or any progress? Did you reboot?

---

### Post by Robbyx on 2010-12-21
> **sikander3786 said:**
> Ok. So what is happening now? Is it still stuck at generating Grub.cfg? Or any progress? Did you reboot?

I closed the terminal as it remained stuck at generating grub.cfg. No progress. I did not reboot until you told me it was safe.

---

### Post by sikander3786 on 2010-12-21
Run this command.

```
sudo update-grub
```

Does it successfully generate grub.cfg?

And also, post the output of bootinfoscript as per instructions here in order to let us see any possible reasons behind grub.cfg failure.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by Robbyx on 2010-12-21
> **sikander3786 said:**
> Run this command.

```
sudo update-grub
```

Does it successfully generate grub.cfg?

And also, post the output of bootinfoscript as per instructions here in order to let us see any possible reasons behind grub.cfg failure.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

It hangs when I try to generate the grub.

Same problem when I run the boot_info script and in this case the results file does not get created. I have tried running it from the desktop and from another drive.I also changed its properties so that it was executable on the other drive.

---

### Post by dino99 on 2010-12-21
so follow step by step:


clean the cache: sudo rm /var/cache/apt/archives/*

open synaptic and uncheck third parties if any, then update

remove/purge then reinstall 2.6.35.24-generic-pae (headers & image)

report here if troubles

---

### Post by Robbyx on 2010-12-21
When I go into synaptic I get the following error message:

> Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running.  Please close that application first.

I have htop and can not see an application that contains "apt" in it, on a search.

I have not cleaned the cache yet.

---

### Post by Robbyx on 2010-12-21
I ended up rebooting, not because I wanted to but I could not get out of a man help sheet in terminal when I had dropped out of the GDM. I did a CTRL ALT DEL and it rebooted. Fortunately it restarted and allowed me boot into Ubuntu so all is well. I was able to do a sudo dpkg --configure -a and  I have the latest kernel installed. What a relief. Thank you for your help.

---

