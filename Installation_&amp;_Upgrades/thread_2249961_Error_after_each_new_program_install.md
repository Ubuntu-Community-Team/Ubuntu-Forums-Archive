---
title: "Error after each new program install"
date: 2014-10-25
forum: Installation &amp; Upgrades
---

### Post by ankomonster on 2014-10-25
After a fresh install of Ubuntu 14.10 (64bit) i get after each program installation (easytag in this case) an error.
However, if i check the installed programm after wards it works well.

```
installArchives() failed: Selecting previously unselected package libid3-3.8.3c2a.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 193243 files and directories currently installed.)
Preparing to unpack .../libid3-3.8.3c2a_3.8.3-15_amd64.deb ...
Unpacking libid3-3.8.3c2a (3.8.3-15) ...
Selecting previously unselected package libid3tag0.
Preparing to unpack .../libid3tag0_0.15.1b-11_amd64.deb ...
Unpacking libid3tag0 (0.15.1b-11) ...
Selecting previously unselected package libopusfile0.
Preparing to unpack .../libopusfile0_0.5-1_amd64.deb ...
Unpacking libopusfile0 (0.5-1) ...
Selecting previously unselected package easytag.
Preparing to unpack .../easytag_2.2.2-1ubuntu1_amd64.deb ...
Unpacking easytag (2.2.2-1ubuntu1) ...
Selecting previously unselected package gnome-icon-theme-full.
Preparing to unpack .../gnome-icon-theme-full_3.12.0-1ubuntu1_all.deb ...
Unpacking gnome-icon-theme-full (3.12.0-1ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for bamfdaemon (0.5.1+14.10.20140925-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.55ubuntu1) ...
Processing triggers for man-db (2.7.0.2-2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for gnome-icon-theme (3.12.0-1ubuntu1) ...
Setting up icedtea-netx:amd64 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libid3-3.8.3c2a (3.8.3-15) ...
Setting up libid3tag0 (0.15.1b-11) ...
Setting up libopusfile0 (0.5-1) ...
Setting up easytag (2.2.2-1ubuntu1) ...
Setting up gnome-icon-theme-full (3.12.0-1ubuntu1) ...
update-alternatives: using /usr/share/icons/gnome/scalable/places/ubuntu-logo.svg to provide /usr/share/icons/gnome/scalable/places/start-here.svg (start-here.svg) in auto mode
update-alternatives: warning: skip creation of /usr/share/icons/gnome/256x256/places/start-here.png because associated file /usr/share/icons/gnome/256x256/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist
update-alternatives: warning: skip creation of /usr/share/icons/gnome/48x48/places/start-here.png because associated file /usr/share/icons/gnome/48x48/places/ubuntu-logo.png (of link group start-here.svg) doesn't exist
Processing triggers for libc-bin (2.19-10ubuntu2) ...
Errors were encountered while processing:
 icedtea-netx:amd64
Error in function: 
Setting up icedtea-netx:amd64 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
```

What can i do to solve this.

---

### Post by Vladlenin5000 on 2014-10-26
Hi, welcome.

Apparently it's a Java issue that may or may not be related to having two different versions already installed. Besides it's available in the Ubuntu repositories therefore it can be installed from the Ubuntu Software Center.
How are you trying to install and what version?

---

### Post by ankomonster on 2014-10-26
I installed Ubuntu 14.10 (64bit) fresh install with a live dvd . 
The programs which i install are installed with software center. As far as i can see it's Java 6

---

### Post by Vladlenin5000 on 2014-10-26
> **ankomonster said:**
> The programs which i install are installed with software center. As far as i can see it's Java 6

No, not really. Not this one you're complaining about at least. Installing from the USC doesn't produce verbose (all those messages in the terminal). So - again - how are you installing Easytag (or from where) and what version?

---

### Post by ankomonster on 2014-10-26
Java is installed through installing: Ubuntu restricted extras. 

I think that's what you mean.

---

### Post by Vladlenin5000 on 2014-10-26
> **ankomonster said:**
> I think that's what you mean.

It certainly isn't. Since the beginning I was asking about **Easytag**, the software you're complaining about and that you haven't installed directly from the Ubuntu repositories via USC (but you should). So, for the third time, please answer the questions in my previous posts.

---

### Post by ankomonster on 2014-10-26
I did install Easytag from the Ubuntu Software Center and it is version 2.2.2

---

### Post by Vladlenin5000 on 2014-10-26
Easytag 2.2.1-1ubuntu1 is indeed the correct version for 14.10 (Utopic Unicorn). So, where does the text in your first post comes from?

---

### Post by ankomonster on 2014-10-26
That is the error info i got during the installation of easytag.
But Easytag was an example. 
it happens with every programm i install from USC.

---

### Post by Vladlenin5000 on 2014-10-26
So, you open the USC, search and select the software you want, then click install, type your password and then a terminal windows just pops up with those error messages?... Weird, to say the least.
Please try a full update of your OS before anything else. At the terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Post the error messages, if any, so others can help you with it.

PS - Please note the word "others" in the previous sentence. That means others will get you trough this small ordeal of yours (hopefully). I won't be here. Please don't take it personally because it really isn't. It has nothing to do with you. It's just that my personal 'style' isn't welcome at this forum so... I'm out. Good luck.

---

### Post by bapoumba on 2014-10-26
> **ankomonster said:**
> That is the error info i got during the installation of easytag.
But Easytag was an example. 
it happens with every programm i install from USC.

The errors with icedtea-netx ? As Vladlenin pointed out previously, this package is part of an open-jdk installation : [http://packages.ubuntu.com/utopic/icedtea-netx](http://packages.ubuntu.com/utopic/icedtea-netx)

Please post the outputs to :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by ankomonster on 2014-10-26
[FONT=Verdana]Terminal: [/FONT]sudo apt-get update
         sudo apt-get upgrade
         sudo apt-get dist-upgrade

Afterwards i did a pc restart and installedBreath-icon theme with USC and got the same error text again. (text below)
```
installArchives() failed: Selecting previously unselected package breathe-icon-theme.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 201222 files and directories currently installed.)
Preparing to unpack .../breathe-icon-theme_0.51.2_all.deb ...
Unpacking breathe-icon-theme (0.51.2) ...
Error in function: 
Setting up icedtea-netx:amd64 (1.5.1-1ubuntu1) ...
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: warning: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 2
```

---

### Post by bapoumba on 2014-10-27
What we would need for now is the output to the update/upgrade commands.

---

### Post by ankomonster on 2014-10-27
In the terminal:[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]           sudo apt-get upgrade
           sudo apt-get dist-upgrade


```
anko@anko-All-Series:~$ sudo apt-get update
[sudo] password for anko: 
Sorry, probeer opnieuw
[sudo] password for anko: 
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic InRelease
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release.gpg                            
Genegeerd [http://dl.google.com](http://dl.google.com) stable InRelease                                
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release                                
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Sources                           
Geraakt [http://dl.google.com](http://dl.google.com) stable Release.gpg                                
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main amd64 Packages                    
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic InRelease                        
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main i386 Packages                     
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates InRelease                
Geraakt [http://dl.google.com](http://dl.google.com) stable Release                                    
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports InRelease              
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security InRelease                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic Release.gpg                        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates Release.gpg                
Geraakt [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                        
Ophalen:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports Release.gpg [933 B]    
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic Release                            
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates Release                    
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release.gpg                 
Geraakt [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                         
Ophalen:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports Release [59,7 kB]      
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main Sources                       
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release                     
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted Sources                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe Sources                   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse Sources                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main amd64 Packages                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted amd64 Packages          
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-nl_NL               
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Sources                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe amd64 Packages            
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-nl                  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse amd64 Packages          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main i386 Packages                 
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en                  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted i386 Packages           
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Sources          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe i386 Packages            
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse i386 Packages          
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Sources           
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main Translation-nl               
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main Translation-en               
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse Translation-nl         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse Translation-en         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted Translation-nl         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted Translation-en         
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Sources         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe Translation-nl           
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe Translation-en           
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/main Sources              
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/restricted Sources        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/universe Sources          
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main amd64 Packages        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/multiverse Sources        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/main amd64 Packages       
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/restricted amd64 Packages 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/universe amd64 Packages   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/multiverse amd64 Packages  
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted amd64 Packages   
Genegeerd [http://dl.google.com](http://dl.google.com) stable/main Translation-nl_NL                   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/main i386 Packages         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/restricted i386 Packages   
Genegeerd [http://dl.google.com](http://dl.google.com) stable/main Translation-nl                      
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/universe i386 Packages     
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe amd64 Packages     
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/multiverse i386 Packages   
Genegeerd [http://dl.google.com](http://dl.google.com) stable/main Translation-en                      
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/main Translation-en        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/multiverse Translation-en  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/restricted Translation-en
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/universe Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse amd64 Packages
Ophalen:3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/main Sources [14 B]
Ophalen:4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/restricted Sources [14 B]
Ophalen:5 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/universe Sources [1388 B]
Ophalen:6 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/multiverse Sources [14 B]
Ophalen:7 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/main amd64 Packages [14 B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main i386 Packages          
Ophalen:8 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/restricted amd64 Packages [14 B]
Ophalen:9 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/universe amd64 Packages [705 B]
Ophalen:10 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/multiverse amd64 Packages [14 B]
Ophalen:11 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/main i386 Packages [14 B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted i386 Packages    
Ophalen:12 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/restricted i386 Packages [14 B]
Ophalen:13 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/universe i386 Packages [707 B]
Ophalen:14 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/multiverse i386 Packages [14 B]
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/main Translation-en      
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/multiverse Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe i386 Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/restricted Translation-en
Ophalen:15 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/universe Translation-en [256 B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse i386 Packages    
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Translation-en
63,9 kB opgehaald in 2s (22,8 kB/s)
Pakketlijsten worden ingelezen... Klaar
anko@anko-All-Series:~$
```

---

### Post by ankomonster on 2014-10-27
[I]In the terminal:
[/I]
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

results in:
```
anko@anko-All-Series:~$ sudo apt-get update
[sudo] password for anko: 
Sorry, probeer opnieuw
[sudo] password for anko: 
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic InRelease
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release.gpg                            
Genegeerd [http://dl.google.com](http://dl.google.com) stable InRelease                                
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic Release                                
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Sources                           
Geraakt [http://dl.google.com](http://dl.google.com) stable Release.gpg                                
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main amd64 Packages                    
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic InRelease                        
Geraakt [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main i386 Packages                     
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates InRelease                
Geraakt [http://dl.google.com](http://dl.google.com) stable Release                                    
Genegeerd [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports InRelease              
Genegeerd [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security InRelease                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic Release.gpg                        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates Release.gpg                
Geraakt [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages                        
Ophalen:1 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports Release.gpg [933 B]    
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic Release                            
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates Release                    
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release.gpg                 
Geraakt [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                         
Ophalen:2 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports Release [59,7 kB]      
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main Sources                       
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security Release                     
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted Sources                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe Sources                   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse Sources                 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main amd64 Packages                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted amd64 Packages          
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-nl_NL               
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Sources                
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe amd64 Packages            
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-nl                  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse amd64 Packages          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main i386 Packages                 
Genegeerd [http://extras.ubuntu.com](http://extras.ubuntu.com) utopic/main Translation-en                  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted i386 Packages           
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Sources          
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe i386 Packages            
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse i386 Packages          
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Sources           
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main Translation-nl               
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/main Translation-en               
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse Translation-nl         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/multiverse Translation-en         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted Translation-nl         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/restricted Translation-en         
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Sources         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe Translation-nl           
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic/universe Translation-en           
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/main Sources              
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/restricted Sources        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/universe Sources          
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main amd64 Packages        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/multiverse Sources        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/main amd64 Packages       
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/restricted amd64 Packages 
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/universe amd64 Packages   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/multiverse amd64 Packages  
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted amd64 Packages   
Genegeerd [http://dl.google.com](http://dl.google.com) stable/main Translation-nl_NL                   
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/main i386 Packages         
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/restricted i386 Packages   
Genegeerd [http://dl.google.com](http://dl.google.com) stable/main Translation-nl                      
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/universe i386 Packages     
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe amd64 Packages     
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/multiverse i386 Packages   
Genegeerd [http://dl.google.com](http://dl.google.com) stable/main Translation-en                      
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/main Translation-en        
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/multiverse Translation-en  
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/restricted Translation-en
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-updates/universe Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse amd64 Packages
Ophalen:3 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/main Sources [14 B]
Ophalen:4 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/restricted Sources [14 B]
Ophalen:5 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/universe Sources [1388 B]
Ophalen:6 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/multiverse Sources [14 B]
Ophalen:7 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/main amd64 Packages [14 B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main i386 Packages          
Ophalen:8 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/restricted amd64 Packages [14 B]
Ophalen:9 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/universe amd64 Packages [705 B]
Ophalen:10 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/multiverse amd64 Packages [14 B]
Ophalen:11 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/main i386 Packages [14 B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted i386 Packages    
Ophalen:12 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/restricted i386 Packages [14 B]
Ophalen:13 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/universe i386 Packages [707 B]
Ophalen:14 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/multiverse i386 Packages [14 B]
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/main Translation-en      
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/multiverse Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe i386 Packages
Geraakt [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/restricted Translation-en
Ophalen:15 [http://nl.archive.ubuntu.com](http://nl.archive.ubuntu.com) utopic-backports/universe Translation-en [256 B]
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse i386 Packages    
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/main Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/multiverse Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/restricted Translation-en
Geraakt [http://security.ubuntu.com](http://security.ubuntu.com) utopic-security/universe Translation-en
63,9 kB opgehaald in 2s (22,8 kB/s)
Pakketlijsten worden ingelezen... Klaar
anko@anko-All-Series:~$
```

---

### Post by bapoumba on 2014-10-27
OK thanks, these are only the outputs to the update command. We also need the output to the second one (the upgrade command).

In the mean time, I have found this : [https://bugs.launchpad.net/ubuntu/+source/icedtea-web/+bug/1385478](https://bugs.launchpad.net/ubuntu/+source/icedtea-web/+bug/1385478)
Probably the bug that affects you. You should mark it as affecting you too (log into Launchpad with the same login/password as Ubuntu One and click the little icon). You can also subscribe to the bug to get notified about its status.

---

### Post by ankomonster on 2014-10-27
This is after apt-get dist-upgrade:

```
anko@anko-All-Series:~$ sudo apt-get dist-upgrade
[sudo] password for anko: 
Pakketlijsten worden ingelezen... Klaar
Boom van vereisten wordt opgebouwd       
De status informatie wordt gelezen... Klaar
Opwaardering wordt doorgerekend... Klaar
0 pakketten opgewaardeerd, 0 pakketten nieuw geïnstalleerd, 0 te verwijderen en 0 niet opgewaardeerd.
1 pakketten niet volledig geïnstalleerd of verwijderd.
Door deze operatie zal er 0 B extra schijfruimte gebruikt worden.
Wilt u doorgaan? [J/n] j
Instellen van icedtea-netx:amd64 (1.5.1-1ubuntu1) ...
update-alternatives: waarschuwing: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: waarschuwing: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: waarschuwing: forcing reinstallation of alternative /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/itweb-settings because link group itweb-settings is broken
update-alternatives: waarschuwing: not replacing /usr/share/man/man1/itweb-settings.1.gz with a link
update-alternatives: error: alternative path /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/javaws doesn't exist
dpkg: error processing package icedtea-netx:amd64 (--configure):
 subproces installed post-installation script gaf een foutwaarde 2 terug
Fouten gevonden tijdens behandelen van:
 icedtea-netx:amd64
E: Sub-process /usr/bin/dpkg returned an error code (1)
anko@anko-All-Series:~$
```

---

### Post by bapoumba on 2014-10-27
OK thanks.
You may find fixes here :
[https://answers.launchpad.net/ubuntu/+source/icedtea-web/+question/254216](https://answers.launchpad.net/ubuntu/+source/icedtea-web/+question/254216)
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=759226](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=759226)

---

### Post by ankomonster on 2014-10-27
my problem is solved with: [B][https://answers.launchpad.net/ubuntu/+source/icedtea-web/+question/254216](https://answers.launchpad.net/ubuntu/+source/icedtea-web/+question/254216)


[/B]&#8203;Thanks for your help

---

### Post by bapoumba on 2014-10-27
You are welcome :)
Please mark your thread as solved (under Thread tools), thanks.

You can also have a look here for placing code tags in a post with BBCode : [http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

