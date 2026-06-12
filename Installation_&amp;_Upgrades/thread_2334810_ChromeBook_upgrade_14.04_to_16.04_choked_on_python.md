---
title: "ChromeBook upgrade 14.04 to 16.04 choked on python3-software-properites"
date: 2016-08-22
forum: Installation &amp; Upgrades
---

### Post by mrpete3 on 2016-08-22
I have successfully upgraded two PC's from 14.04 LTS to 16.04 LTS using the Software Updater app. I also have a ChromeBook with Ubuntu 14.04 LTS installed. I found that the Software Updater app never really got started on the ChromeBook, so I found a post to help me and I ran

(trusty)peeter@localhost:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                           
Get:2 Upgrade tool [1262 kB]                                                   
Fetched 1262 kB in 0s (0 B/s)                                                  
authenticate 'xenial.tar.gz' against 'xenial.tar.gz.gpg' 
extracting 'xenial.tar.gz'

Reading cache

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Building data structures... Done 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial InRelease                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates InRelease                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security InRelease                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/restricted amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/universe amd64 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/universe Translation-en                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/universe Sources                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/multiverse Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/main amd64 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/restricted amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/universe amd64 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/multiverse amd64 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/main i386 Packages                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/restricted i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/universe i386 Packages            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/multiverse i386 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/main Translation-en               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/multiverse Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/restricted Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/universe Translation-en           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/restricted Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/universe Sources                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/multiverse Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/main amd64 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/restricted amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/universe amd64 Packages          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/multiverse amd64 Packages        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/main i386 Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/restricted i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/universe i386 Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/multiverse i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/main Translation-en              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/multiverse Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/restricted Translation-en        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/universe Translation-en          
Fetched 0 B in 6s (16.2 MB/s)                                                  
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Updating repository information
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial InRelease                                 
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates InRelease [95.7 kB]             
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security InRelease [94.5 kB]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/main Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/restricted Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/universe Sources                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/multiverse Sources                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/main amd64 Packages                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/restricted amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/universe amd64 Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/multiverse amd64 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/main i386 Packages                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/restricted i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/universe i386 Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/multiverse i386 Packages                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/main Translation-en                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/multiverse Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/restricted Translation-en                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial/universe Translation-en                   
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/main Sources [181 kB]           
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/restricted Sources [64 B]       
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/universe Sources [90.4 kB]      
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/multiverse Sources [3220 B]     
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/main amd64 Packages [376 kB]    
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/restricted amd64 Packages [64 B]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/universe amd64 Packages [319 kB]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/multiverse amd64 Packages [5488 B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/main i386 Packages [371 kB]    
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/restricted i386 Packages [64 B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/universe i386 Packages [316 kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/multiverse i386 Packages [4280 B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/main Translation-en [142 kB]   
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/multiverse Translation-en [2428 B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/restricted Translation-en [64 B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-updates/universe Translation-en [109 kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/main Sources [36.8 kB]        
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/restricted Sources [64 B]     
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/universe Sources [8956 B]     
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/multiverse Sources [728 B]    
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/main amd64 Packages [134 kB]  
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/restricted amd64 Packages [64 B]
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/universe amd64 Packages [40.2 kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/multiverse amd64 Packages [1176 B]
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/main i386 Packages [130 kB]   
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/restricted i386 Packages [64 B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/universe i386 Packages [40.2 kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/multiverse i386 Packages [1344 B]
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/main Translation-en [54.9 kB] 
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/multiverse Translation-en [628 B]
Get:33 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/restricted Translation-en [64 B]
Get:34 [http://archive.ubuntu.com](http://archive.ubuntu.com) xenial-security/universe Translation-en [24.3 kB]
Fetched 2584 kB in 6s (11.8 MB/s)                                              

Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 

Calculating the changes

Calculating the changes

Do you want to start the upgrade? 


10 installed packages are no longer supported by Canonical. You can 
still get support from the community. 

35 packages are going to be removed. 277 new packages are going to be 
installed. 992 packages are going to be upgraded. 

Installing the upgrade can take several hours. Once the download has 
finished, the process cannot be canceled. 

 Continue [yN]  Details [d]y

Fetching
Fetched 0 B in 0s (0 B/s)                                                      

Upgrading

Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/xenial", line 8, in <module>
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeMain.py", line 242, in main
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeController.py", line 1876, in run
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeController.py", line 1841, in fullUpgrade
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeController.py", line 1257, in doDistUpgrade
UnboundLocalError: local variable 'e' referenced before assignment
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/apport_python_hook.py", line 109, in apport_excepthook
    pr.add_proc_info(extraenv=['PYTHONPATH', 'PYTHONHOME'])
  File "/usr/lib/python3/dist-packages/apport/report.py", line 532, in add_proc_info
    self['ExecutableTimestamp'] = str(int(os.stat(self['ExecutablePath']).st_mtime))
PermissionError: [Errno 13] Permission denied: '/tmp/ubuntu-release-upgrader-hhuo4k27/xenial'

Original exception was:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/xenial", line 8, in <module>
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeMain.py", line 242, in main
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeController.py", line 1876, in run
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeController.py", line 1841, in fullUpgrade
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeController.py", line 1257, in doDistUpgrade
UnboundLocalError: local variable 'e' referenced before assignment
Error in atexit._run_exitfuncs:
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-hhuo4k27/DistUpgrade/DistUpgradeController.py", line 1062, in _enableAptCronJob
PermissionError: [Errno 1] Operation not permitted: '/etc/cron.daily/apt'


Please help.

---

### Post by TheFu on 2016-08-22
Welcome to the forums.

Just to clarify.
* was this a full install of 14.04?  Not crouton?
* What model and version of chromebook is it?  Is there any complications known for that model with Ubuntu or full installations?
* Any use of LVM or encryption?

I ask these questions that you may post the answers and someone with the same model might respond. Chromebook answers tend to be extremely model specific.  With my Toshiba, I had to jump through all sorts of hoops to get Ubuntu installed and working (with LVM and encryption), but with an older Acer C720, it was like any other PC.

---

