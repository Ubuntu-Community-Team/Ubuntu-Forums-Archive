---
title: "problem installing almoast any aplication"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by asg31 on 2009-12-26
i have problem installing almoast any application i searched and i run some diagnostics!?!?!

```
radek@radek-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of splashy-themes:
 splashy-themes depends on splashy (>= 0.3.12-1); however:
  Package splashy is not installed.
dpkg: error processing splashy-themes (--configure):
 dependency problems - leaving unconfigured
Setting up ttf-dustin (20030517-6) ...
Updating fontconfig cache for /usr/share/fonts/truetype/dustin
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Setting up libdirectfb-extra (1.2.7-2ubuntu1) ...
Setting up libimlib2 (1.4.2-5) ...

Setting up libsplashy1 (0.3.13-5ubuntu1) ...

Setting up wbar (1.3.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 splashy-themes
radek@radek-laptop:~$ sudo apt-get clean
radek@radek-laptop:~$ sudo apt-get update
Hit http://nz.archive.ubuntu.com karmic Release.gpg
Hit http://repository.cairo-dock.org karmic Release.gpg                        
Ign http://nz.archive.ubuntu.com karmic/main Translation-en_NZ                 
Hit http://ppa.launchpad.net karmic Release.gpg                                
Ign http://nz.archive.ubuntu.com karmic/restricted Translation-en_NZ           
Ign http://nz.archive.ubuntu.com karmic/universe Translation-en_NZ             
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://repository.cairo-dock.org karmic/cairo-dock Translation-en_NZ       
Hit http://repository.cairo-dock.org intrepid Release.gpg                      
Ign http://nz.archive.ubuntu.com karmic/multiverse Translation-en_NZ           
Hit http://nz.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://ppa.launchpad.net karmic/main Translation-en_NZ                     
Ign http://nz.archive.ubuntu.com karmic-updates/main Translation-en_NZ         
Ign http://security.ubuntu.com karmic-security/main Translation-en_NZ          
Ign http://nz.archive.ubuntu.com karmic-updates/restricted Translation-en_NZ   
Ign http://repository.cairo-dock.org intrepid/cairo-dock Translation-en_NZ     
Hit http://repository.cairo-dock.org karmic Release                  
Hit http://ppa.launchpad.net karmic Release                          
Ign http://nz.archive.ubuntu.com karmic-updates/universe Translation-en_NZ     
Hit http://repository.cairo-dock.org intrepid Release                          
Ign http://nz.archive.ubuntu.com karmic-updates/multiverse Translation-en_NZ   
Hit http://nz.archive.ubuntu.com karmic Release                                
Hit http://repository.cairo-dock.org karmic/cairo-dock Packages                
Hit http://nz.archive.ubuntu.com karmic-updates Release                        
Hit http://repository.cairo-dock.org intrepid/cairo-dock Packages              
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_NZ    
Hit http://ppa.launchpad.net karmic/main Packages                              
Hit http://nz.archive.ubuntu.com karmic/main Packages
Hit http://nz.archive.ubuntu.com karmic/restricted Packages                 
Ign http://security.ubuntu.com karmic-security/universe Translation-en_NZ   
Hit http://nz.archive.ubuntu.com karmic/main Sources                        
Hit http://nz.archive.ubuntu.com karmic/restricted Sources                  
Hit http://nz.archive.ubuntu.com karmic/universe Packages                   
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_NZ 
Hit http://nz.archive.ubuntu.com karmic/universe Sources                    
Hit http://nz.archive.ubuntu.com karmic/multiverse Packages                 
Hit http://security.ubuntu.com karmic-security Release                      
Hit http://nz.archive.ubuntu.com karmic/multiverse Sources                  
Hit http://nz.archive.ubuntu.com karmic-updates/main Packages               
Hit http://nz.archive.ubuntu.com karmic-updates/restricted Packages         
Hit http://security.ubuntu.com karmic-security/main Packages                
Hit http://nz.archive.ubuntu.com karmic-updates/main Sources                
Hit http://nz.archive.ubuntu.com karmic-updates/restricted Sources             
Hit http://nz.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://security.ubuntu.com karmic-security/restricted Packages          
Hit http://nz.archive.ubuntu.com karmic-updates/universe Sources            
Hit http://nz.archive.ubuntu.com karmic-updates/multiverse Packages            
Hit http://nz.archive.ubuntu.com karmic-updates/multiverse Sources             
Hit http://security.ubuntu.com karmic-security/main Sources                 
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Reading package lists... Done                         
radek@radek-laptop:~$ sudo apt-get install cairo-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  cairo-dock: Depends: cairo-dock-core (>= 2.1.3-0alpha0-20091223-0ubuntu1~ppa0~karmic) but it is not going to be installed
              Depends: cairo-dock-plug-ins (>= 2.0.0) but it is not going to be installed
  splashy-themes: Depends: splashy (>= 0.3.12-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

``` 
I DID It I removed splashy themes

---

### Post by steveneddy on 2009-12-26
I'm not entirely sure what you are trying to ask, but it looks like you need to install **splashy**

```
sudo apt-get install splashy
```

---

