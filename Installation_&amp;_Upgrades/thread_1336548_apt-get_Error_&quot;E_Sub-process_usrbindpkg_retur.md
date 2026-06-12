---
title: "apt-get Error &quot;E: Sub-process /usr/bin/dpkg returned an error code (1)&quot;"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by freedom_seekar on 2009-11-24
Hi,
 I am new to Kubuntu(9.10) and I am facing some issues with Kpackmanagement Somebuddy Please help me out.
While I was Installing Cheese my system restarted (Laptop battery down), Then I tried to uninstall and reinstall Cheese and got the below Error
System Config:-
Kubuntu 9.10
----------------------------------------------------------------------
neon@Troy:~$ sudo apt-get install -f cheese
Reading package lists... Done
Building dependency tree
Reading state information... Done
cheese is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cheese (2.28.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing cheese (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 cheese
E: Sub-process /usr/bin/dpkg returned an error code (1)
----------------------------------------------------------------------
Then I tried 
-------------------------------------------------------------
neon@Troy:~$ sudo apt-get updgrade
E: Invalid operation updgrade
neon@Troy:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cheese (2.28.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing cheese (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 cheese
E: Sub-process /usr/bin/dpkg returned an error code (1)
neon@Troy:~$
-------------------------------------------------------------
I also Tried
--------------------------------------------------------------
neon@Troy:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cheese (2.28.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing cheese (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 cheese
E: Sub-process /usr/bin/dpkg returned an error code (1)
neon@Troy:~$
---------------------------------------------------------------

---

### Post by lykwydchykyn on 2009-11-24
Sounds like the package you downloaded is corrupt.  Try these commands in sequence:

```

sudo apt-get clean
sudo apt-get remove cheese
sudo apt-get install cheese

```

If it still errors out, post the errors here.

---

### Post by freedom_seekar on 2009-11-24
Hi Thanks for the suggestions,..
I tried ur suggestions but I got errors.
----------------------------------------------------------
neon@Troy:~$ sudo apt-get clean
[sudo] password for neon:      
neon@Troy:~$ sudo apt-get remove cheese
Reading package lists... Done          
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gstreamer0.10-x libgnome-keyring0 libproxy0 libcamel1.2-14 gstreamer0.10-plugins-good libsoup2.4-1 libedataserver1.2-11 libbonobo2-0
  libebook1.2-9 libsoup-gnome2.4-1 libbonobo2-common libgnome-desktop-2-11
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  cheese
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 7,315kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 133182 files and directories currently installed.)
Removing cheese ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing cheese (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 cheese
E: Sub-process /usr/bin/dpkg returned an error code (1)
neon@Troy:~$ sudo apt-get install cheese
Reading package lists... Done
Building dependency tree
Reading state information... Done
cheese is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up cheese (2.28.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing cheese (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 cheese
E: Sub-process /usr/bin/dpkg returned an error code (1)
neon@Troy:~$

----------------------------------------------------------

---

### Post by lykwydchykyn on 2009-11-24
Ok, here's what I think then:
the pre-remove and post-install scripts for cheese are corrupted.  To fix this, we have to basically make them empty scripts, then it should uninstall.

So try these commands, exactly as written, in sequence:

```

sudo -i
echo "exit 0" > /var/lib/dpkg/info/cheese.prerm
echo "exit 0" > /var/lib/dpkg/info/cheese.postinst
apt-get remove --purge cheese
apt-get clean
apt-get install cheese
exit

```
I have no way to test this, but this is based on what I read in this bug report: 
[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/374136](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/374136)

---

### Post by freedom_seekar on 2009-11-25
Hi I tried your suggestions but, It dosen't seem to work,..
But I tried something else which solved the issue.
```

sudo -i
rm -rf /var/lib/dpkg/info/cheese.*
apt-get remove cheese
apt-get install cheese

```

Output:-
> 
root@Troy:/var/lib/dpkg/info# apt-get remove cheese
Reading package lists... Done                      
Building dependency tree                           
Reading state information... Done                  
The following packages were automatically installed and are no longer required:
  gstreamer0.10-x libgnome-keyring0 libproxy0 libcamel1.2-14 gstreamer0.10-plugins-good
  libsoup2.4-1 libedataserver1.2-11 libbonobo2-0 libebook1.2-9 libsoup-gnome2.4-1      
  libbonobo2-common libgnome-desktop-2-11                                              
Use 'apt-get autoremove' to remove them.                                               
The following packages will be REMOVED:                                                
  cheese                                                                               
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.                         
1 not fully installed or removed.                                                      
After this operation, 7,315kB disk space will be freed.                                
Do you want to continue [Y/n]? y                                                       
(Reading database ... 35%                                                              
dpkg: warning: files list file for package `cheese' missing, assuming package has no files currently installed.                                                                           
(Reading database ... 134458 files and directories currently installed.)                     
Removing cheese ...                                                                          
root@Troy:/var/lib/dpkg/info# apt-get remove cheese                                          
Reading package lists... Done                                                                
Building dependency tree                                                                     
Reading state information... Done                                                            
Package cheese is not installed, so not removed                                              
The following packages were automatically installed and are no longer required:              
  gstreamer0.10-x libgnome-keyring0 libproxy0 libcamel1.2-14 gstreamer0.10-plugins-good      
  libsoup2.4-1 libedataserver1.2-11 libbonobo2-0 libebook1.2-9 libsoup-gnome2.4-1            
  libbonobo2-common libgnome-desktop-2-11                                                    
Use 'apt-get autoremove' to remove them.                                                     
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.                               
root@Troy:/var/lib/dpkg/info# apt-get install cheese
Reading package lists... Done                       
Building dependency tree                            
Reading state information... Done                   
Suggested packages:                                 
  nautilus-sendto                                   
The following NEW packages will be installed:       
  cheese                                            
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,481kB of archives.                              
After this operation, 7,315kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main cheese 2.28.1-0ubuntu1 [2,481kB]
Fetched 2,481kB in 2s (1,181kB/s)                                           
Selecting previously deselected package cheese.                             
(Reading database ... 134459 files and directories currently installed.)    
Unpacking cheese (from .../cheese_2.28.1-0ubuntu1_i386.deb) ...             
Processing triggers for hicolor-icon-theme ...                              
Processing triggers for man-db ...                                          
Setting up cheese (2.28.1-0ubuntu1) ...               


Thank U very much for Your Help.

Cheers,
Ravi.

---

