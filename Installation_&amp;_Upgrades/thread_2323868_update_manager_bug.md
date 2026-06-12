---
title: "update manager bug"
date: 2016-05-09
forum: Installation &amp; Upgrades
---

### Post by chester2 on 2016-05-09
greetings,

Running Ubuntu 14.04.4 on HP pavillion G6 lappie. No probs for yrs, today update manager stalled and this message shows

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Any help much appreciated.

Ta

Chester

---

### Post by grahammechanical on 2016-05-09
That is not a bug with Update Manager. Try this and post the printout in the thread enclosed with QUOTE tags.

```
sudo apt-get update
sudo apt-get upgrade
```

Sometimes these system messages suggest a solution. Did you get a suggestion this time? Have you tried it? 

Regards

---

### Post by chester2 on 2016-05-10
Greetings,

After running apt-get update I get the following 

"```
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release                               
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates Release [55.4 kB]           
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release                               
  
Get:6 [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release.gpg [198 B]                 
Get:7 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]                 
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release                     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [55.5 kB]            
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release                     
  
Hit [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                               
Err [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release                               
  
Get:10 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Sources [496 kB]      
Get:11 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [142 kB]       
Get:13 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg [316 B]
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [4,476 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [47.9 kB]  
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [2,718 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [607 kB]
Get:18 [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex [274 B] 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Get:19 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Sources [8,708 B]
Get:20 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Sources [127 kB]  
Get:21 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Sources [10.2 kB]
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main amd64 Packages [989 kB]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_AU           
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en  
Get:23 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted amd64 Packages [16.2 kB]
Get:24 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe amd64 Packages [275 kB]
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [16.9 kB]
Get:26 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main i386 Packages [1,051 kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [11.6 kB]
Get:28 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [131 kB]
Get:29 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [3,160 B]
Get:30 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [663 kB] 
Get:31 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted i386 Packages [16.1 kB]
Get:32 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe i386 Packages [284 kB]
Get:33 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse i386 Packages [17.1 kB]
Get:34 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main TranslationIndex [208 B]
Get:35 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [202 B]
Get:36 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted TranslationIndex [202 B]
Get:37 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe TranslationIndex [205 B]
Get:38 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/main Translation-en [415 kB]
Get:39 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/multiverse Translation-en [9,806 B]
Get:40 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/restricted Translation-en [3,869 B]
Get:41 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-updates/universe Translation-en [165 kB]
Get:42 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [11.6 kB]
Get:43 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [139 kB]
Get:44 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [3,339 B]
Get:45 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [208 B]
Get:46 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [199 B]
Get:47 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [202 B]
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [205 B]
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [253 kB]
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en [1,698 B]
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en [2,976 B]
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [83.9 kB]
Fetched 6,123 kB in 22s (273 kB/s)                                             
Reading package lists... Error!
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) precise-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://download.ebz.epson.net](http://download.ebz.epson.net) lsb3.2 Release: The following signatures were invalid: BADSIG E5E86C008AA65D56 Seiko Epson Corporation (Epson Inkjet Printer Driver) <epson-linux-inkjet@avasys.jp>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures were invalid: BADSIG 67E4A52AC865EB40 Launchpad PPA for OpenCPN

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/precise/Release](http://au.archive.ubuntu.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/precise-backports/Release](http://au.archive.ubuntu.com/ubuntu/dists/precise-backports/Release)  

W: Failed to fetch [http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release](http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release](http://archive.canonical.com/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://ppa.launchpad.net/opencpn/opencpn/ubuntu/dists/precise/Release](http://ppa.launchpad.net/opencpn/opencpn/ubuntu/dists/precise/Release)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release](http://extras.ubuntu.com/ubuntu/dists/precise/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."

On the top shortcut bar there is a red button with white horizontal bar, click on said item and it states the last few lines of code as above and suggests that "this usually means your installed packages have unmet dependancies
```" 

Thoughts?

C

---

### Post by vasa1 on 2016-05-10
In your first post you mentioned you were are 14.04 aka Trusty, but your next post gives the impression you're on 12.04 aka Precise.

What does **lsb_release -a** show?

Maybe you should put up the contents of **/etc/apt/sources.list** as well.

---

### Post by kansasnoob on 2016-05-10
I see you're using the au.archive and that was recently problematic for someone else:

[http://ubuntuforums.org/showthread.php?t=2322029](http://ubuntuforums.org/showthread.php?t=2322029)

So I'd try switching from the au.archive to the main server and see what happens:

[http://i.stack.imgur.com/YGtwc.png](http://i.stack.imgur.com/YGtwc.png)

---

### Post by chester2 on 2016-05-10
Greetings,

Thanks for the help all, changed to the main server for updates, ran update manager and problem disappeared. Excellent.

And yes Vasa1 I am running 12.04 (precise), a senior moment.....

Once again, ta muchly.

Chester

---

### Post by Bucky Ball on 2016-05-11
All good. Please mark as solved to help others (Thread Tools at top right or follow the link in my signature below). Thanks. ;)

(PS: Marking as solved will not close the thread to further discussion.)

---

