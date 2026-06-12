---
title: "PPAs not working"
date: 2012-03-25
forum: Installation &amp; Upgrades
---

### Post by Inoki on 2012-03-25
Guys I have the following problem,

when I try to add any PPA I constantly get the error 404 Not Found, while others tried the same PPA and it worked for them.

I use the command sudo add-apt-repository PPA, it normally imports the PPA with keys but when I refresh, I get that error. Any help?

I'm running Xubuntu 11.10 x64 bit modified with a bit of Linux Mint stuff, like Mintupdate.

---

### Post by wildmanne39 on 2012-03-25
Hi is this the format you are using?
```
sudo add-apt-repository ppa:elementaryart/elementarydesktop
```
It sounds like the server may be down or the ppa is not on the server at this time.

Post a link to it here please.
Thanks

---

### Post by Inoki on 2012-03-25
Yer, the exact same format. But no third party PPAs are working for me.

---

### Post by wildmanne39 on 2012-03-25
Ok, run ```
sudo apt-get update
```
post the results here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Inoki on 2012-03-25
```
innerdistance@innerdistance-Satellite-L650:~$ sudo add-apt-repository ppa:nilarimogard/webupd8
[sudo] password for innerdistance: 
You are about to add the following PPA to your system:
 WebUpd8
 PPA maintained by Web Upd8: http://www.webupd8.org/

To add this PPA, simply paste this in a terminal (Ubuntu Karmic +):
sudo add-apt-repository ppa:nilarimogard/webupd8

Packages in this PPA: audacious, autotrash, awn-applet-radio, awn-applet-wm, bluetile, cmus, defrag, dockbarx, dockbarx-themes-extra, dropbox-share, ekiga, exaile, fatrat, gimp, gimp-plugin-registry, gnome-globalmenu, gnome-subtitles, gnome-window-applets, grsync, gthumb, launchpad-getkeys, mc (Midnight Commander), minitunes, minitube, mintmenu, n2n, nautilus-columns, newsbeuter, pinta, ppa-purge, fixed pulseaudio-equalizer, specto, subtitleeditor, switcher, talika, terminator, turpial, update-java, watchvideo, youtube-dl and zaz. Almost all packages are updated to their latest version.

For other (specialized) PPAs we maintain, see: https://launchpad.net/~webupd8team
 More info: https://launchpad.net/~nilarimogard/+archive/webupd8
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.5HiDHxtIqp --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 1DB29AFFF6C70907B57AA31F531EE72F4C9D234C
gpg: requesting key 4C9D234C from hkp server keyserver.ubuntu.com
gpg: k&#318;ú&#269; 4C9D234C: importovaný verejný k&#318;ú&#269; "Launchpad webupd8"
gpg: Celkovo spracovaných k&#318;ú&#269;ov: 1
gpg:               importované: 1  (RSA: 1)
innerdistance@innerdistance-Satellite-L650:~$ sudo apt-get update
Ign http://extras.ubuntu.com oneiric InRelease                                                                                                                                                                    
Ign http://archive.canonical.com oneiric InRelease                                                                                                      
Ign http://security.ubuntu.com oneiric-security InRelease                                                                       
Ign http://sk.archive.ubuntu.com oneiric InRelease                                                                              
Ign http://sk.archive.ubuntu.com oneiric-updates InRelease                                                                      
Ign http://sk.archive.ubuntu.com oneiric-backports InRelease                                                                    
Ign http://ppa.launchpad.net debian InRelease                                                                                                            
Ign http://packages.linuxmint.com debian InRelease                                                                                                       
Ign http://ppa.launchpad.net debian Release.gpg                                                                                 
Získava sa:1 http://security.ubuntu.com oneiric-security Release.gpg [198 B]                                                    
Získava sa:2 http://archive.canonical.com oneiric Release.gpg [198 B]                                                           
Získava sa:3 http://extras.ubuntu.com oneiric Release.gpg [72 B]                                                                
Získava sa:4 http://packages.linuxmint.com debian Release.gpg [197 B]                                                           
Ign http://ppa.launchpad.net debian Release                                                                                                                      
Už existuje http://extras.ubuntu.com oneiric Release                                                                            
Už existuje http://security.ubuntu.com oneiric-security Release                                                                 
Už existuje http://archive.canonical.com oneiric Release                                               
Získava sa:5 http://packages.linuxmint.com debian Release [12,2 kB]                                                                                     
Už existuje http://extras.ubuntu.com oneiric/main Sources                                                                                                        
Už existuje http://security.ubuntu.com oneiric-security/main Sources                                                                                             
Už existuje http://archive.canonical.com oneiric/partner Sources                                                                        
Ign http://ppa.launchpad.net debian/main TranslationIndex                                                                                                
Už existuje http://extras.ubuntu.com oneiric/main amd64 Packages                                                                
Už existuje http://extras.ubuntu.com oneiric/main i386 Packages                                                                 
Už existuje http://security.ubuntu.com oneiric-security/restricted Sources                                                                               
Už existuje http://security.ubuntu.com oneiric-security/universe Sources                                                                                 
Už existuje http://security.ubuntu.com oneiric-security/multiverse Sources                                                                               
Už existuje http://security.ubuntu.com oneiric-security/main amd64 Packages                                                                              
Už existuje http://security.ubuntu.com oneiric-security/restricted amd64 Packages                                                                        
Už existuje http://archive.canonical.com oneiric/partner amd64 Packages                                                                                  
Už existuje http://archive.canonical.com oneiric/partner i386 Packages                                                                                   
Ign http://archive.canonical.com oneiric/partner TranslationIndex                                                                                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                                                                                               
Už existuje http://security.ubuntu.com oneiric-security/universe amd64 Packages                                                 
Už existuje http://security.ubuntu.com oneiric-security/multiverse amd64 Packages                                               
Už existuje http://security.ubuntu.com oneiric-security/main i386 Packages                                                                               
Už existuje http://security.ubuntu.com oneiric-security/restricted i386 Packages                                                                         
Už existuje http://security.ubuntu.com oneiric-security/universe i386 Packages                                                                           
Získava sa:6 http://packages.linuxmint.com debian/main amd64 Packages [12,6 kB]                                                                          
Získava sa:7 http://sk.archive.ubuntu.com oneiric Release.gpg [198 B]                                                                                                          
Získava sa:8 http://sk.archive.ubuntu.com oneiric-updates Release.gpg [198 B]                                                                                    
Získava sa:9 http://sk.archive.ubuntu.com oneiric-backports Release.gpg [198 B]                                                                                  
Už existuje http://sk.archive.ubuntu.com oneiric Release                                                                                                         
Už existuje http://security.ubuntu.com oneiric-security/multiverse i386 Packages                                                                                                
Už existuje http://security.ubuntu.com oneiric-security/main TranslationIndex                                                                            
Už existuje http://security.ubuntu.com oneiric-security/multiverse TranslationIndex                                                                      
Už existuje http://security.ubuntu.com oneiric-security/restricted TranslationIndex                                                                      
Už existuje http://security.ubuntu.com oneiric-security/universe TranslationIndex                                                                        
Už existuje http://sk.archive.ubuntu.com oneiric-updates Release                                                                                         
Už existuje http://security.ubuntu.com oneiric-security/main Translation-en                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric-backports Release                                                                                                                
Už existuje http://sk.archive.ubuntu.com oneiric/main Sources                                                                                                                                                     
Už existuje http://sk.archive.ubuntu.com oneiric/restricted Sources                                                                                                                                               
Už existuje http://sk.archive.ubuntu.com oneiric/universe Sources                                                                                                                                                 
Už existuje http://sk.archive.ubuntu.com oneiric/multiverse Sources                                                                                                                                               
Už existuje http://sk.archive.ubuntu.com oneiric/main amd64 Packages                                                                                                                                              
Už existuje http://security.ubuntu.com oneiric-security/multiverse Translation-en                                                                                                                                 
Už existuje http://security.ubuntu.com oneiric-security/restricted Translation-en                                                                                                                                 
Získava sa:10 http://packages.linuxmint.com debian/import amd64 Packages [56,3 kB]                                                                                                                                
Už existuje http://sk.archive.ubuntu.com oneiric/restricted amd64 Packages                                                                                                                                        
Už existuje http://sk.archive.ubuntu.com oneiric/universe amd64 Packages                                                                                                                                          
Už existuje http://sk.archive.ubuntu.com oneiric/multiverse amd64 Packages                                                                                                                                        
Už existuje http://sk.archive.ubuntu.com oneiric/main i386 Packages                                                                                                                                               
Už existuje http://security.ubuntu.com oneiric-security/universe Translation-en                                                                                                                                   
Už existuje http://sk.archive.ubuntu.com oneiric/restricted i386 Packages                                                                                                                                         
Už existuje http://sk.archive.ubuntu.com oneiric/universe i386 Packages                                                                                                                                           
Už existuje http://sk.archive.ubuntu.com oneiric/multiverse i386 Packages                                                                                                                                         
Už existuje http://sk.archive.ubuntu.com oneiric/main TranslationIndex                                                                                                                                            
Už existuje http://sk.archive.ubuntu.com oneiric/multiverse TranslationIndex                                                                                                                                      
Už existuje http://sk.archive.ubuntu.com oneiric/restricted TranslationIndex                                                                                                                                      
Získava sa:11 http://packages.linuxmint.com debian/backport amd64 Packages [20 B]                                                                                                                                 
Získava sa:12 http://packages.linuxmint.com debian/main i386 Packages [12,6 kB]                                                                                                                                   
Už existuje http://sk.archive.ubuntu.com oneiric/universe TranslationIndex                                                                                                                                        
Už existuje http://sk.archive.ubuntu.com oneiric-updates/main Sources                                                                                                                                             
Už existuje http://sk.archive.ubuntu.com oneiric-updates/restricted Sources                                                                                                                                       
Už existuje http://sk.archive.ubuntu.com oneiric-updates/universe Sources                                                                                                                                         
Už existuje http://sk.archive.ubuntu.com oneiric-updates/multiverse Sources                                                                                                                                       
Chyba http://ppa.launchpad.net debian/main Sources                                                                                                                                                                
  404  Not Found
Chyba http://ppa.launchpad.net debian/main amd64 Packages                                                                                                                                                         
  404  Not Found
Chyba http://ppa.launchpad.net debian/main i386 Packages                                                                                                                                                          
  404  Not Found
Získava sa:13 http://packages.linuxmint.com debian/import i386 Packages [56,4 kB]                                                                                                                                 
Už existuje http://sk.archive.ubuntu.com oneiric-updates/main amd64 Packages                                                                                                                                      
Už existuje http://sk.archive.ubuntu.com oneiric-updates/restricted amd64 Packages                                                                                                                                
Už existuje http://sk.archive.ubuntu.com oneiric-updates/universe amd64 Packages                                                                                                                                  
Už existuje http://sk.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages                                                                                                                                
Už existuje http://sk.archive.ubuntu.com oneiric-updates/main i386 Packages                                                                                                                                       
Už existuje http://sk.archive.ubuntu.com oneiric-updates/restricted i386 Packages                                                                                                                                 
Už existuje http://sk.archive.ubuntu.com oneiric-updates/universe i386 Packages                                                                                                                                   
Už existuje http://sk.archive.ubuntu.com oneiric-updates/multiverse i386 Packages                                                                                                                                 
Už existuje http://sk.archive.ubuntu.com oneiric-updates/main TranslationIndex                                                                                                                                    
Ign http://extras.ubuntu.com oneiric/main Translation-sk_SK                                                                                                                                                       
Získava sa:14 http://packages.linuxmint.com debian/backport i386 Packages [20 B]                                                                                                                                  
Ign http://packages.linuxmint.com debian/backport TranslationIndex                                                                                                                                                
Ign http://packages.linuxmint.com debian/import TranslationIndex                                                                                                                                                  
Ign http://packages.linuxmint.com debian/main TranslationIndex                                                                                                                                                    
Už existuje http://sk.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex                                                                                                                              
Ign http://extras.ubuntu.com oneiric/main Translation-sk                                                                                                                                                          
Ign http://archive.canonical.com oneiric/partner Translation-sk_SK                                                                                                                                                
Ign http://ppa.launchpad.net debian/main Translation-sk_SK                                                                                                                                                        
Ign http://extras.ubuntu.com oneiric/main Translation-en                                                                                                                                                          
Ign http://archive.canonical.com oneiric/partner Translation-sk                                                                                                                                                   
Ign http://ppa.launchpad.net debian/main Translation-sk                                                                                                                                                           
Ign http://archive.canonical.com oneiric/partner Translation-en                                                                                                                                                   
Už existuje http://sk.archive.ubuntu.com oneiric-updates/restricted TranslationIndex                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric-updates/universe TranslationIndex                                                                                                                                
Už existuje http://sk.archive.ubuntu.com oneiric-backports/main Sources                                                                                                                                           
Už existuje http://sk.archive.ubuntu.com oneiric-backports/restricted Sources                                                                                                                                     
Už existuje http://sk.archive.ubuntu.com oneiric-backports/universe Sources                                                                                                                                       
Už existuje http://sk.archive.ubuntu.com oneiric-backports/multiverse Sources                                                                                                                                     
Už existuje http://sk.archive.ubuntu.com oneiric-backports/main amd64 Packages                                                                                                                                    
Už existuje http://sk.archive.ubuntu.com oneiric-backports/restricted amd64 Packages                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric-backports/universe amd64 Packages                                                                                                                                
Ign http://ppa.launchpad.net debian/main Translation-en                                                                                                                                                           
Už existuje http://sk.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric-backports/main i386 Packages                                                                                                                                     
Už existuje http://sk.archive.ubuntu.com oneiric-backports/restricted i386 Packages                                                                                                                               
Už existuje http://sk.archive.ubuntu.com oneiric-backports/universe i386 Packages                                                                                                                                 
Už existuje http://sk.archive.ubuntu.com oneiric-backports/multiverse i386 Packages                                                                                                                               
Už existuje http://sk.archive.ubuntu.com oneiric-backports/main TranslationIndex                                                                                                                                  
Už existuje http://sk.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex                                                                                                                            
Už existuje http://sk.archive.ubuntu.com oneiric-backports/restricted TranslationIndex                                                                                                                            
Už existuje http://sk.archive.ubuntu.com oneiric-backports/universe TranslationIndex                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric/main Translation-sk                                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric/main Translation-en                                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric/multiverse Translation-sk                                                                                                                                        
Už existuje http://sk.archive.ubuntu.com oneiric/multiverse Translation-en                                                                                                                                        
Už existuje http://sk.archive.ubuntu.com oneiric/restricted Translation-sk                                                                                                                                        
Už existuje http://sk.archive.ubuntu.com oneiric/restricted Translation-en                                                                                                                                        
Už existuje http://sk.archive.ubuntu.com oneiric/universe Translation-sk                                                                                                                                          
Už existuje http://sk.archive.ubuntu.com oneiric/universe Translation-en                                                                                                                                          
Už existuje http://sk.archive.ubuntu.com oneiric-updates/main Translation-en                                                                                                                                      
Už existuje http://sk.archive.ubuntu.com oneiric-updates/multiverse Translation-en                                                                                                                                
Už existuje http://sk.archive.ubuntu.com oneiric-updates/restricted Translation-en                                                                                                                                
Už existuje http://sk.archive.ubuntu.com oneiric-updates/universe Translation-en                                                                                                                                  
Už existuje http://sk.archive.ubuntu.com oneiric-backports/main Translation-en                                                                                                                                    
Už existuje http://sk.archive.ubuntu.com oneiric-backports/multiverse Translation-en                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric-backports/restricted Translation-en                                                                                                                              
Už existuje http://sk.archive.ubuntu.com oneiric-backports/universe Translation-en                                                                                                                                
Ign http://packages.linuxmint.com debian/backport Translation-sk_SK                                                                                                                                               
Ign http://packages.linuxmint.com debian/backport Translation-sk                                                                                                                                                  
Ign http://packages.linuxmint.com debian/backport Translation-en                                                                                                                                                  
Ign http://packages.linuxmint.com debian/import Translation-sk_SK                                                                                                                                                 
Ign http://packages.linuxmint.com debian/import Translation-sk                                                                                                                                                    
Ign http://packages.linuxmint.com debian/import Translation-en                                                                                                                                                    
Ign http://packages.linuxmint.com debian/main Translation-sk_SK                                                                                                                                                   
Ign http://packages.linuxmint.com debian/main Translation-sk                                                                                                                                                      
Ign http://packages.linuxmint.com debian/main Translation-en                                                                                                                                                      
152 kB sa stiahlo za 18 s (8*406 B/s)                                                                                                                                                                             
W: Zlyhalo stiahnutie http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/debian/main/source/Sources  404  Not Found

W: Zlyhalo stiahnutie http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/debian/main/binary-amd64/Packages  404  Not Found

W: Zlyhalo stiahnutie http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/debian/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by oldos2er on 2012-03-25
If you're using 11.10, change the webupd8 PPAs to [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/oneiric/](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu/dists/oneiric/) 

I would also remove any debian repositories if I were you.

---

### Post by Inoki on 2012-03-25
I'm not a too experienced user, so if you could somehow guide me through the process I'd be grateful.

---

### Post by wildmanne39 on 2012-03-25
Hi, you have quite a lot of repositories like debian and mint, I recommend setting them back to default here is a link to do that.
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)
Thanks

---

### Post by oldos2er on 2012-03-25
> **Anathaen said:**
> I'm not a too experienced user, so if you could somehow guide me through the process I'd be grateful.

Run ```
gksu software-properties-gtk
``` in a terminal, uncheck the appropriate boxes under the 'Other Software' tab. Close the program when you're done, and it should prompt you to reload the sources lists; let it do so.

---

### Post by Inoki on 2012-04-01
Nope, doesn't help. Today I tried to add the clamav update PPA with the command ```
sudo add-apt-repository ppa:ubuntu-clamav/ppa
``` it even added the PPA with keys, but when I update, always the same, 404 Not Found. Am running Xubuntu 11.10 x64 bit

---

### Post by oldos2er on 2012-04-01
Can you post the full output of ```
sudo apt-get update
``` ?

---

### Post by Inoki on 2012-04-05
Could this be the problem? I have Xubuntu 11.10 installed, but Ubuntu Tweak shows I got LinuxMint 1 Debian installed >.>

---

### Post by Elfy on 2012-04-05
I would be inclined to make sure that all of your source.lists are referring to the correct version.

Check them in software properties

```
gksudo software-properties-gtk
```

You have all sorts of repo's in your sources.

---

