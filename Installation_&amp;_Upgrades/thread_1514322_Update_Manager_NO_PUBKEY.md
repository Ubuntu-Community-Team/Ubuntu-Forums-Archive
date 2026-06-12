---
title: "Update Manager NO_PUBKEY"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by JustinR on 2010-06-20
Hey everybody,

I've noticed this problem in Update Manager, when ever I check for updates it gives me an error message:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8E5D2411637A5E2A
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8E5D2411637A5E2A

So when I try to find the public key using a method I found on the forums earlier today:

```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 8E5D2411637A5E2A
```

It returns

> 
gpg: requesting key 637A5E2A from hkp server subkeys.pgp.net
gpgkeys: key 8E5D2411637A5E2A not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


So I didn't try the rest of the solution.

Does anybody have the same problem? What is key 8E5D2411637A5E2A?
It doesn't seem to impair Ubuntu or its updating process - it appears to update everything on the system even without the key. So I'm not sure if I'm missing anything from not having that key or can I just delete it?

Thank you.

---

### Post by oldos2er on 2010-06-20
Have you tried the Ubuntu key server? ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8E5D2411637A5E2A
```

---

### Post by JustinR on 2010-06-20
Thank you oldos2er! That works and there is no more error in Update Manager.

---

### Post by wojox on 2010-06-20
Please mark as Solved. :p

---

### Post by reakin on 2010-07-21
Not solved for me, I still get the same GPG error, with the ubuntu key server or other ones. Below is my attempt to update keys and apt lists

```
r@r-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/launchpad-c-korn.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
r@r-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 2EBC26B60C5A2783 40976EAF437D05B5 40976EAF437D05B5 FC918B335044912E 71346C8340130828 A040830F7FAC5991
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyring /etc/apt/trusted.gpg.d/launchpad-c-korn.gpg --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 2EBC26B60C5A2783 40976EAF437D05B5 40976EAF437D05B5 FC918B335044912E 71346C8340130828 A040830F7FAC5991
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key 5044912E from hkp server keyserver.ubuntu.com
gpg: requesting key 40130828 from hkp server keyserver.ubuntu.com
gpg: requesting key 7FAC5991 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 0C5A2783: "Medibuntu Packaging Team <admin@lists.medibuntu.org>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key 5044912E: "Dropbox Automatic Signing Key <linux@dropbox.com>" not changed
gpg: key 40130828: "Launchpad PPA for Christoph Korn" not changed
gpg: key 7FAC5991: "Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>" not changed
gpg: Total number processed: 7
gpg:              unchanged: 7
r@r-laptop:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [191B]                                                                                      
Get:2 http://linux.dropbox.com lucid Release.gpg [489B]                                                                                   
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_AU                                                                         
Get:3 http://archive.ubuntu.com lucid Release.gpg [189B]                                                                               
Hit http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_AU                                                                        
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_AU                                           
Get:4 http://linux.dropbox.com lucid Release [2,599B]                                                       
Get:5 http://dl.google.com stable Release [1,310B]                                                                                        
Ign http://linux.dropbox.com lucid Release                                                                                   
Err http://dl.google.com stable Release                                                                                                   
  
Get:6 http://ppa.launchpad.net lucid Release.gpg [307B]                                                                                   
Ign http://ppa.launchpad.net/c-korn/ppa/ubuntu/ lucid/main Translation-en_AU                                               
Hit http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_AU                                                   
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_AU                               
Hit http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_AU                             
Get:7 http://archive.ubuntu.com lucid-updates Release.gpg [189B]                                                           
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_AU                                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_AU                     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_AU                       
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_AU                     
Get:8 http://archive.ubuntu.com lucid-security Release.gpg [189B]                                                          
Hit http://linux.dropbox.com lucid/main Packages                                                                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_AU                                                
Get:9 http://ppa.launchpad.net lucid Release [57.3kB]                                                
Ign http://ppa.launchpad.net lucid Release                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_AU
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_AU
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_AU
Get:10 http://archive.ubuntu.com lucid Release [57.2kB]
Ign http://archive.ubuntu.com lucid Release                                                   
Get:11 http://packages.medibuntu.org lucid Release.gpg [197B]                                 
Ign http://packages.medibuntu.org/ lucid/free Translation-en_AU                
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_AU
Get:12 http://archive.ubuntu.com lucid-updates Release [44.7kB]
Ign http://archive.ubuntu.com lucid-updates Release                                           
Hit http://ppa.launchpad.net lucid/main Packages                                              
Get:13 http://archive.ubuntu.com lucid-security Release [38.5kB]     
Ign http://archive.ubuntu.com lucid-security Release    
Get:14 http://packages.medibuntu.org lucid Release [6,854B]
Hit http://archive.ubuntu.com lucid/main Packages       
Hit http://archive.ubuntu.com lucid/restricted Packages 
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Packages   
Hit http://archive.ubuntu.com lucid/universe Sources    
Hit http://archive.ubuntu.com lucid/multiverse Packages 
Ign http://packages.medibuntu.org lucid Release         
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/restricted Sources                
Hit http://archive.ubuntu.com lucid-security/universe Packages                 
Hit http://archive.ubuntu.com lucid-security/universe Sources                  
Hit http://archive.ubuntu.com lucid-security/multiverse Packages               
Hit http://archive.ubuntu.com lucid-security/multiverse Sources                
Hit http://packages.medibuntu.org lucid/non-free Packages                      
Fetched 9,920B in 3s (2,987B/s)
Reading package lists... Done
W: GPG error: http://linux.dropbox.com lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC918B335044912E
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991

W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 71346C8340130828
W: GPG error: http://archive.ubuntu.com lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://archive.ubuntu.com lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://packages.medibuntu.org lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by StudioCascade on 2010-08-31
I also get the same error on key 8E5D2411637A5E2A
I discovered that this had something to do with the Akirad Repository. (from Cinelerra)
The problem gets solved when I remove the following entries from '3rd party software':
```
Akirad Repository - Main (http://ppa.launchpad.net/akirad/akirad/ubuntu lucid) 
Akirad Repository - Main (http://ppa.launchpad.net/akirad/ppa/ubuntu lucid) 
Akirad Repository Sources- Main (http://ppa.launchpad.net/akirad/akirad/ubuntu lucid) 
Akirad Repository Sources- Main (http://ppa.launchpad.net/akirad/ppa/ubuntu lucid) 
```

But... when i restart my computer, these entries are back in my repository.
Does anyone know what i can do about that?

Thanks a lot.

---

