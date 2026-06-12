---
title: "Problems installing applications - Grub-Pc error"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by lithio on 2010-06-18
Hi, recently upgraded the Ubuntu 10.4,  and before I finished, It threw a bug in the grub-pc, since then when I  install any application, in the end It throw this error.

The error is  this:Errors were encountered while processing:
    **grub-pc**
**E: Sub-proccess /usr/bin/dpkg retourned an error code (1)**
A package failed to install. Trying to recover:
Configuring grub-pc (1.98-lubuntu6) ...
dpkg: error to process grub-pc (--configure):
subprocess post-installation script installed returned error exit code 10
Errors were encountered while processing:
    **grub-pc**

Anyone know why? and  how I can fix it?

Thank you very much, and I q is here  the right place to post it: P

---

### Post by tommcd on 2010-06-18
What version of Ubuntu did you upgrade to 10.04 *from*?? Was it 8.04? or 9.10??

Try running in the terminal:
```

sudo dpkg --configure -a
sudo apt-get update

```
and then try installing or upgrading.
If that returns errors, try:
```

sudo dpkg --clear-avail && sudo apt-get update

```
If you still have errors, try:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
Sudo apt-get upgrade

```
Post the output of those commands if this does not help.

And welcome to the Ubuntu forums!

---

### Post by Tishko on 2010-07-25
Hello,

sdpkg-This command is not found and not available for install. I run dpkg instead. I can confirm this problem but any of the listed solution didnot help. Please, post a workaround of this bug as I am stuck and cant install any software.
Greetings
Tish

---

### Post by tommcd on 2010-07-25
> **Tishko said:**
> 
sdpkg-This command is not found and not available for install. I run dpkg instead. I can confirm this problem but any of the listed solution didnot help. Please, post a workaround of this bug as I am stuck and cant install any software.

I am sorry. The **sdpkg** was  a careless typo on my part. You are right that the correct command is **dpkg**.
I have edited and corrected my first post in order to avoid any further confusion in case anyone else reads this thread.

1. Can you try running the commands I posted and post their output here please?
The only references I can find for this recommend using the commands I posted:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420884](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420884)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/426239](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/426239)

2. Was this an upgrade from a previous version of Ubuntu? Or was it a clean install?
3. Is this a **Wubi** install inside Windows? Or is this a real Ubuntu install to a dedicated partition on the hard drive?
4. What version of Ubuntu are you using? Please provide more detail on this (answer 1-4 please).

Unfortunately, I am not sure what else you could try at this point.

---

### Post by BasicXP on 2010-07-29
Hello! I have same problem with grub-pc 1.98-ubuntu7. I have cleanly installed Ubuntu 10.04.1 (not Wubi).
Here is my output (my system is in Russian):
```
basicxp@ROMAN-5720ZG:~$ sudo dpkg --configure -a
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; grub-pc (1.98-1ubuntu7) ...
dpkg: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088; grub-pc (--configure):
 &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081; post-installation &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 10
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 grub-pc
```
```
basicxp@ROMAN-5720ZG:~$ sudo dpkg --clear-avail && sudo apt-get update
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release.gpg
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1048;&#1075;&#1085; http://deb.opera.com/opera/ stable/non-free Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/main Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/universe Translation-ru                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release.gpg                                                      
&#1048;&#1075;&#1085; http://deb.opera.com/opera-beta/ stable/non-free Translation-ru                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-ru                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-ru                                   
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-ru                                     
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-ru                                   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1048;&#1075;&#1085; http://archive.canonical.com/ubuntu/ lucid/partner Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release.gpg                                                                  
&#1048;&#1075;&#1085; http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-ru                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release.gpg                                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Packages                                                            
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Sources                                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Sources                                                             
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Sources                                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1048;&#1075;&#1085; http://archive.canonical.com/ lucid/partner Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release                                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Sources                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Packages                                                        
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Packages                                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Packages                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Sources                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Sources                                                     
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Sources                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Sources                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid/main Packages                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Packages                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Packages                                              
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/main Sources                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Sources                                                          
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/restricted Sources                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release.gpg                       
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Sources
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release.gpg
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Packages
&#1048;&#1075;&#1085; https://private-ppa.launchpad.net/ubuntu-font-beta-testing/ppa/ubuntu/ lucid/main Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Packages
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Sources
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
```
```
basicxp@ROMAN-5720ZG:~$ sudo dpkg --clear-avail && sudo apt-get update
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release.gpg
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1048;&#1075;&#1085; http://deb.opera.com/opera/ stable/non-free Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/main Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/universe Translation-ru                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release.gpg                                                      
&#1048;&#1075;&#1085; http://deb.opera.com/opera-beta/ stable/non-free Translation-ru                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-ru                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-ru                                   
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-ru                                     
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-ru                                   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1048;&#1075;&#1085; http://archive.canonical.com/ubuntu/ lucid/partner Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release.gpg                                                                  
&#1048;&#1075;&#1085; http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-ru                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release.gpg                                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Packages                                                            
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Sources                                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Sources                                                             
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Sources                                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1048;&#1075;&#1085; http://archive.canonical.com/ lucid/partner Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release                                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Sources                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Packages                                                        
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Packages                                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Packages                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Sources                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Sources                                                     
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Sources                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Sources                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid/main Packages                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Packages                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Packages                                              
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/main Sources                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Sources                                                          
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/restricted Sources                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release.gpg                       
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Sources
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release.gpg
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Packages
&#1048;&#1075;&#1085; https://private-ppa.launchpad.net/ubuntu-font-beta-testing/ppa/ubuntu/ lucid/main Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Packages
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Sources
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
basicxp@ROMAN-5720ZG:~$ ^C
basicxp@ROMAN-5720ZG:~$ clear

basicxp@ROMAN-5720ZG:~$ sudo apt-get install -f
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1085;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; &#1076;&#1086; &#1082;&#1086;&#1085;&#1094;&#1072; &#1080;&#1083;&#1080; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1086; 1 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1076;&#1072;&#1085;&#1085;&#1086;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080;, &#1086;&#1073;&#1098;&#1105;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1074;&#1086;&#1079;&#1088;&#1072;&#1089;&#1090;&#1105;&#1090; &#1085;&#1072; 0B.
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; grub-pc (1.98-1ubuntu7) ...
dpkg: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088; grub-pc (--configure):
 &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081; post-installation &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 10
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
basicxp@ROMAN-5720ZG:~$ sudo dpkg --configure -a
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; grub-pc (1.98-1ubuntu7) ...
dpkg: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088; grub-pc (--configure):
 &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081; post-installation &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 10
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 grub-pc
basicxp@ROMAN-5720ZG:~$ sudo apt-get update
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release.gpg
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/main Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/universe Translation-ru                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release.gpg                                                      
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-ru                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-ru                                   
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-ru                                     
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-ru                                   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1048;&#1075;&#1085; http://deb.opera.com/opera/ stable/non-free Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Packages                                                            
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Sources                                                       
&#1048;&#1075;&#1085; http://deb.opera.com/opera-beta/ stable/non-free Translation-ru                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Sources                                                             
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1048;&#1075;&#1085; http://archive.canonical.com/ubuntu/ lucid/partner Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release.gpg                                                       
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-ru                                          
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-ru                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release.gpg                                                                  
&#1048;&#1075;&#1085; http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-ru                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Sources                                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Sources                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release.gpg                                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Packages                                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Packages                                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Packages                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Sources                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Sources                                                     
&#1048;&#1075;&#1085; http://archive.canonical.com/ lucid/partner Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Sources                                               
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-ru                                      
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-ru                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release                                                           
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release                                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Sources                                                 
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Packages                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Packages                                              
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Packages                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid/main Packages                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/main Sources                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Packages                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Sources                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Sources                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Sources                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Sources                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Sources                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/restricted Sources                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Packages                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Packages               
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                         
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release.gpg
&#1048;&#1075;&#1085; https://private-ppa.launchpad.net/ubuntu-font-beta-testing/ppa/ubuntu/ lucid/main Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Packages
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Sources
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
basicxp@ROMAN-5720ZG:~$ sudo apt-get upgrade
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0, &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; 0 &#1085;&#1086;&#1074;&#1099;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1076;&#1083;&#1103; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1080;&#1103; &#1086;&#1090;&#1084;&#1077;&#1095;&#1077;&#1085;&#1086; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;, &#1080; 0 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1085;&#1077; &#1086;&#1073;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086;.
&#1085;&#1077; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;&#1086; &#1076;&#1086; &#1082;&#1086;&#1085;&#1094;&#1072; &#1080;&#1083;&#1080; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1086; 1 &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;.
&#1055;&#1086;&#1089;&#1083;&#1077; &#1076;&#1072;&#1085;&#1085;&#1086;&#1081; &#1086;&#1087;&#1077;&#1088;&#1072;&#1094;&#1080;&#1080;, &#1086;&#1073;&#1098;&#1105;&#1084; &#1079;&#1072;&#1085;&#1103;&#1090;&#1086;&#1075;&#1086; &#1076;&#1080;&#1089;&#1082;&#1086;&#1074;&#1086;&#1075;&#1086; &#1087;&#1088;&#1086;&#1089;&#1090;&#1088;&#1072;&#1085;&#1089;&#1090;&#1074;&#1072; &#1074;&#1086;&#1079;&#1088;&#1072;&#1089;&#1090;&#1105;&#1090; &#1085;&#1072; 0B.
&#1061;&#1086;&#1090;&#1080;&#1090;&#1077; &#1087;&#1088;&#1086;&#1076;&#1086;&#1083;&#1078;&#1080;&#1090;&#1100; [&#1044;/&#1085;]? y
&#1053;&#1072;&#1089;&#1090;&#1088;&#1072;&#1080;&#1074;&#1072;&#1077;&#1090;&#1089;&#1103; &#1087;&#1072;&#1082;&#1077;&#1090; grub-pc (1.98-1ubuntu7) ...
dpkg: &#1085;&#1077; &#1091;&#1076;&#1072;&#1083;&#1086;&#1089;&#1100; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1072;&#1090;&#1100; &#1087;&#1072;&#1088;&#1072;&#1084;&#1077;&#1090;&#1088; grub-pc (--configure):
 &#1087;&#1086;&#1076;&#1087;&#1088;&#1086;&#1094;&#1077;&#1089;&#1089; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1089;&#1094;&#1077;&#1085;&#1072;&#1088;&#1080;&#1081; post-installation &#1074;&#1086;&#1079;&#1074;&#1088;&#1072;&#1090;&#1080;&#1083; &#1082;&#1086;&#1076; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080; 10
&#1055;&#1088;&#1080; &#1086;&#1073;&#1088;&#1072;&#1073;&#1086;&#1090;&#1082;&#1077; &#1089;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1080;&#1093; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074; &#1087;&#1088;&#1086;&#1080;&#1079;&#1086;&#1096;&#1083;&#1080; &#1086;&#1096;&#1080;&#1073;&#1082;&#1080;:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Here are all the three outputs you requested.

---

### Post by tommcd on 2010-07-29
Unfortunately, the fact that the errors are in Russian prevents me from making any sense of it. Since you seem to speak English well, can you translate that please?
As a start, I would try commenting out (put a # in front of) all those opera and ppa repos you have in your 
/etc/apt/sources.list, then run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
If that does not work then run these commands again:
```

sudo dpkg --configure -a
sudo apt-get update

```
and if still unsuccessful:
```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
Sudo apt-get upgrade

```

And welcome to the Ubuntu forums!

---

### Post by BasicXP on 2010-08-11
Thank you! I tried to do everything you said. Here is my try to translate the outputs:

```
basicxp@ROMAN-5720ZG:~$ sudo dpkg --configure -a
Setting up package grub-pc (1.98-1ubuntu7) ...
dpkg: can not parse grub-pc parameter (--configure):
 post-installation sub-process returned error code 10
While installing this package(s) errors occured:
 grub-pc
```

Honestly, I was very lazy to translate bunch of repeated words in the next two outputs, those are:
**&#1042; &#1082;&#1101;&#1096;&#1077;** means **Cached**
**&#1048;&#1075;&#1085;** means **Ignored**

```
basicxp@ROMAN-5720ZG:~$ sudo dpkg --clear-avail && sudo apt-get update
Cached http://ru.archive.ubuntu.com lucid Release.gpg
Cached http://deb.opera.com stable Release.gpg                                                                     
&#1048;&#1075;&#1085; http://deb.opera.com/opera/ stable/non-free Translation-ru                                                     
Cached http://deb.opera.com stable Release.gpg                                                                     
Cached http://ru.archive.ubuntu.com/ubuntu/ lucid/main Translation-ru                                              
Cached http://ru.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-ru                                        
Cached http://ru.archive.ubuntu.com/ubuntu/ lucid/universe Translation-ru                                          
Cached http://ru.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-ru                                        
Cached http://ru.archive.ubuntu.com lucid-updates Release.gpg                                                      
&#1048;&#1075;&#1085; http://deb.opera.com/opera-beta/ stable/non-free Translation-ru                                                
Cached http://deb.opera.com stable Release                                                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-ru                                         
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-ru                                   
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-ru                                     
Ign http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-ru                                   
Cached http://ru.archive.ubuntu.com lucid Release                                                                  
Cached http://archive.canonical.com lucid Release.gpg                                                              
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-ru                                              
Cached http://ppa.launchpad.net lucid Release.gpg                                                                  
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-ru                                       
Cached http://ru.archive.ubuntu.com lucid-updates Release                                                          
Cached http://archive.ubuntu.com lucid Release.gpg                                                                 
Cached http://ru.archive.ubuntu.com lucid/main Packages                                                            
Cached http://ru.archive.ubuntu.com lucid/restricted Packages                                                      
Cached http://deb.opera.com stable Release                                                                         
Cached http://ru.archive.ubuntu.com lucid/restricted Sources                                                       
Cached http://ru.archive.ubuntu.com lucid/main Sources                                                             
Cached http://ru.archive.ubuntu.com lucid/multiverse Sources                                                       
Cached http://archive.canonical.com lucid Release.gpg                                                              
Ign http://archive.canonical.com/ lucid/partner Translation-ru                                                     
Cached http://ppa.launchpad.net lucid Release                                                                      
Cached http://ru.archive.ubuntu.com lucid/universe Sources                                                         
Cached http://archive.canonical.com lucid Release                                                                  
Cached http://ru.archive.ubuntu.com lucid/universe Packages                                                        
Ign http://deb.opera.com stable/non-free Packages                                                                  
Cached http://archive.ubuntu.com lucid Release                                                                     
Cached http://ru.archive.ubuntu.com lucid/multiverse Packages                                                      
Cached http://ru.archive.ubuntu.com lucid-updates/main Packages                                                    
Cached http://ru.archive.ubuntu.com lucid-updates/restricted Packages                                              
Cached http://ru.archive.ubuntu.com lucid-updates/restricted Sources                                               
Cached http://ru.archive.ubuntu.com lucid-updates/main Sources                                                     
Ign http://deb.opera.com stable/non-free Packages                                                                  
Cached http://ru.archive.ubuntu.com lucid-updates/multiverse Sources                                               
Cached http://ru.archive.ubuntu.com lucid-updates/universe Sources                                                 
Cached http://archive.canonical.com lucid Release                                                                  
Cached http://ppa.launchpad.net lucid/main Packages                                                                
Cached http://ru.archive.ubuntu.com lucid-updates/universe Packages                                                
Cached http://ru.archive.ubuntu.com lucid-updates/multiverse Packages                                              
Ign http://deb.opera.com stable/non-free Packages                                                                  
Cached http://archive.ubuntu.com lucid/main Sources                                                                
Cached http://archive.canonical.com lucid/partner Packages                                                         
Cached http://archive.canonical.com lucid/partner Sources                                                          
Ign http://deb.opera.com stable/non-free Packages                                                                  
Cached http://archive.ubuntu.com lucid/restricted Sources                                                          
Cached http://deb.opera.com stable/non-free Packages                                                               
Cached http://archive.canonical.com lucid/partner Packages                                                         
Cached http://deb.opera.com stable/non-free Packages                               
Cached http://security.ubuntu.com lucid-security Release.gpg                       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-ru
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-ru
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-ru
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-ru
Cached http://security.ubuntu.com lucid-security Release
Cached http://security.ubuntu.com lucid-security/main Packages
Cached http://security.ubuntu.com lucid-security/restricted Packages
Cached http://security.ubuntu.com lucid-security/restricted Sources
Cached http://security.ubuntu.com lucid-security/main Sources
Cached http://security.ubuntu.com lucid-security/multiverse Sources
Cached http://security.ubuntu.com lucid-security/universe Sources
Cached https://private-ppa.launchpad.net lucid Release.gpg
Cached http://security.ubuntu.com lucid-security/universe Packages
Cached http://security.ubuntu.com lucid-security/multiverse Packages
Ign https://private-ppa.launchpad.net/ubuntu-font-beta-testing/ppa/ubuntu/ lucid/main Translation-ru
Cached https://private-ppa.launchpad.net lucid Release
Cached https://private-ppa.launchpad.net lucid/main Packages
Cached https://private-ppa.launchpad.net lucid/main Sources
Reading package lists... Done
```

```
basicxp@ROMAN-5720ZG:~$ sudo dpkg --clear-avail && sudo apt-get update
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release.gpg
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1048;&#1075;&#1085; http://deb.opera.com/opera/ stable/non-free Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/main Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/universe Translation-ru                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release.gpg                                                      
&#1048;&#1075;&#1085; http://deb.opera.com/opera-beta/ stable/non-free Translation-ru                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-ru                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-ru                                   
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-ru                                     
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-ru                                   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1048;&#1075;&#1085; http://archive.canonical.com/ubuntu/ lucid/partner Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release.gpg                                                                  
&#1048;&#1075;&#1085; http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-ru                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release.gpg                                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Packages                                                            
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Sources                                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Sources                                                             
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Sources                                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1048;&#1075;&#1085; http://archive.canonical.com/ lucid/partner Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release                                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Sources                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Packages                                                        
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Packages                                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Packages                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Sources                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Sources                                                     
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Sources                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Sources                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid/main Packages                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Packages                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Packages                                              
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/main Sources                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Sources                                                          
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/restricted Sources                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release.gpg                       
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-ru
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Sources
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Sources
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release.gpg
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Packages
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Packages
&#1048;&#1075;&#1085; https://private-ppa.launchpad.net/ubuntu-font-beta-testing/ppa/ubuntu/ lucid/main Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Packages
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Sources
Reading package lists... Done

basicxp@ROMAN-5720ZG:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading status information... Done
0 updated, 0 new packages installed, 0 marked for deletion and 0 packages not updated.
1 package not fully installed or deleted.
After this operation, disk usage will grow by 0B.
Setting up grub-pc package (1.98-1ubuntu7) ...
dpkg: unable to parse a grub-pc parameter (--configure):
 post-installation sub-process returned error code 10
Error occured during set up of these packages:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

basicxp@ROMAN-5720ZG:~$ sudo dpkg --configure -a
Setting up grub-pc package (1.98-1ubuntu7) ...
dpkg: unable to parse a grub-pc parameter (--configure):
 post-installation subprocess returned error code 10
Error occured during set up of these packages:
 grub-pc
basicxp@ROMAN-5720ZG:~$ sudo apt-get update
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release.gpg
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/main Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/universe Translation-ru                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-ru                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release.gpg                                                      
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-ru                                         
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-ru                                   
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-ru                                     
&#1048;&#1075;&#1085; http://ru.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-ru                                   
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates Release                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1048;&#1075;&#1085; http://deb.opera.com/opera/ stable/non-free Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release.gpg                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Packages                                                            
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/restricted Sources                                                       
&#1048;&#1075;&#1085; http://deb.opera.com/opera-beta/ stable/non-free Translation-ru                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/main Sources                                                             
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1048;&#1075;&#1085; http://archive.canonical.com/ubuntu/ lucid/partner Translation-ru                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release.gpg                                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release.gpg                                                       
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-ru                                          
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-ru                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release.gpg                                                                  
&#1048;&#1075;&#1085; http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-ru                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Sources                                                       
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Sources                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release.gpg                                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/universe Packages                                                        
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid/multiverse Packages                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Packages                                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable Release                                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Packages                                              
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/restricted Sources                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/main Sources                                                     
&#1048;&#1075;&#1085; http://archive.canonical.com/ lucid/partner Translation-ru                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Sources                                               
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-ru                                      
&#1048;&#1075;&#1085; http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-ru                                    
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security Release                                                           
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid Release                                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Sources                                                 
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid Release                                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/universe Packages                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://ru.archive.ubuntu.com lucid-updates/multiverse Packages                                              
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Packages                                                     
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid Release                                                                  
&#1048;&#1075;&#1085; http://deb.opera.com stable/non-free Packages                                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://ppa.launchpad.net lucid/main Packages                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/main Sources                                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Packages                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/restricted Sources                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/main Sources                                                      
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Sources                                                
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Sources                                                  
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                                                         
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Sources                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://deb.opera.com stable/non-free Packages                                                               
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.ubuntu.com lucid/restricted Sources                                                          
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/universe Packages                                                 
&#1042; &#1082;&#1101;&#1096;&#1077; http://security.ubuntu.com lucid-security/multiverse Packages               
&#1042; &#1082;&#1101;&#1096;&#1077; http://archive.canonical.com lucid/partner Packages                         
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release.gpg
&#1048;&#1075;&#1085; https://private-ppa.launchpad.net/ubuntu-font-beta-testing/ppa/ubuntu/ lucid/main Translation-ru
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid Release
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Packages
&#1042; &#1082;&#1101;&#1096;&#1077; https://private-ppa.launchpad.net lucid/main Sources
Reading package lists... Done

basicxp@ROMAN-5720ZG:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading status information... Done
0 updated, 0 new packages installed, 0 marked for deletion and 0 packages not updated.
1 package not fully installed or deleted.
After this operation, disk usage will grow by 0B.
Do you want to continue [y/n]? y
Setting up grub-pc package (1.98-1ubuntu7) ...
dpkg: unable to parse a grub-pc parameter (--configure):
 post-installation sub-process returned error code 10
Error occured during set up of these packages:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by tommcd on 2010-08-12
Sorry, but I have not found a specific solution for this.
Did you try comment out all those opera and ppa repos in your sources.list like I suggested in my last post? Do that and then run the commands I gave in my last post.

What happens if you try to reinstall grub-pc?
```
sudo apt-get install --reinstall grub-pc
```

---

### Post by BasicXP on 2010-08-12
I did not comment those out, as the problem appeared before I actually added any custom repos to the list. And the package (grub-pc) was trying to reinstall each time I install a new package. I did that a few time - it didn't help.

---

### Post by Data-Base on 2011-03-26
I have the same problem !!!
```

**root@sande:/home/vds# sudo apt-get install -f**
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-server
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up grub-pc (1.98-1ubuntu10) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@sande:/home/vds#
```


```
**root@sande:/home/vds# sudo dpkg --configure -a**
Setting up grub-pc (1.98-1ubuntu10) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
root@sande:/home/vds#
```

---

### Post by tommcd on 2011-03-27
> **Data-Base said:**
> I have the same problem !!!

How exactly did this happen? You need to provide some details here. 
Please answer:
1. What version of Ubuntu are you using? Since the terminal output of "*sudo apt-get install -f*" that you posted shows that your kernel is 2.6.32-21, I would assume that you are using Ubuntu 10.04. Is this correct?
2. Is this a Wubi (inside Windows) install? Or is this a real install to a dedicated linux partition on your hard drive?
3. Was this a clean install of Ubuntu (10.04)? Or did you upgrade from a previous Ubuntu version?
4. Do you have any third party repositories (including PPA repos) added to your system?
4. Are you able to install updates and software using Update Manager and Synaptic, or not?

Try running from the terminal: ```
sudo dpkg-reconfigure grub-pc
``` Then run: ```
sudo update-grub
```Then reboot and see if this fixes things. If it does not, then post the output of those commands here please.

---

