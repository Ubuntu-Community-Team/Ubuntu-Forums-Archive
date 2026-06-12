---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2016-02-20
forum: Installation &amp; Upgrades
---

### Post by maximus5113 on 2016-02-20
Hi all, 

I have tried to solve this problem but and red some articles about it but I couldn't find any solution to this.

sudo apt-get update
```

Ign http://ubuntu.inode.at trusty InRelease
Hit http://ubuntu.inode.at trusty-updates InRelease                            
Hit http://ubuntu.inode.at trusty-security InRelease                           
Hit http://ubuntu.inode.at trusty-proposed InRelease                           
Ign http://archive.canonical.com trusty InRelease                              
Hit http://ubuntu.inode.at trusty Release.gpg                                  
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://ubuntu.inode.at trusty-updates/main amd64 Packages                  
Hit http://archive.canonical.com trusty Release                                
Hit http://ubuntu.inode.at trusty-updates/restricted amd64 Packages            
Hit http://ubuntu.inode.at trusty-updates/universe amd64 Packages              
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://ubuntu.inode.at trusty-updates/multiverse amd64 Packages            
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://ubuntu.inode.at trusty-updates/main i386 Packages                   
Hit http://ubuntu.inode.at trusty-updates/restricted i386 Packages             
Hit http://archive.canonical.com trusty/partner Translation-en                 
Hit http://ubuntu.inode.at trusty-updates/universe i386 Packages               
Hit http://ubuntu.inode.at trusty-updates/multiverse i386 Packages             
Hit http://ubuntu.inode.at trusty-updates/main Translation-en                  
Hit http://ubuntu.inode.at trusty-updates/multiverse Translation-en            
Hit http://ubuntu.inode.at trusty-updates/restricted Translation-en            
Hit http://ubuntu.inode.at trusty-updates/universe Translation-en              
Hit http://ubuntu.inode.at trusty-security/main amd64 Packages                 
Hit http://ubuntu.inode.at trusty-security/restricted amd64 Packages           
Hit http://ubuntu.inode.at trusty-security/universe amd64 Packages             
Hit http://ubuntu.inode.at trusty-security/multiverse amd64 Packages           
Hit http://ubuntu.inode.at trusty-security/main i386 Packages                  
Hit http://ubuntu.inode.at trusty-security/restricted i386 Packages            
Hit http://ubuntu.inode.at trusty-security/universe i386 Packages              
Hit http://ubuntu.inode.at trusty-security/multiverse i386 Packages            
Hit http://ubuntu.inode.at trusty-security/main Translation-en                 
Hit http://ubuntu.inode.at trusty-security/multiverse Translation-en           
Hit http://ubuntu.inode.at trusty-security/restricted Translation-en           
Hit http://ubuntu.inode.at trusty-security/universe Translation-en             
Hit http://ubuntu.inode.at trusty-proposed/restricted amd64 Packages           
Hit http://ubuntu.inode.at trusty-proposed/universe amd64 Packages             
Hit http://ubuntu.inode.at trusty-proposed/multiverse amd64 Packages           
Hit http://ubuntu.inode.at trusty-proposed/main amd64 Packages                 
Hit http://ubuntu.inode.at trusty-proposed/restricted i386 Packages            
Hit http://ubuntu.inode.at trusty-proposed/universe i386 Packages              
Hit http://ubuntu.inode.at trusty-proposed/multiverse i386 Packages            
Hit http://ubuntu.inode.at trusty-proposed/main i386 Packages                  
Hit http://ubuntu.inode.at trusty-proposed/main Translation-en                 
Hit http://ubuntu.inode.at trusty-proposed/multiverse Translation-en           
Hit http://ubuntu.inode.at trusty-proposed/restricted Translation-en           
Hit http://ubuntu.inode.at trusty-proposed/universe Translation-en             
Hit http://ubuntu.inode.at trusty Release                                      
Hit http://ubuntu.inode.at trusty/main amd64 Packages                          
Hit http://ubuntu.inode.at trusty/restricted amd64 Packages                    
Hit http://ubuntu.inode.at trusty/universe amd64 Packages                      
Hit http://ubuntu.inode.at trusty/multiverse amd64 Packages                    
Hit http://ubuntu.inode.at trusty/main i386 Packages                           
Hit http://ubuntu.inode.at trusty/restricted i386 Packages                     
Hit http://ubuntu.inode.at trusty/universe i386 Packages                       
Hit http://ubuntu.inode.at trusty/multiverse i386 Packages                     
Hit http://ubuntu.inode.at trusty/main Translation-en                          
Hit http://ubuntu.inode.at trusty/multiverse Translation-en                    
Hit http://ubuntu.inode.at trusty/restricted Translation-en                    
Hit http://ubuntu.inode.at trusty/universe Translation-en                      
Ign http://ubuntu.inode.at trusty/main Translation-en_US                       
Ign http://ubuntu.inode.at trusty/multiverse Translation-en_US                 
Ign http://ubuntu.inode.at trusty/restricted Translation-en_US                 
Ign http://ubuntu.inode.at trusty/universe Translation-en_US                   
Hit http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                           
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://extras.ubuntu.com trusty Release                       
Hit http://ppa.launchpad.net trusty/main Translation-en            
Hit http://extras.ubuntu.com trusty/main amd64 Packages
Hit http://extras.ubuntu.com trusty/main i386 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en_US
Ign http://extras.ubuntu.com trusty/main Translation-en
Reading package lists... Done

```

sudo apt-get upgrade
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  base-files initscripts libnuma1 libsnmp-base libsnmp30 openssh-client
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/1.693 kB of archives.
After this operation, 3.523 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 511817 files and directories currently installed.)
Preparing to unpack .../openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb ...
Unpacking openssh-client (1:6.6p1-2ubuntu2.6) over (1:6.6p1-2ubuntu2.6) ...
dpkg: error processing archive /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/prerm': Is a directory
Preparing to unpack .../base-files_7.2ubuntu5.4+elementary18~ubuntu14.04.1_amd64.deb ...
Unpacking base-files (7.2ubuntu5.4+elementary18~ubuntu14.04.1) over (7.2ubuntu5.3+elementary17~ubuntu0.3.1.1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-2) ...
Processing triggers for cracklib-runtime (2.9.1-1build1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

sudo apt-get install -f
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  openssh-client
Suggested packages:
  ssh-askpass libpam-ssh keychain monkeysphere
The following packages will be upgraded:
  openssh-client
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
10 not fully installed or removed.
Need to get 0 B/562 kB of archives.
After this operation, 3.522 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Setting up base-files (7.2ubuntu5.4+elementary18~ubuntu14.04.1) ...
(Reading database ... 511817 files and directories currently installed.)
Preparing to unpack .../openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb ...
Unpacking openssh-client (1:6.6p1-2ubuntu2.6) over (1:6.6p1-2ubuntu2.6) ...
dpkg: error processing archive /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/prerm': Is a directory
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

sudo apt-get dist-upgrade
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  initscripts libnuma1 libsnmp-base libsnmp30 openssh-client
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 0 B/1.603 kB of archives.
After this operation, 3.523 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 511817 files and directories currently iIgn http://ubuntu.inode.at trusty InRelease
Hit http://ubuntu.inode.at trusty-updates InRelease                            
Hit http://ubuntu.inode.at trusty-security InRelease                           
Hit http://ubuntu.inode.at trusty-proposed InRelease                           
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://ubuntu.inode.at trusty Release.gpg                                  
Hit http://ubuntu.inode.at trusty-updates/main amd64 Packages                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://ubuntu.inode.at trusty-updates/restricted amd64 Packages            
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ubuntu.inode.at trusty-updates/universe amd64 Packages              
Hit http://ubuntu.inode.at trusty-updates/multiverse amd64 Packages            
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://ubuntu.inode.at trusty-updates/main i386 Packages                   
Hit http://ubuntu.inode.at trusty-updates/restricted i386 Packages             
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ubuntu.inode.at trusty-updates/universe i386 Packages               
Hit http://ubuntu.inode.at trusty-updates/multiverse i386 Packages             
Hit http://ubuntu.inode.at trusty-updates/main Translation-en                  
Hit http://ubuntu.inode.at trusty-updates/multiverse Translation-en            
Hit http://ubuntu.inode.at trusty-updates/restricted Translation-en            
Hit http://ubuntu.inode.at trusty-updates/universe Translation-en              
Hit http://ubuntu.inode.at trusty-security/main amd64 Packages                 
Hit http://ubuntu.inode.at trusty-security/restricted amd64 Packages           
Hit http://ubuntu.inode.at trusty-security/universe amd64 Packages             
Hit http://ubuntu.inode.at trusty-security/multiverse amd64 Packages           
Hit http://ubuntu.inode.at trusty-security/main i386 Packages                  
Hit http://ubuntu.inode.at trusty-security/restricted i386 Packages            
Hit http://ubuntu.inode.at trusty-security/universe i386 Packages              
Hit http://ubuntu.inode.at trusty-security/multiverse i386 Packages            
Hit http://ubuntu.inode.at trusty-security/main Translation-en                 
Hit http://ubuntu.inode.at trusty-security/multiverse Translation-en           
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Hit http://ubuntu.inode.at trusty-security/restricted Translation-en           
Hit http://ubuntu.inode.at trusty-security/universe Translation-en             
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ubuntu.inode.at trusty-proposed/restricted amd64 Packages           
Hit http://ubuntu.inode.at trusty-proposed/universe amd64 Packages             
Hit http://ubuntu.inode.at trusty-proposed/multiverse amd64 Packages           
Hit http://ubuntu.inode.at trusty-proposed/main amd64 Packages                 
Hit http://ubuntu.inode.at trusty-proposed/restricted i386 Packages            
Hit http://ubuntu.inode.at trusty-proposed/universe i386 Packages              
Hit http://ubuntu.inode.at trusty-proposed/multiverse i386 Packages            
Hit http://ubuntu.inode.at trusty-proposed/main i386 Packages                  
Hit http://ubuntu.inode.at trusty-proposed/main Translation-en                 
Hit http://ubuntu.inode.at trusty-proposed/multiverse Translation-en           
Hit http://ubuntu.inode.at trusty-proposed/restricted Translation-en           
Hit http://ubuntu.inode.at trusty-proposed/universe Translation-en             
Hit http://ubuntu.inode.at trusty Release                                      
Hit http://ubuntu.inode.at trusty/main amd64 Packages                          
Hit http://ubuntu.inode.at trusty/restricted amd64 Packages                    
Hit http://ubuntu.inode.at trusty/universe amd64 Packages                      
Hit http://ubuntu.inode.at trusty/multiverse amd64 Packages                    
Hit http://ubuntu.inode.at trusty/main i386 Packages                           
Hit http://ubuntu.inode.at trusty/restricted i386 Packages                     
Hit http://ubuntu.inode.at trusty/universe i386 Packages                       
Hit http://ubuntu.inode.at trusty/multiverse i386 Packages                     
Hit http://ubuntu.inode.at trusty/main Translation-en                          
Hit http://ubuntu.inode.at trusty/multiverse Translation-en                    
Hit http://ubuntu.inode.at trusty/restricted Translation-en                    
Hit http://ubuntu.inode.at trusty/universe Translation-en                      
Ign http://ubuntu.inode.at trusty/main Translation-en_US                       
Ign http://ubuntu.inode.at trusty/multiverse Translation-en_US                 
Ign http://ubuntu.inode.at trusty/restricted Translation-en_US                 
Ign http://ubuntu.inode.at trusty/universe Translation-en_US                   
Ign http://archive.canonical.com trusty InRelease                              
Hit http://ppa.launchpad.net trusty InRelease                               
Hit http://archive.canonical.com trusty Release.gpg
Hit http://archive.canonical.com trusty Release    
Hit http://ppa.launchpad.net trusty/main amd64 Packages
Hit http://ppa.launchpad.net trusty/main i386 Packages
Hit http://archive.canonical.com trusty/partner amd64 Packages    
Hit http://ppa.launchpad.net trusty/main Translation-en
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://archive.canonical.com trusty/partner Translation-ennstalled.)
Preparing to unpack .../openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb ...
Unpacking openssh-client (1:6.6p1-2ubuntu2.6) over (1:6.6p1-2ubuntu2.6) ...
dpkg: error processing archive /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/prerm': Is a directory
Preparing to unpack .../libnuma1_2.0.9~rc5-1ubuntu3.14.04.2_amd64.deb ...
Unpacking libnuma1:amd64 (2.0.9~rc5-1ubuntu3.14.04.2) over (2.0.9~rc5-1ubuntu3.14.04.1) ...
Preparing to unpack .../libsnmp-base_5.7.2~dfsg-8.1ubuntu3.2_all.deb ...
Unpacking libsnmp-base (5.7.2~dfsg-8.1ubuntu3.2) over (5.7.2~dfsg-8.1ubuntu3.1) ...
Preparing to unpack .../libsnmp30_5.7.2~dfsg-8.1ubuntu3.2_amd64.deb ...
Unpacking libsnmp30:amd64 (5.7.2~dfsg-8.1ubuntu3.2) over (5.7.2~dfsg-8.1ubuntu3.1) ...
Preparing to unpack .../initscripts_2.88dsf-41ubuntu6.3_amd64.deb ...
Unpacking initscripts (2.88dsf-41ubuntu6.3) over (2.88dsf-41ubuntu6.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
thx for your help in advance.;)
ps im using elementary freya, hopefully you can still help me since it is a problem with dpkg

---

### Post by v3.xx on 2016-02-20
We run different flavors, but ..

You can remove the offending file in
/var/cache/apt/archives/openssh-client*
and update.

Sometimes this works
```
sudo dpkg --clear-avail

```
Or you can clean the entire cache
```
sudo apt-get clean #and then update
```

Myself, I like just using a bigger hammer :)
```
sudo dpkg -i --force-overwrite-all /var/cache/apt/archives/openssh-client*
```

---

### Post by maximus5113 on 2016-02-20
> 
Myself, I like just using a bigger hammer :smile:
     ```

     sudo dpkg -i --force-overwrite-all /var/cache/apt/archives/openssh-client* 

```

there is no --force-overwrite-all, using --force-overwrite this is the outcome:
```

max@max-ThinkPad-T430s:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/openssh-client*
(Reading database ... 511817 files and directories currently installed.)
Preparing to unpack .../openssh-client_1%3a6.6p1-2ubuntu2.4_amd64.deb ...
Unpacking openssh-client (1:6.6p1-2ubuntu2.4) over (1:6.6p1-2ubuntu2.6) ...
dpkg: error processing archive /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.4_amd64.deb (--install):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/prerm': Is a directory
Preparing to unpack .../openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb ...
Unpacking openssh-client (1:6.6p1-2ubuntu2.6) over (1:6.6p1-2ubuntu2.6) ...
dpkg: error processing archive /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb (--install):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/prerm': Is a directory
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.4_amd64.deb
 /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb

```

---

### Post by QDR06VV9 on 2016-02-20
So what I would try would be theses steps:

1. Clear the apt cache
```
sudo apt-get clean
```

2.. Update the list of available software packages:
```
sudo apt-get update
```

3. Try to finish all pending installations
```
sudo apt-get -f install
```

4. Reset the cache
```
sudo dpkg --configure -a
```

5. Try the upgrade again
```
sudo apt-get upgrade
```

And if that fails..
Run one line at a time
 	 	```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

This will rebuild the cache.
Hope this is helpful.

---

### Post by maximus5113 on 2016-02-20
> **runrickus said:**
> So what I would try would be theses steps:

1. Clear the apt cache
```
sudo apt-get clean
```

2.. Update the list of available software packages:
```
sudo apt-get update
```

3. Try to finish all pending installations
```
sudo apt-get -f install
```

4. Reset the cache
```
sudo dpkg --configure -a
```

5. Try the upgrade again
```
sudo apt-get upgrade
```

And if that fails..
Run one line at a time
          ```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

This will rebuild the cache.
Hope this is helpful.

no, that doesn't do it, 
```
sudo apt-get -f install
```
still gives the same output

---

### Post by QDR06VV9 on 2016-02-20
Are you installing openssh from your natural software manager or an outside PPA
Better yet what is your method used in installing openssh?

openssh-client

---

### Post by maximus5113 on 2016-02-20
> **runrickus said:**
> Are you installing openssh from your natural software manager or an outside PPA
Better yet what is your method used in installing openssh?

openssh-client

there are no PPAs active.

---

### Post by QDR06VV9 on 2016-02-20
Well I can see these two 
[B]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en  

[/B]also I see > The following packages will be upgraded:   initscripts libnuma1 libsnmp-base libsnmp30 openssh-client 5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 9 not fully installed or removed.You could try uninstalling those and try installing open ssh-client again
Report all errors back here.

---

### Post by maximus5113 on 2016-02-20
> **runrickus said:**
> Well I can see these two 
[B]Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en  

[/B]also I see You could try uninstalling those and try installing open ssh-client again
Report all errors back here.

I dont't see how that could be the problem since it seems that dpkg has an error while unpacking, further more it says 
```
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/prerm': Is a directory
```
but /var/lib/dpkg/tmp.ci/prerm doesn't even exist

---

### Post by QDR06VV9 on 2016-02-22
I am as stumped as you!?
Here is a couple more links that have a happy ending with the "/var/lib/dpkg/tmp.ci/prerm"
A bit of reading but worth a look..
[https://lkubuntu.wordpress.com/2011/06/29/easy-way-to-fix-dpkg-svn-error/](https://lkubuntu.wordpress.com/2011/06/29/easy-way-to-fix-dpkg-svn-error/)

[http://forums.debian.net/viewtopic.php?f=17&t=49891&start=15](http://forums.debian.net/viewtopic.php?f=17&t=49891&start=15)
The page above^^^^^^^is on page 2 of that thread just to let you know that there is a page 1 also.
Good Luck and Regards

---

### Post by maximus5113 on 2016-02-23
> **runrickus said:**
> I am as stumped as you!?
Here is a couple more links that have a happy ending with the "/var/lib/dpkg/tmp.ci/prerm"
A bit of reading but worth a look..
[https://lkubuntu.wordpress.com/2011/06/29/easy-way-to-fix-dpkg-svn-error/](https://lkubuntu.wordpress.com/2011/06/29/easy-way-to-fix-dpkg-svn-error/)

[http://forums.debian.net/viewtopic.php?f=17&t=49891&start=15](http://forums.debian.net/viewtopic.php?f=17&t=49891&start=15)
The page above^^^^^^^is on page 2 of that thread just to let you know that there is a page 1 also.
Good Luck and Regards

Thx anyways :)

---

