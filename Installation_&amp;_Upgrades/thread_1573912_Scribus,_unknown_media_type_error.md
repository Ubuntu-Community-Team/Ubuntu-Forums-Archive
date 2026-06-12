---
title: "Scribus, unknown media type error"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by efranor on 2010-09-13
I tried to install Scribus on my laptop but somehow it says this. I have edited kde.xml and run the update after removeing the areas and running the update-mime- database but still i get those errors:
efranor@efranor-laptop:~$ sudo apt-get install scribus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.40.0 libboost-date-time1.40.0 libasound2-plugins
  gnash-common libspeexdsp1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  scribus-template scribus-doc
The following NEW packages will be installed:
  scribus
0 upgraded, 1 newly installed, 0 to remove and 44 not upgraded.
4 not fully installed or removed.
Need to get 0B/9,606kB of archives.
After this operation, 27.5MB of additional disk space will be used.
(Reading database ... 189558 files and directories currently installed.)
Unpacking scribus (from .../scribus_1.3.3.13.dfsg~svn20081228-2ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/scribus_1.3.3.13.dfsg~svn20081228-2ubuntu2_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/share/scribus/translations/scribus.eo.qm': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for shared-mime-info ...
Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Processing triggers for man-db ...                                           
Errors were encountered while processing:                                    
 /var/cache/apt/archives/scribus_1.3.3.13.dfsg~svn20081228-2ubuntu2_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by efranor on 2010-09-13
Ok got the problem but now a new one has arisen...

Reading package lists... Done                                                
Building dependency tree                                                     
Reading state information... Done                                            
The following packages were automatically installed and are no longer required:                                                                           
  libboost-thread1.40.0 libboost-date-time1.40.0 libasound2-plugins          
  gnash-common libspeexdsp1                                                  
Use 'apt-get autoremove' to remove them.                                     
Suggested packages:                                                          
  scribus-template scribus-doc
The following NEW packages will be installed:
  scribus
0 upgraded, 1 newly installed, 0 to remove and 44 not upgraded.
4 not fully installed or removed.
Need to get 0B/9,606kB of archives.
After this operation, 27.5MB of additional disk space will be used.
(Reading database ... 189558 files and directories currently installed.)
Unpacking scribus (from .../scribus_1.3.3.13.dfsg~svn20081228-2ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/scribus_1.3.3.13.dfsg~svn20081228-2ubuntu2_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./usr/share/scribus/translations/scribus.eo.qm': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/scribus_1.3.3.13.dfsg~svn20081228-2ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
efranor@efranor-laptop:/usr/share/mime/packages$

---

