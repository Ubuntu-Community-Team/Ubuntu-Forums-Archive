---
title: "Error while doing regular updates"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by nmr on 2010-10-10
Hi,

I am trying to update my existing 10.04 before upgrading to 10.10.

When I go to the Update Manager, there are available updates, but when I click install there is always an error:

"Falhou obter [http://ppa.launchpad.net/lucid-bleed/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/lucid-bleed/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Falhou o download de alguns ficheiros de índice, foram ignorados ou os antigos foram usados em seu lugar."

I have a portuguese version of Ubuntu. I don't know the exact, original  english version, but it must be something like:

"Fail when atempting to obtain (....) 
 Some index files download failed, were ignored ou the old one were used in their place"

When I type sudo-get update, this is the full log:

```

Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-pt_PT   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-pt_PT
Ign http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/lucid-bleed/pp/ubuntu/ lucid/main Translation-pt_PT
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-pt_PT
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-pt_PT
Hit http://pt.archive.ubuntu.com lucid Release.gpg                             
Ign http://pt.archive.ubuntu.com/ubuntu/ lucid/main Translation-pt_PT          
Ign http://pt.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-pt_PT    
Ign http://pt.archive.ubuntu.com/ubuntu/ lucid/universe Translation-pt_PT      
Ign http://pt.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-pt_PT    
Hit http://pt.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://pt.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-pt_PT  
Ign http://pt.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-pt_PT
Ign http://pt.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-pt_PT
Ign http://pt.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-pt_PT
Obter:1 http://dl.google.com stable Release.gpg [189B]                         
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-pt_PT       
Hit http://security.ubuntu.com lucid-security Release                          
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://linux.dropbox.com lucid Release.gpg                                 
Hit http://pt.archive.ubuntu.com lucid Release                                 
Hit http://pt.archive.ubuntu.com lucid-updates Release                         
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-pt_PT              
Ign http://ppa.launchpad.net lucid/main Packages                               
Obter:2 http://dl.google.com stable Release [2544B]                            
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://pt.archive.ubuntu.com lucid/main Packages                           
Hit http://linux.dropbox.com lucid Release                                     
Ign http://ppa.launchpad.net lucid/main Packages                               
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Hit http://pt.archive.ubuntu.com lucid/restricted Packages                     
Hit http://pt.archive.ubuntu.com lucid/main Sources                            
Hit http://pt.archive.ubuntu.com lucid/restricted Sources                      
Hit http://pt.archive.ubuntu.com lucid/universe Packages                       
Hit http://pt.archive.ubuntu.com lucid/universe Sources                        
Hit http://pt.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://pt.archive.ubuntu.com lucid/multiverse Sources                      
Hit http://pt.archive.ubuntu.com lucid-updates/main Packages                   
Hit http://pt.archive.ubuntu.com lucid-updates/restricted Packages             
Hit http://pt.archive.ubuntu.com lucid-updates/main Sources                    
Err http://ppa.launchpad.net lucid/main Packages                               
  404  Not Found
Hit http://pt.archive.ubuntu.com lucid-updates/restricted Sources              
Hit http://pt.archive.ubuntu.com lucid-updates/universe Packages               
Hit http://pt.archive.ubuntu.com lucid-updates/universe Sources                
Hit http://pt.archive.ubuntu.com lucid-updates/multiverse Packages             
Hit http://pt.archive.ubuntu.com lucid-updates/multiverse Sources              
Hit http://linux.dropbox.com lucid/main Packages                               
Obter:3 http://dl.google.com stable/main Packages [1092B]    
Obtidos 3825B em 4s (819B/s)    
W: Falhou obter http://ppa.launchpad.net/lucid-bleed/pp/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Falhou o download de alguns ficheiros de índice, foram ignorados ou os antigos foram usados em seu lugar.

```I am also having a few problems with rhythmbox, movie player (the native player, in portuguese it's "Reprodutor de filmes") and vlc - some files require addicional pluggins, but they are failling to install. Maybe the two erros are related.

I am a very basic, ignorant, recent user of Ubuntu (I started using it just a little before Lucid was released, and have not manage to become, in no ways, an expert). So far, the very few glitches I have come across, I was able to workaround by reading the available documentation and foruns, and following the advices given. 

For this particular error, I was not able to find any thread or wiki regarding it.

Can anyone please give advice? I would like to get all 10.04 updates, before upgrading to 10.10. A few days I tried 10.10 alpha and it went bad. I got the grub prompt and, though there was documentation on how to resolve it, I could not, on my own. So I had to do a clean install, losing everything I had on my hard disk (which was not good and meant some lost time, but no tragedy, 'cause most important files are in an external disk).

---

### Post by mörgæs on 2010-10-10
If 10.10 Alpha did not work, I think you should try a 10.10 (final version) live boot as a first step before trying to upgrade.

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by nmr on 2010-10-10
Thank you, mörgæs, for the advice, I will do that, and try it before installing. Should I not be worried then about this failure to do these updates? Will they be gone when I succeed upgrading to 10.10?

---

### Post by nmr on 2010-10-11
I dd a clean install, from a live CD of 10.10.

Working fine. (I had that problem with the mouse left button not working, but installed [this]("https://bugs.launchpad.net/udev/+bug/637208/comments/40") and it worked)

I am closing this thread.

---

