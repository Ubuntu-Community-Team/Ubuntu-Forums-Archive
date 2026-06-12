---
title: "update problem"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by luca-barazzuol on 2013-10-17
Since about 3 weeks I am not more able to update my ubuntu 13.04.

I got this error: 

```
luke@u12:~$ sudo apt-get upgrade
[sudo] password for luke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnome-terminal gnome-terminal-data gnupg gnupg-agent gnupg-curl gnupg2 gpgsm gpgv libegl1-mesa libegl1-mesa-drivers libgbm1 libgl1-mesa-dri libgl1-mesa-dri:i386 libgl1-mesa-glx
  libgl1-mesa-glx:i386 libglapi-mesa libglapi-mesa:i386 libgles2-mesa libicu48 libicu48:i386 liblightdm-gobject-1-0 liblightdm-qt-2-0 libopenvg1-mesa libsasl2-2 libsasl2-2:i386
  libsasl2-modules libsasl2-modules:i386 libxatracker1 lightdm scdaemon spotify-client steam:i386 steam-launcher
33 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 70,8 MB of archives.
After this operation, 20,0 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main libsasl2-modules amd64 2.1.25.dfsg1-6ubuntu0.1 [63,1 kB]
Get:2 http://repository.spotify.com/ stable/non-free spotify-client amd64 1:0.9.4.183.g644e24e.428-1 [47,4 MB]        
Get:3 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main libsasl2-modules i386 2.1.25.dfsg1-6ubuntu0.1 [59,3 kB]                 
Get:4 http://repo.steampowered.com/steam/ precise/steam steam-launcher all 1.0.0.43 [2057 kB]        
Get:5 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main libsasl2-2 i386 2.1.25.dfsg1-6ubuntu0.1 [68,6 kB]      
Get:6 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main libsasl2-2 amd64 2.1.25.dfsg1-6ubuntu0.1 [69,4 kB]
Get:7 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libgles2-mesa amd64 9.1.7-1ubuntu2 [12,4 kB]
Get:8 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libgl1-mesa-dri i386 9.1.7-1ubuntu2 [3326 kB]    
Get:9 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libgl1-mesa-dri amd64 9.1.7-1ubuntu2 [3572 kB]                                                                     
Get:10 http://repo.steampowered.com/steam/ precise/steam steam i386 1.0.0.43 [4312 B]                                                                                              
Get:11 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libgl1-mesa-glx i386 9.1.7-1ubuntu2 [103 kB]                                                                      
Get:12 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libgl1-mesa-glx amd64 9.1.7-1ubuntu2 [105 kB]                                                                     
Get:13 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libglapi-mesa amd64 9.1.7-1ubuntu2 [20,6 kB]                                                                      
Get:14 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libglapi-mesa i386 9.1.7-1ubuntu2 [20,8 kB]                                                                       
Get:15 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libegl1-mesa-drivers amd64 9.1.7-1ubuntu2 [988 kB]                                                                
Get:16 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libgbm1 amd64 9.1.7-1ubuntu2 [16,4 kB]                                                                            
Get:17 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libopenvg1-mesa amd64 9.1.7-1ubuntu2 [13,1 kB]                                                                    
Get:18 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libegl1-mesa amd64 9.1.7-1ubuntu2 [55,0 kB]                                                                       
Get:19 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main libicu48 i386 4.8.1.1-12ubuntu0.1 [4771 kB]                                                                        
Get:20 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main libicu48 amd64 4.8.1.1-12ubuntu0.1 [4718 kB]                                                                       
Get:21 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main libxatracker1 amd64 9.1.7-1ubuntu2 [135 kB]                                                                       
Get:22 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main lightdm amd64 1.6.0-0ubuntu4 [103 kB]                                                                             
Get:23 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main gpgv amd64 1.4.12-7ubuntu1.2 [185 kB]                                                                              
Get:24 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main gnupg amd64 1.4.12-7ubuntu1.2 [817 kB]                                                                             
Get:25 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main gnome-terminal-data all 3.6.1-0ubuntu4.1 [61,3 kB]                                                                
Get:26 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main gnome-terminal amd64 3.6.1-0ubuntu4.1 [110 kB]                                                                    
Get:27 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main gnupg-agent amd64 2.0.19-2ubuntu1.1 [427 kB]                                                                       
Get:28 http://it.archive.ubuntu.com/ubuntu/ raring-updates/main gnupg2 amd64 2.0.19-2ubuntu1.1 [1043 kB]                                                                           
Get:29 http://it.archive.ubuntu.com/ubuntu/ raring-updates/universe gnupg-curl amd64 1.4.12-7ubuntu1.2 [20,5 kB]                                                                   
Get:30 http://it.archive.ubuntu.com/ubuntu/ raring-updates/universe scdaemon amd64 2.0.19-2ubuntu1.1 [182 kB]                                                                      
Get:31 http://it.archive.ubuntu.com/ubuntu/ raring-updates/universe gpgsm amd64 2.0.19-2ubuntu1.1 [218 kB]                                                                         
Get:32 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main liblightdm-gobject-1-0 amd64 1.6.0-0ubuntu4 [32,7 kB]                                                             
Get:33 http://it.archive.ubuntu.com/ubuntu/ raring-proposed/main liblightdm-qt-2-0 amd64 1.6.0-0ubuntu4 [31,2 kB]                                                                  
Fetched 70,8 MB in 3min 19s (355 kB/s)                                                                                                                                             
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
Setting up tzdata (2013g-0ubuntu0.13.04) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by slickymaster on 2013-10-17
Hi luca-barazzuol, welcome to the forums.

Try to reinstall debconf```
sudo apt-get install debconf --reinstall
```

---

### Post by luca-barazzuol on 2013-10-17
Same problem:

```
luke@u12:~$ sudo apt-get install debconf --reinstall
[sudo] password for luke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.8.0-29-generic linux-image-extra-3.8.0-29-generic python-central
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 33 not upgraded.
9 not fully installed or removed.
Need to get 149 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://it.archive.ubuntu.com/ubuntu/ raring/main debconf all 1.5.49ubuntu1 [149 kB]
Fetched 149 kB in 0s (318 kB/s)
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
Setting up tzdata (2013g-0ubuntu0.13.04) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
debconf: DbDriver "config": mkdir :No such file or directory
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by slickymaster on 2013-10-17
> **luca-barazzuol said:**
> Same problem:

```
luke@u12:~$ sudo apt-get install debconf --reinstall
[sudo] password for luke: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.8.0-29-generic linux-image-extra-3.8.0-29-generic python-central
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 33 not upgraded.
9 not fully installed or removed.
Need to get 149 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://it.archive.ubuntu.com/ubuntu/ raring/main debconf all 1.5.49ubuntu1 [149 kB]
Fetched 149 kB in 0s (318 kB/s)
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
[SIZE=3][COLOR=#ff0000]debconf: DbDriver "config": mkdir :No such file or directory[/COLOR][/SIZE]
Setting up tzdata (2013g-0ubuntu0.13.04) ...
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 44, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in -e at /usr/share/perl5/Debconf/DbDriver/File.pm line 46, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value in pattern match (m//) at /usr/share/perl5/Debconf/DbDriver/File.pm line 47, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in -d at /usr/share/perl5/Debconf/DbDriver/File.pm line 48, <DEBCONF_CONFIG> chunk 3.
Use of uninitialized value $directory in concatenation (.) or string at /usr/share/perl5/Debconf/DbDriver/File.pm line 49, <DEBCONF_CONFIG> chunk 3.
[SIZE=3][COLOR=#ff0000]debconf: DbDriver "config": mkdir :No such file or directory[/COLOR][/SIZE]
dpkg: error processing tzdata (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

debconf might be missing it's directory in **/var/cach**. Let's us confirm whether it's there or not. Please post the output of```
ls /var/cache/
```

---

### Post by luca-barazzuol on 2013-10-17
```
luke@u12:~$ ls /var/cache/
apt  apt-xapian-index  cracklib  cups  fontconfig  jockey  ldconfig  lightdm  man  samba


```

---

### Post by luca-barazzuol on 2013-10-17
I think I solved. Following your advise I created the dir /var/cache/debconf and now the update process runs well.

Thanks

LuKe

---

### Post by slickymaster on 2013-10-17
Glad you fix it.
Yes. Once we confirmed that there was no **debconf** in **/var/cache**, all it was needed was to create it by issuing the command at a terminal window:```
sudo mkdir /var/cache/debconf
```

---

