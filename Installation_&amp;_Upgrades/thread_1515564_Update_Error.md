---
title: "Update Error"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by miss_beckie_louise on 2010-06-22
Every time I log on, or get told I have updates this comes up:



W[I]: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263 
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead. [/I]



Is there anything I can do for all my updates to work again? Please let me know! I'm getting kinda desperate.

---

### Post by Don Barzini on 2010-06-22
> **miss_beckie_louise said:**
> Is there anything I can do for all my updates to work again? Please let me know! I'm getting kinda desperate.

Try this in a terminal window Miss Beckie Louise.....

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5 58403026387EE263 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5 40976EAF437D05B5
```

Then run...

```
sudo apt-get update
```

See if that works....

---

### Post by miss_beckie_louise on 2010-06-22
I tried it, but this came up

[i]
Get: 1 [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_GB               
Get: 2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg [189B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_GB                 
Get: 3 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB       
Get: 4 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release.gpg [189B]                
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Translation-en_GB               
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_GB                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_GB               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_GB               
Get: 5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release.gpg [189B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Translation-en_GB         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Translation-en_GB             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Translation-en_GB       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB       
Get: 6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB     
Get: 7 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Translation-en_GB        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Translation-en_GB  
Get: 8 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release [1016B]         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB      
Get: 9 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg [189B]            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_GB       
Get: 10 [http://dl.google.com](http://dl.google.com) stable Release [2544B]                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_GB           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_GB
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_GB
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                        
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy Release                     
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release                              
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages                        
Get: 11 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release [58.5kB]               
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Get: 12 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release [58.5kB]              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources                         
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release                            
  
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy/main Packages                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release                           
Get: 13 [http://dl.google.com](http://dl.google.com) stable/main Packages [1056B]                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
  
Fetched 5116B in 1s (4665B/s)
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
[/i]


:S confused.

---

### Post by Don Barzini on 2010-06-22
Try this now...

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 437D05B5

```

Maybe this too if the above doesn't work....

```
sudo gpg --keyserver keyserver.ubuntu.com --recv-keys 437D05B5 && gpg --export --armor 437D05B5 | sudo apt-key add -
```

---

### Post by miss_beckie_louise on 2010-06-22
I put the first one in, but I dunno if it worked: 


Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 437D05B5
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: public key "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1


How do I tell?

---

### Post by miss_beckie_louise on 2010-06-22
Oh, I checked my updates and they all went but one: 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263


Is it just WINE?? Coz I've had problems with it since I installed it in the first place.

---

### Post by Don Barzini on 2010-06-22
> **miss_beckie_louise said:**
> 
How do I tell?

Run...

```
sudo apt-get update
```

If that still doesn't work..... you may have to try something more drastic like recreating all of your .gpg files in your /etc/apt directory such as this user had to do here....

[http://techpad.co.uk/content.php?sid=84](http://techpad.co.uk/content.php?sid=84)

He deleted them.... But, I would rename them first, then recreate them as he did.

---

### Post by Don Barzini on 2010-06-22
> **miss_beckie_louise said:**
> Oh, I checked my updates and they all went but one: 

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263


Is it just WINE?? Coz I've had problems with it since I installed it in the first place.

You could comment out that repository line in your **/etc/apt/sources.list** file if you no longer use the program and require updates.

---

### Post by miss_beckie_louise on 2010-06-22
Thank you so much for the help! I tried it and what was on the website n neither worked. I'll leave it, but at least it works now!

:D WHOOP!

---

### Post by miss_beckie_louise on 2010-06-22
> **Don Barzini said:**
> You could comment out that repository line in your **/etc/apt/sources.list** file if you no longer use the program and require updates.

Permission Denied :(

---

### Post by Don Barzini on 2010-06-22
> **miss_beckie_louise said:**
> Permission Denied :(

```
gksudo gedit /etc/apt/sources.list
```

Then just put a **#** in front of the line listing that repository.

Good Luck.

---

### Post by miss_beckie_louise on 2010-06-22
Thank you :) I got it up looked at it and had no idea what to do, but no warning signs have come up :) so i'm guessing it's all worked :D

Thanks!

---

