---
title: "libqt5core5a dependency conflict in 16.04"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2016-10-16
I'm  getting the same  **dependency problem** (with** *libqt5core5a***) when I try to install both *OnionShare* (version 0.9.1-1 from
 *deb [http://ppa.launchpad.net/micahflee/ppa/ubuntu](http://ppa.launchpad.net/micahflee/ppa/ubuntu) xenial main*) and *Calibre*, in Ubuntu-MATE 16.04:

  ```
--> sudo aptitude install onionshare
The following NEW packages will be installed:
  libqt5designer5{ab} onionshare python3-pyqt5{ab} python3-sip{a} 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,961 kB of archives. After unpacking 20.5 MB will be used.
The following packages have unmet dependencies:
 python3-pyqt5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:   
              - libqt5core5a, but 5.6.1+dfsg-2~xenial+build2 is installed. 
libqt5designer5 : Depends: qtbase-abi-5-5-1 which is a virtual package, provided by:   
              - libqt5core5a, but 5.6.1+dfsg-2~xenial+build2 is installed. 
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libqt5designer5 [Not Installed]                    
2)     onionshare [Not Installed]                         
3)     python3-pyqt5 [Not Installed]                      

Accept this solution? [Y/n/q/?] 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
```

  (I get the same message as above when I try to install Calibre, which is *not* from a PPA.)

  ```
--> apt-cache policy libqt5core5a  
libqt5core5a:
  Installed: 5.6.1+dfsg-2~xenial+build2
  Candidate: 5.6.1+dfsg-2~xenial+build2
  Version table:
*** 5.6.1+dfsg-2~xenial+build2 100
       100 /var/lib/dpkg/status
    5.5.1+dfsg-16ubuntu7.1 500
       500 [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive) xenial-updates/main amd64 Packages
    5.5.1+dfsg-16ubuntu7 500
       500 [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive) xenial/main amd64 Packages
```
  Also:
  ```
--> sudo aptitude -f install libqt5core5a
libqt5core5a is already installed at the requested version(5.6.1+dfsg-2~xenial+build2)
```
  Two other (perhaps relevant) libraries ( ***libqt5gui5*** and ***libqt5opengl5*** ) are installed in addition to ***libqt5core5a***.  All three of them are at version *5.6.1+dfsg-2~xenial+build2*.

  But the following (also perhaps relevant) libraries are **not** installed, and all of *these* appear in Synaptic at version *5.5.1+dfsg-16ubuntu6*:

  [B][I]libqt5gui5-gles
libqt5opengl5-gles
libqt5opengl5-gles-dev
libqt5opengl5-dev
libqt5network5
[/I][/B]  
  Naturally, I'm reluctant to do anything with ***libqt5core5a*** until I know what I'm doing, since, as the name ***core*** suggests, this library affects a ton of other packages.

  Should I try to find the *5.5.1+dfsg-16ubuntu7.1*  version, install it, & then remove the 5.6.1? 

  (I'm not sure where I'd find it, though, since version *5.5.1* is not in Synaptic, and I already have -- in */etc/apt/sources.list* -- both of the "500" repos that are 
listed under the [COLOR=#008000]*apt-cache policy libqt5core5a*[/COLOR] command above (or at least I think I do): 
  ```
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) xenial-updates restricted main
```
  and 
  ```
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) xenial restricted main 
```
  (*Onionshare*, btw, installed with no problems in MATE-14.04. The developr says it should work with any version of Qt5.)

  *Basically, I'm asking:* ***How should this conflict be resolved?***

---

### Post by ian-weisser on 2016-10-16
Well, one easy way is to use the non-conflicting Onionshare and Calibre from the Ubuntu repositories instead of the conflicting non-Ubuntu versions.

---

### Post by watchpocket on 2016-10-16
Not true for Calibre -- I have no PPA for that. When trying to install Calibre from Synaptic, I get the same warnings.  

Also, cancelling out the OnionShare PPA and installing Synaptic's older version of OnionShare is just a way of avoiding the problem, it seems to me, which will only rear its head again later.  (Also, I'd like to have the current version of OnionShare.)

Your solution *would* be good, though, were I desperately needing to use OnionShare right away.  But one way or another, I need to tackle the dependency problem.

---

### Post by ian-weisser on 2016-10-16
The problem looks like a version conflict.
If so, the only way around it it using package management is to upgrade or downgrade until both applications use a common version of the conflicted dependency again...once you figure out which dependency(ies) have the conflict.
If it is a version conflict, the only other solution is to compile one or both yourself against the chosen dependenciy...not a convenient solution for some.

If it's some other type of conflict, then the solution is different.

---

### Post by monkeybrain20122 on 2016-10-17
It seems that you get the qt5-5.6.1 packages from some ppa  but onionshare requires 5.5.1 (which is the system qt5) so you have to downgrade it to 5.5.1 (5.5.1 is not in synaptic because it only shows the highest version, but if you right click libqt5core5a and choose properties > version you will see all versions available. Force downgrade is not recommended. Instead, use ppa-purge

```
sudo apt-get install ppa-purge
```

Then find out from which ppa from synaptic you have installed 5.6.1, say foo
then 

```
sudo ppa-purge ppa:foo/ppa
```
where "ppa:foo/ppa" is the apt-line you used to install the ppa.

 you don't need to install calibre from ppa or use Ubuntu's terribly out of date version, get it from upstream [https://calibre-ebook.com/download_linux](https://calibre-ebook.com/download_linux) You will be alerted of available updates when you open calibre. It comes with its own version of libqt5core and is installed in /opt so it won't create conflict with the system version.

P.s I did a simulated install of calibre from the repo. It doesn't show any error.

---

### Post by watchpocket on 2016-10-18
Would ppa-purge work if the PPA that the 5.6.1 *libqt5core5a* came from has already been removed from software sources?  Perhaps then I'd need to run purge for that PPA *even though* it may have been removed.

I still don't quite see how I can just remove 5.6.1 before installing 5.5.1 -- so many other important programs would be removed with 5.6.1.  I don't have a clear idea how to make the transition from 5.6.1 to 5.5.1.  

Is 5.5.1 already installed (but just not showing in Synaptic (since, as you note, Synaptic only shows the highest version), and if so, would 5.5.1 automatically become operational upon the removal of 5.6.1?

Edit: OK, I see from the ppa-purge manpage that this is exactly what happens.  Now to locate the offending PPA.

---

### Post by watchpocket on 2016-10-20
> but if you right click libqt5core5a and choose properties > version  you will see all versions available. Force downgrade is not recommended.  Instead, use ppa-purge.

I've run ppa-purge on most of my PPAs and at this point I'm thinking that the PPA from which I got the 5.6.1 version of *libqt5core5a* is no longer installed.  

What's the worst that could happen by forcing the previous version in Synaptic? Or by downgrading using aptitude?

---

### Post by monkeybrain20122 on 2016-10-20
> **watchpocket said:**
> Would ppa-purge work if the PPA that the 5.6.1 *libqt5core5a* came from has already been removed from software sources?  Perhaps then I'd need to run purge for that PPA *even though* it may have been removed.

.

You have to re-activate the source to use ppa-purge since it has to read the metadata for the packages in it and the dependencies, ppa-purge will downgrade 5.6.1 smartly instead of leaving you a broken system.

---

### Post by monkeybrain20122 on 2016-10-20
> **watchpocket said:**
> 
What's the worst that could happen by forcing the previous version in Synaptic? Or by downgrading using aptitude?

Depends. It may be nothing, it may leave your software packaging system in a bad state. It depends on the package and where it is in the dependency tree. That's why I recommend ppa-purge.

---

### Post by watchpocket on 2016-10-30
> **monkeybrain20122 said:**
> You have to re-activate the source to use ppa-purge since it has to read the metadata for the packages in it and the dependencies, ppa-purge will downgrade 5.6.1 smartly instead of leaving you a broken system.

Apparently I long ago deleted the PPA that caused the dependency issue, and I don't know what PPA to re-activate. I'm thinking the next-best solution may be to use aptitude, with the following choice:

```
--> ***sudo aptitude install onionshare***
...
Accept this solution? [Y/n/q/?] ***n***
open: 622; closed: 803; defer: 45; conflict: 150 
The following actions will resolve these dependencies:

       Remove the following packages:                                                                     
1)       gwenview                                                                                         
2)       kinit                                                                                            
3)       kio                                                                                              
4)       kstars                                                                                           
5)       kwayland-integration                                                                             
6)       libkf5baloo5                                                                                     
7)       libkf5balooengine5                                                                               
8)       libkf5bookmarks5                                                                                 
9)       libkf5dbusaddons-bin                                                                             
10)      libkf5iconthemes-bin                                                                             
11)      libkf5idletime5                                                                                  
12)      libkf5kdelibs4support5                                                                           
13)      libkf5kdelibs4support5-bin                                                                       
14)      libkf5kiofilewidgets5                                                                            
15)      libkf5newstuff5                                                                                  
16)      libkf5plotting5                                                                                  
17)      libkf5solid5                                                                                     
18)      libkf5waylandclient5                                                                             
19)      libqgsttools-p1                                                                                  
20)      libqt5multimedia5-plugins                                                                        
21)      libqt5multimediawidgets5                                                                         
22)      libqt5waylandclient5                                                                             
23)      qtwayland5                                                                                       

       Downgrade the following packages:                                                                  
24)      libkf5activities5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
25)      libkf5archive5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]              
26)      libkf5attica5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]               
27)      libkf5auth-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]             
28)      libkf5auth5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]                 
29)      libkf5codecs-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
30)      libkf5codecs5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]               
31)      libkf5completion-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]       
32)      libkf5completion5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
33)      libkf5config-bin [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]            
34)      libkf5config-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
35)      libkf5configcore5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
36)      libkf5configgui5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]            
37)      libkf5configwidgets-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]    
38)      libkf5configwidgets5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]        
39)      libkf5coreaddons-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]       
40)      libkf5coreaddons5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
41)      libkf5crash5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]                
42)      libkf5dbusaddons-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]       
43)      libkf5dbusaddons5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
44)      libkf5filemetadata-bin [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]      
45)      libkf5filemetadata-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]     
46)      libkf5filemetadata3 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]         
47)      libkf5globalaccel-bin [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]       
48)      libkf5globalaccel-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]      
49)      libkf5globalaccel5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]          
50)      libkf5globalaccelprivate5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]   
51)      libkf5gpgmepp5 [16.04.3-0ubuntu1~ubuntu16.04~ppa1 (now) -> 15.12.3-0ubuntu1 (xenial)]            
52)      libkf5guiaddons5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]            
53)      libkf5i18n-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]             
54)      libkf5i18n5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]                 
55)      libkf5iconthemes-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]
55)      libkf5iconthemes-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]       
56)      libkf5iconthemes5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
57)      libkf5itemmodels5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
58)      libkf5itemviews-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]        
59)      libkf5itemviews5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]            
60)      libkf5jobwidgets-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]       
61)      libkf5jobwidgets5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
62)      libkf5kiocore5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]              
63)      libkf5kiontlm5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]              
64)      libkf5kiowidgets5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
65)      libkf5notifications-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]    
66)      libkf5notifications5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]        
67)      libkf5parts-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]            
68)      libkf5parts-plugins [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]         
69)      libkf5parts5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]                
70)      libkf5service-bin [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
71)      libkf5service-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]          
72)      libkf5service5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]              
73)      libkf5sonnet5-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]          
74)      libkf5sonnetcore5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
75)      libkf5sonnetui5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]             
76)      libkf5style5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]                
77)      libkf5textwidgets-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]      
78)      libkf5textwidgets5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]          
79)      libkf5wallet-bin [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0a-0ubuntu1 (xenial)]           
80)      libkf5wallet-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0a-0ubuntu1 (xenial)]          
81)      libkf5wallet5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0a-0ubuntu1 (xenial)]              
82)      libkf5widgetsaddons-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]    
83)      libkf5widgetsaddons5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]        
84)      libkf5windowsystem-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]     
85)      libkf5windowsystem5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]         
86)      libkf5xmlgui-bin [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]            
87)      libkf5xmlgui-data [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]           
88)      libkf5xmlgui5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]               
89)      libkwalletbackend5-5 [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0a-0ubuntu1 (xenial)]       
90)      libqt5core5a [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]       
91)      libqt5dbus5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]        
92)      libqt5gui5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]         
93)      libqt5libqgtk2 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]     
94)      libqt5multimedia5 [5.6.1-2~xenial+build1 (now) -> 5.5.1-4ubuntu2 (xenial)]                       
95)      libqt5network5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]     
96)      libqt5opengl5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]      
97)      libqt5printsupport5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]
98)      libqt5qml5 [5.6.1-4~xenial+build1 (now) -> 5.5.1-2ubuntu6 (xenial)]                              
99)      libqt5quick5 [5.6.1-4~xenial+build1 (now) -> 5.5.1-2ubuntu6 (xenial)]                            
100)     libqt5script5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-2build1 (xenial)]                  
101)     libqt5sql5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]         
102)     libqt5sql5-sqlite [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]  
103)     libqt5svg5 [5.6.1-2~xenial+build1 (now) -> 5.5.1-2build1 (xenial)]                               
104)     libqt5test5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]        
105)     libqt5webkit5 [5.6.1+dfsg-3~xenial+build2 (now) -> 5.5.1+dfsg-2ubuntu1 (xenial)]                 
106)     libqt5widgets5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]     
107)     libqt5x11extras5 [5.6.1-2~xenial+build1 (now) -> 5.5.1-3build1 (xenial)]                         
108)     libqt5xml5 [5.6.1+dfsg-2~xenial+build2 (now) -> 5.5.1+dfsg-16ubuntu7.2 (xenial-updates)]         
109)     sonnet-plugins [5.24.0-0ubuntu1~ubuntu16.04~ppa1 (now) -> 5.18.0-0ubuntu1 (xenial)]              

       Leave the following dependencies unresolved:                                                       
110)     libkf5dbusaddons5 recommends libkf5dbusaddons-bin (= 5.18.0-0ubuntu1)                            
111)     libkf5iconthemes5 recommends libkf5iconthemes-bin (= 5.18.0-0ubuntu1)                            
112)     libkf5windowsystem5 recommends kwayland-integration                                              
113)     libkf5windowsystem5 recommends qtwayland5                                                        
114)     wireshark-qt recommends libqt5multimedia5-plugins                                                
115)     libkf5configcore5 recommends libkf5config-bin (= 5.24.0-0ubuntu1~ubuntu16.04~ppa1)               
116)     libkf5service5 recommends libkf5service-bin (= 5.24.0-0ubuntu1~ubuntu16.04~ppa1)                 
117)     libkf5idletime5 recommends kwayland-integration                                                  
118)     libkf5sonnetui5 recommends sonnet-plugins (= 5.24.0-0ubuntu1~ubuntu16.04~ppa1)                   
119)     libkf5iconthemes5 recommends libkf5iconthemes-bin (= 5.24.0-0ubuntu1~ubuntu16.04~ppa1)           
120)     libkf5dbusaddons5 recommends libkf5dbusaddons-bin (= 5.24.0-0ubuntu1~ubuntu16.04~ppa1)

Accept this solution? [Y/n/q/?] 
The following packages will be DOWNGRADED:
  libkf5attica5 libkf5auth-data libkf5auth5 libkf5codecs-data libkf5codecs5 libkf5completion-data libkf5completion5 libkf5config-bin libkf5config-data libkf5configcore5 
  libkf5configgui5 libkf5configwidgets-data libkf5configwidgets5 libkf5coreaddons-data libkf5coreaddons5 libkf5crash5 libkf5dbusaddons-data libkf5dbusaddons5 libkf5globalaccel-bin 
  libkf5globalaccel-data libkf5globalaccel5 libkf5globalaccelprivate5 libkf5guiaddons5 libkf5i18n-data libkf5i18n5 libkf5iconthemes-data libkf5iconthemes5 libkf5itemviews-data 
  libkf5itemviews5 libkf5service-bin libkf5service-data libkf5service5 libkf5sonnet5-data libkf5sonnetcore5 libkf5sonnetui5 libkf5style5 libkf5textwidgets-data libkf5textwidgets5 
  libkf5widgetsaddons-data libkf5widgetsaddons5 libkf5windowsystem-data libkf5windowsystem5 libkf5xmlgui-bin libkf5xmlgui-data libkf5xmlgui5 libqt5core5a libqt5dbus5 libqt5gui5 
  libqt5libqgtk2 libqt5multimedia5 libqt5network5 libqt5opengl5 libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5script5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 
  libqt5webkit5 libqt5widgets5 libqt5x11extras5 libqt5xml5 sonnet-plugins 
The following NEW packages will be installed:
  libqt5designer5{a} onionshare python3-pyqt5{a} python3-sip{a} 
The following packages will be REMOVED:
  astrometry.net{u} catdoc{u} gwenview{a} indi-bin{u} kamera{u} kinit{a} kio{a} kstars{a} kstars-data{u} kwayland-data{u} kwayland-integration{a} libastrometry0{u} libcfitsio-bin{u} 
  libcfitsio2{u} libdbusmenu-qt5{u} liberfa1{u} libindi-data{u} libindi-plugins{u} libindialignmentdriver1{u} libindidriver1{u} libkf5activities5{u} libkf5archive5{u} libkf5baloo5{a} 
  libkf5balooengine5{a} libkf5bookmarks-data{u} libkf5bookmarks5{a} libkf5dbusaddons-bin{a} libkf5filemetadata-bin{u} libkf5filemetadata-data{u} libkf5filemetadata3{u} 
  libkf5gpgmepp5{u} libkf5iconthemes-bin{a} libkf5idletime5{a} libkf5itemmodels5{u} libkf5jobwidgets-data{u} libkf5jobwidgets5{u} libkf5kdcraw5{u} libkf5kdelibs4support-data{u} 
  libkf5kdelibs4support5{a} libkf5kdelibs4support5-bin{a} libkf5kiocore5{u} libkf5kiofilewidgets5{a} libkf5kiontlm5{u} libkf5kiowidgets5{u} libkf5kipi-data{u} libkf5kipi31.0.0{u} 
  libkf5newstuff-data{u} libkf5newstuff5{a} libkf5notifications-data{u} libkf5notifications5{u} libkf5parts-data{u} libkf5parts-plugins{u} libkf5parts5{u} libkf5plotting5{a} 
  libkf5solid5{a} libkf5solid5-data{u} libkf5wallet-bin{u} libkf5wallet-data{u} libkf5wallet5{u} libkf5waylandclient5{a} libkwalletbackend5-5{u} liblmdb0{u} libnova-0.14-0{u} 
  libphonon4qt5-4{u} libqgsttools-p1{a} libqt5multimedia5-plugins{a} libqt5multimediawidgets5{a} libqt5waylandclient5{a} libwcs5{u} libxcb-xinerama0{u} python-astrometry{u} 
  python-astropy{u} python-beautifulsoup{u} python-yaml{u} qt5-image-formats-plugins{u} qtwayland5{a} sextractor{u} xplanet{u} xplanet-images{u} 
The following packages are RECOMMENDED but will NOT be installed:
  qttranslations5-l10n 
0 packages upgraded, 4 newly installed, 65 downgraded, 79 to remove and 0 not upgraded.

```

But I'm on uncertain ground. My worry here is:  What about 110 throught 120 above -- the ten unresolved dependency libraries (and 114 -- the wireshark-qt dependency)?  [EDIT: I see that the recommendations are to use the lower version of all of these, which should minimize problems.]
 
  I'm not completely sure yet that I want to go ahead with this action until I  have a clearer sense that it's my best choice (though it may be my only  viable choice, given that ppa-purge won't help).  

  I do want to be able to roll back all the 5.6.1 qt libraries to 5.5.1,  so I can install OnionShare and Calibre, and because I *think* 5.5.1 is  the system version that's right/appropriate for Mate 16.04. 

I find these dependency issues to be some complicated stuff.  Any tips appreciated.

---

### Post by ian-weisser on 2016-10-30
Tip #1: Deleting a source is _not_ the same as uninstalling the software. You must do _both_ when getting rid of a PPA.
Tip #2: After you delete software, remember to run apt autoremove to uninstall remaining orphaned dependencies.
Tip #3: After you delete a source, remember to apt clean (not autoclean) those PPA packages from your local package cache, lest they get reinstalled. Also, since you changed your sources, apt update your package database.

One fairly simple-to-understand way to avoid a huge aptitude choice is to uninstall each of those PPA-provided packages, one by one. Run autoremove occasionally. Record what unexpectedly is offered for removal so you remember to reinstall it when your purge is complete. As you uninstall a package, delete the PPA-provided package from your /var/cache/apt/archives, too.

This method will take you down a bit of a rabbit hole, working deeper and deeper through each layer of dependencies. Your notes are the way back, once you have completed purging the conflicting packages.

Personally, I see nothing wrong with aptitude's suggested solution. Were it me, I would tell aptitude 'Y'.

---

### Post by watchpocket on 2016-10-31
> **ian-weisser said:**
> As you uninstall a package, delete the PPA-provided package from your /var/cache/apt/archives, too.

There seems to be nothing in my /var/cache/apt/archives (and I've already deleted (manually) a few of the packages that aptitude indicated should be removed):
```
--> sudo ls -la /var/cache/apt/archives 
total 104
drwxr-xr-x 3 root root 94208 Oct 30 23:22 .
drwxr-xr-x 4 root root  4096 Oct 31 00:10 ..
-rw-r----- 1 root root     0 Apr 20  2016 lock
drwx------ 2 _apt root  4096 Oct 30 19:19 partial
-->
-->
--> sudo ls -la /var/cache/apt/archives/partial   
00:12:27 
total 100
drwx------ 2 _apt root  4096 Oct 30 19:19 .
drwxr-xr-x 3 root root 94208 Oct 30 23:22 ..
```

Is this as it should be?  [EDIT:  I went ahead and replied "yes" to the aptitude command, and I see I now have a bunch of stuff in /var/cache/apt/archives/, but they're the 5.5.1 qt libs, in other words, the versions I think I want to keep. *** I should leave those there, correct?***]

[2nd EDIT: All those packages that a few minutes ago were in /var/cache/apt/archives/ are now gone. I did run the standard maintenance commands, maybe those caused the removal of those packages, though this wasn't indicated when I ran the commands (autoclean, autoremove, update, upgrade etc).  In any event, my dependency issue has been SOLVED, thanks to aptitude.]

---

