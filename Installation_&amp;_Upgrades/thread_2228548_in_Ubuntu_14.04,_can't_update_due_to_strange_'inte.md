---
title: "in Ubuntu 14.04, can't update due to strange 'internet connection' problem"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by floyd2 on 2014-06-08
Hi there - I'm totally new, please be extremely patient and tolerant in your replies :).  
  I'm trying to get some software, but keep getting the 'from untrusted sources' message.  I get it for everyting - like Chromium - so decided to risk it and just click 'OK'.  But if I do that enough, it goes back to square one, so I don't get the new software.
     Then, I decided it might be update related, so I went to get my updates, but when I do that, I can't install them.  the updater tells me to check my internet connection.  I don't understand this, because the internet seems to be working fine - that's why I can post this.  
  Any suggestions are most welcome.

cheers,

Floyd

---

### Post by ajgreeny on 2014-06-08
Can you show us the output of ```
sudo apt-get update
sudo apt-get upgrade
``` in terminal for a start please.

Use code tags for the copied output, please, which is the # icon in the toolbar of the "Reply to Thread" text input box.

---

### Post by floyd2 on 2014-06-08
Thanks for that.  This is the output of the first command, sudo apt-get update (hope I've got the icons right)

```
#loyd@floyd-H87M-D3H:~$ sudo apt-get update
[sudo] password for floyd: 
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://deb.opera.com](http://deb.opera.com) trusty InRelease                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources                         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty InRelease                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://deb.opera.com](http://deb.opera.com) trusty Release.gpg                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates InRelease                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://deb.opera.com](http://deb.opera.com) trusty Release                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed InRelease                     
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release.gpg [933 B]                  
Hit [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports Release.gpg [933 B]        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Get:4 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed Release.gpg [933 B]         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages             
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:5 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates Release [58.5 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages       
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages         
Get:6 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports Release [58.6 kB]          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages       
Get:7 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed Release [58.5 kB]           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Sources/DiffIndex                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Sources                        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted Sources/DiffIndex           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe Sources/DiffIndex             
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner amd64 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse Sources/DiffIndex           
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main amd64 Packages/DiffIndex          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_AU                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted amd64 Packages/DiffIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe amd64 Packages/DiffIndex      
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse amd64 Packages/DiffIndex    
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_AU               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en                  
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main i386 Packages/DiffIndex           
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted i386 Packages/DiffIndex     
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe i386 Packages/DiffIndex       
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse i386 Packages/DiffIndex     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Translation-en_AU                 
Err [http://deb.opera.com](http://deb.opera.com) trusty/non-free amd64 Packages                        
  404  Not Found
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse Translation-en_AU           
Err [http://deb.opera.com](http://deb.opera.com) trusty/non-free i386 Packages                         
  404  Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted Translation-en_AU           
Ign [http://deb.opera.com](http://deb.opera.com) trusty/non-free Translation-en_AU                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe Translation-en_AU             
Ign [http://deb.opera.com](http://deb.opera.com) trusty/non-free Translation-en                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe Translation-en                
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main Sources [57.7 kB]
Get:9 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]    
Get:10 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe Sources [30.1 kB]  
Get:11 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse Sources [2,234 B]
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main amd64 Packages [142 kB]
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [14 B]
Get:14 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe amd64 Packages [80.5 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_AU             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_AU                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Get:15 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [7,089 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en_AU              
Get:16 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main i386 Packages [139 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_AU                     
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:17 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:18 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe i386 Packages [80.8 kB]
Get:19 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [7,273 B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main Translation-en            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_AU          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_AU    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_AU      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe Translation-en        
Get:20 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main Sources [14 B]       
Get:21 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted Sources [14 B] 
Get:22 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe Sources [5,816 B]
Get:23 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse Sources [768 B]
Get:24 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main amd64 Packages [14 B]
Get:25 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [14 B]
Get:26 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe amd64 Packages [6,318 B]
Get:27 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [619 B]
Get:28 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main i386 Packages [14 B] 
Get:29 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted i386 Packages [14 B]
Get:30 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe i386 Packages [6,313 B]
Get:31 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [619 B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main Translation-en          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe Translation-en      
Get:32 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/multiverse amd64 Packages [648 B]
Get:33 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/restricted amd64 Packages [14 B]
Get:34 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/main amd64 Packages [91.7 kB]
Get:35 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/universe amd64 Packages [59.6 kB]
Get:36 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/multiverse i386 Packages [649 B]
Get:37 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/restricted i386 Packages [14 B]
Get:38 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/main i386 Packages [88.1 kB]
Get:39 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/universe i386 Packages [59.7 kB]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/main Translation-en_AU        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/main Translation-en           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/multiverse Translation-en_AU  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/multiverse Translation-en     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/restricted Translation-en_AU  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/restricted Translation-en     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/universe Translation-en       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main Sources                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse Sources                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main amd64 Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted amd64 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe amd64 Packages                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/restricted i386 Packages               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty/multiverse i386 Packages               
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-updates/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/main Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/multiverse Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/restricted Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-backports/universe Translation-en_AU
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty-proposed/universe Translation-en_AU
Fetched 1,047 kB in 1min 12s (14.4 kB/s)
W: GPG error: [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) trusty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://deb.opera.com/opera/dists/trusty/non-free/binary-amd64/Packages](http://deb.opera.com/opera/dists/trusty/non-free/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://deb.opera.com/opera/dists/trusty/non-free/binary-i386/Packages](http://deb.opera.com/opera/dists/trusty/non-free/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
floyd@floyd-H87M-D3H:~$ 

#
```

---

### Post by floyd2 on 2014-06-08
....and a similar heap of stuff has come through from the second command.  I'm going to try one of my downloads now and after restarting the thing

---

### Post by floyd2 on 2014-06-08
Re-started it, same problem, so here is the output for the second command: sudo apt-get upgrade:

#Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libqt5gui5 linux-generic linux-headers-generic linux-image-generic
  linux-signed-generic linux-signed-image-generic
0 to upgrade, 0 to newly install, 0 to remove and 6 not to upgrade.

#

---

### Post by floyd2 on 2014-06-09
well, I'm still here.  Just did update and upgrade as before.  Can't install the updates that Ubuntu recommends because of the untrusted source problem and can't download things (just tried it with a browser)....any suggestions very gratefully recieved!

---

### Post by bapoumba on 2014-06-09
Your Opera repository is giving a 404 (even for me here). Please remove it from Software Sources, close the Software Sources window and run again :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by floyd2 on 2014-06-09
thank you.  So I should remove Opera and run those two again?  Will do!  Thanks a lot (please let me know if that's NOT the way to remove it)

cheers,

Floyd

---

### Post by bapoumba on 2014-06-09
> **floyd2 said:**
> thank you.  So I should remove Opera and run those two again?  Will do!  Thanks a lot (please let me know if that's NOT the way to remove it)

cheers,

Floyd
Yes, there is a GPG error, we will see if it remains or not, that will have to be taken care of separately.

---

### Post by floyd2 on 2014-06-09
Done!  I removed Opera, restarted the computer and tried again.  I still got a couple of 404s after the update command, and I still have the 'untrusted packages' problem with downloading software though.

any other suggestions?  
thanks again,

Floyd

---

### Post by bapoumba on 2014-06-09
lol, I did not make myself clear. Remove Opera is one thing. What I was meaning is remove the Opera repositories from Software Sources, please see here for details. Go to Software Sources, untick the deb.opera.com repositories, exit the Software Sources and run the commands again. Sorry :)
[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by floyd2 on 2014-06-10
lol, that's very 'new person' of me, isn't it?  Thanks a lot.  I did as you suggested and re ran the commands.  This time I did not get any 404s. I'm going to try and download a thing or two to see if I still get that persistent 'untrustworthy packages' thing.  Just one more question: should I avoid Opera?

cheers,

Floyd

---

### Post by bapoumba on 2014-06-11
:)

Well, for Opera, you should use a supported ppa. I'll have a look.

---

### Post by floyd2 on 2014-07-04
Does it make a difference if I get Opera from the Ubuntu Software Centre rather than from the Opera website?

---

### Post by bapoumba on 2014-07-04
I'd get it from Ubuntu repositories rather than other sources, so Software Center. Opera website may have a later release (I have not checked) so it really depends on what you are looking for, better package manager integration vs more bleeding edge. Maybe install the ubuntu package and see if it fits your needs ?

---

