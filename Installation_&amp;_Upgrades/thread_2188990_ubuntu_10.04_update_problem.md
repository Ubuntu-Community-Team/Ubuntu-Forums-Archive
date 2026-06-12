---
title: "ubuntu 10.04 update problem"
date: 2013-11-20
forum: Installation &amp; Upgrades
---

### Post by surja1 on 2013-11-20
Hi all,

I am facing problem to update ubuntu 10.04 via both terminal and form update manager .
The output in the terminal after giving 
sudo apt-get update is as
[PHP]surja@surja-laptop:~$ sudo apt-get update
Des:1 http://dl.google.com stable Release.gpg [198B]                                                                        
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US                                                
Des:2 http://ppa.launchpad.net lucid Release.gpg [316B]                                                                     
Ign http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu/ lucid/main Translation-en_US                         
Des:3 http://ppa.launchpad.net lucid Release.gpg [316B]                                                                     
Des:4 http://archive.ubuntu.com lucid Release.gpg [189B]                                                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US                                                          
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US                                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US                                                    
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US                                                      
Des:5 http://archive.ubuntu.com lucid-updates Release.gpg [198B]                                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/univers Translation-en_US                                               
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                                  
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                            
Des:6 http://archive.canonical.com lucid Release.gpg [198B]                                                                 
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US                                                    
Obj http://dl.google.com stable Release                                                                                     
Ign http://ppa.launchpad.net/team-iquik/alsa/ubuntu/ lucid/main Translation-en_US                                           
Des:7 http://ppa.launchpad.net lucid Release.gpg [316B]                                                                     
Ign http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/ lucid/main Translation-en_US                                      
Obj http://ppa.launchpad.net lucid Release                                                                                  
Des:8 http://linux.dropbox.com lucid Release.gpg [489B]                                                                     
Ign http://linux.dropbox.com/ubuntu/ lucid/main Translation-en_US                                                           
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                              
Des:9 http://archive.ubuntu.com lucid-security Release.gpg [198B]                                                           
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US                                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US                                             
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US                                           
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US                                           
Des:10 http://archive.ubuntu.com lucid-proposed Release.gpg [198B]                                                          
Obj http://dl.google.com stable/main Packages                                                                               
Obj http://archive.canonical.com lucid Release                                                                              
Ign http://cz.archive.ubuntu.com hardy-updates Release.gpg                                                                  
Ign http://cz.archive.ubuntu.com/ubuntu/ hardy-updates/universe Translation-en_US                          
Des:11 http://ppa.launchpad.net lucid Release [13.9kB]                                                     
Ign http://ppa.launchpad.net lucid Release                                                                                  
Des:12 http://linux.dropbox.com lucid Release [2,599B]                                                                      
Ign http://archive.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US                                           
Ign http://archive.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US                                                 
Ign http://archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US                          
Obj http://archive.canonical.com lucid/partner Packages                                                    
Ign http://cz.archive.ubuntu.com hardy-updates Release                                                     
Des:13 http://ppa.launchpad.net lucid Release [14.0kB]                                                     
Ign http://ppa.launchpad.net lucid Release                                                                                  
Ign http://archive.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US                                             
Obj http://archive.ubuntu.com lucid Release                                                                
Des:14 http://archive.ubuntu.com lucid-updates Release [58.3kB]                                                             
Obj http://ppa.launchpad.net lucid/main Packages                                                                            
Ign http://cz.archive.ubuntu.com hardy-updates/universe Packages                                                
Des:15 http://linux.dropbox.com lucid/main Packages [1,148B]                                                    
Obj http://ppa.launchpad.net lucid/main Packages                                                                       
Ign http://cz.archive.ubuntu.com hardy-updates/universe Sources                       
Des:16 http://archive.ubuntu.com lucid-security Release [57.3kB]
Ign http://cz.archive.ubuntu.com hardy-updates/universe Packages                                            
Obj http://ppa.launchpad.net lucid/main Packages                                     
Obj http://archive.ubuntu.com lucid-proposed Release                                 
Obj http://archive.ubuntu.com lucid/main Packages
Obj http://archive.ubuntu.com lucid/restricted Packages
Obj http://archive.ubuntu.com lucid/multiverse Packages
Obj http://archive.ubuntu.com lucid/restricted Sources                          
Obj http://archive.ubuntu.com lucid/main Sources       
Obj http://archive.ubuntu.com lucid/multiverse Sources 
Obj http://archive.ubuntu.com lucid/universe Sources   
Obj http://archive.ubuntu.com lucid/universe Packages                        
Ign http://cz.archive.ubuntu.com hardy-updates/universe Sources              
Des:17 http://archive.ubuntu.com lucid-security/main Packages [524kB]
Err http://cz.archive.ubuntu.com hardy-updates/universe Packages
  404  Not Found
Err http://cz.archive.ubuntu.com hardy-updates/universe Sources
  404  Not Found
Des:18 http://archive.ubuntu.com lucid-security/universe Sources [46.6kB]                                                   
Des:19 http://archive.ubuntu.com lucid-security/main Sources [239kB]                                                        
Des:20 http://archive.ubuntu.com lucid-security/multiverse Sources [2,347B]                                                 
Des:21 http://archive.ubuntu.com lucid-security/restricted Sources [1,267B]                                                 
Des:22 http://archive.ubuntu.com lucid-security/universe Packages [148kB]                                                   
Des:23 http://archive.ubuntu.com lucid-security/restricted Packages [2,867B]                                                
Des:24 http://archive.ubuntu.com lucid-security/multiverse Packages [5,366B]                                                
Obj http://archive.ubuntu.com lucid-proposed/restricted Packages                                                            
Obj http://archive.ubuntu.com lucid-proposed/main Packages                                                                  
Obj http://archive.ubuntu.com lucid-proposed/multiverse Packages                                                            
Obj http://archive.ubuntu.com lucid-proposed/universe Packages                                                              
Obj http://archive.ubuntu.com lucid-proposed/restricted Sources                                                             
Obj http://archive.ubuntu.com lucid-proposed/main Sources                                                                   
Obj http://archive.ubuntu.com lucid-proposed/multiverse Sources                                                             
Obj http://archive.ubuntu.com lucid-proposed/universe Sources                                                               
Descargados 1,092kB en 10s (106kB/s)                                                                                        
W: GPG error: http://ppa.launchpad.net lucid Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 210AE75EDC1FE094
W: GPG error: http://ppa.launchpad.net lucid Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY D225991A72B194E5
W: Imposible obtener http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  Unable to find expected entry  univers/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Imposible obtener http://cz.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz  404  Not Found

W: Imposible obtener http://cz.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.gz  404  Not Found

E: Algunos archivos de índice no se han podido descargar, se han ignorado,
o se ha utilizado unos antiguos en su lugar.
[/PHP]

Please help me.
Thanks in advance.

---

### Post by Bucky Ball on 2013-11-20
10.04 is no longer supported. There won't be any updates and the repos are probably closed. 

You have a couple of choices. You can go to Software Sources>Updates>Notify me of new Ubuntu versions, and set that to long term releases and update to 12.04 LTS or do a clean install of 12.04 LTS or another release.

12.04 LTS has five years support rather than three.

---

### Post by mörgæs on 2013-11-20
+1 to the above.

In addition, your system has traces back to 8.04, which means that the installation is at least five years old. A clean install is recommended.

---

