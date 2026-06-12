---
title: "[SOLVED] cleaning up bad installation files/links"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by zachthejones on 2007-12-07
I"m sure there's a simple solution, I just have no idea where to go or what to do. I was downloading/installing a program through synaptic and chose a couple of extra add-ons to go with it. The program installed fine - but I got an error message when Synaptic tried to install them. I didn't really need them, the rest of the install was fine, so I just shrugged  my shoulders and went on.

Unfortunately, now everytime I download/install through synaptic or terminal it tries to install these add-ons - and gives me an error message every time. And it does the same thing every time I have to update something. It's really getting annoying pretty quick.

How can I get it to stop trying to install these add-ons?

---

### Post by Pumalite on 2007-12-07
Post the entire error message.
You can start with: 
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

---

### Post by zachthejones on 2007-12-08
I just got an update notificaiton for ubuntu today. after initiating the update and letting it do its thing, it popped up a window saying, 'An error occured.' and the next line says, "The following details are provided:" and the window says this:
```
E: lyricue-bible-kjv: subprocess post-installation script returned error exit status 127
E: lyricue-bible-mes: subprocess post-installation script returned error exit status 127
E: lyricue-bible-niv: subprocess post-installation script returned error exit status 127
E: lyricue-bible-nlt: subprocess post-installation script returned error exit status 127
```

is that what you need? I can install a program through terminal and give you the error output if that's better.

---

### Post by Pumalite on 2007-12-08
Did you run the commands I gave you in post # 2?

---

### Post by zachthejones on 2007-12-08
sorry, here ya go...

when I run "sudo apt-get install -f" I get this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up lyricue-bible-kjv (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-kjv.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-kjv.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-kjv (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-mes (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-mes.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-mes.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-mes (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-niv (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-niv.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-niv.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-niv (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-nlt (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-nlt.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-nlt.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-nlt (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 lyricue-bible-kjv
 lyricue-bible-mes
 lyricue-bible-niv
 lyricue-bible-nlt
E: Sub-process /usr/bin/dpkg returned an error code (1)
zach@zach-desktop:~$ 
```

when I run "sudo apt-get update" this is what I get:
```
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://dl.google.com stable Release                                        
Err http://dl.google.com stable Release                                        
  
Get:2 http://download.tuxfamily.org gutsy Release.gpg [189B]                   
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_US
Get:3 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:4 http://www.adebenham.com ./ Release.gpg [189B]                           
Ign http://www.adebenham.com ./ Translation-en_US                              
Get:5 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Get:6 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Get:7 http://dl.google.com stable Release [748B]                               
Ign http://dl.google.com stable Release                                        
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Hit http://dl.google.com stable/non-free Packages                              
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Get:8 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com gutsy Release                                 
Hit http://archive.canonical.com gutsy Release                                 
Hit http://security.ubuntu.com gutsy-security Release                          
Hit http://download.tuxfamily.org gutsy Release                                
Hit http://www.adebenham.com ./ Release                                        
Get:9 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://us.archive.ubuntu.com gutsy/main Packages                           
Hit http://us.archive.ubuntu.com gutsy/restricted Packages                     
Hit http://us.archive.ubuntu.com gutsy/main Sources                            
Ign http://giss.tv ./ Release.gpg                                              
Ign http://giss.tv ./ Translation-en_US                                        
Hit http://us.archive.ubuntu.com gutsy/restricted Sources                      
Hit http://us.archive.ubuntu.com gutsy/universe Packages                       
Hit http://us.archive.ubuntu.com gutsy/universe Sources                        
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages                     
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources                      
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Ign http://giss.tv ./ Release                                                  
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://giss.tv ./ Packages                                                 
Err http://www.adebenham.com ./ Release                                        
  
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Packages        
Hit http://giss.tv ./ Packages                                                 
Get:10 http://www.adebenham.com ./ Release [495B]                              
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Sources         
Ign http://www.adebenham.com ./ Release                              
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US   
Ign http://www.adebenham.com ./ Packages                             
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages         
Hit http://www.adebenham.com ./ Packages       
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Hit http://packages.medibuntu.org gutsy Release
Ign http://packages.medibuntu.org gutsy/free Packages
Ign http://packages.medibuntu.org gutsy/non-free Packages
Ign http://packages.medibuntu.org gutsy/free Sources
Ign http://packages.medibuntu.org gutsy/non-free Sources
Hit http://packages.medibuntu.org gutsy/free Packages
Hit http://packages.medibuntu.org gutsy/non-free Packages                      
Hit http://packages.medibuntu.org gutsy/free Sources                           
Hit http://packages.medibuntu.org gutsy/non-free Sources                       
Fetched 1627B in 7s (208B/s)                                                   
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://www.adebenham.com ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A7BC8E1B734D1F5
W: You may want to run apt-get update to correct these problems
zach@zach-desktop:~$ 
```

when I run "sudo apt-get upgrade" I get:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up lyricue-bible-kjv (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-kjv.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-kjv.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-kjv (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-mes (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-mes.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-mes.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-mes (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-niv (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-niv.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-niv.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-niv (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-nlt (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-nlt.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-nlt.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-nlt (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 lyricue-bible-kjv
 lyricue-bible-mes
 lyricue-bible-niv
 lyricue-bible-nlt
E: Sub-process /usr/bin/dpkg returned an error code (1)
zach@zach-desktop:~$ 

```

but I seem to still be having the same problem.

---

### Post by Pumalite on 2007-12-08
Run first:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
And report back with output.

---

### Post by zachthejones on 2007-12-08
on running "sudo dpkg --configure -a", I get this output:
```
Setting up lyricue-bible-mes (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-mes.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-mes.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-mes (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-nlt (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-nlt.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-nlt.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-nlt (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-kjv (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-kjv.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-kjv.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-kjv (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-niv (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-niv.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-niv.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-niv (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 lyricue-bible-mes
 lyricue-bible-nlt
 lyricue-bible-kjv
 lyricue-bible-niv
zach@zach-desktop:~$ 
```

The output for "sudo apt-get update" is:
```
Get:1 http://dl.google.com stable Release.gpg [189B]
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://dl.google.com stable Release                                        
Err http://dl.google.com stable Release                                        
  
Get:2 http://security.ubuntu.com gutsy-security Release.gpg [191B]             
Ign http://security.ubuntu.com gutsy-security/main Translation-en_US           
Get:3 http://packages.medibuntu.org gutsy Release.gpg [189B]                   
Ign http://packages.medibuntu.org gutsy/free Translation-en_US                 
Get:4 http://us.archive.ubuntu.com gutsy Release.gpg [191B]                    
Ign http://us.archive.ubuntu.com gutsy/main Translation-en_US                  
Get:5 http://dl.google.com stable Release [748B]                               
Get:6 http://download.tuxfamily.org gutsy Release.gpg [189B]                   
Ign http://download.tuxfamily.org gutsy/avant-window-navigator Translation-en_US
Get:7 http://www.adebenham.com ./ Release.gpg [189B]                           
Ign http://dl.google.com stable Release                                        
Get:8 http://archive.canonical.com gutsy Release.gpg [191B]                    
Ign http://archive.canonical.com gutsy/partner Translation-en_US               
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_US     
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_US       
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_US     
Ign http://www.adebenham.com ./ Translation-en_US                              
Ign http://giss.tv ./ Release.gpg                                              
Ign http://giss.tv ./ Translation-en_US                                        
Hit http://dl.google.com stable/non-free Packages                              
Ign http://us.archive.ubuntu.com gutsy/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com gutsy/universe Translation-en_US              
Ign http://us.archive.ubuntu.com gutsy/multiverse Translation-en_US            
Hit http://security.ubuntu.com gutsy-security Release                          
Ign http://packages.medibuntu.org gutsy/non-free Translation-en_US             
Hit http://packages.medibuntu.org gutsy Release                                
Get:9 http://us.archive.ubuntu.com gutsy-updates Release.gpg [191B]            
Ign http://us.archive.ubuntu.com gutsy-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com gutsy-updates/restricted Translation-en_US    
Hit http://download.tuxfamily.org gutsy Release                                
Hit http://archive.canonical.com gutsy Release                                 
Ign http://us.archive.ubuntu.com gutsy-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com gutsy-updates/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com gutsy Release                                 
Hit http://www.adebenham.com ./ Release                                        
Ign http://giss.tv ./ Release                                                  
Hit http://us.archive.ubuntu.com gutsy-updates Release                         
Hit http://security.ubuntu.com gutsy-security/main Packages                    
Ign http://packages.medibuntu.org gutsy/free Packages                          
Ign http://giss.tv ./ Packages                                                 
Hit http://security.ubuntu.com gutsy-security/restricted Packages              
Hit http://security.ubuntu.com gutsy-security/main Sources                     
Hit http://security.ubuntu.com gutsy-security/restricted Sources               
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Packages        
Err http://www.adebenham.com ./ Release                                        
  
Hit http://archive.canonical.com gutsy/partner Packages                        
Ign http://packages.medibuntu.org gutsy/non-free Packages                      
Ign http://packages.medibuntu.org gutsy/free Sources                           
Ign http://packages.medibuntu.org gutsy/non-free Sources                       
Hit http://giss.tv ./ Packages                                                 
Hit http://us.archive.ubuntu.com gutsy/main Packages                           
Hit http://security.ubuntu.com gutsy-security/universe Packages                
Hit http://security.ubuntu.com gutsy-security/universe Sources                 
Hit http://security.ubuntu.com gutsy-security/multiverse Packages              
Hit http://security.ubuntu.com gutsy-security/multiverse Sources               
Hit http://download.tuxfamily.org gutsy/avant-window-navigator Sources         
Get:10 http://www.adebenham.com ./ Release [495B]                              
Ign http://www.adebenham.com ./ Release                                        
Hit http://archive.canonical.com gutsy/partner Sources                         
Hit http://packages.medibuntu.org gutsy/free Packages                
Hit http://packages.medibuntu.org gutsy/non-free Packages            
Hit http://packages.medibuntu.org gutsy/free Sources                 
Ign http://www.adebenham.com ./ Packages                             
Hit http://us.archive.ubuntu.com gutsy/restricted Packages
Hit http://us.archive.ubuntu.com gutsy/main Sources
Hit http://us.archive.ubuntu.com gutsy/restricted Sources
Hit http://packages.medibuntu.org gutsy/non-free Sources
Hit http://www.adebenham.com ./ Packages       
Hit http://us.archive.ubuntu.com gutsy/universe Packages
Hit http://us.archive.ubuntu.com gutsy/universe Sources
Hit http://us.archive.ubuntu.com gutsy/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy/multiverse Sources
Hit http://us.archive.ubuntu.com gutsy-updates/main Packages
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Packages
Hit http://us.archive.ubuntu.com gutsy-updates/main Sources
Hit http://us.archive.ubuntu.com gutsy-updates/restricted Sources
Hit http://us.archive.ubuntu.com gutsy-updates/universe Packages
Hit http://us.archive.ubuntu.com gutsy-updates/universe Sources
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com gutsy-updates/multiverse Sources
Fetched 1627B in 1s (1223B/s)
Reading package lists... Done
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://www.adebenham.com ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7A7BC8E1B734D1F5
W: You may want to run apt-get update to correct these problems
zach@zach-desktop:~$ 
```

and then the output for "sudo apt-get upgrade" is:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up lyricue-bible-kjv (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-kjv.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-kjv.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-kjv (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-mes (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-mes.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-mes.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-mes (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-niv (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-niv.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-niv.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-niv (--configure):
 subprocess post-installation script returned error exit status 127
Setting up lyricue-bible-nlt (0.2) ...
grep: /etc/mysql/debian.cnf: No such file or directory
/var/lib/dpkg/info/lyricue-bible-nlt.postinst: 44: mysql: not found
/var/lib/dpkg/info/lyricue-bible-nlt.postinst: 44: mysql: not found
dpkg: error processing lyricue-bible-nlt (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 lyricue-bible-kjv
 lyricue-bible-mes
 lyricue-bible-niv
 lyricue-bible-nlt
E: Sub-process /usr/bin/dpkg returned an error code (1)
zach@zach-desktop:~$ 

```

pretty much still the same, I believe

---

### Post by Pumalite on 2007-12-08
I ran out of suggestions. Hopefully someone will chime in.

---

### Post by zachthejones on 2007-12-08
okay, here's my thinking process on this: when I use synaptic for multiple installations, somewhere a list/log is generated for the installation program to work through. Apparently as it finishes installing something from the list/log it removes it from said list/log. The flip side of this being that it does not remove items which do not install,

All I gotta do is figure out how to purge or edit this list/log and I'll be back in business. But I have no idea where to start.

---

### Post by Pumalite on 2007-12-08
Take a look at /var/lib/dpkg/status

---

### Post by zachthejones on 2007-12-09
this may be what I'm looking for, I'm not sure. I opened up the file in gedit and found several of the add-ons in the list, here's what one of 'em looked like:

```
Package: lyricue-bible-mes
Status: install ok half-configured
Priority: optional
Section: x11
Installed-Size: 6436
Maintainer: Lyricue Developers List <lds-devel@lists.sourceforge.net>
Architecture: all
Version: 0.2
Provides: lyricue-bible
Description: The Message for use with lyricue
 The Message Bible as a mysql database for use in lyricue
```

I think the problem is in the "Status: install ok half-configured" line, because all the other programs which installed correctly read "Status: install ok installed"

Can I just delete the section for each of these add-ons from this file? will that solve the problem?

(I should probably make a back-up first, eh? ;-) )

---

### Post by Pumalite on 2007-12-09
You can change the status to 'installed...ok...installed'. But, remember, this is a half cure. It only allows you to use your apt-get again, but the mess is left behind.

---

### Post by zachthejones on 2007-12-09
I guess I'll do that for now...but if anyone out there knows how to clean up the mess, let me know!

---

### Post by zachthejones on 2007-12-26
as a further note, I eventually realized i could just uninstall the programs which were giving me the problem - which I did through Synaptic.  haven't had any trouble since!

---

### Post by Pumalite on 2007-12-26
Usually the best solution is the simplest. It just didn't occur to me at that time. Sorry.

---

### Post by jmw5098 on 2007-12-27
I have the same problem.  However, I can't find the programs to be able to uninstall them.

When I install other apps, I get an error message:
[INDENT]E: python-mutagen: subprocess post-installation script returned error exit status 1
E: exfalso: dependency problems - leaving unconfigured
E: quodlibet: dependency problems - leaving unconfigured
[/INDENT]
I looked in the status file and they look like this:

[INDENT]Package: exfalso
Status: install ok unpacked
Priority: optional[/INDENT]

I could change it to 'install ok installed', right?  But I would rather clean it up or just uninstall them.  How would I go about do that?

---

### Post by Pumalite on 2007-12-28
Try:
sudo dpkg --remove --force-remove-reinstreq <packagename>

---

### Post by jmw5098 on 2007-12-28
I tried sudo dpkg --remove --force-remove-reinstreq quodlibet and got
```
(Reading database ... 102876 files and directories currently installed.)
Removing quodlibet ...

```

But, when I opened 'Add/Remove Programs' after doing this, I got an error about the status file not matching something....

However, I tried this and it seemed to have fixed my problems: 
```
sudo dpkg --purge [package name]
```
I'm not real sure if I did something bad by doing it, but right now it seems to have worked.

Thanks for the help.

---

### Post by Pumalite on 2007-12-28
You are welcome. Good luck.

---

