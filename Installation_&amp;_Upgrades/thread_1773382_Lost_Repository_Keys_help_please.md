---
title: "Lost Repository Keys help please"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by bojo on 2011-06-02
Hi Guys,

I installed Natty 11.04 - 64 bit and by mistake I lost most of the repository keys. When I go to Synaptic and click on Restore Defaults nothing happens.

Please help, I just need to restore the default Ubuntu keys. I believe I have the repository links.

Thank you in advance.

---

### Post by sahabcse on 2011-06-02
Please refer below url for more info

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by bojo on 2011-06-02
I did check it and I have the repositories but not the keys. It describes how to install a key but I do not have them and I don't know where to find them.

---

### Post by webofunni on 2011-06-02
which key is causing the problem. What is the output of 

```

sudo apt-get update

```

?

---

### Post by bojo on 2011-06-02
Here is the output.
```


root@cheetah:~# apt-get update
Ign http://extras.ubuntu.com natty InRelease
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                    
Get:2 http://extras.ubuntu.com natty Release [9,753 B]                                                     
Ign http://extras.ubuntu.com natty Release                                                                   
Ign http://extras.ubuntu.com natty/main Sources/DiffIndex                                            
Ign http://extras.ubuntu.com natty/main amd64 Packages/DiffIndex            
Ign http://extras.ubuntu.com natty/main TranslationIndex                    
Hit http://extras.ubuntu.com natty/main Sources                             
Hit http://extras.ubuntu.com natty/main amd64 Packages                                            
Ign http://extras.ubuntu.com natty/main Translation-en_CA                                         
Ign http://extras.ubuntu.com natty/main Translation-en                                            
Ign http://archive.canonical.com natty InRelease                            
Hit http://archive.canonical.com natty Release.gpg                          
Hit http://archive.canonical.com natty Release
Hit http://archive.canonical.com natty/partner Sources       
Hit http://archive.canonical.com natty/partner amd64 Packages
Ign http://archive.canonical.com natty/partner TranslationIndex                                                                          
Ign http://archive.canonical.com natty/partner Translation-en_CA                                                                         
Ign http://archive.canonical.com natty/partner Translation-en                                                                            
Get:3 http://archive.ubuntu.com natty InRelease                                                                                          
Ign http://archive.ubuntu.com natty InRelease                                                                                            
Get:4 http://archive.ubuntu.com natty-updates InRelease [1,684 B]                                                                        
Ign http://archive.ubuntu.com natty-updates InRelease                                                                                    
Get:5 http://archive.ubuntu.com natty-security InRelease                                                                                 
Ign http://archive.ubuntu.com natty-security InRelease                                                                                   
Ign http://archive.ubuntu.com natty/restricted Sources/DiffIndex                                                                         
Ign http://archive.ubuntu.com natty/main Sources/DiffIndex                                                                               
Ign http://archive.ubuntu.com natty/multiverse Sources/DiffIndex                                                                         
Ign http://archive.ubuntu.com natty/universe Sources/DiffIndex                                                                           
Ign http://archive.ubuntu.com natty/main amd64 Packages/DiffIndex                                                                        
Ign http://archive.ubuntu.com natty/restricted amd64 Packages/DiffIndex                                                                  
Ign http://archive.ubuntu.com natty/universe amd64 Packages/DiffIndex                                                                    
Ign http://archive.ubuntu.com natty/multiverse amd64 Packages/DiffIndex                                                                  
Ign http://archive.ubuntu.com natty/main TranslationIndex                                                                                
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                                                                          
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                                                                          
Ign http://archive.ubuntu.com natty/universe TranslationIndex                                                                            
Ign http://archive.ubuntu.com natty-updates/restricted Sources/DiffIndex                                                                 
Ign http://archive.ubuntu.com natty-updates/main Sources/DiffIndex                                                                       
Ign http://archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex                                                                 
Ign http://archive.ubuntu.com natty-updates/universe Sources/DiffIndex                                                                   
Ign http://archive.ubuntu.com natty-updates/main amd64 Packages/DiffIndex                                                                
Ign http://archive.ubuntu.com natty-updates/restricted amd64 Packages/DiffIndex                                                          
Ign http://archive.ubuntu.com natty-updates/universe amd64 Packages/DiffIndex                                                            
Ign http://archive.ubuntu.com natty-updates/multiverse amd64 Packages/DiffIndex                                                          
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex                                                                        
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex                                                                  
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex                                                                  
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex                                                                    
Ign http://archive.ubuntu.com natty-security/restricted Sources/DiffIndex                                                                
Ign http://archive.ubuntu.com natty-security/main Sources/DiffIndex                                                                      
Ign http://archive.ubuntu.com natty-security/multiverse Sources/DiffIndex                                                                
Ign http://archive.ubuntu.com natty-security/universe Sources/DiffIndex                                                                  
Ign http://archive.ubuntu.com natty-security/main amd64 Packages/DiffIndex                                                               
Ign http://archive.ubuntu.com natty-security/restricted amd64 Packages/DiffIndex                                                         
Ign http://archive.ubuntu.com natty-security/universe amd64 Packages/DiffIndex                                                           
Ign http://archive.ubuntu.com natty-security/multiverse amd64 Packages/DiffIndex                                                         
Ign http://archive.ubuntu.com natty-security/main TranslationIndex                                                                       
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex                                                                 
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex                                                                 
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex                                                                   
Hit http://archive.ubuntu.com natty/restricted Sources                                                                                   
Hit http://archive.ubuntu.com natty/main Sources                                                                                         
Hit http://archive.ubuntu.com natty/multiverse Sources                                                                                   
Hit http://archive.ubuntu.com natty/universe Sources                                                                                     
Hit http://archive.ubuntu.com natty/main amd64 Packages                                                                                  
Hit http://archive.ubuntu.com natty/restricted amd64 Packages                                                                            
Hit http://archive.ubuntu.com natty/universe amd64 Packages                                                                              
Hit http://archive.ubuntu.com natty/multiverse amd64 Packages                                                                            
Hit http://archive.ubuntu.com natty/main Translation-en_CA                                                                               
Hit http://archive.ubuntu.com natty/restricted Translation-en_CA                                                                         
Hit http://archive.ubuntu.com natty-updates/restricted Sources                                                                           
Hit http://archive.ubuntu.com natty-updates/main Sources                                                                                 
Hit http://archive.ubuntu.com natty-updates/multiverse Sources                                                                           
Hit http://archive.ubuntu.com natty-updates/universe Sources                                                                             
Hit http://archive.ubuntu.com natty-updates/main amd64 Packages                                                                          
Hit http://archive.ubuntu.com natty-updates/restricted amd64 Packages                                                                    
Hit http://archive.ubuntu.com natty-updates/universe amd64 Packages                                                                      
Hit http://archive.ubuntu.com natty-updates/multiverse amd64 Packages                                                                    
Hit http://archive.ubuntu.com natty-security/restricted Sources                                                                          
Hit http://archive.ubuntu.com natty-security/main Sources                                                                                
Hit http://archive.ubuntu.com natty-security/multiverse Sources                                                                          
Hit http://archive.ubuntu.com natty-security/universe Sources                                                                            
Hit http://archive.ubuntu.com natty-security/main amd64 Packages                                                                         
Hit http://archive.ubuntu.com natty-security/restricted amd64 Packages                                                                   
Hit http://archive.ubuntu.com natty-security/universe amd64 Packages                                                                     
Hit http://archive.ubuntu.com natty-security/multiverse amd64 Packages                                                                   
Ign http://archive.ubuntu.com natty/main Translation-en                                                                                  
Ign http://archive.ubuntu.com natty/multiverse Translation-en_CA                                                                         
Ign http://archive.ubuntu.com natty/multiverse Translation-en                                                                            
Ign http://archive.ubuntu.com natty/restricted Translation-en                                                                            
Ign http://archive.ubuntu.com natty/universe Translation-en_CA                                                                           
Ign http://archive.ubuntu.com natty/universe Translation-en                                                                              
Ign http://archive.ubuntu.com natty-updates/main Translation-en_CA                                                                       
Ign http://archive.ubuntu.com natty-updates/main Translation-en                                                                          
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_CA                                                                 
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en                                                                    
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_CA                                                                 
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en                                                                    
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_CA
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_CA
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_CA
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_CA
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_CA
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Fetched 5,062 B in 18s (274 B/s)
Reading package lists... Done
W: GPG error: http://extras.ubuntu.com natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.ubuntu.com natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://archive.ubuntu.com natty-updates InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: http://archive.ubuntu.com natty-security InRelease: The following signatures were invalid: NODATA 1 NODATA 2
root@cheetah:~# 


```root@cheetah:~# apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                    
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release [9,753 B]                                                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources/DiffIndex                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages/DiffIndex            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main amd64 Packages                                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_CA                                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                            
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                          
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner Sources       
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner amd64 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                                                                          
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_CA                                                                         
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                                                                            
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                                                                            
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease [1,684 B]                                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease                                                                                    
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease                                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources/DiffIndex                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources/DiffIndex                                                                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources/DiffIndex                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources/DiffIndex                                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main amd64 Packages/DiffIndex                                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted amd64 Packages/DiffIndex                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe amd64 Packages/DiffIndex                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse amd64 Packages/DiffIndex                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex                                                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse TranslationIndex                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted TranslationIndex                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe TranslationIndex                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources/DiffIndex                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources/DiffIndex                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Sources/DiffIndex                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources/DiffIndex                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main amd64 Packages/DiffIndex                                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted amd64 Packages/DiffIndex                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe amd64 Packages/DiffIndex                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse amd64 Packages/DiffIndex                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main TranslationIndex                                                                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse TranslationIndex                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted TranslationIndex                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe TranslationIndex                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Sources/DiffIndex                                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Sources/DiffIndex                                                                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Sources/DiffIndex                                                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Sources/DiffIndex                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main amd64 Packages/DiffIndex                                                               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted amd64 Packages/DiffIndex                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe amd64 Packages/DiffIndex                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse amd64 Packages/DiffIndex                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main TranslationIndex                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse TranslationIndex                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted TranslationIndex                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe TranslationIndex                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Sources                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Sources                                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Sources                                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main amd64 Packages                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted amd64 Packages                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe amd64 Packages                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse amd64 Packages                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_CA                                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en_CA                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Sources                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Sources                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Sources                                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Sources                                                                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main amd64 Packages                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted amd64 Packages                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe amd64 Packages                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse amd64 Packages                                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Sources                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Sources                                                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Sources                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Sources                                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main amd64 Packages                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted amd64 Packages                                                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe amd64 Packages                                                                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse amd64 Packages                                                                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en                                                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en_CA                                                                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/multiverse Translation-en                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/restricted Translation-en                                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en_CA                                                                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/universe Translation-en                                                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en_CA                                                                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/main Translation-en                                                                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en_CA                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/multiverse Translation-en                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en_CA                                                                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/restricted Translation-en                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates/universe Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/restricted Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security/universe Translation-en
Fetched 5,062 B in 18s (274 B/s)
Reading package lists... Done
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-updates InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-security InRelease: The following signatures were invalid: NODATA 1 NODATA 2
root@cheetah:~# 
[/CODE]

So when something like this happens where should I look for the key?

The only number I can see is 16126D3A3E5C1192 but is "this" the key? I did try to search and couldn't find detailed explanation.

Thank you,

---

### Post by webofunni on 2011-06-04
try

```

apt-key update

```

if that not solving paste here the output of 

```

apt-key list

```

---

### Post by bojo on 2011-06-04
Guys - this is solved already 
```

root@cheetah:~# apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/3E5C1192 2010-09-20
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

pub   1024D/98AB5139 2010-05-18
uid                  Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
sub   2048g/281DDC4B 2010-05-18


```

I did use the link from sahabcse

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

The keyserver is 

[http://keyserver.ubuntu.com/](http://keyserver.ubuntu.com/)

I solved it by taking the key # from another system. What I couldn't understand - if I did not have access to another system how to find the key I needed. I think this would end up looking on the keyserver itself and for a person not familiar with it can be confusing. Never the less - if somebody needs the keys I posted them above

Thanks all

---

### Post by DarkDancer on 2011-06-05
I blame Hoffman....

---

