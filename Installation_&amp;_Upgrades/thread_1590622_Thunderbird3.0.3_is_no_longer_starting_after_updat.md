---
title: "Thunderbird3.0.3 is no longer starting after updating"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by pc-kid on 2010-10-08
I installed the normal recommended aptidue updates this morning. As a result of that, thunderbird is no longer starting:

/usr/bin/thunderbird-3.0            
/usr/lib/thunderbird-3.0.3pre/thunderbird-bin: symbol lookup error: /usr/lib/libnssutil3.so: undefined symbol: PL_ClearArenaPool 

I'm running a 64bit ubuntu, but 32bit firefox. Can anyone help me, please??? 

locate libnssutil3 | xargs ls -la 
ls: Access to /usr/lib/firefox-3.6.11pre/libnssutil3.so not possible: No such file or directory 
-rwxr-xr-x 1 dsc        dsc         80328 2008-03-26 06:44 /home/dsc/Dokumente/Songbird/xulrunner/libnssutil3.so 
-r--r--r-- 1 root       root       119512 2010-02-01 18:24 /opt/openoffice.org/basis3.2/program/libnssutil3.so 
-rw-r--r-- 1 root       root        95952 2009-08-01 17:17 /usr/lib32/libnssutil3.so 
lrwxrwxrwx 1 root       root           14 2009-12-12 20:24 /usr/lib32/libnssutil3.so.1d -> libnssutil3.so 
-rw-r--r-- 1 root       root       125824 2010-10-05 00:45 /usr/lib/libnssutil3.so 
lrwxrwxrwx 1 root       root           14 2010-10-08 08:16 /usr/lib/libnssutil3.so.1d -> libnssutil3.so 
-rwxr-xr-x 1 root       root        78800 2009-12-05 02:58 /usr/lib/thunderbird/libnssutil3.so 

/var/log/dpkg.log: 
2010-10-08 08:16:32 startup archives unpack                              
2010-10-08 08:16:44 upgrade libssl0.9.8 0.9.8g-15ubuntu3.5 0.9.8g-15ubuntu3.6 
2010-10-08 08:16:44 status half-configured libssl0.9.8 0.9.8g-15ubuntu3.5     
2010-10-08 08:16:44 status unpacked libssl0.9.8 0.9.8g-15ubuntu3.5            
2010-10-08 08:16:44 status half-installed libssl0.9.8 0.9.8g-15ubuntu3.5      
2010-10-08 08:16:44 status half-installed libssl0.9.8 0.9.8g-15ubuntu3.5      
2010-10-08 08:16:44 status unpacked libssl0.9.8 0.9.8g-15ubuntu3.6            
2010-10-08 08:16:44 status unpacked libssl0.9.8 0.9.8g-15ubuntu3.6            
2010-10-08 08:16:44 upgrade libnspr4-dev 4.8-0ubuntu0.9.04.1 4.8.6-0ubuntu0.9.04.1 
2010-10-08 08:16:44 status half-configured libnspr4-dev 4.8-0ubuntu0.9.04.1        
2010-10-08 08:16:44 status unpacked libnspr4-dev 4.8-0ubuntu0.9.04.1               
2010-10-08 08:16:44 status half-installed libnspr4-dev 4.8-0ubuntu0.9.04.1         
2010-10-08 08:16:44 status half-installed libnspr4-dev 4.8-0ubuntu0.9.04.1         
2010-10-08 08:16:44 status unpacked libnspr4-dev 4.8.6-0ubuntu0.9.04.1             
2010-10-08 08:16:44 status unpacked libnspr4-dev 4.8.6-0ubuntu0.9.04.1             
2010-10-08 08:16:44 upgrade libnspr4-0d 4.8-0ubuntu0.9.04.1 4.8.6-0ubuntu0.9.04.1  
2010-10-08 08:16:44 status half-configured libnspr4-0d 4.8-0ubuntu0.9.04.1         
2010-10-08 08:16:44 status unpacked libnspr4-0d 4.8-0ubuntu0.9.04.1                
2010-10-08 08:16:44 status half-installed libnspr4-0d 4.8-0ubuntu0.9.04.1          
2010-10-08 08:16:44 status half-installed libnspr4-0d 4.8-0ubuntu0.9.04.1          
2010-10-08 08:16:45 status unpacked libnspr4-0d 4.8.6-0ubuntu0.9.04.1              
2010-10-08 08:16:45 status unpacked libnspr4-0d 4.8.6-0ubuntu0.9.04.1              
2010-10-08 08:16:45 upgrade firefox-gnome-support  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty  3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:45 status half-configured firefox-gnome-support  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                           
2010-10-08 08:16:45 status unpacked firefox-gnome-support  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                  
2010-10-08 08:16:45 status half-installed firefox-gnome-support  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                            
2010-10-08 08:16:45 status half-installed firefox-gnome-support  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                            
2010-10-08 08:16:45 status unpacked firefox-gnome-support  3.6.11+build2+nobinonly-0ubuntu0.9.04.1                                                 
2010-10-08 08:16:45 status unpacked firefox-gnome-support  3.6.11+build2+nobinonly-0ubuntu0.9.04.1                                                 
2010-10-08 08:16:45 upgrade firefox-branding  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty  3.6.11+build2+nobinonly-0ubuntu0.9.04.1      
2010-10-08 08:16:45 status half-configured firefox-branding  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                
2010-10-08 08:16:45 status unpacked firefox-branding  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                       
2010-10-08 08:16:45 status half-installed firefox-branding  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                 
2010-10-08 08:16:45 status half-installed firefox-branding  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                 
2010-10-08 08:16:45 status unpacked firefox-branding  3.6.11+build2+nobinonly-0ubuntu0.9.04.1                                                      
2010-10-08 08:16:45 status unpacked firefox-branding  3.6.11+build2+nobinonly-0ubuntu0.9.04.1                                                      
2010-10-08 08:16:45 upgrade libnss3-dev 3.12.6-0ubuntu0.9.04.1  3.12.8-0ubuntu0.9.04.1                                                             
2010-10-08 08:16:45 status half-configured libnss3-dev  3.12.6-0ubuntu0.9.04.1                                                                     
2010-10-08 08:16:45 status unpacked libnss3-dev  3.12.6-0ubuntu0.9.04.1                                                                            
2010-10-08 08:16:45 status half-installed libnss3-dev  3.12.6-0ubuntu0.9.04.1                                                                      
2010-10-08 08:16:45 status half-installed libnss3-dev  3.12.6-0ubuntu0.9.04.1                                                                      
2010-10-08 08:16:45 status unpacked libnss3-dev  3.12.8-0ubuntu0.9.04.1                                                                            
2010-10-08 08:16:45 status unpacked libnss3-dev  3.12.8-0ubuntu0.9.04.1                                                                            
2010-10-08 08:16:45 upgrade libnss3-1d 3.12.6-0ubuntu0.9.04.1  3.12.8-0ubuntu0.9.04.1                                                              
2010-10-08 08:16:45 status half-configured libnss3-1d  3.12.6-0ubuntu0.9.04.1                                                                      
2010-10-08 08:16:45 status unpacked libnss3-1d  3.12.6-0ubuntu0.9.04.1                                                                             
2010-10-08 08:16:45 status half-installed libnss3-1d  3.12.6-0ubuntu0.9.04.1                                                                       
2010-10-08 08:16:45 status half-installed libnss3-1d  3.12.6-0ubuntu0.9.04.1                                                                       
2010-10-08 08:16:46 status unpacked libnss3-1d  3.12.8-0ubuntu0.9.04.1                                                                             
2010-10-08 08:16:46 status unpacked libnss3-1d  3.12.8-0ubuntu0.9.04.1                                                                             
2010-10-08 08:16:46 upgrade firefox  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty  3.6.11+build2+nobinonly-0ubuntu0.9.04.1               
2010-10-08 08:16:46 status half-configured firefox  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                         
2010-10-08 08:16:46 status unpacked firefox  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                                
2010-10-08 08:16:46 status half-installed firefox  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                          
2010-10-08 08:16:46 status triggers-pending menu 2.1.41ubuntu1                                                                                     
2010-10-08 08:16:47 status half-installed firefox  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                          
2010-10-08 08:16:47 status half-installed firefox  3.6.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                          
2010-10-08 08:16:47 status unpacked firefox  3.6.11+build2+nobinonly-0ubuntu0.9.04.1                                                               
2010-10-08 08:16:47 status unpacked firefox  3.6.11+build2+nobinonly-0ubuntu0.9.04.1                                                               
2010-10-08 08:16:47 upgrade openssl 0.9.8g-15ubuntu3.5  0.9.8g-15ubuntu3.6                                                                         
2010-10-08 08:16:47 status half-configured openssl  0.9.8g-15ubuntu3.5                                                                             
2010-10-08 08:16:47 status unpacked openssl 0.9.8g-15ubuntu3.5                                                                                     
2010-10-08 08:16:47 status half-installed openssl 0.9.8g-15ubuntu3.5                                                                               
2010-10-08 08:16:47 status triggers-pending man-db 2.5.5-1build1                                                                                   
2010-10-08 08:16:47 status half-installed openssl 0.9.8g-15ubuntu3.5                                                                               
2010-10-08 08:16:47 status half-installed openssl 0.9.8g-15ubuntu3.5                                                                               
2010-10-08 08:16:47 status unpacked openssl 0.9.8g-15ubuntu3.6                                                                                     
2010-10-08 08:16:47 status unpacked openssl 0.9.8g-15ubuntu3.6                                                                                     
2010-10-08 08:16:48 upgrade xulrunner-1.9.1-gnome-support  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:48 status half-configured  xulrunner-1.9.1-gnome-support  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty                             
2010-10-08 08:16:48 status unpacked xulrunner-1.9.1-gnome-support  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty                                    
2010-10-08 08:16:48 status half-installed  xulrunner-1.9.1-gnome-support  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty                              
2010-10-08 08:16:48 status half-installed  xulrunner-1.9.1-gnome-support  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty                              
2010-10-08 08:16:48 status unpacked xulrunner-1.9.1-gnome-support  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1                                                   
2010-10-08 08:16:48 status unpacked xulrunner-1.9.1-gnome-support  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1                                                   
2010-10-08 08:16:48 upgrade xulrunner-1.9.1  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1               
2010-10-08 08:16:48 status half-configured xulrunner-1.9.1  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty                                           
2010-10-08 08:16:48 status unpacked xulrunner-1.9.1  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty                                                  
2010-10-08 08:16:48 status half-installed xulrunner-1.9.1  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty                                            
2010-10-08 08:16:49 status half-installed xulrunner-1.9.1  1.9.1.14~hg20100918r27094+nobinonly-0ubuntu1~umd1~jaunty                                            
2010-10-08 08:16:50 status unpacked xulrunner-1.9.1  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1                                                                 
2010-10-08 08:16:50 status unpacked xulrunner-1.9.1  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1                                                                 
2010-10-08 08:16:50 upgrade xulrunner-1.9.2  1.9.2.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty  1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1               
2010-10-08 08:16:50 status half-configured xulrunner-1.9.2  1.9.2.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                           
2010-10-08 08:16:50 status unpacked xulrunner-1.9.2  1.9.2.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                                  
2010-10-08 08:16:50 status half-installed xulrunner-1.9.2  1.9.2.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                            
2010-10-08 08:16:51 status half-installed xulrunner-1.9.2  1.9.2.11~hg20100918r34583+nobinonly-0ubuntu1~umd1~jaunty                                            
2010-10-08 08:16:52 status unpacked xulrunner-1.9.2  1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1                                                                 
2010-10-08 08:16:52 status unpacked xulrunner-1.9.2  1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1                                                                 
2010-10-08 08:16:52 trigproc menu 2.1.41ubuntu1 2.1.41ubuntu1                                                                                                  
2010-10-08 08:16:52 status half-configured menu 2.1.41ubuntu1                                                                                                  
2010-10-08 08:16:52 status installed menu 2.1.41ubuntu1                                                                                                        
2010-10-08 08:16:52 trigproc man-db 2.5.5-1build1 2.5.5-1build1                                                                                                
2010-10-08 08:16:52 status half-configured man-db 2.5.5-1build1                                                                                                
2010-10-08 08:16:53 status installed man-db 2.5.5-1build1                                                                                                      
2010-10-08 08:16:53 startup packages configure                                                                                                                 
2010-10-08 08:16:53 configure libssl0.9.8 0.9.8g-15ubuntu3.6  0.9.8g-15ubuntu3.6                                                                               
2010-10-08 08:16:53 status unpacked libssl0.9.8 0.9.8g-15ubuntu3.6                                                                                             
2010-10-08 08:16:53 status half-configured libssl0.9.8  0.9.8g-15ubuntu3.6                                                                                     
2010-10-08 08:16:54 status installed libssl0.9.8 0.9.8g-15ubuntu3.6                                                                                            
2010-10-08 08:16:54 status triggers-pending libc6 2.9-4ubuntu6.2                                                                                               
2010-10-08 08:16:54 configure libnspr4-0d 4.8.6-0ubuntu0.9.04.1  4.8.6-0ubuntu0.9.04.1                                                                         
2010-10-08 08:16:54 status unpacked libnspr4-0d  4.8.6-0ubuntu0.9.04.1                                                                                         
2010-10-08 08:16:54 status half-configured libnspr4-0d  4.8.6-0ubuntu0.9.04.1                                                                                  
2010-10-08 08:16:54 status installed libnspr4-0d  4.8.6-0ubuntu0.9.04.1                                                                                        
2010-10-08 08:16:54 configure libnspr4-dev 4.8.6-0ubuntu0.9.04.1  4.8.6-0ubuntu0.9.04.1                                                                        
2010-10-08 08:16:54 status unpacked libnspr4-dev  4.8.6-0ubuntu0.9.04.1                                                                                        
2010-10-08 08:16:54 status half-configured libnspr4-dev  4.8.6-0ubuntu0.9.04.1                                                                                 
2010-10-08 08:16:54 status installed libnspr4-dev  4.8.6-0ubuntu0.9.04.1                                                                                       
2010-10-08 08:16:54 configure libnss3-1d 3.12.8-0ubuntu0.9.04.1  3.12.8-0ubuntu0.9.04.1                                                                        
2010-10-08 08:16:54 status unpacked libnss3-1d  3.12.8-0ubuntu0.9.04.1                                                                                         
2010-10-08 08:16:54 status half-configured libnss3-1d  3.12.8-0ubuntu0.9.04.1                                                                                  
2010-10-08 08:16:54 status installed libnss3-1d  3.12.8-0ubuntu0.9.04.1                                                                                        
2010-10-08 08:16:54 configure libnss3-dev 3.12.8-0ubuntu0.9.04.1  3.12.8-0ubuntu0.9.04.1                                                                       
2010-10-08 08:16:54 status unpacked libnss3-dev  3.12.8-0ubuntu0.9.04.1                                                                                        
2010-10-08 08:16:54 status half-configured libnss3-dev  3.12.8-0ubuntu0.9.04.1                                                                                 
2010-10-08 08:16:54 status installed libnss3-dev  3.12.8-0ubuntu0.9.04.1                                                                                       
2010-10-08 08:16:54 configure openssl 0.9.8g-15ubuntu3.6  0.9.8g-15ubuntu3.6                                                                                   
2010-10-08 08:16:54 status unpacked openssl 0.9.8g-15ubuntu3.6                                                                                                 
2010-10-08 08:16:54 status unpacked openssl 0.9.8g-15ubuntu3.6 
2010-10-08 08:16:54 status half-configured openssl 0.9.8g-15ubuntu3.6 
2010-10-08 08:16:54 status installed openssl 0.9.8g-15ubuntu3.6 
2010-10-08 08:16:54 configure xulrunner-1.9.1  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked xulrunner-1.9.1 1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked xulrunner-1.9.1 1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked xulrunner-1.9.1 1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status half-configured xulrunner-1.9.1 1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status installed xulrunner-1.9.1 1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 configure xulrunner-1.9.1-gnome-support  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1  1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked xulrunner-1.9.1-gnome-support 1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status half-configured xulrunner-1.9.1-gnome-support 1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status installed xulrunner-1.9.1-gnome-support 1.9.1.14+build3+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 configure xulrunner-1.9.2  1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1  1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked xulrunner-1.9.2 1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked xulrunner-1.9.2 1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked xulrunner-1.9.2 1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status half-configured xulrunner-1.9.2 1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status installed xulrunner-1.9.2 1.9.2.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 configure firefox-branding 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox-branding 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status half-configured firefox-branding 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status installed firefox-branding 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 configure firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status unpacked firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:54 status half-configured firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:55 status installed firefox 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:55 status triggers-pending menu 2.1.41ubuntu1 
2010-10-08 08:16:55 status triggers-awaited menu 2.1.41ubuntu1 
2010-10-08 08:16:55 configure firefox-gnome-support  3.6.11+build2+nobinonly-0ubuntu0.9.04.1  3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:55 status unpacked firefox-gnome-support 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:55 status half-configured firefox-gnome-support 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:55 status installed firefox-gnome-support 3.6.11+build2+nobinonly-0ubuntu0.9.04.1 
2010-10-08 08:16:55 trigproc libc6 2.9-4ubuntu6.2 2.9-4ubuntu6.2 
2010-10-08 08:16:55 status half-configured libc6 2.9-4ubuntu6.2 
2010-10-08 08:16:55 status installed libc6 2.9-4ubuntu6.2 
2010-10-08 08:16:55 trigproc menu 2.1.41ubuntu1 2.1.41ubuntu1 
2010-10-08 08:16:55 status half-configured menu 2.1.41ubuntu1 
2010-10-08 08:16:55 status installed menu 2.1.41ubuntu1

---

### Post by Peter09 on 2010-10-08
What happens if you run Thunderbird from a terminal.

---

### Post by pc-kid on 2010-10-08
I startet it from a terminal. Nothing happened exept the error message:

DSC:> /usr/bin/thunderbird-3.0            
/usr/lib/thunderbird-3.0.3pre/thunderbird-bin: symbol lookup error: /usr/lib/libnssutil3.so: undefined symbol: PL_ClearArenaPool

---

### Post by pc-kid on 2010-10-10
Is anyone able to help me?

---

### Post by pc-kid on 2010-10-12
Problem solved by uninstalling thunderbird 3.0 and installing thunderbird 3.1.4

---

