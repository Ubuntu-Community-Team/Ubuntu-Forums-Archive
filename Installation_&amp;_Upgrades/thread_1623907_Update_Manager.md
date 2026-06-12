---
title: "Update Manager"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by Jim Lewis on 2010-11-17
Last week, the little orange triangle that tells me I have updates to install turned up.

When clicked, I got the Update Manager and when asking it to check on what's available it tried to download 70 some items, but stalled on number 47.

I got a message: "Could not download all repository indexes."

The box below contained a list of files, such as: "http:/security . . . etc."

At the bottom of the list was the statement:  "Some indexes failed to download.  They have been ignored, or old ones used instead."  

From there all I can do is back out of the Update Manager.

The orange triangle remains, and I get the same result when I click on it.

Something isn't working right.  Is it important?  Is there a fix?

Thanks,

Jim

---

### Post by sikander3786 on 2010-11-17
Go to Applications > Accessories > Terminal and post the output of,

```
sudo apt-get update
```

---

### Post by Jim Lewis on 2010-11-17
Same thing:

jim@jim-desktop:~$ sudo apt-get update
[sudo] password for jim: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg               
Ign [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release.gpg        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid Release                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates Release            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages       
Hit [http://archive.canonical.com](http://archive.canonical.com) intrepid/partner Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources
  404 Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources
  404 Not Found [IP: 91.189.88.37 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages
  404 Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/main Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources
  404 Not Found [IP: 91.189.88.37 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/restricted Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/universe Sources
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Packages
  404 Not Found [IP: 91.189.88.30 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
  404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.37 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.88.30 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.88.30 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
jim@jim-desktop:~$

---

### Post by sikander3786 on 2010-11-17
Are you using Intrepid? Intrepid reached end of life long time ago and the repositories have been shut down.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You need a newer version. Consider 10.04.1 or 10.10.

---

