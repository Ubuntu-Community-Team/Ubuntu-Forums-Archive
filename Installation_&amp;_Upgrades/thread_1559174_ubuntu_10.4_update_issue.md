---
title: "ubuntu 10.4 update issue"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by aniljaganath on 2010-08-23
I am facing the following issue in updating the ubuntu 10.4 to install some software like wine.
[INDENT]e5253564@bagvapp:/$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [2,328B]                                            
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg [2,305B]
Get:3 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US [2,374B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg [2,330B]
89% [3 Translation-en_US bzip2 0B] [Waiting for headers] [4 Release.gpg 1,410B/2,330B 60%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US                  
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US [2,345B]             
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US [2,357B]
60% [5 Translation-en_US bzip2 0B] [6 Translation-en_US 79B/2,357B 3%] [4 Release.gpg 1,410B/2,330B 60%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                                      
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US [2,353B]                       
52% [6 Translation-en_US bzip2 0B] [7 Translation-en_US 294B/2,353B 12%] [4 Release.gpg 1,410B/2,330B 60%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                                  
Get:8 [http://archive.canonical.com](http://archive.canonical.com) lucid Release [2,320B]                                                 
Err [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                         
  
Get:9 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US [2,357B]    
57% [7 Translation-en_US bzip2 0B] [9 Translation-en_US 513B/2,357B 21%] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US                        
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [2,321B]                           
52% [9 Translation-en_US bzip2 0B] [10 Release.gpg 728B/2,321B 31%] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US                 
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US [2,361B]   
Get:12 [http://archive.canonical.com](http://archive.canonical.com) jaunty Release [2,322B]     
Err [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                    
  
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US [2,373B]
57% [11 Translation-en_US bzip2 0B] [13 Translation-en_US 1,190B/2,373B 50%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US [2,369B]
53% [13 Translation-en_US bzip2 0B] [14 Translation-en_US 1,389B/2,369B 58%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Get:15 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US [2,373B]
46% [14 Translation-en_US bzip2 0B] [15 Translation-en_US 232B/2,373B 9%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [2,323B]     
48% [15 Translation-en_US bzip2 0B] [16 Release.gpg 1,791B/2,323B 77%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US [2,363B]
Get:18 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US [2,375B]
46% [17 Translation-en_US bzip2 0B] [18 Translation-en_US 889B/2,375B 37%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Get:19 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US [2,371B]
47% [18 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
41% [19 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Get:20 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US [2,375B]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release.gpg [2,323B]
40% [20 Translation-en_US bzip2 0B] [21 Release.gpg 1,484B/2,323B 63%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:22 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US [2,375B]
40% [22 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Get:23 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US [2,363B]
Get:24 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US [2,375B]
39% [23 Translation-en_US bzip2 0B] [24 Translation-en_US 1,212B/2,375B 51%]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US 
Get:25 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US [2,371B]
39% [24 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US
35% [25 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release [2,297B]  
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [2,313B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release       
  
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
  
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [2,315B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
  
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release [2,315B]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release
  
Fetched 68.0kB in 3s (22.4kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.canonical.com](http://archive.canonical.com) jaunty Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-proposed Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/lucid/Release](http://archive.canonical.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release](http://archive.canonical.com/ubuntu/dists/jaunty/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-proposed/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/INDENT]Please give your suggestion, how to resolve the issue.

I have also tried to install wine with the help of synaptic manager. it also fails with different file size mismatch errors.

---

### Post by mörgæs on 2010-08-23
There is some cruft on this machine. It seems to have been upgraded at least twice, and there are still references to 9.04 (being just another example that a clean install is safer).

Try to remove all pointers to earlier versions in **sources.list** by adding a # in front and see if it works.

---

### Post by aniljaganath on 2010-08-24
Thanks for the quick response.

But as I am a novice user. still I am not getting it clearly.
I have checked the sources.list file and the contents are shown below:
[INDENT]# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Beta i386 (20090324)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
#deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free # disabled on upgrade to karmic
[/INDENT]I don't know, if the content is correct.
So please help me to come out of this problem.

Thanks in advance

---

### Post by jeddycakes on 2010-08-24
Dude, I agree with mörgæs, it look like there a lot of old stuff on there that could be conflicting with what your trying to do; its a problem I have faced myself before.

I recommend that you more all data that you want to keep (pr0n, illegal movies/music etc) to an external source, and just reformat and reinstall. Its a ball-ache but this way you'll have a nice new clean system with no conflictions.

---

### Post by aniljaganath on 2010-08-24
Thanks man.
Actually I am using this through Vmware player.
I have a ubuntu 9.04 vmware image, then I have upgraded it to ubuntu 10.04
There I have faced these problems.

---

### Post by aniljaganath on 2010-08-24
Today, I have downloaded Ubuntu 10.04 from ubuntu website. and installed it in vmware player.

After that I am also facing the same problem:
[INDENT]e5253564@ubuntu:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [2,325B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [2,311B]
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US [2,365B]
Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US [2,377B]
89% [3 Translation-en_US bzip2 0B] [Waiting for headers] [4 Translation-en_US 1,419B/2,377B 59%]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US                    
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US [2,351B]                
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US [2,363B]
60% [5 Translation-en_US bzip2 0B] [6 Translation-en_US 73B/2,363B 3%] [4 Translation-en_US 1,419B/2,377B 59%]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                                         
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US [2,359B]                          
52% [6 Translation-en_US bzip2 0B] [7 Translation-en_US 282B/2,359B 11%] [4 Translation-en_US 1,419B/2,377B 59%]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                                     
Get:8 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US [2,373B]                     
Get:9 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US [2,377B]                   
47% [4 Translation-en_US bzip2 0B] [7 Translation-en_US 282B/2,359B 11%] [9 Translation-en_US 453B/2,377B 19%]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US                            
36% [8 Translation-en_US bzip2 0B] [7 Translation-en_US 282B/2,359B 11%] [9 Translation-en_US 453B/2,377B 19%]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US                              
34% [9 Translation-en_US bzip2 0B] [7 Translation-en_US 282B/2,359B 11%] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US            
Get:10 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US [2,363B]       
37% [7 Translation-en_US bzip2 0B] [10 Translation-en_US 1,855B/2,363B 78%] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US                        
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [2,327B]                           
Get:12 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US [2,367B]
36% [10 Translation-en_US bzip2 0B] [12 Translation-en_US 949B/2,367B 40%] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US                     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [2,317B]                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release              
  
Get:14 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US [2,379B]
42% [12 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
35% [14 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Get:15 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US [2,375B]
Get:16 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US [2,379B]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [2,303B]                  
40% [17 Release gpgv 2,303B] [15 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                    
  
34% [16 Translation-en_US bzip2 0B] [Waiting for headers]bzip2: (stdin) is not a bzip2 file.
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [2,319B]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
  
Fetched 42.3kB in 2s (19.7kB/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/INDENT]
So now I am facing the same probelm in new installation also.

---

### Post by aniljaganath on 2010-08-24
The update problem with new ubuntu 10.04 installation is resolved.
The internet connection was creating problem with the new setup.

Thanks

---

### Post by mörgæs on 2010-08-24
Good. Please mark the thread 'solved'.

---

