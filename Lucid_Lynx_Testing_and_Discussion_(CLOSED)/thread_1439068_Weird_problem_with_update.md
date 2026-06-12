---
title: "Weird problem with update"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by littlesatan on 2010-03-25
Hey guys.
I don't remember when exactly it started, and have no idea what can cause this. Even when I comment all lines in my sources.list, I still getting this:
```
$ sudo apt-get update
Ign http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/lucid/release/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/scott/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/ubuntu/lucid/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release
Hit http://ppa.launchpad.net lucid Release
Ign http://ppa.launchpad.net lucid Release
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net**/lucid/release/ubuntu/dists/lucid/main/**binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net**/ubuntu/lucid/ubuntu/dists/lucid/main/**binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by jaoc223 on 2010-03-25
I'm having the same issues with ppa as well as with the main servers, it started two days ago for me.

---

### Post by _h_ on 2010-03-25
I've gotten that before when I had Karmic installed, wait like a day or so. Launchpad usually has the repos back and working in a short time.

---

### Post by dino99 on 2010-03-25
what are you doing with ppa ?
download from official lucid repo and remove all others extra repo

---

### Post by psyke83 on 2010-03-25
> **littlesatan said:**
> Hey guys.
I don't remember when exactly it started, and have no idea what can cause this. Even when I comment all lines in my sources.list, I still getting this:
```
$ sudo apt-get update
Ign http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/lucid/release/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/scott/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/ubuntu/lucid/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release
Hit http://ppa.launchpad.net lucid Release
Ign http://ppa.launchpad.net lucid Release
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Hit http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Ign http://ppa.launchpad.net lucid/main Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net**/lucid/release/ubuntu/dists/lucid/main/**binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net**/ubuntu/lucid/ubuntu/dists/lucid/main/**binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

You're using a PPA which appears to have been removed. If it really isn't listed in **/etc/apt/sources.list**, then it's an independent file in the **/etc/apt/sources.list.d/** folder. When you find the repository definition, delete the file or comment the lines within it.

---

### Post by jaoc223 on 2010-03-26
psyke83 what does it mean if you're getting the ignore from us main servers?

jaco@ubuntu:~$ sudo apt-get update
[sudo] password for jaco: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,374kB]     
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,222B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [651kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,768B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,533kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,183kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [194kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [118kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 11.1MB in 7s (1,561kB/s)                                               
Reading package lists... Done
jaco@ubuntu:~$

---

### Post by dino99 on 2010-03-26
that part is ignored only: Translation-en_US

so, it can be a typo or i10n temporary problem, dont worry

---

### Post by psyke83 on 2010-03-26
I notice that you still have PPA lines listed in your output - including a Karmic repository. Ideally you should remove the Karmic ones, otherwise you may experience problems.

---

### Post by jaoc223 on 2010-03-26
Thanks for quick replies guys, I will sort out the karmic and ppa's.
Thanks again. Jaco

---

### Post by littlesatan on 2010-03-26
> **psyke83 said:**
> You're using a PPA which appears to have been removed. If it really isn't listed in **/etc/apt/sources.list**, then it's an independent file in the **/etc/apt/sources.list.d/** folder. When you find the repository definition, delete the file or comment the lines within it.
[psyke83]("http://ubuntuforums.org/member.php?u=50843"),
Yeah, you're right: the problem caused by **lucid-release-lucid.list** and **ubuntu-lucid-lucid.list** in **sources.list.d/**. Thanks.

---

