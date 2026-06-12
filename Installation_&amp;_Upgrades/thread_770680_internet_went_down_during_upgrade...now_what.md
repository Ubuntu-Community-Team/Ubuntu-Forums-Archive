---
title: "internet went down during upgrade...now what?"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by mjiba on 2008-04-27
Last night, I tried to use the Update Manager to Upgrade from 7.10 to 8.04. I had downloaded about 1/4 of the files when my internet connection went down and the installation process stopped.  Since then, whenever I try to upgrade from the Update Manager (yes I did click the box to check for new updates), there is no option to upgrade (just the normal update screen telling me my system is up to date).  What am I doing wrong???

<SOLVED>
please see post #20 for my solution. was able to get update manager to upgrade to hardy!!!

---

### Post by Pumalite on 2008-04-27
If your Internet is back; run:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by mjiba on 2008-04-27
Thanks for the reply.  Unfortunately, it did not work.

mjiba@mjiba:~$ sudo dpkg --configure -a
mjiba@mjiba:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mjiba@mjiba:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                  
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [191B]            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US    
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release [65.9kB]                      
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release [58.5kB]              
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages [4065kB]            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages [7664B]           
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages [158kB]           
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages [1075kB]               
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages [83.0kB]   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages [259kB]        
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages [9936B]  
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages [4263B]  
Fetched 5787kB in 5m1s (19.2kB/s)                                              
Reading package lists... Done
mjiba@mjiba:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Pumalite on 2008-04-27
Thry the official method again:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
Choose the best Server for you.

---

### Post by nwtarr on 2008-04-27
Hmm, i have same, but more bad trouble.

I start upgrading and leave computer, when i back, the screen displays problem with package perl-modules, internet connection going down, because, network-manager is desapier from "tray".

I rebooted, but network-manager not apper.

I insert my CD-ROM with "Gutsy Gibbon" and start revery in Synaptic.

Recovering succesful finised and i reboot my PC, but... but i got a new problem when linux boot, with line /etc/rc or something else (can't read, becouse some strange garbage symbols flood over all display). 

I reboot again, have same problem, then boot in revery mode, but no fsck, no ls and other programs not avaible, i reboot again and got new problem with boot-loader...

Tomorrow, i try to reinstall from fresh burned CD with Hardy...

Be very careful!

---

### Post by mjiba on 2008-05-03
any other ideas what i can do??? i have seen other threads about similar problems but have not seen a solution as of yet.

---

### Post by Pumalite on 2008-05-03
Try to upgrade again. Post the output.

---

### Post by mjiba on 2008-05-04
I have tried this with several sources including main server, server for US, and the best server.  

mjiba@mjiba:~$ sudo apt-get update
[sudo] password for mjiba:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US       
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US          
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [191B]    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US  
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Fetched 4B in 1s (3B/s)  
Reading package lists... Done
mjiba@mjiba:~$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mjiba@mjiba:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Pumalite on 2008-05-04
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by mjiba on 2008-05-04
sorry, maybe i wasn't clear in my prior posts. i have tried using update manager to upgrade but when i check for possible upgrades, there is no option to upgrade to 8.04.  it says my system is up to date.

---

### Post by Pumalite on 2008-05-04
Post:
uname -a

---

### Post by mjiba on 2008-05-04
mjiba@mjiba:~$ uname -a
Linux mjiba 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

---

### Post by Pumalite on 2008-05-04
Well. you are in Gutsy, no doubt. You could try this, but I haven't tried it with Hardy Heron:

sudo sed -i 's/gutsy/hardy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

### Post by mjiba on 2008-05-04
no go.

sudo apt-get dist-upgrade gives same results.  system is up to date. i guess the easiest thing to do at this point is burn a CD of Hardy and try an upgrade that way.  

thanks for your help though.

---

### Post by Pumalite on 2008-05-04
Good luck.

---

### Post by mjiba on 2008-05-04
ok, so just burned hardy ISO.  my machine recognizes the disk but no prompt to upgrade.  

ran gksu "sh /cdrom/cdromupgrade"
and nothing happens.  

does anyone have an idea about what's going on here???

---

### Post by Pumalite on 2008-05-04
You need the Alternate CD to upgrade.

---

### Post by mjiba on 2008-05-04
ahh shoot.  guess i didn't have enough coffee today.  will do.  thanks again

---

### Post by Pumalite on 2008-05-04
Make it Turkish coffee.

---

### Post by mjiba on 2008-05-04
Ok, so finally got my system to upgrade.  Don't know if this is a recommended solution, but it worked.  A friend who is much more knowledgeable than i am suggested editing /etc/apt/sources.list and changing lines with gutsy to hardy.  
eg. 
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
becomes:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted

I then ran update manager which listed an enormous amount of updates and then immediately informed me that i needed to do a partial upgrade.  I clicked ok and here i am!

please understand that i am a total newb and did not figure this out myself.  i cannot recommend this to anyone else but can report that it worked for me.  can someone confirm that this is an acceptable way for others to upgrade their systems???

---

