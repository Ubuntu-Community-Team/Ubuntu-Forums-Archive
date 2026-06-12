---
title: "Problem updating to  linux-image-3.2.0-26-generic"
date: 2012-07-04
forum: Installation &amp; Upgrades
---

### Post by Megaptera on 2012-07-04
I've run update manager and 'cos of the error below I ran terminal to update && upgrade just in case.

However I get the following error message. I've a fairly standard Xubuntu 12.04 (no major alterations/tweaks)

Can anyone help sort it out please? Nothing on my Google searches seems relevant, so help welcome.

```
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-26-generic; however:
  Package linux-image-3.2.0-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 linux-image-3.2.0-26-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks

---

### Post by jmfal on 2012-07-04
You can try  rebooting into the recovery kernal and  run>>>dpkg fix broken

and answer yes to the prompts and run the command at the prompt if you are asked to

```
  sudo dpkg --configure  -a     
```

---

### Post by dino99 on 2012-07-04
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install dkms
sudo apt-get install -f

---

### Post by Megaptera on 2012-07-04
Thanks for the replies!
Do I run jmfal's solution first, then try update and if that fails try dino99's solution - or do I run one after the other & then try update?

Thanks for clarifying!

---

### Post by jmfal on 2012-07-04
You can run them one at a time, and try Dino's first

---

### Post by Megaptera on 2012-07-04
:DMany thanks I'll get on with that now

---

### Post by Megaptera on 2012-07-04
> **dino99 said:**
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo apt-get update
sudo apt-get install dkms
sudo apt-get install -f

Tried that, unfortunately no further forward. 

Will now try jmfal's solution.

Results so far:```
richard@dell:~$ sudo apt-get clean
[sudo] password for richard: 
richard@dell:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
richard@dell:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-26-generic; however:
  Package linux-image-3.2.0-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 linux-image-3.2.0-26-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@dell:~$ sudo apt-get update
Ign http://extras.ubuntu.com precise InRelease
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://security.ubuntu.com precise-security InRelease                      
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://extras.ubuntu.com precise/main Sources                              
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]  
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:3 http://security.ubuntu.com precise-security/main Sources [22.1 kB]       
Get:4 http://security.ubuntu.com precise-security/restricted Sources [14 B]    
Get:5 http://security.ubuntu.com precise-security/universe Sources [7,832 B]   
Get:6 http://security.ubuntu.com precise-security/multiverse Sources [713 B]   
Get:7 http://security.ubuntu.com precise-security/main amd64 Packages [67.1 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Ign http://ppa.launchpad.net precise/main Translation-en_GB                    
Get:8 http://security.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:9 http://security.ubuntu.com precise-security/universe amd64 Packages [18.6 kB]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en                       
Get:10 http://security.ubuntu.com precise-security/multiverse amd64 Packages [1,155 B]
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [69.5 kB]
Get:12 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [18.7 kB]
Get:14 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://gb.archive.ubuntu.com precise InRelease
Ign http://gb.archive.ubuntu.com precise-updates InRelease
Ign http://gb.archive.ubuntu.com precise-backports InRelease
Get:15 http://gb.archive.ubuntu.com precise Release.gpg [198 B]
Get:16 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:17 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]
Get:18 http://gb.archive.ubuntu.com precise Release [49.6 kB]
Get:19 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:20 http://gb.archive.ubuntu.com precise-backports Release [49.6 kB]
Get:21 http://gb.archive.ubuntu.com precise/main Sources [934 kB]
Get:22 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:23 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Get:24 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:25 http://gb.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]     
Get:26 http://gb.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:27 http://gb.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
Get:28 http://gb.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:29 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:30 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:31 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:32 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex             
Get:33 http://gb.archive.ubuntu.com precise-updates/main Sources [124 kB]      
Get:34 http://gb.archive.ubuntu.com precise-updates/main Sources [124 kB]      
Get:35 http://gb.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:36 http://gb.archive.ubuntu.com precise-updates/universe Sources [30.9 kB]
Get:37 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:38 http://gb.archive.ubuntu.com precise-updates/main amd64 Packages [310 kB]
Get:39 http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]
Get:40 http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages [85.2 kB]
Get:41 http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,829 B]
Get:42 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [313 kB]
Get:43 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:44 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [85.7 kB]
Get:45 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex
Get:46 http://gb.archive.ubuntu.com precise-backports/main Sources [1,845 B]
Get:47 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:48 http://gb.archive.ubuntu.com precise-backports/universe Sources [10.3 kB]
Get:49 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:50 http://gb.archive.ubuntu.com precise-backports/main amd64 Packages [1,271 B]
Get:51 http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:52 http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages [8,958 B]
Get:53 http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]
Get:54 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:55 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:56 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [8,940 B]
Get:57 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://gb.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB
Hit http://gb.archive.ubuntu.com precise/main Translation-en
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 19.9 MB in 5min 10s (64.1 kB/s)                                        
Reading package lists... Done
richard@dell:~$ sudo apt-get update
[sudo] password for richard: 
Ign http://extras.ubuntu.com precise InRelease
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release                                   
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://ppa.launchpad.net precise/main Sources                              
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security Release.gpg                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://security.ubuntu.com precise-security Release                        
Hit http://security.ubuntu.com precise-security/main Sources                   
Hit http://security.ubuntu.com precise-security/restricted Sources             
Hit http://security.ubuntu.com precise-security/universe Sources               
Hit http://security.ubuntu.com precise-security/multiverse Sources             
Hit http://security.ubuntu.com precise-security/main amd64 Packages            
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages      
Hit http://security.ubuntu.com precise-security/universe amd64 Packages        
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages      
Hit http://security.ubuntu.com precise-security/main i386 Packages             
Hit http://security.ubuntu.com precise-security/restricted i386 Packages       
Hit http://security.ubuntu.com precise-security/universe i386 Packages         
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages       
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://extras.ubuntu.com precise/main Translation-en_GB                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_GB    
Ign http://ppa.launchpad.net precise/main Translation-en       
Ign http://gb.archive.ubuntu.com precise InRelease
Ign http://gb.archive.ubuntu.com precise-updates InRelease
Ign http://gb.archive.ubuntu.com precise-backports InRelease
Get:1 http://gb.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:3 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]
Get:4 http://gb.archive.ubuntu.com precise Release [49.6 kB]
Get:5 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:6 http://gb.archive.ubuntu.com precise-backports Release [49.6 kB]
Get:7 http://gb.archive.ubuntu.com precise/main Sources [934 kB]
Get:8 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]
Get:9 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]
Get:10 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:11 http://gb.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]     
Get:12 http://gb.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:13 http://gb.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB] 
Get:14 http://gb.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:15 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:16 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:17 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:18 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://gb.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://gb.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://gb.archive.ubuntu.com precise/universe TranslationIndex             
Get:19 http://gb.archive.ubuntu.com precise-updates/main Sources [124 kB]      
Get:20 http://gb.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:21 http://gb.archive.ubuntu.com precise-updates/universe Sources [30.9 kB] 
Get:22 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:23 http://gb.archive.ubuntu.com precise-updates/main amd64 Packages [310 kB]
Get:24 http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages [2,417 B]
Get:25 http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages [85.2 kB]
Get:26 http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages [1,829 B]
Get:27 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [313 kB]
Get:28 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:29 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [85.7 kB]
Get:30 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Hit http://gb.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:31 http://gb.archive.ubuntu.com precise-backports/main Sources [1,845 B]   
Get:32 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:33 http://gb.archive.ubuntu.com precise-backports/universe Sources [10.3 kB]
Get:34 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:35 http://gb.archive.ubuntu.com precise-backports/main amd64 Packages [1,271 B]
Get:36 http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:37 http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages [8,958 B]
Get:38 http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages [996 B]
Get:39 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:40 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:41 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [8,940 B]
Get:42 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Get:43 http://gb.archive.ubuntu.com precise-backports/main TranslationIndex [71 B]
Get:44 http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex [71 B]
Get:45 http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:46 http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex [72 B]
Hit http://gb.archive.ubuntu.com precise/main Translation-en_GB                
Hit http://gb.archive.ubuntu.com precise/main Translation-en                   
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en_GB          
Hit http://gb.archive.ubuntu.com precise/restricted Translation-en             
Hit http://gb.archive.ubuntu.com precise/universe Translation-en_GB            
Hit http://gb.archive.ubuntu.com precise/universe Translation-en               
Hit http://gb.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://gb.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://gb.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://gb.archive.ubuntu.com precise-backports/universe Translation-en     
Fetched 19.6 MB in 17s (1,147 kB/s)                                            
Reading package lists... Done
richard@dell:~$ sudo apt-get install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
dkms is already the newest version.
dkms set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-26-generic; however:
  Package linux-image-3.2.0-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 linux-image-3.2.0-26-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@dell:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-26-generic; however:
  Package linux-image-3.2.0-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Errors were encountered while processing:
 linux-image-3.2.0-26-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@dell:~$ 

```

---

### Post by jmfal on 2012-07-04
Are you trying to compile a kernal??

---

### Post by dino99 on 2012-07-04
"  3 not fully installed "

so open synaptic to watch these broken packages first

---

### Post by matt_symes on 2012-07-04
Hi

Let's try to work through the problem.
[FONT=monospace]
[/FONT]> /usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected

Please post the output of
 
```
cat /etc/default/grub
```

Kind regards

---

### Post by Megaptera on 2012-07-04
> **jmfal said:**
> Are you trying to compile a kernal??

No - just trying to update.

---

### Post by matt_symes on 2012-07-04
Hi

@megaptera

^^^. Just wanted to make sure you did not miss my post.

Kind regard

---

### Post by Megaptera on 2012-07-04
> **matt_symes said:**
> Hi

Let's try to work through the problem.
[FONT=monospace]
[/FONT]

Please post the output of
 
```
cat /etc/default/grub
```

Kind regards

Thanks for your help.

Hopefully this is it ...

```
richard@dell:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1024x768-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
richard@dell:~$ 

```

---

### Post by Megaptera on 2012-07-04
> **matt_symes said:**
> Hi

@megaptera

^^^. Just wanted to make sure you did not miss my post.

Kind regard

Sorry, I was posting at same time. Might be away for a couple of hours but will check when I'm back on-line :D

---

### Post by matt_symes on 2012-07-04
Hi

Open a terminal and type

```
sudo nano /etc/default/grub
```Scroll down to the line that says
```

GRUB_GFXMODE=>>1024x768-24<<
```and comment it out as so
[FONT=monospace]
[/FONT]```
#GRUB_GFXMODE=>>1024x768-24<<
```Press ctrl + o to save the file and ctrl + x to exit nano.

Then type

```
sudo apt-get install -f
```Kind regards

---

### Post by bogan on 2012-07-04
Hi!, **matt_symes**,

Is not the line:```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap" 
```Also questionable??

? Better to try: ?? ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
# video=uvesafb:mode_option=\"1024x768x24\"mtrr=3,scroll=ywrap 
# Should there not be some spaces in that, anyway?

```Excuse me if I am showing my ignorance, trying to learn.

Chao!, **bogan.**

---

### Post by matt_symes on 2012-07-04
Hi

@bogan

Any kernel boot options not understood by the kernel are ignored by the kernel. It should also be the same with any well written modules.

Let's take this one step at a time and wait for the OP to post back with his current status. I've seen problems made worse by rushing these things.

Kind regards

---

### Post by Megaptera on 2012-07-04
Hi matt_symes,
I've followed your instructions at #15 above and obtained this - not sure what it means though!
Thanks again for helping ...

```
richard@dell:~$ sudo nano /etc/default/grub
[sudo] password for richard: 
richard@dell:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found memtest86+ image: /memtest86+.bin
error: syntax error.
error: Incorrect command.
error: syntax error.
error: line no: 106
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
done
Setting up linux-image-generic (3.2.0.26.28) ...
Setting up linux-generic (3.2.0.26.28) ...
richard@dell:~$ 

```

---

### Post by matt_symes on 2012-07-04
Hi

Well that is one error down. Let's take a look at all your grub files as your grub config is obviously corrupted.

I think i may be a good idea to go with bogan suggestion.

Some questions first though. 

Your default grub line contains these options. Did you add them and if you did, why did you add them ?
[FONT=monospace]
[/FONT]> video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrapAs at least one of the grub configuration files are corrupted so let's see exactly what you have got. 

Please post the output of

```
grep "^" /etc/default/grub /etc/grub.d/*
```Kind regards

---

### Post by Megaptera on 2012-07-04
Here's the output ....

```
/etc/grub.d/05_debian_theme:	fi
/etc/grub.d/05_debian_theme:done
/etc/grub.d/05_debian_theme:
/etc/grub.d/05_debian_theme:# Next try to use the background image and colors specified by desktop-base.
/etc/grub.d/05_debian_theme:if set_background_image "${WALLPAPER}" "${COLOR_NORMAL}" "${COLOR_HIGHLIGHT}"; then
/etc/grub.d/05_debian_theme:	exit 0
/etc/grub.d/05_debian_theme:fi
/etc/grub.d/05_debian_theme:
/etc/grub.d/05_debian_theme:# If we haven't found a background image yet, use the default from desktop-base.
/etc/grub.d/05_debian_theme:if set_background_image "/usr/share/images/desktop-base/desktop-grub.png"; then
/etc/grub.d/05_debian_theme:	exit 0
/etc/grub.d/05_debian_theme:fi
/etc/grub.d/05_debian_theme:
/etc/grub.d/05_debian_theme:# Finally, if all of the above fails, use the default theme.
/etc/grub.d/05_debian_theme:set_default_theme
/etc/grub.d/10_linux:#! /bin/sh
/etc/grub.d/10_linux:set -e
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:# grub-mkconfig helper script.
/etc/grub.d/10_linux:# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
/etc/grub.d/10_linux:#
/etc/grub.d/10_linux:# GRUB is free software: you can redistribute it and/or modify
/etc/grub.d/10_linux:# it under the terms of the GNU General Public License as published by
/etc/grub.d/10_linux:# the Free Software Foundation, either version 3 of the License, or
/etc/grub.d/10_linux:# (at your option) any later version.
/etc/grub.d/10_linux:#
/etc/grub.d/10_linux:# GRUB is distributed in the hope that it will be useful,
/etc/grub.d/10_linux:# but WITHOUT ANY WARRANTY; without even the implied warranty of
/etc/grub.d/10_linux:# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
/etc/grub.d/10_linux:# GNU General Public License for more details.
/etc/grub.d/10_linux:#
/etc/grub.d/10_linux:# You should have received a copy of the GNU General Public License
/etc/grub.d/10_linux:# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:prefix="/usr"
/etc/grub.d/10_linux:exec_prefix="${prefix}"
/etc/grub.d/10_linux:datarootdir="${prefix}/share"
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:. "${datarootdir}/grub/grub-mkconfig_lib"
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:export TEXTDOMAIN=grub
/etc/grub.d/10_linux:export TEXTDOMAINDIR="${datarootdir}/locale"
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:CLASS="--class gnu-linux --class gnu --class os"
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
/etc/grub.d/10_linux:  OS=GNU/Linux
/etc/grub.d/10_linux:else
/etc/grub.d/10_linux:  OS="${GRUB_DISTRIBUTOR}"
/etc/grub.d/10_linux:  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr 'A-Z' 'a-z' | cut -d' ' -f1) ${CLASS}"
/etc/grub.d/10_linux:fi
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:# loop-AES arranges things so that /dev/loop/X can be our root device, but
/etc/grub.d/10_linux:# the initrds that Linux uses don't like that.
/etc/grub.d/10_linux:case ${GRUB_DEVICE} in
/etc/grub.d/10_linux:  /dev/loop/*|/dev/loop[0-9])
/etc/grub.d/10_linux:    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
/etc/grub.d/10_linux:    # We can't cope with devices loop-mounted from files here.
/etc/grub.d/10_linux:    case ${GRUB_DEVICE} in
/etc/grub.d/10_linux:      /dev/*) ;;
/etc/grub.d/10_linux:      *) exit 0 ;;
/etc/grub.d/10_linux:    esac
/etc/grub.d/10_linux:  ;;
/etc/grub.d/10_linux:esac
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
/etc/grub.d/10_linux:    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
/etc/grub.d/10_linux:    || uses_abstraction "${GRUB_DEVICE}" lvm; then
/etc/grub.d/10_linux:  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
/etc/grub.d/10_linux:else
/etc/grub.d/10_linux:  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
/etc/grub.d/10_linux:fi
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:if [ "x`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2>/dev/null || true`" = xbtrfs ] \
/etc/grub.d/10_linux:    || [ "x`stat -f --printf=%T /`" = xbtrfs ]; then
/etc/grub.d/10_linux:  rootsubvol="`make_system_path_relative_to_its_root /`"
/etc/grub.d/10_linux:  rootsubvol="${rootsubvol#/}"
/etc/grub.d/10_linux:  if [ "x${rootsubvol}" != x ]; then
/etc/grub.d/10_linux:    GRUB_CMDLINE_LINUX="rootflags=subvol=${rootsubvol} ${GRUB_CMDLINE_LINUX}"
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:fi
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:for word in $GRUB_CMDLINE_LINUX_DEFAULT; do
/etc/grub.d/10_linux:  if [ "$word" = splash ]; then
/etc/grub.d/10_linux:    GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT \$vt_handoff"
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:done
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:# add crashkernel option if we have the required tools
/etc/grub.d/10_linux:if [ -x "/usr/bin/makedumpfile" ] && [ -x "/sbin/kexec" ]; then
/etc/grub.d/10_linux:    GRUB_CMDLINE_EXTRA="$GRUB_CMDLINE_EXTRA crashkernel=384M-2G:64M,2G-:128M"
/etc/grub.d/10_linux:fi
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:linux_entry ()
/etc/grub.d/10_linux:{
/etc/grub.d/10_linux:  os="$1"
/etc/grub.d/10_linux:  version="$2"
/etc/grub.d/10_linux:  recovery="$3"
/etc/grub.d/10_linux:  args="$4"
/etc/grub.d/10_linux:  if ${recovery} ; then
/etc/grub.d/10_linux:    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
/etc/grub.d/10_linux:  else
/etc/grub.d/10_linux:    title="$(gettext_quoted "%s, with Linux %s")"
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
/etc/grub.d/10_linux:  cat << EOF
/etc/grub.d/10_linux:	recordfail
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:  if ! ${recovery} ; then
/etc/grub.d/10_linux:      save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:      cat << EOF
/etc/grub.d/10_linux:	gfxmode \$linux_gfx_mode
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  cat << EOF
/etc/grub.d/10_linux:	insmod gzio
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  if [ x$dirname = x/ ]; then
/etc/grub.d/10_linux:    if [ -z "${prepare_root_cache}" ]; then
/etc/grub.d/10_linux:      prepare_root_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE} | sed -e "s/^/\t/")"
/etc/grub.d/10_linux:    fi
/etc/grub.d/10_linux:    printf '%s\n' "${prepare_root_cache}"
/etc/grub.d/10_linux:  else
/etc/grub.d/10_linux:    if [ -z "${prepare_boot_cache}" ]; then
/etc/grub.d/10_linux:      prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
/etc/grub.d/10_linux:    fi
/etc/grub.d/10_linux:    printf '%s\n' "${prepare_boot_cache}"
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:  if [ "x$5" != "xquiet" ]; then
/etc/grub.d/10_linux:    message="$(gettext_printf "Loading Linux %s ..." ${version})"
/etc/grub.d/10_linux:    cat << EOF
/etc/grub.d/10_linux:	echo	'$message'
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:  cat << EOF
/etc/grub.d/10_linux:	linux	${rel_dirname}/${basename} root=${linux_root_device_thisversion} ro ${args}
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:  if test -n "${initrd}" ; then
/etc/grub.d/10_linux:    if [ "x$5" != "xquiet" ]; then
/etc/grub.d/10_linux:      message="$(gettext_printf "Loading initial ramdisk ...")"
/etc/grub.d/10_linux:      cat << EOF
/etc/grub.d/10_linux:	echo	'$message'
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:    fi
/etc/grub.d/10_linux:    cat << EOF
/etc/grub.d/10_linux:	initrd	${rel_dirname}/${initrd}
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:  cat << EOF
/etc/grub.d/10_linux:}
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:}
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:case x`uname -m` in
/etc/grub.d/10_linux:    xi?86 | xx86_64)
/etc/grub.d/10_linux:	list=`for i in /boot/vmlinuz-* /vmlinuz-* /boot/kernel-* ; do
/etc/grub.d/10_linux:                  if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
/etc/grub.d/10_linux:              done` ;;
/etc/grub.d/10_linux:    *) 
/etc/grub.d/10_linux:	list=`for i in /boot/vmlinuz-* /boot/vmlinux-* /vmlinuz-* /vmlinux-* /boot/kernel-* ; do
/etc/grub.d/10_linux:                  if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
/etc/grub.d/10_linux:	     done` ;;
/etc/grub.d/10_linux:esac
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:prepare_boot_cache=
/etc/grub.d/10_linux:prepare_root_cache=
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:cat << 'EOF'
/etc/grub.d/10_linux:function gfxmode {
/etc/grub.d/10_linux:	set gfxpayload="${1}"
/etc/grub.d/10_linux:	if [ "${1}" = "keep" ]; then
/etc/grub.d/10_linux:		set vt_handoff=vt.handoff=7
/etc/grub.d/10_linux:	else
/etc/grub.d/10_linux:		set vt_handoff=
/etc/grub.d/10_linux:	fi
/etc/grub.d/10_linux:}
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:# Use ELILO's generic "efifb" when it's known to be available.
/etc/grub.d/10_linux:# FIXME: We need an interface to select vesafb in case efifb can't be used.
/etc/grub.d/10_linux:if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
/etc/grub.d/10_linux:  echo "set linux_gfx_mode=$GRUB_GFXPAYLOAD_LINUX"
/etc/grub.d/10_linux:else
/etc/grub.d/10_linux:  cat << EOF
/etc/grub.d/10_linux:if [ "\${recordfail}" != 1 ]; then
/etc/grub.d/10_linux:  if [ -e \${prefix}/gfxblacklist.txt ]; then
/etc/grub.d/10_linux:    if hwmatch \${prefix}/gfxblacklist.txt 3; then
/etc/grub.d/10_linux:      if [ \${match} = 0 ]; then
/etc/grub.d/10_linux:        set linux_gfx_mode=keep
/etc/grub.d/10_linux:      else
/etc/grub.d/10_linux:        set linux_gfx_mode=text
/etc/grub.d/10_linux:      fi
/etc/grub.d/10_linux:    else
/etc/grub.d/10_linux:      set linux_gfx_mode=text
/etc/grub.d/10_linux:    fi
/etc/grub.d/10_linux:  else
/etc/grub.d/10_linux:    set linux_gfx_mode=keep
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:else
/etc/grub.d/10_linux:  set linux_gfx_mode=text
/etc/grub.d/10_linux:fi
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:fi
/etc/grub.d/10_linux:cat << EOF
/etc/grub.d/10_linux:export linux_gfx_mode
/etc/grub.d/10_linux:if [ "\${linux_gfx_mode}" != "text" ]; then load_video; fi
/etc/grub.d/10_linux:EOF
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:in_submenu=false
/etc/grub.d/10_linux:while [ "x$list" != "x" ] ; do
/etc/grub.d/10_linux:  linux=`version_find_latest $list`
/etc/grub.d/10_linux:  echo "Found linux image: $linux" >&2
/etc/grub.d/10_linux:  basename=`basename $linux`
/etc/grub.d/10_linux:  dirname=`dirname $linux`
/etc/grub.d/10_linux:  rel_dirname=`make_system_path_relative_to_its_root $dirname`
/etc/grub.d/10_linux:  version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
/etc/grub.d/10_linux:  alt_version=`echo $version | sed -e "s,\.old$,,g"`
/etc/grub.d/10_linux:  linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  initrd=
/etc/grub.d/10_linux:  for i in "initrd.img-${version}" "initrd-${version}.img" \
/etc/grub.d/10_linux:	   "initrd-${version}" "initramfs-${version}.img" \
/etc/grub.d/10_linux:	   "initrd.img-${alt_version}" "initrd-${alt_version}.img" \
/etc/grub.d/10_linux:	   "initrd-${alt_version}" "initramfs-${alt_version}.img" \
/etc/grub.d/10_linux:	   "initramfs-genkernel-${version}" \
/etc/grub.d/10_linux:	   "initramfs-genkernel-${alt_version}"; do
/etc/grub.d/10_linux:    if test -e "${dirname}/${i}" ; then
/etc/grub.d/10_linux:      initrd="$i"
/etc/grub.d/10_linux:      break
/etc/grub.d/10_linux:    fi
/etc/grub.d/10_linux:  done
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  config=
/etc/grub.d/10_linux:  for i in "${dirname}/config-${version}" "${dirname}/config-${alt_version}" "/etc/kernels/kernel-config-${version}" ; do
/etc/grub.d/10_linux:    if test -e "${i}" ; then
/etc/grub.d/10_linux:      config="${i}"
/etc/grub.d/10_linux:      break
/etc/grub.d/10_linux:    fi
/etc/grub.d/10_linux:  done
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  initramfs=
/etc/grub.d/10_linux:  if test -n "${config}" ; then
/etc/grub.d/10_linux:      initramfs=`grep CONFIG_INITRAMFS_SOURCE= "${config}" | cut -f2 -d= | tr -d \"`
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  if test -n "${initrd}" ; then
/etc/grub.d/10_linux:    echo "Found initrd image: ${dirname}/${initrd}" >&2
/etc/grub.d/10_linux:  elif test -z "${initramfs}" ; then
/etc/grub.d/10_linux:    # "UUID=" magic is parsed by initrd or initramfs.  Since there's
/etc/grub.d/10_linux:    # no initrd or builtin initramfs, it can't work here.
/etc/grub.d/10_linux:    linux_root_device_thisversion=${GRUB_DEVICE}
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  linux_entry "${OS}" "${version}" false \
/etc/grub.d/10_linux:      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
/etc/grub.d/10_linux:      quiet
/etc/grub.d/10_linux:  if [ "x${GRUB_DISABLE_RECOVERY}" != "xtrue" ]; then
/etc/grub.d/10_linux:    if [ -x /lib/recovery-mode/recovery-menu ]; then
/etc/grub.d/10_linux:      linux_entry "${OS}" "${version}" true \
/etc/grub.d/10_linux:        "recovery nomodeset ${GRUB_CMDLINE_LINUX}"
/etc/grub.d/10_linux:    else
/etc/grub.d/10_linux:      linux_entry "${OS}" "${version}" true \
/etc/grub.d/10_linux:        "single nomodeset ${GRUB_CMDLINE_LINUX}"
/etc/grub.d/10_linux:    fi
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:  if [ "$list" ] && ! $in_submenu; then
/etc/grub.d/10_linux:    echo "submenu \"Previous Linux versions\" {"
/etc/grub.d/10_linux:    in_submenu=:
/etc/grub.d/10_linux:  fi
/etc/grub.d/10_linux:done
/etc/grub.d/10_linux:
/etc/grub.d/10_linux:if $in_submenu; then
/etc/grub.d/10_linux:  echo "}"
/etc/grub.d/10_linux:fi
/etc/grub.d/20_linux_xen:#! /bin/sh
/etc/grub.d/20_linux_xen:set -e
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:# grub-mkconfig helper script.
/etc/grub.d/20_linux_xen:# Copyright (C) 2006,2007,2008,2009,2010  Free Software Foundation, Inc.
/etc/grub.d/20_linux_xen:#
/etc/grub.d/20_linux_xen:# GRUB is free software: you can redistribute it and/or modify
/etc/grub.d/20_linux_xen:# it under the terms of the GNU General Public License as published by
/etc/grub.d/20_linux_xen:# the Free Software Foundation, either version 3 of the License, or
/etc/grub.d/20_linux_xen:# (at your option) any later version.
/etc/grub.d/20_linux_xen:#
/etc/grub.d/20_linux_xen:# GRUB is distributed in the hope that it will be useful,
/etc/grub.d/20_linux_xen:# but WITHOUT ANY WARRANTY; without even the implied warranty of
/etc/grub.d/20_linux_xen:# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
/etc/grub.d/20_linux_xen:# GNU General Public License for more details.
/etc/grub.d/20_linux_xen:#
/etc/grub.d/20_linux_xen:# You should have received a copy of the GNU General Public License
/etc/grub.d/20_linux_xen:# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:prefix="/usr"
/etc/grub.d/20_linux_xen:exec_prefix="${prefix}"
/etc/grub.d/20_linux_xen:datarootdir="${prefix}/share"
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:. "${datarootdir}/grub/grub-mkconfig_lib"
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:export TEXTDOMAIN=grub
/etc/grub.d/20_linux_xen:export TEXTDOMAINDIR="${datarootdir}/locale"
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:CLASS="--class gnu-linux --class gnu --class os --class xen"
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:if [ "x${GRUB_DISTRIBUTOR}" = "x" ] ; then
/etc/grub.d/20_linux_xen:  OS=GNU/Linux
/etc/grub.d/20_linux_xen:else
/etc/grub.d/20_linux_xen:  OS="${GRUB_DISTRIBUTOR} GNU/Linux"
/etc/grub.d/20_linux_xen:  CLASS="--class $(echo ${GRUB_DISTRIBUTOR} | tr 'A-Z' 'a-z' | cut -d' ' -f1) ${CLASS}"
/etc/grub.d/20_linux_xen:fi
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:# loop-AES arranges things so that /dev/loop/X can be our root device, but
/etc/grub.d/20_linux_xen:# the initrds that Linux uses don't like that.
/etc/grub.d/20_linux_xen:case ${GRUB_DEVICE} in
/etc/grub.d/20_linux_xen:  /dev/loop/*|/dev/loop[0-9])
/etc/grub.d/20_linux_xen:    GRUB_DEVICE=`losetup ${GRUB_DEVICE} | sed -e "s/^[^(]*(\([^)]\+\)).*/\1/"`
/etc/grub.d/20_linux_xen:    # We can't cope with devices loop-mounted from files here.
/etc/grub.d/20_linux_xen:    case ${GRUB_DEVICE} in
/etc/grub.d/20_linux_xen:      /dev/*) ;;
/etc/grub.d/20_linux_xen:      *) exit 0 ;;
/etc/grub.d/20_linux_xen:    esac
/etc/grub.d/20_linux_xen:  ;;
/etc/grub.d/20_linux_xen:esac
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:if [ "x${GRUB_DEVICE_UUID}" = "x" ] || [ "x${GRUB_DISABLE_LINUX_UUID}" = "xtrue" ] \
/etc/grub.d/20_linux_xen:    || ! test -e "/dev/disk/by-uuid/${GRUB_DEVICE_UUID}" \
/etc/grub.d/20_linux_xen:    || uses_abstraction "${GRUB_DEVICE}" lvm; then
/etc/grub.d/20_linux_xen:  LINUX_ROOT_DEVICE=${GRUB_DEVICE}
/etc/grub.d/20_linux_xen:else
/etc/grub.d/20_linux_xen:  LINUX_ROOT_DEVICE=UUID=${GRUB_DEVICE_UUID}
/etc/grub.d/20_linux_xen:fi
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:# Allow overriding GRUB_CMDLINE_LINUX and GRUB_CMDLINE_LINUX_DEFAULT.
/etc/grub.d/20_linux_xen:if [ "${GRUB_CMDLINE_LINUX_XEN_REPLACE}" ]; then
/etc/grub.d/20_linux_xen:  GRUB_CMDLINE_LINUX="${GRUB_CMDLINE_LINUX_XEN_REPLACE}"
/etc/grub.d/20_linux_xen:fi
/etc/grub.d/20_linux_xen:if [ "${GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT}" ]; then
/etc/grub.d/20_linux_xen:  GRUB_CMDLINE_LINUX_DEFAULT="${GRUB_CMDLINE_LINUX_XEN_REPLACE_DEFAULT}"
/etc/grub.d/20_linux_xen:fi
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:if [ "x`${grub_probe} --device ${GRUB_DEVICE} --target=fs 2>/dev/null || true`" = xbtrfs ] \
/etc/grub.d/20_linux_xen:    || [ "x`stat -f --printf=%T /`" = xbtrfs ]; then
/etc/grub.d/20_linux_xen:  rootsubvol="`make_system_path_relative_to_its_root /`"
/etc/grub.d/20_linux_xen:  rootsubvol="${rootsubvol#/}"
/etc/grub.d/20_linux_xen:  if [ "x${rootsubvol}" != x ]; then
/etc/grub.d/20_linux_xen:    GRUB_CMDLINE_LINUX="rootflags=subvol=${rootsubvol} ${GRUB_CMDLINE_LINUX}"
/etc/grub.d/20_linux_xen:  fi
/etc/grub.d/20_linux_xen:fi
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:linux_entry ()
/etc/grub.d/20_linux_xen:{
/etc/grub.d/20_linux_xen:  os="$1"
/etc/grub.d/20_linux_xen:  version="$2"
/etc/grub.d/20_linux_xen:  xen_version="$3"
/etc/grub.d/20_linux_xen:  recovery="$4"
/etc/grub.d/20_linux_xen:  args="$5"
/etc/grub.d/20_linux_xen:  xen_args="$6"
/etc/grub.d/20_linux_xen:  if ${recovery} ; then
/etc/grub.d/20_linux_xen:    title="$(gettext_quoted "%s, with Xen %s and Linux %s (recovery mode)")"
/etc/grub.d/20_linux_xen:  else
/etc/grub.d/20_linux_xen:    title="$(gettext_quoted "%s, with Xen %s and Linux %s")"
/etc/grub.d/20_linux_xen:  fi
/etc/grub.d/20_linux_xen:  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${xen_version}" "${version}"
/etc/grub.d/20_linux_xen:  if ! ${recovery} ; then
/etc/grub.d/20_linux_xen:      save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/20_linux_xen:  fi
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:  if [ -z "${prepare_boot_cache}" ]; then
/etc/grub.d/20_linux_xen:    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
/etc/grub.d/20_linux_xen:  fi
/etc/grub.d/20_linux_xen:  printf '%s\n' "${prepare_boot_cache}"
/etc/grub.d/20_linux_xen:  xmessage="$(gettext_printf "Loading Xen %s ..." ${xen_version})"
/etc/grub.d/20_linux_xen:  lmessage="$(gettext_printf "Loading Linux %s ..." ${version})"
/etc/grub.d/20_linux_xen:  cat << EOF
/etc/grub.d/20_linux_xen:	echo	'$xmessage'
/etc/grub.d/20_linux_xen:	multiboot	${rel_xen_dirname}/${xen_basename} placeholder ${xen_args}
/etc/grub.d/20_linux_xen:	echo	'$lmessage'
/etc/grub.d/20_linux_xen:	module	${rel_dirname}/${basename} placeholder root=${linux_root_device_thisversion} ro ${args}
/etc/grub.d/20_linux_xen:EOF
/etc/grub.d/20_linux_xen:  if test -n "${initrd}" ; then
/etc/grub.d/20_linux_xen:    message="$(gettext_printf "Loading initial ramdisk ...")"
/etc/grub.d/20_linux_xen:    cat << EOF
/etc/grub.d/20_linux_xen:	echo	'$message'
/etc/grub.d/20_linux_xen:	module	${rel_dirname}/${initrd}
/etc/grub.d/20_linux_xen:EOF
/etc/grub.d/20_linux_xen:  fi
/etc/grub.d/20_linux_xen:  cat << EOF
/etc/grub.d/20_linux_xen:}
/etc/grub.d/20_linux_xen:EOF
/etc/grub.d/20_linux_xen:}
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:linux_list=`for i in /boot/vmlinu[xz]-* /vmlinu[xz]-* /boot/kernel-*; do
/etc/grub.d/20_linux_xen:    if grub_file_is_not_garbage "$i"; then
/etc/grub.d/20_linux_xen:    	basename=$(basename $i)
/etc/grub.d/20_linux_xen:	version=$(echo $basename | sed -e "s,^[^0-9]*-,,g")
/etc/grub.d/20_linux_xen:	dirname=$(dirname $i)
/etc/grub.d/20_linux_xen:	config=
/etc/grub.d/20_linux_xen:	for j in "${dirname}/config-${version}" "${dirname}/config-${alt_version}" "/etc/kernels/kernel-config-${version}" ; do
/etc/grub.d/20_linux_xen:	    if test -e "${j}" ; then
/etc/grub.d/20_linux_xen:		config="${j}"
/etc/grub.d/20_linux_xen:		break
/etc/grub.d/20_linux_xen:	    fi
/etc/grub.d/20_linux_xen:	done
/etc/grub.d/20_linux_xen:        if (grep -qx "CONFIG_XEN_DOM0=y" "${config}" 2> /dev/null || grep -qx "CONFIG_XEN_PRIVILEGED_GUEST=y" "${config}" 2> /dev/null); then echo -n "$i " ; fi
/etc/grub.d/20_linux_xen:    fi
/etc/grub.d/20_linux_xen:    done`
/etc/grub.d/20_linux_xen:if [ "x${linux_list}" = "x" ] ; then
/etc/grub.d/20_linux_xen:    exit 0
/etc/grub.d/20_linux_xen:fi
/etc/grub.d/20_linux_xen:xen_list=`for i in /boot/xen*; do
/etc/grub.d/20_linux_xen:        if grub_file_is_not_garbage "$i" ; then echo -n "$i " ; fi
/etc/grub.d/20_linux_xen:      done`
/etc/grub.d/20_linux_xen:prepare_boot_cache=
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:while [ "x${xen_list}" != "x" ] ; do
/etc/grub.d/20_linux_xen:    list="${linux_list}"
/etc/grub.d/20_linux_xen:    current_xen=`version_find_latest $xen_list`
/etc/grub.d/20_linux_xen:    xen_basename=`basename ${current_xen}`
/etc/grub.d/20_linux_xen:    xen_dirname=`dirname ${current_xen}`
/etc/grub.d/20_linux_xen:    rel_xen_dirname=`make_system_path_relative_to_its_root $xen_dirname`
/etc/grub.d/20_linux_xen:    xen_version=`echo $xen_basename | sed -e "s,.gz$,,g;s,^xen-,,g"`
/etc/grub.d/20_linux_xen:    echo "submenu \"Xen ${xen_version}\" {"
/etc/grub.d/20_linux_xen:    while [ "x$list" != "x" ] ; do
/etc/grub.d/20_linux_xen:	linux=`version_find_latest $list`
/etc/grub.d/20_linux_xen:	echo "Found linux image: $linux" >&2
/etc/grub.d/20_linux_xen:	basename=`basename $linux`
/etc/grub.d/20_linux_xen:	dirname=`dirname $linux`
/etc/grub.d/20_linux_xen:	rel_dirname=`make_system_path_relative_to_its_root $dirname`
/etc/grub.d/20_linux_xen:	version=`echo $basename | sed -e "s,^[^0-9]*-,,g"`
/etc/grub.d/20_linux_xen:	alt_version=`echo $version | sed -e "s,\.old$,,g"`
/etc/grub.d/20_linux_xen:	linux_root_device_thisversion="${LINUX_ROOT_DEVICE}"
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:	initrd=
/etc/grub.d/20_linux_xen:	for i in "initrd.img-${version}" "initrd-${version}.img" \
/etc/grub.d/20_linux_xen:	    "initrd-${version}" "initrd.img-${alt_version}" \
/etc/grub.d/20_linux_xen:	    "initrd-${alt_version}.img" "initrd-${alt_version}" \
/etc/grub.d/20_linux_xen:	    "initramfs-genkernel-${version}" \
/etc/grub.d/20_linux_xen:	    "initramfs-genkernel-${alt_version}" ; do
/etc/grub.d/20_linux_xen:	    if test -e "${dirname}/${i}" ; then
/etc/grub.d/20_linux_xen:		initrd="$i"
/etc/grub.d/20_linux_xen:		break
/etc/grub.d/20_linux_xen:	    fi
/etc/grub.d/20_linux_xen:	done
/etc/grub.d/20_linux_xen:	if test -n "${initrd}" ; then
/etc/grub.d/20_linux_xen:	    echo "Found initrd image: ${dirname}/${initrd}" >&2
/etc/grub.d/20_linux_xen:	else
/etc/grub.d/20_linux_xen:    # "UUID=" magic is parsed by initrds.  Since there's no initrd, it can't work here.
/etc/grub.d/20_linux_xen:	    linux_root_device_thisversion=${GRUB_DEVICE}
/etc/grub.d/20_linux_xen:	fi
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:	linux_entry "${OS}" "${version}" "${xen_version}" false \
/etc/grub.d/20_linux_xen:	    "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_LINUX_DEFAULT}" "${GRUB_CMDLINE_XEN} ${GRUB_CMDLINE_XEN_DEFAULT}"
/etc/grub.d/20_linux_xen:	if [ "x${GRUB_DISABLE_RECOVERY}" != "xtrue" ]; then
/etc/grub.d/20_linux_xen:	    linux_entry "${OS}" "${version}" "${xen_version}" true \
/etc/grub.d/20_linux_xen:		"single ${GRUB_CMDLINE_LINUX}" "${GRUB_CMDLINE_XEN}"
/etc/grub.d/20_linux_xen:	fi
/etc/grub.d/20_linux_xen:
/etc/grub.d/20_linux_xen:	list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
/etc/grub.d/20_linux_xen:    done
/etc/grub.d/20_linux_xen:    echo "}"
/etc/grub.d/20_linux_xen:    xen_list=`echo $xen_list | tr ' ' '\n' | grep -vx $current_xen | tr '\n' ' '`
/etc/grub.d/20_linux_xen:done
/etc/grub.d/20_memtest86+:#!/bin/sh
/etc/grub.d/20_memtest86+:set -e
/etc/grub.d/20_memtest86+:
/etc/grub.d/20_memtest86+:if [ -f /usr/lib/grub/grub-mkconfig_lib ]; then
/etc/grub.d/20_memtest86+:  . /usr/lib/grub/grub-mkconfig_lib
/etc/grub.d/20_memtest86+:  LX=linux16
/etc/grub.d/20_memtest86+:elif [ -f /usr/lib/grub/update-grub_lib ]; then
/etc/grub.d/20_memtest86+:  . /usr/lib/grub/update-grub_lib
/etc/grub.d/20_memtest86+:  LX=linux
/etc/grub.d/20_memtest86+:else
/etc/grub.d/20_memtest86+:  # no grub file, so we notify and exit gracefully
/etc/grub.d/20_memtest86+:  echo "Cannot find grub config file, exiting." >&2
/etc/grub.d/20_memtest86+:  exit 0
/etc/grub.d/20_memtest86+:fi
/etc/grub.d/20_memtest86+:
/etc/grub.d/20_memtest86+:# We can't cope with loop-mounted devices here.
/etc/grub.d/20_memtest86+:case ${GRUB_DEVICE_BOOT} in
/etc/grub.d/20_memtest86+:  /dev/loop/*|/dev/loop[0-9]) exit 0 ;;
/etc/grub.d/20_memtest86+:esac
/etc/grub.d/20_memtest86+:
/etc/grub.d/20_memtest86+:prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
/etc/grub.d/20_memtest86+:
/etc/grub.d/20_memtest86+:if test -e /boot/memtest86+.bin ; then
/etc/grub.d/20_memtest86+:  MEMTESTPATH=$( make_system_path_relative_to_its_root "/boot/memtest86+.bin" )
/etc/grub.d/20_memtest86+:  echo "Found memtest86+ image: $MEMTESTPATH" >&2
/etc/grub.d/20_memtest86+:  cat << EOF
/etc/grub.d/20_memtest86+:menuentry "Memory test (memtest86+)" {
/etc/grub.d/20_memtest86+:EOF
/etc/grub.d/20_memtest86+:  printf '%s\n' "${prepare_boot_cache}"
/etc/grub.d/20_memtest86+:  cat << EOF
/etc/grub.d/20_memtest86+:	$LX	$MEMTESTPATH
/etc/grub.d/20_memtest86+:}
/etc/grub.d/20_memtest86+:menuentry "Memory test (memtest86+, serial console 115200)" {
/etc/grub.d/20_memtest86+:EOF
/etc/grub.d/20_memtest86+:  printf '%s\n' "${prepare_boot_cache}"
/etc/grub.d/20_memtest86+:  cat << EOF
/etc/grub.d/20_memtest86+:	$LX	$MEMTESTPATH console=ttyS0,115200n8
/etc/grub.d/20_memtest86+:}
/etc/grub.d/20_memtest86+:EOF
/etc/grub.d/20_memtest86+:fi
/etc/grub.d/20_memtest86+:
/etc/grub.d/20_memtest86+:#if test -e /boot/memtest86+_multiboot.bin ; then
/etc/grub.d/20_memtest86+:#  MEMTESTPATH=$( make_system_path_relative_to_its_root "/boot/memtest86+_multiboot.bin" )
/etc/grub.d/20_memtest86+:#  echo "Found memtest86+ multiboot image: $MEMTESTPATH" >&2
/etc/grub.d/20_memtest86+:#  cat << EOF
/etc/grub.d/20_memtest86+:#menuentry "Memory test (memtest86+, experimental multiboot)" {
/etc/grub.d/20_memtest86+:#EOF
/etc/grub.d/20_memtest86+:#  printf '%s\n' "${prepare_boot_cache}"
/etc/grub.d/20_memtest86+:#  cat << EOF
/etc/grub.d/20_memtest86+:#	multiboot	$MEMTESTPATH
/etc/grub.d/20_memtest86+:#}
/etc/grub.d/20_memtest86+:#menuentry "Memory test (memtest86+, serial console 115200, experimental multiboot)" {
/etc/grub.d/20_memtest86+:#EOF
/etc/grub.d/20_memtest86+:#  printf '%s\n' "${prepare_boot_cache}"
/etc/grub.d/20_memtest86+:#  cat << EOF
/etc/grub.d/20_memtest86+:#	multiboot	$MEMTESTPATH console=ttyS0,115200n8
/etc/grub.d/20_memtest86+:#}
/etc/grub.d/20_memtest86+:#EOF
/etc/grub.d/20_memtest86+:#fi
/etc/grub.d/30_os-prober:#! /bin/sh
/etc/grub.d/30_os-prober:set -e
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:# grub-mkconfig helper script.
/etc/grub.d/30_os-prober:# Copyright (C) 2006,2007,2008,2009  Free Software Foundation, Inc.
/etc/grub.d/30_os-prober:#
/etc/grub.d/30_os-prober:# GRUB is free software: you can redistribute it and/or modify
/etc/grub.d/30_os-prober:# it under the terms of the GNU General Public License as published by
/etc/grub.d/30_os-prober:# the Free Software Foundation, either version 3 of the License, or
/etc/grub.d/30_os-prober:# (at your option) any later version.
/etc/grub.d/30_os-prober:#
/etc/grub.d/30_os-prober:# GRUB is distributed in the hope that it will be useful,
/etc/grub.d/30_os-prober:# but WITHOUT ANY WARRANTY; without even the implied warranty of
/etc/grub.d/30_os-prober:# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
/etc/grub.d/30_os-prober:# GNU General Public License for more details.
/etc/grub.d/30_os-prober:#
/etc/grub.d/30_os-prober:# You should have received a copy of the GNU General Public License
/etc/grub.d/30_os-prober:# along with GRUB.  If not, see <http://www.gnu.org/licenses/>.
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:prefix="/usr"
/etc/grub.d/30_os-prober:exec_prefix="${prefix}"
/etc/grub.d/30_os-prober:datarootdir="${prefix}/share"
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:. "${datarootdir}/grub/grub-mkconfig_lib"
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:found_other_os=
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:make_timeout () {
/etc/grub.d/30_os-prober:  if [ "x${found_other_os}" = "x" ] ; then
/etc/grub.d/30_os-prober:    if [ "x${1}" != "x" ] ; then
/etc/grub.d/30_os-prober:      if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
/etc/grub.d/30_os-prober:	verbose=
/etc/grub.d/30_os-prober:      else
/etc/grub.d/30_os-prober:	verbose=" --verbose"
/etc/grub.d/30_os-prober:      fi
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:      if [ "x${1}" = "x0" ] ; then
/etc/grub.d/30_os-prober:	cat <<EOF
/etc/grub.d/30_os-prober:if [ "x\${timeout}" != "x-1" ]; then
/etc/grub.d/30_os-prober:  if keystatus; then
/etc/grub.d/30_os-prober:    if keystatus --shift; then
/etc/grub.d/30_os-prober:      set timeout=-1
/etc/grub.d/30_os-prober:    else
/etc/grub.d/30_os-prober:      set timeout=0
/etc/grub.d/30_os-prober:    fi
/etc/grub.d/30_os-prober:  else
/etc/grub.d/30_os-prober:    if sleep$verbose --interruptible 3 ; then
/etc/grub.d/30_os-prober:      set timeout=0
/etc/grub.d/30_os-prober:    fi
/etc/grub.d/30_os-prober:  fi
/etc/grub.d/30_os-prober:fi
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:      else
/etc/grub.d/30_os-prober:	cat << EOF
/etc/grub.d/30_os-prober:if [ "x\${timeout}" != "x-1" ]; then
/etc/grub.d/30_os-prober:  if sleep$verbose --interruptible ${GRUB_HIDDEN_TIMEOUT} ; then
/etc/grub.d/30_os-prober:    set timeout=0
/etc/grub.d/30_os-prober:  fi
/etc/grub.d/30_os-prober:fi
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:      fi
/etc/grub.d/30_os-prober:    fi
/etc/grub.d/30_os-prober:  fi
/etc/grub.d/30_os-prober:}
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:adjust_timeout () {
/etc/grub.d/30_os-prober:  if [ "x$GRUB_BUTTON_CMOS_ADDRESS" != "x" ]; then
/etc/grub.d/30_os-prober:    cat <<EOF
/etc/grub.d/30_os-prober:if cmostest $GRUB_BUTTON_CMOS_ADDRESS ; then
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:    make_timeout "${GRUB_HIDDEN_TIMEOUT_BUTTON}" "${GRUB_TIMEOUT_BUTTON}"
/etc/grub.d/30_os-prober:    echo else
/etc/grub.d/30_os-prober:    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
/etc/grub.d/30_os-prober:    echo fi
/etc/grub.d/30_os-prober:  else
/etc/grub.d/30_os-prober:    make_timeout "${GRUB_HIDDEN_TIMEOUT}" "${GRUB_TIMEOUT}"
/etc/grub.d/30_os-prober:  fi
/etc/grub.d/30_os-prober:}
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then
/etc/grub.d/30_os-prober:  adjust_timeout
/etc/grub.d/30_os-prober:  exit 0
/etc/grub.d/30_os-prober:fi
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:if [ -z "`which os-prober 2> /dev/null`" -o -z "`which linux-boot-prober 2> /dev/null`" ] ; then
/etc/grub.d/30_os-prober:  # missing os-prober and/or linux-boot-prober
/etc/grub.d/30_os-prober:  adjust_timeout
/etc/grub.d/30_os-prober:  exit 0
/etc/grub.d/30_os-prober:fi
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:OSPROBED="`os-prober | tr ' ' '^' | paste -s -d ' '`"
/etc/grub.d/30_os-prober:if [ -z "${OSPROBED}" ] ; then
/etc/grub.d/30_os-prober:  # empty os-prober output, nothing doing
/etc/grub.d/30_os-prober:  adjust_timeout
/etc/grub.d/30_os-prober:  exit 0
/etc/grub.d/30_os-prober:fi
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:osx_entry() {
/etc/grub.d/30_os-prober:	found_other_os=1
/etc/grub.d/30_os-prober:        cat << EOF
/etc/grub.d/30_os-prober:menuentry "${LONGNAME} (${2}-bit) (on ${DEVICE})" --class osx --class darwin --class os {
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:	save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:	prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:	cat << EOF
/etc/grub.d/30_os-prober:        load_video
/etc/grub.d/30_os-prober:        set do_resume=0
/etc/grub.d/30_os-prober:        if [ /var/vm/sleepimage -nt10 / ]; then
/etc/grub.d/30_os-prober:           if xnu_resume /var/vm/sleepimage; then
/etc/grub.d/30_os-prober:             set do_resume=1
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:        fi
/etc/grub.d/30_os-prober:        if [ \$do_resume = 0 ]; then
/etc/grub.d/30_os-prober:           xnu_uuid ${OSXUUID} uuid
/etc/grub.d/30_os-prober:           if [ -f /Extra/DSDT.aml ]; then
/etc/grub.d/30_os-prober:              acpi -e /Extra/DSDT.aml
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:           $1 /mach_kernel boot-uuid=\${uuid} rd=*uuid
/etc/grub.d/30_os-prober:           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
/etc/grub.d/30_os-prober:              xnu_mkext /System/Library/Extensions.mkext
/etc/grub.d/30_os-prober:           else
/etc/grub.d/30_os-prober:              xnu_kextdir /System/Library/Extensions
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:           if [ -f /Extra/Extensions.mkext ]; then
/etc/grub.d/30_os-prober:              xnu_mkext /Extra/Extensions.mkext
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:           if [ -d /Extra/Extensions ]; then
/etc/grub.d/30_os-prober:              xnu_kextdir /Extra/Extensions
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:           if [ -f /Extra/devprop.bin ]; then
/etc/grub.d/30_os-prober:              xnu_devprop_load /Extra/devprop.bin
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:           if [ -f /Extra/splash.jpg ]; then
/etc/grub.d/30_os-prober:              insmod jpeg
/etc/grub.d/30_os-prober:              xnu_splash /Extra/splash.jpg
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:           if [ -f /Extra/splash.png ]; then
/etc/grub.d/30_os-prober:              insmod png
/etc/grub.d/30_os-prober:              xnu_splash /Extra/splash.png
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:           if [ -f /Extra/splash.tga ]; then
/etc/grub.d/30_os-prober:              insmod tga
/etc/grub.d/30_os-prober:              xnu_splash /Extra/splash.tga
/etc/grub.d/30_os-prober:           fi
/etc/grub.d/30_os-prober:        fi
/etc/grub.d/30_os-prober:}
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:}
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:wubi=
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:for OS in ${OSPROBED} ; do
/etc/grub.d/30_os-prober:  DEVICE="`echo ${OS} | cut -d ':' -f 1`"
/etc/grub.d/30_os-prober:  LONGNAME="`echo ${OS} | cut -d ':' -f 2 | tr '^' ' '`"
/etc/grub.d/30_os-prober:  LABEL="`echo ${OS} | cut -d ':' -f 3 | tr '^' ' '`"
/etc/grub.d/30_os-prober:  BOOT="`echo ${OS} | cut -d ':' -f 4`"
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:  if [ -z "${LONGNAME}" ] ; then
/etc/grub.d/30_os-prober:    LONGNAME="${LABEL}"
/etc/grub.d/30_os-prober:  fi
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:  echo "Found ${LONGNAME} on ${DEVICE}" >&2
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:  case ${BOOT} in
/etc/grub.d/30_os-prober:    chain)
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:      case ${LONGNAME} in
/etc/grub.d/30_os-prober:	Windows*)
/etc/grub.d/30_os-prober:	  if [ -z "$wubi" ]; then
/etc/grub.d/30_os-prober:	    if [ -x /usr/share/lupin-support/grub-mkimage ] && \
/etc/grub.d/30_os-prober:	       /usr/share/lupin-support/grub-mkimage --test; then
/etc/grub.d/30_os-prober:	      wubi=yes
/etc/grub.d/30_os-prober:	    else
/etc/grub.d/30_os-prober:	      wubi=no
/etc/grub.d/30_os-prober:	    fi
/etc/grub.d/30_os-prober:	  fi
/etc/grub.d/30_os-prober:	  if [ "$wubi" = yes ]; then
/etc/grub.d/30_os-prober:	    echo "Skipping ${LONGNAME} on Wubi system" >&2
/etc/grub.d/30_os-prober:	    continue
/etc/grub.d/30_os-prober:	  fi
/etc/grub.d/30_os-prober:	  ;;
/etc/grub.d/30_os-prober:      esac
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:      found_other_os=1
/etc/grub.d/30_os-prober:      cat << EOF
/etc/grub.d/30_os-prober:menuentry "${LONGNAME} (on ${DEVICE})" --class windows --class os {
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:      save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:      case ${LONGNAME} in
/etc/grub.d/30_os-prober:	Windows\ Vista*|Windows\ 7*|Windows\ Server\ 2008*)
/etc/grub.d/30_os-prober:	;;
/etc/grub.d/30_os-prober:	*)
/etc/grub.d/30_os-prober:	  cat << EOF
/etc/grub.d/30_os-prober:	drivemap -s (hd0) \${root}
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:	;;
/etc/grub.d/30_os-prober:      esac
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:      cat <<EOF
/etc/grub.d/30_os-prober:	chainloader +1
/etc/grub.d/30_os-prober:}
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:    ;;
/etc/grub.d/30_os-prober:    linux)
/etc/grub.d/30_os-prober:      LINUXPROBED="`linux-boot-prober ${DEVICE} 2> /dev/null | tr ' ' '^' | paste -s -d ' '`"
/etc/grub.d/30_os-prober:      prepare_boot_cache=
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:      for LINUX in ${LINUXPROBED} ; do
/etc/grub.d/30_os-prober:        LROOT="`echo ${LINUX} | cut -d ':' -f 1`"
/etc/grub.d/30_os-prober:        LBOOT="`echo ${LINUX} | cut -d ':' -f 2`"
/etc/grub.d/30_os-prober:        LLABEL="`echo ${LINUX} | cut -d ':' -f 3 | tr '^' ' '`"
/etc/grub.d/30_os-prober:        LKERNEL="`echo ${LINUX} | cut -d ':' -f 4`"
/etc/grub.d/30_os-prober:        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
/etc/grub.d/30_os-prober:        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:        if [ -z "${LLABEL}" ] ; then
/etc/grub.d/30_os-prober:          LLABEL="${LONGNAME}"
/etc/grub.d/30_os-prober:        fi
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:	if [ "${LROOT}" != "${LBOOT}" ]; then
/etc/grub.d/30_os-prober:	  LKERNEL="${LKERNEL#/boot}"
/etc/grub.d/30_os-prober:	  LINITRD="${LINITRD#/boot}"
/etc/grub.d/30_os-prober:	fi
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:	if [ -z "${prepare_boot_cache}" ]; then
/etc/grub.d/30_os-prober:	  prepare_boot_cache="$(prepare_grub_to_access_device ${LBOOT} | sed -e "s/^/\t/")"
/etc/grub.d/30_os-prober:	  [ "${prepare_boot_cache}" ] || continue
/etc/grub.d/30_os-prober:	fi
/etc/grub.d/30_os-prober:	found_other_os=1
/etc/grub.d/30_os-prober:        cat << EOF
/etc/grub.d/30_os-prober:menuentry "${LLABEL} (on ${DEVICE})" --class gnu-linux --class gnu --class os {
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:	save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:	printf '%s\n' "${prepare_boot_cache}"
/etc/grub.d/30_os-prober:	cat <<  EOF
/etc/grub.d/30_os-prober:	linux ${LKERNEL} ${LPARAMS}
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:        if [ -n "${LINITRD}" ] ; then
/etc/grub.d/30_os-prober:          cat << EOF
/etc/grub.d/30_os-prober:	initrd ${LINITRD}
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:        fi
/etc/grub.d/30_os-prober:        cat << EOF
/etc/grub.d/30_os-prober:}
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:      done
/etc/grub.d/30_os-prober:    ;;
/etc/grub.d/30_os-prober:    macosx)
/etc/grub.d/30_os-prober:      OSXUUID="`grub-probe --target=fs_uuid --device ${DEVICE} 2> /dev/null`"
/etc/grub.d/30_os-prober:      osx_entry xnu_kernel 32
/etc/grub.d/30_os-prober:      osx_entry xnu_kernel64 64
/etc/grub.d/30_os-prober:    ;;
/etc/grub.d/30_os-prober:    hurd)
/etc/grub.d/30_os-prober:      found_other_os=1
/etc/grub.d/30_os-prober:      cat << EOF
/etc/grub.d/30_os-prober:menuentry "${LONGNAME} (on ${DEVICE})" --class hurd --class gnu --class os {
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:      save_default_entry | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:      prepare_grub_to_access_device ${DEVICE} | sed -e "s/^/\t/"
/etc/grub.d/30_os-prober:      grub_device="`${grub_probe} --device ${DEVICE} --target=drive`"
/etc/grub.d/30_os-prober:      mach_device="`echo "${grub_device}" | sed -e 's/(\(hd.*\),msdos\(.*\))/\1s\2/'`"
/etc/grub.d/30_os-prober:      grub_fs="`${grub_probe} --device ${DEVICE} --target=fs`"
/etc/grub.d/30_os-prober:      case "${grub_fs}" in
/etc/grub.d/30_os-prober:	*fs)	hurd_fs="${grub_fs}" ;;
/etc/grub.d/30_os-prober:	*)	hurd_fs="${grub_fs}fs" ;;
/etc/grub.d/30_os-prober:      esac
/etc/grub.d/30_os-prober:      cat << EOF
/etc/grub.d/30_os-prober:	multiboot /boot/gnumach.gz root=device:${mach_device}
/etc/grub.d/30_os-prober:	module /hurd/${hurd_fs}.static ${hurd_fs} --readonly \\
/etc/grub.d/30_os-prober:			--multiboot-command-line='\${kernel-command-line}' \\
/etc/grub.d/30_os-prober:			--host-priv-port='\${host-port}' \\
/etc/grub.d/30_os-prober:			--device-master-port='\${device-port}' \\
/etc/grub.d/30_os-prober:			--exec-server-task='\${exec-task}' -T typed '\${root}' \\
/etc/grub.d/30_os-prober:			'\$(task-create)' '\$(task-resume)'
/etc/grub.d/30_os-prober:	module /lib/ld.so.1 exec /hurd/exec '\$(exec-task=task-create)'
/etc/grub.d/30_os-prober:}
/etc/grub.d/30_os-prober:EOF
/etc/grub.d/30_os-prober:    ;;
/etc/grub.d/30_os-prober:    *)
/etc/grub.d/30_os-prober:      echo "  ${LONGNAME} is not yet supported by grub-mkconfig." >&2
/etc/grub.d/30_os-prober:    ;;
/etc/grub.d/30_os-prober:  esac
/etc/grub.d/30_os-prober:done
/etc/grub.d/30_os-prober:
/etc/grub.d/30_os-prober:adjust_timeout
/etc/grub.d/40_custom:#!/bin/sh
/etc/grub.d/40_custom:exec tail -n +3 $0
/etc/grub.d/40_custom:# This file provides an easy way to add custom menu entries.  Simply type the
/etc/grub.d/40_custom:# menu entries you want to add after this comment.  Be careful not to change
/etc/grub.d/40_custom:# the 'exec tail' line above.
/etc/grub.d/41_custom:#!/bin/sh
/etc/grub.d/41_custom:cat <<EOF
/etc/grub.d/41_custom:if [ -f  \$prefix/custom.cfg ]; then
/etc/grub.d/41_custom:  source \$prefix/custom.cfg;
/etc/grub.d/41_custom:fi
/etc/grub.d/41_custom:EOF
/etc/grub.d/41_custom:
/etc/grub.d/README:
/etc/grub.d/README:All executable files in this directory are processed in shell expansion order.
/etc/grub.d/README:
/etc/grub.d/README:  00_*: Reserved for 00_header.
/etc/grub.d/README:  10_*: Native boot entries.
/etc/grub.d/README:  20_*: Third party apps (e.g. memtest86+).
/etc/grub.d/README:
/etc/grub.d/README:The number namespace in-between is configurable by system installer and/or
/etc/grub.d/README:administrator.  For example, you can add an entry to boot another OS as
/etc/grub.d/README:01_otheros, 11_otheros, etc, depending on the position you want it to occupy in
/etc/grub.d/README:the menu; and then adjust the default setting via /etc/default/grub.
richard@dell:~$ 

```

As to that line  video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap   
... I have no idea where, why or when that appeared - I certainly didn't enter it :p

---

### Post by matt_symes on 2012-07-04
Hi

I've just had a look at your scripts. You are missing one script and the very first part of the second one is missing part of it but i assume that is because of your num scroll lines setting. They look fine apart from that.

> As to that line  video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap   
... I have no idea where, why or when that appeared - I certainly didn't enter it :razz:As you did not add them then i suspect they should not be there so let's remove them as per bogan's suggestion. They certainly are not part of a default kernel command line although (if formatted correctly i.e remove >> and << ) they are valid kernel boot commands for a framebuffer.

Open a terminal and type (or copy and paste)
```

sudo sed -i 's/video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap//g' /etc/default/grub
```Then type

```
sudo update-grub
```Post back any errors and on efficacy.

If this fixes it then give yourself a gold star bogan :KS 

Kind regards

---

### Post by Megaptera on 2012-07-04
_Many thanks_ matt_symes and bogan, I think it's OK now ... !!!

```
richard@dell:~$ sudo sed -i 's/video=uvesafb:mode_option=>>1024x768-24<<,mtrr=3,scroll=ywrap//g' /etc/default/grub
[sudo] password for richard: 
richard@dell:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found memtest86+ image: /memtest86+.bin
done

```

---

