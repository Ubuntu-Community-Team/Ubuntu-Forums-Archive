---
title: "software center and updates fail"
date: 2014-11-12
forum: Installation &amp; Upgrades
---

### Post by mike199721 on 2014-11-12
Hello Forums,

My Ubuntu seems to only return errors. Driving me nuts!

I'm trying to update my version because software center and ubuntuone only return errors (can't even open them), but even trying to update ubuntu gives me nothing but an error message!

---

### Post by ian-weisser on 2014-11-12
Please open a terminal and try the following two commands, in order.
The terminal may prompt you for your password. It WON'T echo your keystrokes to the screen, but it IS accepting them.
Please copy-and-paste the entire output here. Use ```
 tags, please.
[code]sudo apt-get update
sudo apt-get upgrade
```

---

### Post by mike199721 on 2014-11-13
Thankyou in advance Ian, I appreciate it very muhc:

```

mike@Nucleus:~$ sudo apt-get update
[sudo] password for mike: 
Hit http://ca.archive.ubuntu.com precise Release.gpg
Get:1 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://ca.archive.ubuntu.com precise-backports Release.gpg                 
Hit http://ca.archive.ubuntu.com precise Release                               
Get:2 http://ca.archive.ubuntu.com precise-updates Release [194 kB]            
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release.gpg                               
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]         
Hit http://ppa.launchpad.net precise Release                                   
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ca.archive.ubuntu.com precise-backports Release                     
Get:4 http://security.ubuntu.com precise-security Release [53.0 kB]            
Hit http://ca.archive.ubuntu.com precise/main Sources                          
Hit http://ca.archive.ubuntu.com precise/restricted Sources                    
Hit http://ca.archive.ubuntu.com precise/universe Sources                      
Hit http://ca.archive.ubuntu.com precise/multiverse Sources                    
Hit http://ca.archive.ubuntu.com precise/main i386 Packages                    
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages                
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex             
Get:5 http://ca.archive.ubuntu.com precise-updates/main Sources [480 kB]       
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:6 http://ca.archive.ubuntu.com precise-updates/restricted Sources [8,000 B]
Get:7 http://ca.archive.ubuntu.com precise-updates/universe Sources [111 kB]   
Get:8 http://ca.archive.ubuntu.com precise-updates/multiverse Sources [8,935 B]
Get:9 http://ca.archive.ubuntu.com precise-updates/main i386 Packages [875 kB] 
Get:10 http://security.ubuntu.com precise-security/main Sources [114 kB]       
Get:11 http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages [13.2 kB]
Get:12 http://ca.archive.ubuntu.com precise-updates/universe i386 Packages [256 kB]
Get:13 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:14 http://security.ubuntu.com precise-security/universe Sources [33.0 kB]  
Get:15 http://security.ubuntu.com precise-security/multiverse Sources [1,801 B]
Get:16 http://security.ubuntu.com precise-security/main i386 Packages [474 kB] 
Get:17 http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:18 http://ca.archive.ubuntu.com precise-updates/main TranslationIndex [10.6 kB]
Get:19 http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex [7,613 B]
Get:20 http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex [7,297 B]
Get:21 http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex [8,333 B]
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA                
Hit http://ca.archive.ubuntu.com precise/main Translation-en                   
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://ca.archive.ubuntu.com precise-backports/main Sources                
Hit http://ca.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://ca.archive.ubuntu.com precise-backports/universe Sources            
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://ca.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://ca.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://ca.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://ca.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://ca.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://ca.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://ca.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://ca.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en             
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA            
Hit http://ca.archive.ubuntu.com precise/universe Translation-en               
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA        
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA    
Get:22 http://ca.archive.ubuntu.com precise-updates/universe Translation-en [145 kB]
Hit http://ca.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://ca.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://ca.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://ca.archive.ubuntu.com precise-backports/universe Translation-en     
Ign http://ppa.launchpad.net precise/main Translation-en_CA                    
Ign http://extras.ubuntu.com precise/main Translation-en_CA                    
Get:23 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:24 http://security.ubuntu.com precise-security/universe i386 Packages [107 kB]
Get:25 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,649 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Ign http://extras.ubuntu.com precise/main Translation-en               
Ign http://ppa.launchpad.net precise/main Translation-en               
Hit http://security.ubuntu.com precise-security/main Translation-en    
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,933 kB in 2s (1,299 kB/s)               
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
mike@Nucleus:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
mike@Nucleus:~$ 

```

---

### Post by ian-weisser on 2014-11-13
Happily, that particular problem is usually quite easy to fix.
First remove the malformed lists, then autogenerate new lists.
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

This fix is explained in detail at  [http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err](http://askubuntu.com/questions/30072/how-do-i-fix-a-problem-with-mergelist-or-status-file-could-not-be-parsed-err)

---

### Post by mike199721 on 2014-11-13
You make this look easy! Thanks!!!

---

### Post by mike199721 on 2014-11-13
how do i mark this as solved?

---

### Post by ian-weisser on 2014-11-13
Look for "Thread Tools" just above Post #1.
Glad you got it sorted.

---

