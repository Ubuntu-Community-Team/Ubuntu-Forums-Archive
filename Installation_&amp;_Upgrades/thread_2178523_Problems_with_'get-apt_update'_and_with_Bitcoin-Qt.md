---
title: "Problems with 'get-apt update' and with Bitcoin-Qt installation"
date: 2013-10-03
forum: Installation &amp; Upgrades
---

### Post by nrwahl-d on 2013-10-03
Let me preface by saying I recently had to reinstall Ubuntu 12.04 on this computer, and that I had previously installed Bitcoin-Qt on it before the re-installation.

I followed what I believe were the same steps, straight from the instructions on teh website.
'sudo add-apt-repository ppa:bitcoin/bitcoin'
'sudo apt-get update'
...
And this is where the problem arose.

reid@reid-computer:~$ sudo apt-get update
[sudo] password for reid: 
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release                       
  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources/DiffIndex                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources/DiffIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages/DiffIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages/DiffIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources/DiffIndex      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources/DiffIndex   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources/DiffIndex     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages/DiffIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Fetched 865 B in 7s (117 B/s)                                                  
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

 
I then tried 'sudo apt-get install bitcoin-qt', which appeared to work at first, but I can't locate the program within my system.

Maybe I'm doing something stupid. I've had a long day of Ubuntu-related frustration and am just trying to get this bit taken care of. Help will be appreciated.

EDIT: After a restart (following a frozen screen), Bitcoin-Qt is accessible. However, I still have this problem with my 'get-apt update' command and I'd appreciate help making sense of that.

---

### Post by Bashing-om on 2013-10-03
nrwahl-d; Hi !

This is a case of It happens because you don't have a suitable public key for a repository. The system is protecting you in that it can not authenticate the source and files. In this case the source is trustworthy and tell the system so thusly:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 40976EAF437D05B5
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 16126D3A3E5C1192

```

[INDENT][INDENT]ain't ubuntu wonderful
[/INDENT][/INDENT]

---

### Post by nrwahl-d on 2013-10-04
Thank you! Everything's as it should be, it seems.
Problem solved by a fellow 479-er, no less.

---

### Post by Bashing-om on 2013-10-04
nrwahl-d; Hey .

Small thing, glad the situation is now under control.

I hate it when I am dense but - The meaning of term "a fellow 479-er" escapes me !

[INDENT][INDENT]sometimes I wonder other times I do not know
[/INDENT][/INDENT]

---

### Post by nrwahl-d on 2013-10-04
"Location: Ozarks, Arkansas"

Most likely you're in the 479 area code. Could be 501 I guess.

---

### Post by Bashing-om on 2013-10-04
nrwahl-d; OK... Now I have comprehension.

Nope, I be a north central ridge runner (retired with a computer running 'buntu flavors).. be in the 501 district.


[INDENT][INDENT]doin' what I can to make things good
[/INDENT][/INDENT]

---

