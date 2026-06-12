---
title: "Problems with GPG keys and updating..."
date: 2011-01-30
forum: Installation &amp; Upgrades
---

### Post by slashwannabe94 on 2011-01-30
Hello all, 

I have ran into another error recently which will not let me update, upgrade or install anything from the repository. I have included screenshots of my software sources to assist you guys in helping me solve this issue... Well here it is dudes and dudettes...

When i use the "sudo apt-get update" command i receive the following output. 

```

```marcom@marcom-desktop:~$ sudo apt-get update
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg [189B]                                                                                       
Get: 2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB [62.9kB]          
Get: 3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB [37.7kB]                      
Get: 4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB [2,332B]
99% [2 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_GB                                                     
38% [3 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_GB                                               
2% [4 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_GB                                              
Get: 5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB [33.9kB]                                    
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release.gpg [198B]                                         
24% [5 Translation-en_GB bzip2 0B] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_GB                                                 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_GB                                             
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_GB       
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_GB       
Get: 7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [189B]                                 
Get: 8 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                                      
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_GB                                    
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_GB 
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_GB         
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_GB                       
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_GB        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_GB          
Get: 10 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                              
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [57.2kB]                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                             
Get: 12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release [57.2kB]             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release                                                      
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                                
Get: 14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release [44.7kB]                           
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release                                               
  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Fetched 980B in 2s (367B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: An error occurred during the signature verification.  The repository is not updated and the previous index files will be used.  GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

```

--------------------------------------------------------------------------------------------------------------------

Thanks, 

SlashWannabe94

---

### Post by slashwannabe94 on 2011-01-30
The images seemed to have not uploaded properly so here is attempt two haha.

---

### Post by slashwannabe94 on 2011-01-30
> **slashwannabe94 said:**
> The images seemed to have not uploaded properly so here is attempt two haha.

Sorry about the double post guys, my internet seems to be going nuts! --- Guess that's what i get for using mobile broadband as a primary method of internet access.

---

### Post by Old_Grey_Wolf on 2011-01-30
Enter this in a terminal 
```
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783
gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -
gpg --keyserver keyserver.ubuntu.com --recv 40976EAF437D05B5
gpg --export --armor 40976EAF437D05B5  | sudo apt-key add -
```
Then try the update again.

---

### Post by slashwannabe94 on 2011-01-30
We have progress dude. 

i now get this error at the bottom of the apt-get update command. 

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures were invalid: BADSIG 2EBC26B60C5A2783 Medibuntu Packaging Team <admin@lists.medibuntu.org>

any ideas dude?

---

### Post by Old_Grey_Wolf on 2011-01-30
A google search gave me this bug report. Follow the instructions at your own risk. I have not had the problem myself so I can not say if it works or not. [https://answers.launchpad.net/medibuntu/+question/98089](https://answers.launchpad.net/medibuntu/+question/98089)

---

### Post by slashwannabe94 on 2011-01-30
Thanks man, i will do.

---

### Post by Old_Grey_Wolf on 2011-01-30
Please, let me know it it worked.

---

### Post by slashwannabe94 on 2011-01-30
Ahhh crap. i followed what the posts said and i think it may have been with malicious intentions. 

i ran the commands 

sudo rm /var/lib/apt/lists/partial/*
 sudo rm /var/lib/apt/lists/*
sudo apt-get update


and after the apt-get update i now receive a new error :( 

E: Lists directory /var/lib/apt/lists/partial is missing.

============================================

Please help me dude.

---

### Post by slashwannabe94 on 2011-01-30
ooo, i fixed the E: Lists directory /var/lib/apt/lists/partial is missing. error by creating a new directory using the sudo mkdir -p /var/lib/apt/lists/partial command. it now proceeds with the update and has no GPG error. that workaround was successful. Thanks for helping me out man :) 

SlashWannabe94

---

### Post by Old_Grey_Wolf on 2011-01-30
Try entering this in the terminal```

sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by Old_Grey_Wolf on 2011-01-30
OK, I see you recreated the directory yourself before I replied. You got me a little concerned. I'm glad it is working for you.

Edit:  I think there is a new way to update the Keys. I'm 62 years old; therefore, I'm not current on the new stuff. I think there is a command like "apt-key update" that gets the keys for you. You may want to google on it and try it the next time you have this problem. :)

---

### Post by slashwannabe94 on 2011-01-31
Thanks man you helped me out here haha. Anyway I'm 16 and i am not even up to date haha. Knowledge comes with age :D

---

