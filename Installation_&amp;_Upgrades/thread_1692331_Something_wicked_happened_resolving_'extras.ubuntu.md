---
title: "Something wicked happened resolving 'extras.ubuntu.com"
date: 2011-02-21
forum: Installation &amp; Upgrades
---

### Post by devilcode on 2011-02-21
Anyone else getting this issue ?

[COLOR=Black]**PROBLEM:**[/COLOR]
```

W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

```**OS VERSION**
```

Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

```

---

### Post by sffvba[e0rt on 2011-02-21
> **devilcode said:**
> Anyone else getting this issue ?

[COLOR=Black]**PROBLEM:**[/COLOR]
```

W:Failed to fetch http://extras.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'extras.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

```**OS VERSION**
```

Distributor ID: Ubuntu
Description:    Ubuntu 10.10
Release:        10.10
Codename:       maverick

```

Hi,

I have gotten messages (or very similar) to these often over the last few years... what I normally do is to change the server I use and then try and update again... this usually fixes any issues the server I normally use might have (and if that doesn't work it means there might be a bigger issue and I would then seek more advice on the forums)...

Try it and see...



404

---

### Post by Frogs Hair on 2011-02-21
I get a failure to connect to sources at times and I find that reloading the synaptic package manager or running ```
sudo apt-get update 
``` does the trick.

---

### Post by devilcode on 2011-02-21
```

sudo apt-get update

```

produces the same really

```

Hit http://gb.archive.ubuntu.com maverick Release.gpg
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                 
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB                              
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                           
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB                         
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                            
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB                                               
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB                                                 
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg                                                                
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB                       
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                    
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB                 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                    
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB                 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                      
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB                   
Hit http://gb.archive.ubuntu.com maverick Release                                                      
Hit http://gb.archive.ubuntu.com maverick-updates Release                                              
Hit http://gb.archive.ubuntu.com maverick/main Sources                                                                       
Hit http://gb.archive.ubuntu.com maverick/restricted Sources                                                                 
Hit http://gb.archive.ubuntu.com maverick/universe Sources                                             
Hit http://gb.archive.ubuntu.com maverick/multiverse Sources                                           
Hit http://gb.archive.ubuntu.com maverick/main i386 Packages                                           
Hit http://gb.archive.ubuntu.com maverick/restricted i386 Packages                                     
Hit http://gb.archive.ubuntu.com maverick/universe i386 Packages                                       
Hit http://gb.archive.ubuntu.com maverick/multiverse i386 Packages                                     
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources                                         
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources                                   
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources                                     
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse Sources                                   
Hit http://gb.archive.ubuntu.com maverick-updates/main i386 Packages                                   
Hit http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages                             
Hit http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages                               
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages                             
Get:1 http://extras.ubuntu.com maverick Release.gpg [72B]                                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB 
Hit http://extras.ubuntu.com maverick Release                        
Hit http://extras.ubuntu.com maverick/main Sources                                         
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Err http://security.ubuntu.com maverick-security Release.gpg                                                                                                                                                                                      
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                                                                                                                                      
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB                                                                                                                                                                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                                                                                                                                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB                                                                                                                                                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                                                                                                                                                
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB                                                                                                                                                             
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                                                                                                                                                  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB                                                                                                                                                               
Hit http://security.ubuntu.com maverick-security Release                                                                                                                                                                                          
Ign http://security.ubuntu.com maverick-security/main Sources/DiffIndex                                                                                                                                                                           
Ign http://security.ubuntu.com maverick-security/restricted Sources/DiffIndex                                                                                                                                                                     
Ign http://security.ubuntu.com maverick-security/universe Sources/DiffIndex                                                                                                                                                                       
Ign http://security.ubuntu.com maverick-security/multiverse Sources/DiffIndex                                                                                                                                                                     
Ign http://security.ubuntu.com maverick-security/main i386 Packages/DiffIndex                                                                                                                                                                     
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIndex                                                                                                                                                               
Ign http://security.ubuntu.com maverick-security/universe i386 Packages/DiffIndex                                                                                                                                                                 
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages/DiffIndex                                                                                                                                                               
Hit http://security.ubuntu.com maverick-security/main Sources                                                                                                                                                                                     
Hit http://security.ubuntu.com maverick-security/restricted Sources                                                                                                                                                                               
Hit http://security.ubuntu.com maverick-security/universe Sources                                                                                                                                                                                 
Hit http://security.ubuntu.com maverick-security/multiverse Sources                                                                                                                                                                               
Hit http://security.ubuntu.com maverick-security/main i386 Packages                                                                                                                                                                               
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages                                                                                                                                                                         
Hit http://security.ubuntu.com maverick-security/universe i386 Packages                                                                                                                                                                           
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages                                                                                                                                                                         
Err http://dl.google.com stable Release.gpg                                                                                                                                                                                                       
  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_GB
Get:2 http://dl.google.com stable Release [1,347B]
Ign http://dl.google.com stable/main i386 Packages/DiffIndex
Get:3 http://dl.google.com stable/main i386 Packages [1,093B]
Fetched 2,512B in 15s (163B/s)
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/maverick-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg  Something wicked happened resolving 'dl.google.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by sikander3786 on 2011-02-21
Most of the time, this error seems to appear when your router was configured as a DNS server and is unable to resolve the addresses. And strangely, the errors seems to appear near the end of the apt-get operation and not the beginning.

A fix is to find your ISPs original DNS server adresses and put it in your network manager. Or use Google DNS or OpenDNS. See Linux instructions here.

[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

---

