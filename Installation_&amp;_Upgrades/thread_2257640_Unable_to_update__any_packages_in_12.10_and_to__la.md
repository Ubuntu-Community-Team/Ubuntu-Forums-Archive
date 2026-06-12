---
title: "Unable to update  any packages in 12.10 and to  latest version 14.10"
date: 2014-12-21
forum: Installation &amp; Upgrades
---

### Post by SathyaNG on 2014-12-21
Hello,

i have installed ubuntu 12.10 in my laptop as dual boot along with Win 8. actually both OS were working fine.

now i found ubuntu 14.10 and  tried to update my current ubuntu 12.10 but none of the opetions mentiond in other posts were not working.
please help me to update 12.10 with latest ubuntu version 14.10.

here is the output of :  asngcs@ubuntu:~$ sudo apt-get update```
asngcs@ubuntu:~$ sudo apt-get update
[sudo] password for asngcs: 
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal InRelease                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed InRelease
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) quantal/partner amd64 Packages       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports Release
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_US   
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en      
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-proposed/universe Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Sources
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe amd64 Packages
  404  Not Found [IP: 91.189.91.24 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-backports/universe Translation-en
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/main/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-proposed/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/source/Sources)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-backports/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.24 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by sudodus on 2014-12-21
> **SathyaNG said:**
> Hello,

i have installed ubuntu 12.10 in my laptop as dual boot along with Win 8. actually both OS were working fine.

now i found ubuntu 14.10 and  tried to update my current ubuntu 12.10 but none of the opetions mentiond in other posts were not working.
please help me to update 12.10 with latest ubuntu version 14.10.



Welcome to the Ubuntu Forums :-)

Ubuntu version 12.10 has passed end of life and cannot easily be upgraded. I suggest that you ***backup*** (save copies of) your personal files and make a fresh installation of Ubuntu 14.04.1 LTS, which is a long time support version (supported until April 2019) while 14.10 is only supported for nine months, until July 2015.

See these links
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by grahammechanical on 2014-12-21
There was a similar post to this the other day. In that thread I provided this link

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

You will have to go from 12.10 to 13.04 to 13.10 and then on to 14.04 before you get a supported Ubuntu. Your choice is to do a series of End of Life upgrades or a fresh install of Ubuntu 14.04. I would advise 14.04 as that has 5 years support from April this year. If you move on to 14.10 you will have to upgrade to 15.04 and then 15.10 before you get the next LTS release, which is 16.04.

Regards.

---

