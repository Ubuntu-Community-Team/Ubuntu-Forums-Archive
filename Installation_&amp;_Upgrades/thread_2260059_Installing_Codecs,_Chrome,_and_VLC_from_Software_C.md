---
title: "Installing Codecs, Chrome, and VLC from Software Center keeps freezing"
date: 2015-01-08
forum: Installation &amp; Upgrades
---

### Post by Andi_GreyScale on 2015-01-08
Finally decide to go from 12.04 to 14.04; I did a clean install from a CD I bought a few months back. It went fine, no issues.

I'm updating everything and got to updating the 3rd party codecs that [OMG Ubuntu says to install right here]("http://www.omgubuntu.co.uk/2014/04/10-things-to-do-after-installing-ubuntu-14-04").

It didn't do much of anything for 20min, and then froze while "Applying" and has been like that for another 10. The Software Center has never been this slow for me back on 12.04

I tried installing Chrome and VLC earlier, also through the Center, did the same thing. I gave up and restarted my system.

Am I doing something wrong?

[SIZE=3]**Edit: SOLVED!**[/SIZE]

---

### Post by coffeecat on 2015-01-09
Your thumbnail simply shows a frozen software centre trying to install ubuntu-restricted-extras. There could be many reasons, so let’s do a few investigations.

Open a terminal and post the output of this command:

```
sudo apt-get update
```

To get the output into your post, highlight it with the mouse, then right-click &#8594; copy and then paste it between [noparse]```
 and 
```[/noparse] tags to make it readable and to preserve formatting. Or you can highlight the pasted output in the advanced message editor and click on the toolbar icon that looks like #.

I’ll assume that software centre didn’t manage to install vlc, so now run this from the terminal:

```
sudo apt-get install vlc
``` 

Press y for yes to OK that if there is no error, and vlc and its dependencies will be installed. If there are then errors after OK-ing it, post all the output. 

Ubuntu-restricted-extras has the complication of having to download files for the mscorefonts and you also have to agree to the EULA, so we could look at that after we see how successful or not the above turns out to be. 

By the way, you can’t install chrome from software centre unless you’ve already activated the google-chrome 3rd party repository for it, or downloaded the deb package from google. Did you mean chrome, or the open-source slightly cut-down version chromium which is in the Ubuntu repositories? If you mean chrome, I’ll post a link but not until we’ve worked out what is going wrong with software centre.

---

### Post by Andi_GreyScale on 2015-01-09
I was eventually able to download VLC, Chrome and the likes. 

But sometimes things freeze. I already tried replying to you, but the entire forum froze so I had to click out of it.

Also those errors the terminal is showing worries me.

```
Hit http://repo.steampowered.com precise InReleaseHit http://repo.steampowered.com precise/steam Sources                         
Hit http://repo.steampowered.com precise/steam amd64 Packages                  
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://repo.steampowered.com precise/steam i386 Packages                   
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Ign http://ppa.launchpad.net trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://ppa.launchpad.net trusty Release                                    
Ign http://repo.steampowered.com precise/steam Translation-en_US               
Hit http://ppa.launchpad.net trusty Release                                    
Ign http://repo.steampowered.com precise/steam Translation-en                  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://ppa.launchpad.net trusty/main Translation-en                        
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://archive.ubuntu.com trusty InRelease                                 
Hit http://archive.ubuntu.com trusty Release.gpg                               
Ign http://archive.canonical.com trusty InRelease                              
Hit http://archive.ubuntu.com trusty Release                                   
Hit http://archive.ubuntu.com trusty/main Sources                              
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://archive.ubuntu.com trusty/restricted Sources                        
Hit http://archive.canonical.com trusty Release                                
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Ign http://us.archive.ubuntu.com trusty InRelease                              
Ign http://us.archive.ubuntu.com trusty-updates InRelease                      
Ign http://us.archive.ubuntu.com trusty-backports InRelease 
Hit http://us.archive.ubuntu.com trusty Release.gpg         
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                  
Hit http://us.archive.ubuntu.com trusty Release             
Get:2 http://us.archive.ubuntu.com trusty-updates Release [62.0 kB]            
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main Sources                          
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                   
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Get:3 http://us.archive.ubuntu.com trusty-updates/universe Sources [96.5 kB]   
Get:4 http://us.archive.ubuntu.com trusty-updates/restricted Sources [2,061 B] 
Get:5 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,543 B] 
Get:6 http://us.archive.ubuntu.com trusty-updates/main Sources [152 kB]        
Get:7 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [392 kB] 
Get:8 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [8,875 B]
Get:9 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [236 kB]
Get:10 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [9,370 B]
Get:11 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [384 kB] 
Get:12 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [8,846 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [237 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [9,553 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Ign http://security.ubuntu.com trusty-security InRelease                       
Get:15 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Get:16 http://security.ubuntu.com trusty-security Release [62.0 kB]
Get:17 http://security.ubuntu.com trusty-security/universe Sources [17.4 kB]
Get:18 http://security.ubuntu.com trusty-security/restricted Sources [2,061 B]
Get:19 http://security.ubuntu.com trusty-security/multiverse Sources [719 B]
Get:20 http://security.ubuntu.com trusty-security/main Sources [59.7 kB]
Get:21 http://security.ubuntu.com trusty-security/main amd64 Packages [187 kB] 
Get:22 http://security.ubuntu.com trusty-security/restricted amd64 Packages [8,875 B]
Get:23 http://security.ubuntu.com trusty-security/universe amd64 Packages [82.2 kB]
Get:24 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,157 B]
Get:25 http://security.ubuntu.com trusty-security/main i386 Packages [179 kB]  
Get:26 http://security.ubuntu.com trusty-security/restricted i386 Packages [8,846 B]
Get:27 http://security.ubuntu.com trusty-security/universe i386 Packages [82.2 kB]
Get:28 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,409 B]
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en       
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Fetched 2,295 kB in 12min 2s (3,174 B/s)                                       
W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.



```

---

### Post by kansasnoob on 2015-01-09
There is no Trusty version of 'openshot' in that PPA:

[https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa](https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa)

People keep trying it anyway:

[https://bugs.launchpad.net/openshot/+bug/1321535](https://bugs.launchpad.net/openshot/+bug/1321535)

[https://bugs.launchpad.net/openshot/+bug/1323885](https://bugs.launchpad.net/openshot/+bug/1323885)

In fact I can't find a version higher than that available in the standard Ubuntu repos so you might as well just purge that PPA using 'ppa-purge':

```
sudo apt-get install ppa-purge
```

```
sudo ppa-purge ppa:openshot.developers/ppa
```

```
sudo apt-get update
```

Then see if the Software Center is playing nice again.

---

### Post by Andi_GreyScale on 2015-01-09
After I do the second code, I get this.

```
Updating packages listsW: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found


W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
Warning:  apt-get update failed for some reason
PPA to be removed: openshot.developers ppa
Warning:  Could not find package list for PPA: openshot.developers ppa
```

> **kansasnoob said:**
> There is no Trusty version of 'openshot' in that PPA:

[https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa](https://launchpad.net/~openshot.developers/+archive/ubuntu/ppa)

People keep trying it anyway:

[https://bugs.launchpad.net/openshot/+bug/1321535](https://bugs.launchpad.net/openshot/+bug/1321535)

[https://bugs.launchpad.net/openshot/+bug/1323885](https://bugs.launchpad.net/openshot/+bug/1323885)

In fact I can't find a version higher than that available in the standard Ubuntu repos so you might as well just purge that PPA using 'ppa-purge':

```
sudo apt-get install ppa-purge
```

```
sudo ppa-purge ppa:openshot.developers/ppa
```

```
sudo apt-get update
```

Then see if the Software Center is playing nice again.

---

### Post by kansasnoob on 2015-01-10
I'm not sure why 'ppa-purge' doesn't work with that ppa but I tried myself and you're right - it doesn't work.

So we'll have to try something different. Open System Settings > Software & Updates, then click on the Other software tab:

[ATTACH=CONFIG]259144[/ATTACH]

Then highlight the 'openbox' ppa's as shown there and click on Remove. You may have to repeat that more than once because I notice you seem to have both i386 and amd64 versions installed.

---

### Post by Andi_GreyScale on 2015-01-10
Thanks, had to remove it only once. =) Also updated again, didn't see any errors this time. 

Everything seems to work fine aside from an issue with my monitor showing an image with a different level of saturation than while I was working on it. I think it would be best for me to start a new thread for that though.

> **kansasnoob said:**
> I'm not sure why 'ppa-purge' doesn't work with that ppa but I tried myself and you're right - it doesn't work.

So we'll have to try something different. Open System Settings > Software & Updates, then click on the Other software tab:

[ATTACH=CONFIG]259144[/ATTACH]

Then highlight the 'openbox' ppa's as shown there and click on Remove. You may have to repeat that more than once because I notice you seem to have both i386 and amd64 versions installed.

---

