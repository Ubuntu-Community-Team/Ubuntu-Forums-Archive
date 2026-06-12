---
title: "[SOLVED] Update Manager refresh &amp;quot;Last updated 8 days ago&amp;quot;"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2008-07-23
I'm running 8.04.1 (All updates)

I've just noticed a problem with the update manager.

The Warning Triangle keeps popping up and when I refresh the sources the Update Manager windows keeps saying:
 
"The package information was last updated 8 days ago." 

This is after I run the update and refresh the sources. I've also changed the location from "United Kingdom" to "Main Server" just in case it was a issue with a mirror!

I've ran 
apt-get autoremove
&
apt-get autoclean

and it now says it was last updated 9 days ago!

Anyone else got this issue?

Or any ideas as to the problem?

---

### Post by solitaire on 2008-07-23
*Bump*

anyone got any ideas?

---

### Post by iaculallad on 2008-07-23
Try:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by solitaire on 2008-07-23
No difference!

Update Manager is still saying it was "Last updated 9 days ago"

---

### Post by watsbe on 2008-07-24
Are you getting any failure reported when you update?
This was happening to me a week or so ago when one of the repositories was down.  Perhaps that "last update" date is the last update for ALL repositories, not just thelast time you ran the update process.

---

### Post by solitaire on 2008-07-24
No errors or failures are being reported.

---

### Post by lenn-art on 2008-07-24
I have the same  problem. My pakketinformation isn't updated for 9 days. However, that's not right!

```
sudo apt-get update && sudo apt-get upgrade 
```doesn't work

---

### Post by solitaire on 2008-07-24
you have to run them seperatly

---

### Post by solitaire on 2008-07-24
*update*
I ran $sudo apt-get update
and gotthe following
```
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_GB                                                              
Hit http://archive.canonical.com hardy Release                                                                                
Hit http://archive.canonical.com hardy/partner Packages                                                                     
Hit http://archive.canonical.com hardy/partner Sources
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB
Hit http://archive.ubuntu.com hardy Release.gpg
Hit http://archive.ubuntu.com hardy/main Translation-en_GB
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://archive.ubuntu.com hardy/universe Translation-en_GB
Hit http://archive.ubuntu.com hardy/restricted Translation-en_GB
Hit http://archive.ubuntu.com hardy/multiverse Translation-en_GB
Hit http://archive.ubuntu.com hardy-backports Release.gpg
Ign http://archive.ubuntu.com hardy-backports/universe Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/main Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/multiverse Translation-en_GB
Ign http://archive.ubuntu.com hardy-backports/restricted Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy-proposed Release.gpg
Ign http://archive.ubuntu.com hardy-proposed/universe Translation-en_GB
Hit http://archive.ubuntu.com hardy-proposed/main Translation-en_GB
Hit http://archive.ubuntu.com hardy-proposed/multiverse Translation-en_GB
Hit http://archive.ubuntu.com hardy-proposed/restricted Translation-en_GB
Hit http://security.ubuntu.com hardy-security/main Packages
Get: 1 http://archive.ubuntu.com hardy-updates Release.gpg [189B]
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_GB
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_GB
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_GB
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_GB
Hit http://archive.ubuntu.com hardy Release            
Hit http://archive.ubuntu.com hardy-backports Release               
Hit http://archive.ubuntu.com hardy-proposed Release
Hit http://security.ubuntu.com hardy-security/restricted Packages   
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Get: 2 http://archive.ubuntu.com hardy-updates Release [58.5kB]
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://archive.ubuntu.com hardy/main Packages  
Hit http://archive.ubuntu.com hardy/universe Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Hit http://archive.ubuntu.com hardy/multiverse Packages
Hit http://archive.ubuntu.com hardy/main Sources
Hit http://archive.ubuntu.com hardy/universe Sources
Hit http://archive.ubuntu.com hardy/restricted Sources
Hit http://archive.ubuntu.com hardy/multiverse Sources
Hit http://archive.ubuntu.com hardy-backports/universe Packages
Hit http://archive.ubuntu.com hardy-backports/main Packages
Hit http://archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://archive.ubuntu.com hardy-backports/restricted Packages
Hit http://archive.ubuntu.com hardy-backports/universe Sources
Hit http://archive.ubuntu.com hardy-backports/main Sources
Hit http://archive.ubuntu.com hardy-backports/multiverse Sources
Hit http://archive.ubuntu.com hardy-backports/restricted Sources
Hit http://archive.ubuntu.com hardy-proposed/universe Packages
Hit http://archive.ubuntu.com hardy-proposed/main Packages
Hit http://archive.ubuntu.com hardy-proposed/multiverse Packages
Hit http://archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://archive.ubuntu.com hardy-proposed/universe Sources
Hit http://archive.ubuntu.com hardy-proposed/main Sources
Hit http://archive.ubuntu.com hardy-proposed/multiverse Sources
Hit http://archive.ubuntu.com hardy-proposed/restricted Sources
Get: 3 http://archive.ubuntu.com hardy-updates/universe Packages [74.5kB]
Get: 4 http://archive.ubuntu.com hardy-updates/main Packages [285kB]
Get: 5 http://archive.ubuntu.com hardy-updates/multiverse Packages [16.4kB]                                                                                                                         
Get: 6 http://archive.ubuntu.com hardy-updates/restricted Packages [6636B]                                                                                                                          
Get: 7 http://archive.ubuntu.com hardy-updates/universe Sources [16.6kB]                                                                                                                            
Get: 8 http://archive.ubuntu.com hardy-updates/main Sources [81.9kB]                                                                                                                                
Get: 9 http://archive.ubuntu.com hardy-updates/multiverse Sources [2612B]                                                                                                                           
Get: 10 http://archive.ubuntu.com hardy-updates/restricted Sources [908B]                                                                                                                           
Fetched 544kB in 7s (70.3kB/s)                                                                                                                                                                      
Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_main_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com hardy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hardy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

I've emptied out the```
 /var/lib/apt/lists/
``` folder and ran the update again and Its ok till i reboot (Or wait a while).
Once I reboot (or leave it for a while) the above error happens again.

It still say's it's been 10 days since i refreshed the sources!!

It's getting annoying!!

Updates are still happening if I run the manually so it's not a huge inconvenience!!

---

### Post by solitaire on 2008-07-28
*Solved* :D:D:D

Worked out that the following files were not being "touched" by the update managers:
```

/var/lib/apt/periodic/update-success-stamp
/var/lib/apt/periodic/update-stamp

```

All i needed to do was run
```

sudo touch /var/lib/apt/periodic/update-success-stamp
sudo touch /var/lib/apt/periodic/update-stamp

```

Now things look ok!!

Looks like some of the packet managers don't "touch" these files so the date last checked does not change!

---

### Post by forkandles on 2008-11-26
This appears to be Bug Number 284541 which does not appear to have been fixed yet.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/284541](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/284541)

Your fix appears to have sorted out your problem but I have 2 things to note on my own 8.10.

The first file you mention, update-success-stamp, is empty.
I do not have the second one, update-stamp.

Any suggestions or is it just a matter of waiting for Bug 284541 to be fixed?

---

### Post by babygenius55 on 2009-09-25
Thank you very much. I don't know why I couldn't find this thread the last 8 times I looked for it. My problem is fixed.

---

