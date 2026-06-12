---
title: "An unresolvable problem occurred while calculating the upgrade"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by aoniumo on 2014-04-19
Could not calculate the upgrade


An unresolvable problem occurred while calculating the upgrade.


 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu


If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.



The above seems to be the error.  I've googled and one of the suggestion is to disable all third-party stuff in the "Other Software" tab and tried again.
The one I tried is from this page:  [http://askubuntu.com/questions/449374/could-not-determine-the-upgrade](http://askubuntu.com/questions/449374/could-not-determine-the-upgrade)
[http://askubuntu.com/questions/449546/ubuntu-13-10-to-14-04-lts-does-not-upgrade-keeps-showing-error](http://askubuntu.com/questions/449546/ubuntu-13-10-to-14-04-lts-does-not-upgrade-keeps-showing-error)

Of course that topic is on hold.  Am I the only one having this problem since I can't find much information on it.

---

### Post by aoniumo on 2014-04-19
Doing the upgrade by terminal also results in the same:

```
Calculating the changes


Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done
```

---

### Post by aoniumo on 2014-04-20
```

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en

```

---

### Post by aoniumo on 2014-04-20
```

Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


Updating repository information
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg                     
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release.gpg [933 B]          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release.gpg                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources              
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates Release [58.5 kB]            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
                                                                               
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [1,712 B]       
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
                                                                               
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [14 B]    
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
                                                                               
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [648 B]     
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
                                                                               
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [1,790 B] 
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
                                                                               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [3,034 B] 
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
                                                                               
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [14 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [1,630 B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
                                                                               
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [6,386 B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
                                                                               
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_US          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_US    
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
                                                                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_US      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages     
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en          
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en    
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en    
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
                                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en      
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
                                                                               
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
                                                                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en_US   
Fetched 74.7 kB in 6s (0 B/s)                                                  


Checking package manager
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 


Calculating the changes


Calculating the changes


Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 


If none of this applies, then please report this bug using the 
command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal. 




Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
siru@ubuntu:~$

```

---

### Post by aoniumo on 2014-04-20
These seems to be all the broken packages.
Any idea how to fix ALL of them?
```

siru@ubuntu:~$ grep Broken /var/log/dist-upgrade/apt.log
Broken libqt5core5a:i386 Breaks on libqt5core5 [ i386 ] < 5.0.2+dfsg1-7ubuntu11.1 > ( libs ) (< 5.2.0+dfsg~)
Broken cups-filters:i386 Conflicts on foomatic-filters [ i386 ] < 4.0.17-1ubuntu1 > ( universe/text )
Broken libharfbuzz0b:i386 Conflicts on libharfbuzz0a [ i386 ] < 0.9.19-1 > ( libs )
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken unity-control-center:i386 Conflicts on gnome-control-center-unity [ i386 ] < 1.3+13.10.20131004-0ubuntu1 > ( gnome )
Broken libgoa-1.0-0b:i386 Conflicts on libgoa-1.0-0 [ i386 ] < 3.8.3-2 > ( libs )
Broken evolution-data-server:i386 Conflicts on evolution-data-server-goa [ i386 ] < 3.8.5-1ubuntu3 > ( gnome ) (< 3.10.3-0ubuntu2~)
Broken unity-control-center-signon:i386 Conflicts on gnome-control-center-signon [ i386 ] < 0.1.7~+13.10.20130724.1-0ubuntu1 > ( gnome )
Broken ubuntu-drivers-common:i386 Conflicts on jockey-common [ i386 ] < 0.9.7-0ubuntu15 > ( admin )
Broken ubuntu-drivers-common:i386 Conflicts on jockey-gtk [ i386 ] < 0.9.7-0ubuntu15 > ( oldlibs )
Broken libunity-core-6.0-9:i386 Conflicts on libunity-core-6.0-8 [ i386 ] < 7.1.2+13.10.20131014.1-0ubuntu1 > ( libs )
Broken libunity-core-6.0-9:i386 Conflicts on unity-common [ i386 ] < none | 7.0.0daily13.06.19~13.04-0ubuntu1 > ( gnome )
Broken libmlt6:i386 Conflicts on libmlt5 [ i386 ] < 0.8.8-2 > ( libs )
Broken libmuffin0:i386 Depends on libcogl12 [ i386 ] < 1.14.0-2 > ( libs ) (>= 1.13.4)
Broken libcogl-pango12:i386 Depends on libcogl12 [ i386 ] < 1.14.0-2 > ( libs ) (>= 1.13.4)
Broken gir1.2-muffin-3.0:i386 Depends on libmuffin0 [ i386 ] < 2.0.5-20131124003925-saucy > ( universe/libs )
Broken python-mlt5:i386 Depends on libmlt5 [ i386 ] < 0.8.8-2 > ( libs )
Broken openshot:i386 Depends on python-mlt [ i386 ] < none -> 0.9.0-3 > ( universe/python )
Broken xserver-xorg-video-glamoregl:i386 Conflicts on xserver-xorg-glamoregl [ i386 ] < 0.5.1-0ubuntu4.2 > ( x11 )
Broken libperl5.14:i386 Depends on perl-base [ i386 ] < 5.14.2-21build1 -> 5.18.2-2ubuntu1 > ( perl ) (= 5.14.2-21build1)
Broken gnome-control-center-datetime:i386 Depends on indicator-datetime [ i386 ] < 13.10.0+13.10.20131023.2-0ubuntu1 -> 13.10.0+14.04.20140415.3-0ubuntu1 > ( misc ) (= 13.10.0+13.10.20131023.2-0ubuntu1)
Broken cinnamon:i386 Depends on gir1.2-muffin-3.0 [ i386 ] < 2.0.5-20131124003925-saucy > ( universe/introspection )
Broken cinnamon:i386 Depends on libcogl-pango12 [ i386 ] < 1.14.0-2 > ( libs ) (>= 1.7.4)
Broken cinnamon:i386 Depends on libcogl12 [ i386 ] < 1.14.0-2 > ( libs ) (>= 1.9.6)
Broken cinnamon:i386 Depends on libmuffin0 [ i386 ] < 2.0.5-20131124003925-saucy > ( universe/libs )
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken libmuffin0:i386 Depends on libcogl12 [ i386 ] < 1.14.0-2 > ( libs ) (>= 1.13.4)
Broken libcogl-pango12:i386 Depends on libcogl12 [ i386 ] < 1.14.0-2 > ( libs ) (>= 1.13.4)
Broken gir1.2-muffin-3.0:i386 Depends on libmuffin0 [ i386 ] < 2.0.5-20131124003925-saucy > ( universe/libs )
Broken cinnamon:i386 Depends on gir1.2-muffin-3.0 [ i386 ] < 2.0.5-20131124003925-saucy > ( universe/introspection )
Broken cinnamon:i386 Depends on libcogl-pango12 [ i386 ] < 1.14.0-2 > ( libs ) (>= 1.7.4)
Broken cinnamon:i386 Depends on libcogl12 [ i386 ] < 1.14.0-2 > ( libs ) (>= 1.9.6)
Broken cinnamon:i386 Depends on libmuffin0 [ i386 ] < 2.0.5-20131124003925-saucy > ( universe/libs )
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken gir1.2-clutter-1.0:i386 Depends on libclutter-1.0-0 [ i386 ] < 1.14.4-3 -> 1.16.4-0ubuntu2 > ( libs ) (>= 1.16.0)
Broken libcogl15:i386 Breaks on libclutter-1.0-0 [ i386 ] < 1.14.4-3 -> 1.16.4-0ubuntu2 > ( libs ) (< 1.15)
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken libcogl15:i386 Breaks on libclutter-1.0-0 [ i386 ] < 1.14.4-3 -> 1.16.4-0ubuntu2 > ( libs ) (< 1.15)
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken libcogl15:i386 Breaks on libclutter-1.0-0 [ i386 ] < 1.14.4-3 -> 1.16.4-0ubuntu2 > ( libs ) (< 1.15)
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken libcogl15:i386 Breaks on libclutter-1.0-0 [ i386 ] < 1.14.4-3 -> 1.16.4-0ubuntu2 > ( libs ) (< 1.15)
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken libcogl15:i386 Breaks on libclutter-1.0-0 [ i386 ] < 1.14.4-3 -> 1.16.4-0ubuntu2 > ( libs ) (< 1.15)
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken libcogl15:i386 Breaks on libclutter-1.0-0 [ i386 ] < 1.14.4-3 -> 1.16.4-0ubuntu2 > ( libs ) (< 1.15)
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
Broken libcogl15:i386 Breaks on libclutter-1.0-0 [ i386 ] < 1.14.4-3 -> 1.16.4-0ubuntu2 > ( libs ) (< 1.15)
Broken libclutter-1.0-0:i386 Breaks on libcogl12 [ i386 ] < 1.14.0-2 > ( libs )
siru@ubuntu:~$

```

---

### Post by aoniumo on 2014-04-20
This was solved by doing this in terminal:
[FONT=Ubuntu Mono]sudo apt-get --purge remove cinnamon[/FONT]

---

