---
title: "terminal command review"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by zhaotianwu on 2011-11-16
I am a beginner user of Ubuntu and absolutely not quite familiar with the terminal command. Could some experts help review the following command? This is what I just did according to a thread trying to fix my samsung wireless connectivity problem. However, it did not work at all, besides I am a bit confused as to what it actually did.
 ```

*******@***:~$ sudo add-apt-repository ppa:voria/ppa
[sudo] password for *******: 
You are about to add the following PPA to your system:
 Linux On My Samsung
 All the fixed packages for a better Ubuntu experience on Samsung netbooks.
Visit http://www.voria.org/forum for more informations.


 More info: https://launchpad.net/~voria/+archive/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.qvOw28ukXy --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv A6E348801F28F6B59D308A6036960FC31E5F36F0
gpg: requesting key 1E5F36F0 from hkp server keyserver.ubuntu.com
gpg: key 1E5F36F0: public key "Launchpad PPA for Fortunato Ventre" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
*******@***:~$ sudo apt-get update
Ign http://ppa.launchpad.net oneiric InRelease
Get:1 http://ppa.launchpad.net oneiric Release.gpg [316 B]                  
Get:2 http://ppa.launchpad.net oneiric Release [9,739 B]                       
Ign http://ca.archive.ubuntu.com oneiric InRelease                             
Get:3 http://ppa.launchpad.net oneiric/main Sources [2,702 B]                  
Get:4 http://ppa.launchpad.net oneiric/main i386 Packages [4,685 B]            
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Ign http://ca.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://ca.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://ca.archive.ubuntu.com oneiric Release.gpg                         
Get:5 http://ca.archive.ubuntu.com oneiric-updates Release.gpg [198 B]       
Ign http://ppa.launchpad.net oneiric/main Translation-en_CA                    
Get:6 http://ca.archive.ubuntu.com oneiric-backports Release.gpg [198 B]     
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Hit http://ca.archive.ubuntu.com oneiric Release                               
Get:7 http://ca.archive.ubuntu.com oneiric-updates Release [32.4 kB]           
Get:8 http://ca.archive.ubuntu.com oneiric-backports Release [24.3 kB]         
Hit http://ca.archive.ubuntu.com oneiric/main Sources                          
Hit http://ca.archive.ubuntu.com oneiric/universe Sources                      
Hit http://ca.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://ca.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://ca.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:9 http://ca.archive.ubuntu.com oneiric-updates/main Sources [77.9 kB]      
Get:10 http://ca.archive.ubuntu.com oneiric-updates/universe Sources [15.3 kB] 
Get:11 http://ca.archive.ubuntu.com oneiric-updates/main i386 Packages [151 kB]
Get:12 http://ca.archive.ubuntu.com oneiric-updates/universe i386 Packages [42.5 kB]
Get:13 http://ca.archive.ubuntu.com oneiric-updates/main TranslationIndex [73 B]
Get:14 http://ca.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en_CA                
Hit http://ca.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://ca.archive.ubuntu.com oneiric/universe Translation-en               
Get:15 http://ca.archive.ubuntu.com oneiric-backports/main Sources [1,577 B]   
Get:16 http://ca.archive.ubuntu.com oneiric-backports/universe Sources [3,400 B]
Get:17 http://ca.archive.ubuntu.com oneiric-backports/main i386 Packages [1,912 B]
Get:18 http://ca.archive.ubuntu.com oneiric-backports/universe i386 Packages [3,773 B]
Get:19 http://ca.archive.ubuntu.com oneiric-backports/main TranslationIndex [72 B]
Get:20 http://ca.archive.ubuntu.com oneiric-backports/universe TranslationIndex [72 B]
Get:21 http://ca.archive.ubuntu.com oneiric-updates/main Translation-en [75.3 kB]
Hit http://ca.archive.ubuntu.com oneiric-updates/universe Translation-en       
Get:22 http://ca.archive.ubuntu.com oneiric-backports/main Translation-en [1,203 B]
Get:23 http://ca.archive.ubuntu.com oneiric-backports/universe Translation-en [3,304 B]
99% [Connecting to security.ubuntu.com (91.189.92.166)]                        
99% [Connecting to security.ubuntu.com (91.189.92.166)]


```

---

### Post by buntudawg on 2011-11-16
From what I can see you have added the voria repository to your sources list. After updating, if it worked, you should now be able to find the various samsung tools in synaptic package manager, or install them via terminal.

---

### Post by raja.genupula on 2011-11-16
+1 yeah . actually in Ubuntu repo's your Samsung driver  information not available so by adding a repo like you did , you can able to get it to download and install from your Ubuntu system . . after completion  of update from software center or terminal you can install it . if you got any errors then post here.

---

### Post by zhaotianwu on 2011-11-16
> **buntudawg said:**
> From what I can see you have added the voria repository to your sources list. After updating, if it worked, you should now be able to find the various samsung tools in synaptic package manager, or install them via terminal.


So it is trusted and harmless, right?

---

### Post by raja.genupula on 2011-11-16
yes man . its fine.

---

