---
title: "sudo apt-get update"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by burke9688 on 2006-12-07
Any way to fix this what I see as a MAJOR problem?



```

jakey@2BR00T4L4UZ:~/ndiswrapper-1.31$ sudo apt-get update
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]                     
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US               
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]             
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US           
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US     
Hit http://security.ubuntu.com edgy-security/main Packages                     
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US       
Hit http://security.ubuntu.com edgy-security/restricted Packages               
Hit http://us.archive.ubuntu.com edgy Release                                  
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://us.archive.ubuntu.com edgy-updates Release                          
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Ign http://us.archive.ubuntu.com edgy/main Packages                            
Hit http://security.ubuntu.com edgy-security/universe Packages                 
Hit http://us.archive.ubuntu.com edgy/restricted Packages                      
Hit http://us.archive.ubuntu.com edgy/main Sources                             
Hit http://us.archive.ubuntu.com edgy/restricted Sources                       
Hit http://us.archive.ubuntu.com edgy/universe Packages                        
Hit http://us.archive.ubuntu.com edgy-updates/main Packages                    
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages
Get:4 http://us.archive.ubuntu.com edgy/main Packages [1220kB]
99% [4 Packages gzip 0]             
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com edgy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 4B in 32s (0B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by averagejoe84 on 2006-12-07
have you tried sudo apt-get clean ?

---

### Post by burke9688 on 2006-12-07
No I have not, but when I finish downloading my bands Album Art and Songs, I'll move my comp to ethernet cable to do that.

This is all for a bigger purpose.
To install wifi, so I can use Ubuntu around thee house.

---

### Post by burke9688 on 2006-12-07
Just tried that.
Got to  Get:4 and gave me this.
```
Get:4 http://us.archive.ubuntu.com edgy/main Packages [1220kB]
99% [4 Packages gzip 0]             
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com edgy/main Packages
  Sub-process gzip returned an error code (1)
Fetched 4B in 31s (0B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by averagejoe84 on 2006-12-07
hmm Got me.. you could just disable that repo for now. I'll do some reading a see what I can find out.

---

### Post by burke9688 on 2006-12-07
> **averagejoe84 said:**
> hmm Got me.. you could just disable that repo for now. I'll do some reading a see what I can find out.

I've been trying to do some reading up on it. But none of what i read made sense, or even related to what i was trying to accomplish!


thank you very much!

---

### Post by averagejoe84 on 2006-12-07
have you read the man page?

---

### Post by mangoHead84 on 2006-12-07
Hi Burke, 

I have the same problem:

srdan@srdan-desktop:/etc/apt$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg [191B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages [25.7kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [12.0kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports/multiverse Sources
Fetched 6B in 4s (1B/s)  
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-amd64/Packages.bz2)  MD5Sum mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-amd64/Packages.bz2)  MD5Sum mismatch
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
srdan@srdan-desktop:/etc/apt$ 


It seems to be something with the "Translation-en_US" packages.

---

### Post by burke9688 on 2006-12-07
From what they both say.

The MD5Sums are mismatched.

SO we need a way to update without the md5 sums.

---

