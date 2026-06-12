---
title: "Trying to upgrade R in Lucid. Any easy and painless way?"
date: 2012-08-31
forum: Installation &amp; Upgrades
---

### Post by floral on 2012-08-31
Hello,
I need your help.
I work on Lucid 10.04. Recently I started working on R (through R studio and terminal) and on Eclipse StatEt
I have constantly warnings and errors. I tried to solve them by searching on the internet and I suspect that the majority of them are caused when working on an older version of R.

Now I want to upgrade R, but the Software Manager does not contain the release of 2.15
I want to avoid .tar.gz files, for obvious reasons 

So, I tried to follow these suggestions [http://stackoverflow.com/questions/10476713/how-to-upgrade-r-in-ubuntu](http://stackoverflow.com/questions/10476713/how-to-upgrade-r-in-ubuntu)
but I get the following error (the translation is in bold and parentheses): 
> ----@laptop:~$ gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
gpg: requesting key E084DAB9 from hkp server keyserver.ubuntu.com
gpg: key E084DAB9: public key "Michael Rutter <marutter@gmail.com>" imported
gpg: &#931;&#965;&#957;&#959;&#955;&#953;&#954;&#972;&#962; &#945;&#961;&#953;&#952;&#956;&#972;&#962; &#960;&#959;&#965; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#940;&#963;&#964;&#951;&#954;&#945;&#957;: 1
gpg:               &#949;&#953;&#963;&#945;&#967;&#952;&#941;&#957;&#964;&#945;: 1  (RSA: 1)
-----@laptop:~$ gpg -a --export E084DAB9 | sudo apt-key add -
[sudo] password for -----: 
OK
-----@laptop:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid Release.gpg
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid/main Translation-el             
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-el       
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid/universe Translation-el         
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-el       
&#934;&#941;&#961;&#949;:1 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates Release.gpg [198B]           
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-el     
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-el
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-el 
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-el
&#934;&#941;&#961;&#949;:2 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-backports Release.gpg [198B]         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-el
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net/gummi/gummi/ubuntu/](http://ppa.launchpad.net/gummi/gummi/ubuntu/) lucid/main Translation-el 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-el      
&#934;&#941;&#961;&#949;:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [198B]                  
&#934;&#941;&#961;&#949;:4 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security Release.gpg [198B]          
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-el
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net/libreoffice/ppa/ubuntu/](http://ppa.launchpad.net/libreoffice/ppa/ubuntu/) lucid/main Translation-el
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/) lucid/main Translation-el
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
&#934;&#941;&#961;&#949;:5 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-proposed Release.gpg [198B]          
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-el
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-el    
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-el
Hit [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-el
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid Release                                 
&#934;&#941;&#961;&#949;:6 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates Release [58,3kB]             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
&#934;&#941;&#961;&#949;:7 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-backports Release [57,3kB]           
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-el               
&#934;&#941;&#961;&#949;:8 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security Release [57,3kB]            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
&#934;&#941;&#961;&#949;:9 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-proposed Release [58,3kB]            
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable/non-free Translation-el             
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/main Packages                           
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/main Sources                            
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/universe Packages                       
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/universe Sources                        
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid/multiverse Sources                      
(Bring) &#934;&#941;&#961;&#949;:10 [http://cran.cnr.berkeley.edu](http://cran.cnr.berkeley.edu) lucid/ Release.gpg [490B]                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
&#934;&#941;&#961;&#949;:11 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates/main Packages [635kB]       
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                         
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-el           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
&#934;&#941;&#961;&#949;:12 [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg [489B]                      
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) lucid/main Translation-el             
Hit [http://www.mendeley.com](http://www.mendeley.com)  Release.gpg                                       
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                          
&#934;&#941;&#961;&#949;:13 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates/restricted Packages [4624B] 
&#934;&#941;&#961;&#949;:14 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates/main Sources [227kB]        
&#934;&#941;&#961;&#949;:15 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6854B]                    
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                            
&#934;&#941;&#961;&#949;:16 [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release [2599B]                         
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://www.mendeley.com/repositories/ubuntu/stable/](http://www.mendeley.com/repositories/ubuntu/stable/)  Translation-el    
&#934;&#941;&#961;&#949;:17 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates/restricted Sources [2196B]  
&#934;&#941;&#961;&#949;:18 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates/universe Packages [296kB]   
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                          
(=Ignore) &#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://cran.cnr.berkeley.edu/bin/linux/ubuntu/](http://cran.cnr.berkeley.edu/bin/linux/ubuntu/) lucid/ Translation-el   
&#934;&#941;&#961;&#949;:19 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates/universe Sources [103kB]    
&#934;&#941;&#961;&#949;:20 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates/multiverse Packages [11,5kB]
&#934;&#941;&#961;&#949;:21 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-updates/multiverse Sources [5821B]  
&#934;&#941;&#961;&#949;:22 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-backports/main Packages [19,0kB]    
&#934;&#941;&#961;&#949;:23 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-backports/restricted Packages [14B] 
&#934;&#941;&#961;&#949;:24 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-backports/universe Packages [55,2kB]
&#934;&#941;&#961;&#949;:25 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-backports/multiverse Packages [1378B]
&#934;&#941;&#961;&#949;:26 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security/main Packages [445kB]      
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages                              
&#934;&#941;&#961;&#949;:27 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security/restricted Packages [2829B]
&#934;&#941;&#961;&#949;:28 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security/main Sources [129kB]       
&#934;&#941;&#961;&#949;:29 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security/restricted Sources [1267B] 
&#934;&#941;&#961;&#949;:30 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security/universe Packages [155kB]  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                          
&#934;&#941;&#961;&#949;:31 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security/universe Sources [42,0kB]  
&#934;&#941;&#961;&#949;:32 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security/multiverse Packages [5356B]
&#934;&#941;&#961;&#949;:33 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-security/multiverse Sources [2321B] 
&#934;&#941;&#961;&#949;:34 [http://linux.dropbox.com](http://linux.dropbox.com) lucid/main Packages [1029B]                   
&#934;&#941;&#961;&#949;:35 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-proposed/restricted Packages [14B]  
&#934;&#941;&#961;&#949;:36 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-proposed/main Packages [138kB]      
&#934;&#941;&#961;&#949;:37 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-proposed/multiverse Packages [14B]  
&#934;&#941;&#961;&#949;:38 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) lucid-proposed/universe Packages [25,8kB] 
&#934;&#941;&#961;&#949;:39 [http://cran.cnr.berkeley.edu](http://cran.cnr.berkeley.edu) lucid/ Release [2270B]                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources                           
Hit [http://www.mendeley.com](http://www.mendeley.com)  Release                                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources                       
&#934;&#941;&#961;&#949;:40 [http://cran.cnr.berkeley.edu](http://cran.cnr.berkeley.edu) lucid/ Packages [49,2kB]                  
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://www.mendeley.com](http://www.mendeley.com)  Packages                                      
&#913;&#947;&#957;&#972;&#951;&#963;&#949; [http://www.mendeley.com](http://www.mendeley.com)  Packages                           
Hit [http://www.mendeley.com](http://www.mendeley.com)  Packages        
&#924;&#949;&#964;&#945;&#966;&#959;&#961;&#964;&#974;&#952;&#951;&#954;&#945;&#957; 2595kB &#963;&#949; 4s (635kB/s)
**W: GPG error:** [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: &#927;&#953; &#960;&#945;&#961;&#945;&#954;&#940;&#964;&#969; &#965;&#960;&#959;&#947;&#961;&#945;&#966;&#941;&#962; &#948;&#949;&#957; &#942;&#964;&#945;&#957; &#948;&#965;&#957;&#945;&#964;&#972;&#957; &#957;&#945; &#949;&#960;&#945;&#955;&#951;&#952;&#949;&#965;&#964;&#959;&#973;&#957; &#949;&#960;&#949;&#953;&#948;&#942; &#948;&#949;&#957; &#942;&#964;&#945;&#957; &#948;&#953;&#945;&#952;&#941;&#963;&#953;&#956;&#959; &#964;&#959; &#948;&#951;&#956;&#972;&#963;&#953;&#959; &#954;&#955;&#949;&#953;&#948;&#943;: NO_PUBKEY 2EBC26B60C5A2783
**(=the signatures below are not possible to be verified because the public key is not available)**
E: &#913;&#948;&#973;&#957;&#945;&#964;&#959; &#964;&#959; &#954;&#955;&#949;&#943;&#948;&#969;&#956;&#945; /var/lib/dpkg/lock - open (11: &#927; &#960;&#972;&#961;&#959;&#962; &#949;&#943;&#957;&#945;&#953; &#960;&#961;&#959;&#963;&#969;&#961;&#953;&#957;&#940; &#956;&#951; &#948;&#953;&#945;&#952;&#941;&#963;&#953;&#956;&#959;&#962;) 
**(= impossible to lock /var/lib/dpkg/lock - open (the source is temporarily unavailable))**
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
My main question is: is there an easy default way to get R upgraded without errors, warnings, remaining in Lucid, once and for all?

And another question. Since I work on Rstudio and Eclipse (I do not actually have any significant output due to the amount of warnings :( ) will I have to configure them with the new R version or will they recognise it on their own?

P.S. I use Ubuntu for 3 years and I do not have the time to learn to use the terminal commands. Linux is so much better than Windows in so many ways, but sometimes I wish I had the .exe file and say just YES and get things installed and done... even with the risk of getting a virus. Now I work on Windows, until I fix this problem.
Thank you for your time :)

---

