---
title: "apt-get is broken for me- can I remove etc/apt files"
date: 2014-06-13
forum: Installation &amp; Upgrades
---

### Post by linbu2 on 2014-06-13
If I remove some of the files under /etc/apt and /etc/apt/apt.conf.d - will it recreate them on reboot, or can I do so by running a command?

---

### Post by Elfy on 2014-06-13
No - it won't rebuild them.

You'll be better served by opening a terminal - Ctrl+T then running 

```
sudo apt-get update
```

to see if there are errors with that, then pasting the WHOLE output from the terminal here for people to see.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by linbu2 on 2014-06-14
Thank you , Elfy

```
 
# sudo apt-get update
Ign http://download.webmin.com sarge InRelease
Ign http://us.archive.ubuntu.com trusty InRelease                                                                                       
Hit http://download.webmin.com sarge Release.gpg                                                                                        
Ign http://security.ubuntu.com trusty-security InRelease                                                                                
Ign http://us.archive.ubuntu.com trusty-updates InRelease                                                                               
Hit http://download.webmin.com sarge Release                                                                                            
Ign http://ppa.launchpad.net trusty InRelease                                                                                           
Ign http://us.archive.ubuntu.com trusty-backports InRelease                                                                             
Ign http://archive.canonical.com precise InRelease                                                                                      
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]                                                                    
Hit http://download.webmin.com sarge/contrib amd64 Packages                                                                             
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge InRelease                                                                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                                                                                     
Hit http://download.webmin.com sarge/contrib i386 Packages                                                                              
Ign http://ppa.launchpad.net trusty InRelease                                                                                           
Hit http://archive.canonical.com precise Release.gpg                                                                                    
Get:2 http://security.ubuntu.com trusty-security Release [58.5 kB]                                                                      
Get:3 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]                                                                   
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release.gpg                                                                  
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg                                                                           
Hit http://archive.canonical.com precise Release                                                                                        
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                         
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge Release                                                                      
Hit http://us.archive.ubuntu.com trusty Release                                                                                         
Get:4 http://us.archive.ubuntu.com trusty-updates Release [58.5 kB]                                                                     
Hit http://archive.canonical.com precise/partner Sources                                                                                
Hit http://ppa.launchpad.net trusty Release.gpg                                                                                         
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib amd64 Packages                                                       
Hit http://archive.canonical.com precise/partner amd64 Packages                                                                         
Hit http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib i386 Packages                                                        
Hit http://ppa.launchpad.net trusty Release                                                                                             
Get:5 http://security.ubuntu.com trusty-security/main Sources [17.5 kB]                                                                 
Hit http://archive.canonical.com precise/partner i386 Packages                                                                          
Hit http://us.archive.ubuntu.com trusty-backports Release                                                                               
Hit http://ppa.launchpad.net trusty Release                                                                                             
Ign http://extras.ubuntu.com trusty InRelease                                                                                           
Get:6 http://security.ubuntu.com trusty-security/restricted Sources [14 B]                                                              
Hit http://us.archive.ubuntu.com trusty/main Sources                                                                                    
Hit http://extras.ubuntu.com trusty Release.gpg                                                                                         
Get:7 http://security.ubuntu.com trusty-security/universe Sources [4,212 B]                                                              
Hit http://ppa.launchpad.net trusty/main Sources                                                                                         
Hit http://us.archive.ubuntu.com trusty/restricted Sources                                                                               
Ign http://download.webmin.com sarge/contrib Translation-en_US                                                                           
Hit http://us.archive.ubuntu.com trusty/universe Sources                                                                                 
Ign http://download.webmin.com sarge/contrib Translation-en                                                                              
Get:8 http://security.ubuntu.com trusty-security/multiverse Sources [688 B]                                                              
Hit http://extras.ubuntu.com trusty Release                                                                                              
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                  
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                                                                               
Get:9 http://security.ubuntu.com trusty-security/main amd64 Packages [55.7 kB]                                                           
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                                                                              
Hit http://extras.ubuntu.com trusty/main Sources                                                                                         
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                   
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages                                                                        
Hit http://extras.ubuntu.com trusty/main amd64 Packages                                                                                 
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                                                                         
Get:10 http://security.ubuntu.com trusty-security/restricted amd64 Packages [14 B]                                                      
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages                                                                       
Hit http://extras.ubuntu.com trusty/main i386 Packages                                                                                  
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                                                                              
Get:11 http://security.ubuntu.com trusty-security/universe amd64 Packages [17.9 kB]                                                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages                                                                        
Get:12 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [1,157 B]                                                   
Hit http://ppa.launchpad.net trusty/main amd64 Packages                                                                                 
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Translation-en_US                                                    
Get:13 http://security.ubuntu.com trusty-security/main i386 Packages [53.1 kB]                                                          
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                                                                          
Hit http://ppa.launchpad.net trusty/main i386 Packages                                                                                  
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages                                                                        
Ign http://webmin.mirror.somersettechsolutions.co.uk sarge/contrib Translation-en                                                       
Ign http://archive.canonical.com precise/partner Translation-en_US                                                                      
Get:14 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]                                 
Hit http://us.archive.ubuntu.com trusty/main Translation-en                                                                             
Ign http://archive.canonical.com precise/partner Translation-en                                                   
Get:15 http://security.ubuntu.com trusty-security/universe i386 Packages [17.9 kB]                                
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en                                                   
Get:16 http://security.ubuntu.com trusty-security/multiverse i386 Packages [1,392 B]        
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en                                                   
Hit http://security.ubuntu.com trusty-security/main Translation-en                          
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                             
Get:17 http://us.archive.ubuntu.com trusty-updates/main Sources [60.0 kB]                   
Ign http://extras.ubuntu.com trusty/main Translation-en_US                                           
Ign http://extras.ubuntu.com trusty/main Translation-en                                                            
Get:18 http://us.archive.ubuntu.com trusty-updates/restricted Sources [14 B]                
Hit http://security.ubuntu.com trusty-security/multiverse Translation-en                     
Get:19 http://us.archive.ubuntu.com trusty-updates/universe Sources [30.1 kB]
Get:20 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [2,228 B]              
Get:21 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [149 kB]              
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Hit http://security.ubuntu.com trusty-security/universe Translation-en          
Get:22 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [14 B]
Get:23 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [81.0 kB]                 
Get:24 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [7,090 B]        
Get:25 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [145 kB]                
Get:26 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [14 B]
Get:27 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [81.4 kB]           
Ign http://ppa.launchpad.net trusty/main Translation-en_US                  
Get:28 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [7,282 B]
Ign http://ppa.launchpad.net trusty/main Translation-en                                       
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en   
Ign http://ppa.launchpad.net trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en
Ign http://ppa.launchpad.net trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en                                                                 
Ign http://security.ubuntu.com trusty-security/multiverse Translation-en_US                                                             
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages                                                             
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US                                                             
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages                                                                   
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages                                                               
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US                                                               
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages                                                             
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages                                                              
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages                                                                    
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
Ign http://us.archive.ubuntu.com trusty-updates/main Translation-en_US                                                                  
Ign http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en_US                                                            
Ign http://us.archive.ubuntu.com trusty-updates/restricted Translation-en_US                                                            
Ign http://us.archive.ubuntu.com trusty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com trusty-backports/universe Translation-en_US
Fetched 852 kB in 12s (67.1 kB/s)
Reading package lists... Done
#

 
```

Thanks again for your help

---

### Post by Elfy on 2014-06-14
no errors then - or did you not post that part ;)

---

### Post by oldos2er on 2014-06-14
I'm guessing APT is broken for you because you have Debian sarge repos in your Ubuntu trusty sources; not something that's usually a good idea.

---

### Post by linbu2 on 2014-06-15
Right, Elfy- no errors- I posted *all*, as requested. 

 OS/2 - yes, I did that too (just a bit of dev on it, unfortunately!  I wish it were still around as an OS, OS.

How do I get rid of the "sarge" repos?  I am going to try, but if I mess  it up, I want to know the right (maybe the complete) way (I will backup  first, of course).

---

### Post by Elfy on 2014-06-15
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.1506
```

Thats it backed up.

```
sudo nano sudo cp /etc/apt/sources.list
```

Put a # at the beginning of lines you don't want.

Ctrl+X, Y, Enter

If you've repos from PPAs to deal with, they live in sudo nano /etc/apt/sources.list.d/

---

### Post by linbu2 on 2014-06-15
I edited "/etc/sources.list" and found that the "sarge" references are from webmin, so I left them alone.  This is also reflected in the "apt-get update" output.  Things were working fine after webmin was installed soon after Ubuntu itself.  I've installed and removed lots of stuff since Webmin was here.

---

### Post by linbu2 on 2014-06-15
I am trying to find out how to completely remove a ppa.  While doing this, I stumbled across a tool that promised to do that.  All I had to do was add their ppa with "add-apt-repository", then install their software (which I expected to fail).  But the intermediate step was, of course "apt-get update" which now fails after what used to be the end, and now is evidently trying to get package lists for the new ppa.  The network connection is bad when it gets there: some servers can't be reached some time out.  So now I need to find out how to **manually** remove that ppa, and maybe one other that I think could be a stinker.

---

### Post by Elfy on 2014-06-15
Bits of the ubuntu infrastructure are down at the moment. Launchpad is one of them - where PPAs live 

To manually remove a PPA - simply remove the offending list from  /etc/apt/sources.list.d/ then update.

---

### Post by linbu2 on 2014-06-15
is there a way to tell apt-get to just deal with one thing at a time.  When I try to remove "kompozer", I get errors from brscan2.  When I try to remove that, I get errors from "kompozer".  If I could just tell apt-get to ignore everything else while it removes (or installs) something- I think that would do it.  It appears that both kmopozer and brscan2 were both removed, but unsuccessfully- incompletely.

---

### Post by linbu2 on 2014-06-15
> **Elfy said:**
> Bits of the ubuntu infrastructure are down at the moment. Launchpad is one of them - where PPAs live 

To manually remove a PPA - simply remove the offending list from  /etc/apt/sources.list.d/ then update.

You're "the man", Elfy!  I will mash into that soon, it's 3:20AM here so I might not report back until tomorrow.  But removing those PPAs is a big start, maybe it'll help too! ;)

---

### Post by Elfy on 2014-06-15
Please bear in mind though that just manually removing PPAs can cause issues with packages afterwards.

It is much much better to use ppa-purge to do that - that will work through and put changed packages back to where they were prior to a PPA - see [http://ubuntuforums.org/showthread.php?t=2229553](http://ubuntuforums.org/showthread.php?t=2229553)

---

### Post by bapoumba on 2014-06-15
There is also a mix of Precise and Trusty repositories in your sources.list. Which Ubuntu release are you using ?

---

### Post by linbu2 on 2014-06-15
I am using Ubuntu (Kubuntu, actually) 14.04.  I use kdm too.

---

### Post by linbu2 on 2014-06-15
Elfy- thanks for the info on PPAs and the thread which holds some clues based on the similarities to my situation.  I'm bookmarking that and will set about working through that process soon.  I have to do a little project first.  I could just trash everything and reinstall, but the whole point of installing it was to learn something and then to master Ubuntu.  So I'd rather beat myself and my PC up a little and have something to show for it in the way of new knowledge and experience.  Thanks for your help and guidance.

Bill

---

