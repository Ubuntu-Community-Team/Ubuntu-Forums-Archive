---
title: "Failed to update"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by bobpur on 2011-03-28
[sudo] password for bobpur: 
Sorry, try again.
[sudo] password for bobpur: 
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                  
  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                         
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                         
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Fetched 588B in 0s (792B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
bobpur@UbuntuNE-laptop:~$ 




This is the result of "sudo apt-get update" I haven't been able to update because of these errors.

Oops! This is The Ubuntu Netbook Edition. 

Is this the OS's fault or do I have a setting screwed up somewhere?


Thanks.

---

### Post by mikewhatever on 2011-03-28
Something seems to be wrong with the internet connection. Are behind a proxy/firewall, for example on a school or company network?

---

