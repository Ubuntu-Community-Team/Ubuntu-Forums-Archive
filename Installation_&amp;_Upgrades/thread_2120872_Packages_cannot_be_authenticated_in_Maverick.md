---
title: "Packages cannot be authenticated in Maverick"
date: 2013-02-27
forum: Installation &amp; Upgrades
---

### Post by chellrose on 2013-02-27
I'm using 10.10 (Maverick) on my work laptop.  (I do realize that it's old and unsupported, but I need something for work that *just works*.  I'm playing with newer versions on my home computer, and when I manage to get a decently working configuration, I'll upgrade the work machine.)

Anywho...  It's been working beautifully for some time, but now all of a sudden, when I try to install packages, I get the warning:
```

WARNING: The following packages cannot be authenticated!
<lists packages>
Install these packages without verification [y/N]?

```(Recently I've tried wicd and Inkscape + a pile of supporting python/perl "suggested packages".  None of these were authenticatable.)

I found it suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=369366") to run sudo apt-get update and I tried that, but it doesn't seem to work either.  Here's the result:

```

Ign http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                               
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US                                            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US                                      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                         
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US                                      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US                                        
Ign http://security.ubuntu.com maverick-security Release                                                                   
Ign http://us.archive.ubuntu.com maverick Release.gpg                                                                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                   
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                                             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                                             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                                               
Ign http://us.archive.ubuntu.com maverick-updates Release.gpg                                                              
Ign http://security.ubuntu.com maverick-security/main Sources/DiffIndex                                                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                                           
Hit http://archive.canonical.com maverick Release.gpg                                                                      
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en                                                   
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US                                                
Ign http://security.ubuntu.com maverick-security/restricted Sources/DiffIndex                                              
Ign http://security.ubuntu.com maverick-security/universe Sources/DiffIndex                                                
Ign http://security.ubuntu.com maverick-security/multiverse Sources/DiffIndex                                              
Ign http://security.ubuntu.com maverick-security/main i386 Packages/DiffIndex                                              
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex                                        
Ign http://security.ubuntu.com maverick-security/universe i386 Packages/DiffIndex                                          
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages/DiffIndex                                        
Hit http://ppa.launchpad.net maverick Release.gpg                                                                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US                                     
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US                                     
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US                                       
Ign http://us.archive.ubuntu.com maverick Release                                                                          
Ign http://ppa.launchpad.net/khnz/ppa/ubuntu/ maverick/main Translation-en                                                 
Ign http://ppa.launchpad.net/khnz/ppa/ubuntu/ maverick/main Translation-en_US                                              
Ign http://extras.ubuntu.com maverick Release.gpg                                                                          
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                          
Ign http://security.ubuntu.com maverick-security/main Sources                                                              
Ign http://security.ubuntu.com maverick-security/restricted Sources                                                        
Ign http://security.ubuntu.com maverick-security/universe Sources                                                          
Ign http://security.ubuntu.com maverick-security/multiverse Sources                                                        
Ign http://security.ubuntu.com maverick-security/main i386 Packages                                                        
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages                                                  
Ign http://us.archive.ubuntu.com maverick-updates Release                                                                  
Hit http://archive.canonical.com maverick Release                                                                          
Ign http://us.archive.ubuntu.com maverick/main Sources/DiffIndex                                                           
Ign http://security.ubuntu.com maverick-security/universe i386 Packages                                                    
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages                                                  
Ign http://security.ubuntu.com maverick-security/main Sources                                                              
Ign http://security.ubuntu.com maverick-security/restricted Sources                                                        
Ign http://security.ubuntu.com maverick-security/universe Sources                                                          
Ign http://security.ubuntu.com maverick-security/multiverse Sources                                                        
Hit http://ppa.launchpad.net maverick Release.gpg                                                                          
Ign http://ppa.launchpad.net/lyx-devel/release/ubuntu/ maverick/main Translation-en                                        
Ign http://ppa.launchpad.net/lyx-devel/release/ubuntu/ maverick/main Translation-en_US                                     
Hit http://ppa.launchpad.net maverick Release                                                                              
Ign http://security.ubuntu.com maverick-security/main i386 Packages                                                        
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                       
Ign http://extras.ubuntu.com maverick Release                                                                              
Ign http://us.archive.ubuntu.com maverick/restricted Sources/DiffIndex                                                     
Ign http://us.archive.ubuntu.com maverick/universe Sources/DiffIndex                                                       
Ign http://us.archive.ubuntu.com maverick/multiverse Sources/DiffIndex                                                     
Ign http://us.archive.ubuntu.com maverick/main i386 Packages/DiffIndex                                                     
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages/DiffIndex                                               
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages/DiffIndex                                                 
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages/DiffIndex                                               
Get:1 http://www.duinsoft.nl debs Release.gpg [490B]                                                                       
Ign http://www.duinsoft.nl/pkg/ debs/all Translation-en                                                                    
Ign http://www.duinsoft.nl/pkg/ debs/all Translation-en_US                                                                 
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages                                                  
Ign http://security.ubuntu.com maverick-security/universe i386 Packages                                                    
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages                                                  
Err http://security.ubuntu.com maverick-security/main Sources                                                              
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com maverick-security/restricted Sources                                                        
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com maverick-security/universe Sources                                                          
  404  Not Found [IP: 91.189.91.13 80]
Ign http://us.archive.ubuntu.com maverick-updates/main Sources/DiffIndex                                                   
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources/DiffIndex                                             
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources/DiffIndex                                               
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources/DiffIndex                                             
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages/DiffIndex                                             
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages/DiffIndex                                       
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages/DiffIndex                                         
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages/DiffIndex                                       
Ign http://us.archive.ubuntu.com maverick/main Sources                                                                     
Err http://security.ubuntu.com maverick-security/multiverse Sources                                                        
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com maverick-security/main i386 Packages                                                        
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com maverick-security/restricted i386 Packages                                                  
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com maverick-security/universe i386 Packages                                                    
  404  Not Found [IP: 91.189.91.13 80]
Err http://security.ubuntu.com maverick-security/multiverse i386 Packages                                                  
  404  Not Found [IP: 91.189.91.13 80]
Hit http://ppa.launchpad.net maverick Release                                                                              
Ign http://us.archive.ubuntu.com maverick/restricted Sources                                                               
Ign http://extras.ubuntu.com maverick/main Sources                                                                         
Ign http://us.archive.ubuntu.com maverick/universe Sources                                                                 
Ign http://us.archive.ubuntu.com maverick/multiverse Sources                                                               
Ign http://us.archive.ubuntu.com maverick/main i386 Packages                                                               
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages                                                         
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages                                                           
Get:2 http://www.duinsoft.nl debs Release [7,951B]                                                                         
Hit http://archive.canonical.com maverick/partner Sources                                                                  
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages                                                         
Ign http://us.archive.ubuntu.com maverick-updates/main Sources                                                             
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources                                                       
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources                                                         
Hit http://ppa.launchpad.net maverick/main Sources                                                                         
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                   
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources                                                       
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages                                                       
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages                                                 
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages                                                   
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages                                                 
Ign http://us.archive.ubuntu.com maverick/main Sources                                                                     
Ign http://us.archive.ubuntu.com maverick/restricted Sources                                                               
Ign http://us.archive.ubuntu.com maverick/universe Sources                                                                 
Ign http://us.archive.ubuntu.com maverick/multiverse Sources                                                               
Ign http://us.archive.ubuntu.com maverick/main i386 Packages                                                               
Ign http://us.archive.ubuntu.com maverick/restricted i386 Packages                                                         
Ign http://us.archive.ubuntu.com maverick/universe i386 Packages                                                           
Ign http://us.archive.ubuntu.com maverick/multiverse i386 Packages                                                         
Ign http://us.archive.ubuntu.com maverick-updates/main Sources                                                             
Ign http://us.archive.ubuntu.com maverick-updates/restricted Sources                                                       
Ign http://extras.ubuntu.com maverick/main i386 Packages                                                                   
Hit http://archive.canonical.com maverick/partner i386 Packages                                                            
Hit http://ppa.launchpad.net maverick/main Sources                                                               
Ign http://us.archive.ubuntu.com maverick-updates/universe Sources                                               
Ign http://us.archive.ubuntu.com maverick-updates/multiverse Sources                                             
Ign http://us.archive.ubuntu.com maverick-updates/main i386 Packages                                             
Ign http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages                                       
Ign http://us.archive.ubuntu.com maverick-updates/universe i386 Packages                                         
Ign http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages                                       
Get:3 http://www.duinsoft.nl debs/all i386 Packages [1,446B]                                                     
Hit http://ppa.launchpad.net maverick/main i386 Packages                                                                   
Err http://us.archive.ubuntu.com maverick/main Sources                                     
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick/restricted Sources                               
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick/universe Sources                                 
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick/multiverse Sources                               
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick/main i386 Packages                               
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick/restricted i386 Packages                         
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick/universe i386 Packages                           
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick/multiverse i386 Packages                         
  404  Not Found [IP: 91.189.91.15 80]
Ign http://extras.ubuntu.com maverick/main Sources                                         
Err http://us.archive.ubuntu.com maverick-updates/main Sources       
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick-updates/restricted Sources 
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick-updates/universe Sources   
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick-updates/multiverse Sources 
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick-updates/main i386 Packages 
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Err http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
  404  Not Found [IP: 91.189.91.15 80]
Ign http://extras.ubuntu.com maverick/main i386 Packages             
Err http://extras.ubuntu.com maverick/main Sources
  404  Not Found
Err http://extras.ubuntu.com maverick/main i386 Packages
  404  Not Found
Hit http://ppa.quickbuild.pearsoncomputing.net maverick Release.gpg
Ign http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu/ maverick/main Translation-en
Ign http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.quickbuild.pearsoncomputing.net maverick Release.gpg
Ign http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu/ maverick/main Translation-en
Ign http://ppa.quickbuild.pearsoncomputing.net/trinity/trinity-builddeps/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.quickbuild.pearsoncomputing.net maverick Release
Hit http://ppa.quickbuild.pearsoncomputing.net maverick Release
Hit http://ppa.quickbuild.pearsoncomputing.net maverick/main Sources                                                       
Hit http://ppa.quickbuild.pearsoncomputing.net maverick/main i386 Packages                                                 
Hit http://ppa.quickbuild.pearsoncomputing.net maverick/main Sources                                                       
Hit http://ppa.quickbuild.pearsoncomputing.net maverick/main i386 Packages
Fetched 9,887B in 16s (596B/s)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/source/Sources.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/restricted/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/universe/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/multiverse/binary-i386/Packages.gz  404  Not Found [IP: 91.189.91.15 80]

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

```Now, I realize that Maverick is no longer officially supported... but I would think that the repositories still exist?  Have they been moved?

And in any case, how do I get packages to be correctly authenticated again?

Many thanks.

---

### Post by dabl on 2013-02-27
Here is all there is to know about the end-of-life repos:

[http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support](http://askubuntu.com/questions/101479/are-existing-updates-available-after-end-of-support)

---

### Post by chellrose on 2013-02-27
Thanks.  I changed the repository location in my sources.list.  It still won't do the apt-get update.  Now I'm seeing errors such as the following:

```

W: Failed to fetch http://us.old-releases.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'us.old-releases.ubuntu.com:http' (-5 - No address associated with hostname)

```

Now sudo apt-get install <whatever package> doesn't find the package either.

---

### Post by dabl on 2013-02-27
I think you're probably done installing packages on 10.10 

 :-({|=

---

### Post by arpanaut on 2013-02-27
I think that you need to lose the "us." from the url as these updated repos. are only from the main server. Not positive, but that's my take.

---

### Post by chellrose on 2013-03-06
Thanks.  I got rid of the "us." and now I'm getting "Could not resolve" errors on all of them.

Spring Break is coming up; perhaps I'll break down and install a new version...

---

