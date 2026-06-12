---
title: "Upgrade problem, apt-get update leads to error message: libapt-pkg.so.4.12: file too"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by Lyfang on 2012-07-08
Hi, want to finding a way to update Lubuntu 12.04 with apt. apt-get update leads to error message: libapt-pkg.so.4.12: file too short. I'm running Lubuntu 12.04 from a DELTACO USB SATA/IDE adapter kit from an USB port. I have tried to repair the file system with the fsck tool. I know that running the ext4 file system without a journal can cause problems. Other than that the system works very well.

From Terminal:
```
dmesg | grep EXT4
```
[    3.033062] EXT4-fs (sdb1): mounted filesystem without journal. Opts: (null)
[    9.255690] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro

Update from Terminal:
```
sudo apt-get update
``` 
apt-get: error while loading shared libraries: /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12: file too short

```
sudo apt-get install <package>
```
apt-get: error while loading shared libraries: /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12: file too short

```
sudo synaptic
```
synaptic: error while loading shared libraries: /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12: file too short

```
sudo update-manager
```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 33, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 39, in <module>
    import apt_pkg
ImportError: /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12: fil för kort
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 64, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 20, in <module>
    import apport.fileutils
  File "/usr/lib/python2.7/dist-packages/apport/fileutils.py", line 22, in <module>
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.7/dist-packages/apport/packaging_impl.py", line 20, in <module>
    import apt
  File "/usr/lib/python2.7/dist-packages/apt/__init__.py", line 21, in <module>
    import apt_pkg
ImportError: /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12: fil för kort

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 33, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.7/dist-packages/UpdateManager/UpdateManager.py", line 39, in <module>
    import apt_pkg
ImportError: /usr/lib/i386-linux-gnu/libapt-pkg.so.4.12: fil för kort

"fil för kort" which means file too short in Swedish.

I also got: "Ett problem inträffade vid kontroll av uppdateringar." which means: A problem occurred when checking for updates.

---

### Post by Lyfang on 2012-07-08
Running fsck & e2fsck from Debian 7 "Wheezy" testing, output in Swedish:
```
root@debian:/# fsck /dev/sdc1
```
fsck från util-linux 2.20.1
e2fsck 1.42.4 (12-Jun-2012)
/dev/sdc1 var inte fläckfritt avmonterat, kontroll framtvingad.
Pass 1: Kontrollerar inoder, block och storlekar
Pass 2: Kontrollerar katalogstruktur
Pass 3: Kontrollerar katalogförbindelser
Pass 4: Kontrollerar referensräknare
Pass 5: Kontrollerar gruppsammanfattningsinformation
/dev/sdc1: 157422/5431296 filer (0.2% ej sammanhängande), 1632724/21717248 block

```
root@debian:/# e2fsck -f /dev/sdc1
```
e2fsck 1.42.4 (12-Jun-2012)
Pass 1: Kontrollerar inoder, block och storlekar
Pass 2: Kontrollerar katalogstruktur
Pass 3: Kontrollerar katalogförbindelser
Pass 4: Kontrollerar referensräknare
Pass 5: Kontrollerar gruppsammanfattningsinformation
/dev/sdc1: 157422/5431296 filer (0.2% ej sammanhängande), 1632724/21717248 block

---

### Post by Lyfang on 2012-07-08
Running from Terminal in Lubuntu 12.04, output in Swedish:
```
sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10_i386.deb
dpkg: fel: läser paketinfofilen "/var/lib/dpkg/available": Är en katalog
```

Source: [http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/libapt-pkg4.12_0.8.16~exp12ubuntu10_i386.deb/download/](http://pkgs.org/ubuntu-12.04/ubuntu-main-i386/libapt-pkg4.12_0.8.16~exp12ubuntu10_i386.deb/download/)

```
sudo dpkg -i libapt-pkg4.12_0.8.16~exp12ubuntu10.2_i386.deb
dpkg: fel: läser paketinfofilen "/var/lib/dpkg/available": Är en katalog
```

Source: [http://packages.ubuntu.com/sv/precise/i386/libapt-pkg4.12/download](http://packages.ubuntu.com/sv/precise/i386/libapt-pkg4.12/download)

---

### Post by Lyfang on 2012-07-08
[SOLVED] Extract libapt-pkg4.12_0.8.16~exp12ubuntu10.2_i386.deb with File Roller. Backup all files mentioned with the cp command. In my case only libapt-pkg.so.4.12.

Or locate files with PCManFM as a superuser to backup file(s) and backup file(s):
```
gksudo pcmanfm
```

Copy both libapt-pkg.so.4.12 & libapt-pkg.so.4.12.0 to the directory /usr/lib/i386-linux-gnu i.e.:
/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12
/usr/lib/i386-linux-gnu/libapt-pkg.so.4.12.0

```
sudo apt-get update 
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Läs:1 [http://repository.spotify.com](http://repository.spotify.com) stable InRelease [2 979 B]                 
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise InRelease                             
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Läs:2 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports InRelease                   
Fel [http://repository.spotify.com](http://repository.spotify.com) stable InRelease                             
  
Läs:3 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise Release.gpg [198 B]                 
Bra [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Läs:4 [http://dl.google.com](http://dl.google.com) stable Release [1 347 B]                            
Läs:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Läs:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Läs:7 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Bra [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Läs:8 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Läs:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49,6 kB]            
Läs:10 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1 237 B]                
Läs:11 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise Release [49,6 kB]                  
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Bra [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Bra [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Läs:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [22,5 kB]      
Läs:13 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates Release [49,6 kB]          
Läs:14 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports Release [49,6 kB]        
Läs:15 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/main Sources [934 kB]              
Läs:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Läs:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [7 832 B]  
Läs:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]  
Läs:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [70,2 kB]
Läs:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Läs:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [19,0 kB]
Läs:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1 394 B]
Bra [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Bra [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Bra [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Bra [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Läs:23 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/restricted Sources [5 470 B]       
Läs:24 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/universe Sources [5 019 kB]        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-sv_SE             
Bra [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Bra [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Bra [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-sv                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-sv_SE                    
Bra [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-sv_SE                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-sv                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-sv                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Läs:25 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Läs:26 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/main i386 Packages [1 274 kB]
Läs:27 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/restricted i386 Packages [8 431 B]
Läs:28 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/universe i386 Packages [4 796 kB]
Läs:29 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/main TranslationIndex                 
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/multiverse TranslationIndex           
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/restricted TranslationIndex           
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/universe TranslationIndex             
Läs:30 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/main Sources [124 kB]      
Läs:31 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/restricted Sources [1 379 B]
Läs:32 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/universe Sources [30,6 kB] 
Läs:33 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/multiverse Sources [1 058 B]
Läs:34 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/main i386 Packages [314 kB]
Läs:35 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/restricted i386 Packages [2 439 B]
Läs:36 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/universe i386 Packages [85,7 kB]
Läs:37 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2 047 B]
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/main TranslationIndex         
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Läs:38 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/main Sources [1 845 B]   
Läs:39 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Läs:40 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/universe Sources [11,1 kB]
Läs:41 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/multiverse Sources [1 383 B]
Läs:42 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/main i386 Packages [1 271 B]
Läs:43 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Läs:44 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/universe i386 Packages [9 703 B]
Läs:45 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/main TranslationIndex       
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/main Translation-sv                   
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/main Translation-en                   
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/multiverse Translation-sv             
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/multiverse Translation-en             
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/restricted Translation-sv             
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/restricted Translation-en             
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/universe Translation-sv               
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise/universe Translation-en               
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/main Translation-en           
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/restricted Translation-en     
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-updates/universe Translation-en       
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/main Translation-en         
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/restricted Translation-en   
Bra [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) precise-backports/universe Translation-en     
Hämtade 13,2 MB på 23s (564 kB/s)                                              
Läser paketlistor... Färdig
W: Ett fel inträffade vid verifiering av signaturen. Förrådet har inte uppdaterats och de tidigare indexfilerna kommer att användas. GPG-fel: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: Följande signaturer kunde inte verifieras för att den öppna nyckeln inte är tillgänglig: NO_PUBKEY 082CCEDF94558F59

W: Misslyckades med att hämta [http://repository.spotify.com/dists/stable/InRelease](http://repository.spotify.com/dists/stable/InRelease)  

W: Några indexfiler gick inte att hämta. De kommer att ignoreras eller så används de gamla istället.
```

The apt-get command now works great!

---

### Post by Lyfang on 2012-07-08
The apt-get command still works great! However Update Manager seems to have a problem but still manages to update successfully (including a Linux kernel install & a restart also successful):

```
Paketåtgärden misslyckades


Installationen eller borttagningen av ett programpaket misslyckades.

installArchives() failed: 
Plockar ut mallar frn paketen: 36%%
Plockar ut mallar frn paketen: 72%%
Plockar ut mallar frn paketen: 100%%
Frkonfigurerar paket ...
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan apparmor.
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan foomatic-filters.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN8> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN8> line 3.
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN8> line 3.

Plockar ut mallar frn paketen: 36%%
Plockar ut mallar frn paketen: 72%%
Plockar ut mallar frn paketen: 100%%
Frkonfigurerar paket ...
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan apparmor.
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan foomatic-filters.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN8> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN8> line 3.
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN8> line 3.

Plockar ut mallar frn paketen: 36%%
Plockar ut mallar frn paketen: 72%%
Plockar ut mallar frn paketen: 100%%
Frkonfigurerar paket ...
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan apparmor.
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan foomatic-filters.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN3> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN3> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN8> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN8> line 3.
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN8> line 3.
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 144706 files and directories currently installed.)
Preparing to replace cron 3.0pl1-120ubuntu3 (using .../cron_3.0pl1-120ubuntu4_i386.deb) ...
cron stop/waiting
Unpacking replacement cron ...
Preparing to replace libapt-inst1.4 0.8.16~exp12ubuntu10 (using .../libapt-inst1.4_0.8.16~exp12ubuntu10.2_i386.deb) ...
Unpacking replacement libapt-inst1.4 ...
Preparing to replace ntpdate 1:4.2.6.p3+dfsg-1ubuntu3 (using .../ntpdate_1%%3a4.2.6.p3+dfsg-1ubuntu3.1_i386.deb) ...
Unpacking replacement ntpdate ...
Preparing to replace libglib2.0-data 2.32.1-0ubuntu2 (using .../libglib2.0-data_2.32.3-0ubuntu1_all.deb) ...
Unpacking replacement libglib2.0-data ...
Preparing to replace libglib2.0-bin 2.32.1-0ubuntu2 (using .../libglib2.0-bin_2.32.3-0ubuntu1_i386.deb) ...
Unpacking replacement libglib2.0-bin ...
Preparing to replace libglib2.0-0 2.32.1-0ubuntu2 (using .../libglib2.0-0_2.32.3-0ubuntu1_i386.deb) ...
Unpacking replacement libglib2.0-0 ...
Preparing to replace apparmor 2.7.102-0ubuntu3 (using .../apparmor_2.7.102-0ubuntu3.1_i386.deb) ...
Unpacking replacement apparmor ...
Preparing to replace libgnutls26 2.12.14-5ubuntu3 (using .../libgnutls26_2.12.14-5ubuntu3.1_i386.deb) ...
Unpacking replacement libgnutls26 ...
Preparing to replace foomatic-filters 4.0.15-0ubuntu1 (using .../foomatic-filters_4.0.16-0ubuntu0.1_i386.deb) ...
Unpacking replacement foomatic-filters ...
Preparing to replace libcairo2 1.10.2-6.1ubuntu2 (using .../libcairo2_1.10.2-6.1ubuntu3_i386.deb) ...
Unpacking replacement libcairo2 ...
Preparing to replace libpango1.0-0 1.30.0-0ubuntu2 (using .../libpango1.0-0_1.30.0-0ubuntu3_i386.deb) ...
Unpacking replacement libpango1.0-0 ...
Preparing to replace google-chrome-stable 19.0.1084.52-r138391 (using .../google-chrome-stable_20.0.1132.47-r144678_i386.deb) ...
Unpacking replacement google-chrome-stable ...
Preparing to replace language-pack-en 1:12.04+20120508 (using .../language-pack-en_1%%3a12.04+20120618_all.deb) ...
Unpacking replacement language-pack-en ...
Replacing files in old package language-pack-en-base ...
Preparing to replace language-pack-gnome-en 1:12.04+20120508 (using .../language-pack-gnome-en_1%%3a12.04+20120618_all.deb) ...
Unpacking replacement language-pack-gnome-en ...
Replacing files in old package language-pack-gnome-en-base ...
Preparing to replace libswscale2 4:0.8.1-0ubuntu1 (using .../libswscale2_4%%3a0.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libswscale2 ...
Preparing to replace libpostproc52 4:0.8.1-0ubuntu1 (using .../libpostproc52_4%%3a0.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libpostproc52 ...
Preparing to replace libavformat53 4:0.8.1-0ubuntu1 (using .../libavformat53_4%%3a0.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libavformat53 ...
Preparing to replace libavcodec53 4:0.8.1-0ubuntu1 (using .../libavcodec53_4%%3a0.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libavcodec53 ...
Preparing to replace libavutil51 4:0.8.1-0ubuntu1 (using .../libavutil51_4%%3a0.8.3-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libavutil51 ...
Preparing to replace libcairo-gobject2 1.10.2-6.1ubuntu2 (using .../libcairo-gobject2_1.10.2-6.1ubuntu3_i386.deb) ...
Unpacking replacement libcairo-gobject2 ...
Preparing to replace libdbusmenu-glib4 0.6.1-0ubuntu3 (using .../libdbusmenu-glib4_0.6.2-0ubuntu0.1_i386.deb) ...
Unpacking replacement libdbusmenu-glib4 ...
Preparing to replace libdbusmenu-gtk3-4 0.6.1-0ubuntu3 (using .../libdbusmenu-gtk3-4_0.6.2-0ubuntu0.1_i386.deb) ...
Unpacking replacement libdbusmenu-gtk3-4 ...
Preparing to replace libgtk-3-bin 3.4.2-0ubuntu0.2 (using .../libgtk-3-bin_3.4.2-0ubuntu0.3_i386.deb) ...
Leaving 'diversion of /usr/sbin/update-icon-caches to /usr/sbin/update-icon-caches.gtk2 by libgtk-3-bin'
Leaving 'diversion of /usr/share/man/man8/update-icon-caches.8.gz to /usr/share/man/man8/update-icon-caches.gtk2.8.gz by libgtk-3-bin'
Unpacking replacement libgtk-3-bin ...
Preparing to replace libgail-3-0 3.4.2-0ubuntu0.2 (using .../libgail-3-0_3.4.2-0ubuntu0.3_i386.deb) ...
Unpacking replacement libgail-3-0 ...
Preparing to replace libgtk-3-0 3.4.2-0ubuntu0.2 (using .../libgtk-3-0_3.4.2-0ubuntu0.3_i386.deb) ...
Unpacking replacement libgtk-3-0 ...
Preparing to replace libgtk-3-common 3.4.2-0ubuntu0.2 (using .../libgtk-3-common_3.4.2-0ubuntu0.3_all.deb) ...
Unpacking replacement libgtk-3-common ...
Preparing to replace shared-mime-info 1.0-0ubuntu4 (using .../shared-mime-info_1.0-0ubuntu4.1_i386.deb) ...
Unpacking replacement shared-mime-info ...
Preparing to replace libglade2-0 1:2.6.4-1ubuntu1 (using .../libglade2-0_1%%3a2.6.4-1ubuntu1.1_i386.deb) ...
Unpacking replacement libglade2-0 ...
Preparing to replace libgutenprint2 5.2.8~pre1-0ubuntu2 (using .../libgutenprint2_5.2.8~pre1-0ubuntu2.1_i386.deb) ...
Unpacking replacement libgutenprint2 ...
Preparing to replace libmtp-common 1.1.3-1 (using .../libmtp-common_1.1.3-1ubuntu0.1_all.deb) ...
Unpacking replacement libmtp-common ...
Preparing to replace libmtp9 1.1.3-1 (using .../libmtp9_1.1.3-1ubuntu0.1_i386.deb) ...
Unpacking replacement libmtp9 ...
Preparing to replace mysql-common 5.5.22-0ubuntu1 (using .../mysql-common_5.5.24-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient18 5.5.22-0ubuntu1 (using .../libmysqlclient18_5.5.24-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement libmysqlclient18 ...
Preparing to replace libpulse0 1:1.1-0ubuntu15 (using .../libpulse0_1%%3a1.1-0ubuntu15.1_i386.deb) ...
Unpacking replacement libpulse0 ...
Preparing to replace libpulse-mainloop-glib0 1:1.1-0ubuntu15 (using .../libpulse-mainloop-glib0_1%%3a1.1-0ubuntu15.1_i386.deb) ...
Unpacking replacement libpulse-mainloop-glib0 ...
Preparing to replace libtiff4 3.9.5-2ubuntu1 (using .../libtiff4_3.9.5-2ubuntu1.1_i386.deb) ...
Unpacking replacement libtiff4 ...
Preparing to replace libv4l-0 0.8.6-1ubuntu1 (using .../libv4l-0_0.8.6-1ubuntu2_i386.deb) ...
Unpacking replacement libv4l-0 ...
Preparing to replace libv4lconvert0 0.8.6-1ubuntu1 (using .../libv4lconvert0_0.8.6-1ubuntu2_i386.deb) ...
Unpacking replacement libv4lconvert0 ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.2 (using .../libwbclient0_2%%3a3.6.3-2ubuntu2.3_i386.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace libxkbfile1 1:1.0.7-1 (using .../libxkbfile1_1%%3a1.0.7-1ubuntu0.1_i386.deb) ...
Unpacking replacement libxkbfile1 ...
Selecting previously unselected package linux-image-3.2.0-26-generic.
Unpacking linux-image-3.2.0-26-generic (from .../linux-image-3.2.0-26-generic_3.2.0-26.41_i386.deb) ...
Done.
Selecting previously unselected package linux-image-3.2.0-26-generic-pae.
Unpacking linux-image-3.2.0-26-generic-pae (from .../linux-image-3.2.0-26-generic-pae_3.2.0-26.41_i386.deb) ...
Done.
Preparing to replace ntp 1:4.2.6.p3+dfsg-1ubuntu3 (using .../ntp_1%%3a4.2.6.p3+dfsg-1ubuntu3.1_i386.deb) ...
 * Stopping NTP server ntpd        
[ OK ]
Unpacking replacement ntp ...
Preparing to replace libsmbclient 2:3.6.3-2ubuntu2.2 (using .../libsmbclient_2%%3a3.6.3-2ubuntu2.3_i386.deb) ...
Unpacking replacement libsmbclient ...
Preparing to replace apt-utils 0.8.16~exp12ubuntu10 (using .../apt-utils_0.8.16~exp12ubuntu10.2_i386.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace isc-dhcp-client 4.1.ESV-R4-0ubuntu5 (using .../isc-dhcp-client_4.1.ESV-R4-0ubuntu5.1_i386.deb) ...
Unpacking replacement isc-dhcp-client ...
Preparing to replace isc-dhcp-common 4.1.ESV-R4-0ubuntu5 (using .../isc-dhcp-common_4.1.ESV-R4-0ubuntu5.1_i386.deb) ...
Unpacking replacement isc-dhcp-common ...
Preparing to replace sudo 1.8.3p1-1ubuntu3.2 (using .../sudo_1.8.3p1-1ubuntu3.3_i386.deb) ...
Unpacking replacement sudo ...
Preparing to replace accountsservice 0.6.15-2ubuntu9 (using .../accountsservice_0.6.15-2ubuntu9.1_i386.deb) ...
Unpacking replacement accountsservice ...
Preparing to replace libaccountsservice0 0.6.15-2ubuntu9 (using .../libaccountsservice0_0.6.15-2ubuntu9.1_i386.deb) ...
Unpacking replacement libaccountsservice0 ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10 (using .../apt-transport-https_0.8.16~exp12ubuntu10.2_i386.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace printer-driver-gutenprint 5.2.8~pre1-0ubuntu2 (using .../printer-driver-gutenprint_5.2.8~pre1-0ubuntu2.1_i386.deb) ...
Unpacking replacement printer-driver-gutenprint ...
Preparing to replace cups-driver-gutenprint 5.2.8~pre1-0ubuntu2 (using .../cups-driver-gutenprint_5.2.8~pre1-0ubuntu2.1_all.deb) ...
Unpacking replacement cups-driver-gutenprint ...
Preparing to replace desktop-file-utils 0.20-0ubuntu2 (using .../desktop-file-utils_0.20-0ubuntu3_i386.deb) ...
Unpacking replacement desktop-file-utils ...
Preparing to replace firefox-locale-en 12.0+build1-0ubuntu0.12.04.1 (using .../firefox-locale-en_13.0.1+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-sv 12.0+build1-0ubuntu0.12.04.1 (using .../firefox-locale-sv_13.0.1+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox-locale-sv ...
Preparing to replace gir1.2-pango-1.0 1.30.0-0ubuntu2 (using .../gir1.2-pango-1.0_1.30.0-0ubuntu3_i386.deb) ...
Unpacking replacement gir1.2-pango-1.0 ...
Preparing to replace gir1.2-gtk-3.0 3.4.2-0ubuntu0.2 (using .../gir1.2-gtk-3.0_3.4.2-0ubuntu0.3_i386.deb) ...
Unpacking replacement gir1.2-gtk-3.0 ...
Preparing to replace libgrip0 0.3.4-0ubuntu1 (using .../libgrip0_0.3.4-0ubuntu2~ubuntu12.04.1_i386.deb) ...
Unpacking replacement libgrip0 ...
Preparing to replace libnautilus-extension1a 1:3.4.2-0ubuntu1 (using .../libnautilus-extension1a_1%%3a3.4.2-0ubuntu3_i386.deb) ...
Unpacking replacement libnautilus-extension1a ...
Preparing to replace linux-generic 3.2.0.24.26 (using .../linux-generic_3.2.0.26.28_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 3.2.0.24.26 (using .../linux-image-generic_3.2.0.26.28_i386.deb) ...
Unpacking replacement linux-image-generic ...
Preparing to replace linux-generic-pae 3.2.0.24.26 (using .../linux-generic-pae_3.2.0.26.28_i386.deb) ...
Unpacking replacement linux-generic-pae ...
Preparing to replace linux-image-generic-pae 3.2.0.24.26 (using .../linux-image-generic-pae_3.2.0.26.28_i386.deb) ...
Unpacking replacement linux-image-generic-pae ...
Selecting previously unselected package linux-headers-3.2.0-26.
Unpacking linux-headers-3.2.0-26 (from .../linux-headers-3.2.0-26_3.2.0-26.41_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-26-generic.
Unpacking linux-headers-3.2.0-26-generic (from .../linux-headers-3.2.0-26-generic_3.2.0-26.41_i386.deb) ...
Selecting previously unselected package linux-headers-3.2.0-26-generic-pae.
Unpacking linux-headers-3.2.0-26-generic-pae (from .../linux-headers-3.2.0-26-generic-pae_3.2.0-26.41_i386.deb) ...
Preparing to replace linux-headers-generic 3.2.0.24.26 (using .../linux-headers-generic_3.2.0.26.28_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-headers-generic-pae 3.2.0.24.26 (using .../linux-headers-generic-pae_3.2.0.26.28_i386.deb) ...
Unpacking replacement linux-headers-generic-pae ...
Preparing to replace linux-libc-dev 3.2.0-25.40 (using .../linux-libc-dev_3.2.0-26.41_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace nautilus-data 1:3.4.2-0ubuntu1 (using .../nautilus-data_1%%3a3.4.2-0ubuntu3_all.deb) ...
Unpacking replacement nautilus-data ...
Preparing to replace python-cupshelpers 1.3.8+20120201-0ubuntu8 (using .../python-cupshelpers_1.3.8+20120201-0ubuntu8.1_all.deb) ...
Unpacking replacement python-cupshelpers ...
Preparing to replace system-config-printer-common 1.3.8+20120201-0ubuntu8 (using .../system-config-printer-common_1.3.8+20120201-0ubuntu8.1_all.deb) ...
Unpacking replacement system-config-printer-common ...
Preparing to replace system-config-printer-gnome 1.3.8+20120201-0ubuntu8 (using .../system-config-printer-gnome_1.3.8+20120201-0ubuntu8.1_all.deb) ...
Unpacking replacement system-config-printer-gnome ...
Preparing to replace virtualbox-qt 4.1.12-dfsg-2 (using .../virtualbox-qt_4.1.12-dfsg-2ubuntu0.1_i386.deb) ...
Unpacking replacement virtualbox-qt ...
Preparing to replace virtualbox 4.1.12-dfsg-2 (using .../virtualbox_4.1.12-dfsg-2ubuntu0.1_i386.deb) ...
Unpacking replacement virtualbox ...
Preparing to replace virtualbox-dkms 4.1.12-dfsg-2 (using .../virtualbox-dkms_4.1.12-dfsg-2ubuntu0.1_all.deb) ...

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.1.12
Kernel:  3.2.0-24-generic-pae (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-24-generic-pae/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.......

DKMS: uninstall completed.

------------------------------
Deleting module version: 4.1.12
completely from the DKMS tree.
------------------------------
Done.
Unpacking replacement virtualbox-dkms ...
Preparing to replace xserver-common 2:1.11.4-0ubuntu10.2 (using .../xserver-common_2%%3a1.11.4-0ubuntu10.3_all.deb) ...
Unpacking replacement xserver-common ...
Preparing to replace xserver-xorg-core 2:1.11.4-0ubuntu10.2 (using .../xserver-xorg-core_2%%3a1.11.4-0ubuntu10.3_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Preparing to replace xserver-xorg-input-evdev 1:2.7.0-0ubuntu1 (using .../xserver-xorg-input-evdev_1%%3a2.7.0-0ubuntu1.2_i386.deb) ...
Unpacking replacement xserver-xorg-input-evdev ...
Preparing to replace xserver-xorg-input-vmmouse 1:12.8.0-1 (using .../xserver-xorg-input-vmmouse_1%%3a12.9.0-0ubuntu0.1_i386.deb) ...
Unpacking replacement xserver-xorg-input-vmmouse ...
Preparing to replace lxkeymap 0.7.99+dfsg-0ubuntu1 (using .../lxkeymap_0.7.99+dfsg-0ubuntu1.1_all.deb) ...
Unpacking replacement lxkeymap ...
Preparing to replace spotify-client 1:0.8.3.278.g21c7566.632-1 (using .../spotify-client_1%%3a0.8.4.103.g9cb177b.260-1_i386.deb) ...
Unpacking replacement spotify-client ...
Processing triggers for man-db ...
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN7> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN7> line 2.
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for cups ...
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan cups.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 1.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 1.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 5.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 5.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 6.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 6.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 6.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 6.
Updating PPD files for gutenprint ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Setting up cron (3.0pl1-120ubuntu4) ...
Installing new version of config file /etc/default/cron ...
cron start/running, process 5773
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.2) ...
Setting up ntpdate (1:4.2.6.p3+dfsg-1ubuntu3.1) ...
Setting up libglib2.0-data (2.32.3-0ubuntu1) ...
Setting up libglib2.0-0 (2.32.3-0ubuntu1) ...
Setting up libglib2.0-bin (2.32.3-0ubuntu1) ...
Setting up apparmor (2.7.102-0ubuntu3.1) ...
Installing new version of config file /etc/apparmor.d/abstractions/ubuntu-email ...
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan apparmor.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 2.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 2.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 3.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 3.
 * Starting AppArmor profiles        Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd

[ OK ]
 * Reloading AppArmor profiles        Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd

[ OK ]
Setting up libgnutls26 (2.12.14-5ubuntu3.1) ...
Setting up foomatic-filters (4.0.16-0ubuntu0.1) ...
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan foomatic-filters.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 3.
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN2> line 3.
dpkg: error processing foomatic-filters (--configure):
 subprocess installed post-installation script returned error exit status 255
No apport report written because MaxReports is reached already
Setting up libcairo2 (1.10.2-6.1ubuntu3) ...
Setting up libpango1.0-0 (1.30.0-0ubuntu3) ...
Setting up google-chrome-stable (20.0.1132.47-r144678) ...
Setting up language-pack-en (1:12.04+20120618) ...
Setting up language-pack-gnome-en (1:12.04+20120618) ...
Setting up libavutil51 (4:0.8.3-0ubuntu0.12.04.1) ...
Setting up libswscale2 (4:0.8.3-0ubuntu0.12.04.1) ...
Setting up libpostproc52 (4:0.8.3-0ubuntu0.12.04.1) ...
Setting up libavcodec53 (4:0.8.3-0ubuntu0.12.04.1) ...
Setting up libavformat53 (4:0.8.3-0ubuntu0.12.04.1) ...
Setting up libcairo-gobject2 (1.10.2-6.1ubuntu3) ...
Setting up libdbusmenu-glib4 (0.6.2-0ubuntu0.1) ...
Setting up libdbusmenu-gtk3-4 (0.6.2-0ubuntu0.1) ...
Setting up libgtk-3-common (3.4.2-0ubuntu0.3) ...
Setting up shared-mime-info (1.0-0ubuntu4.1) ...
Setting up libgtk-3-0 (3.4.2-0ubuntu0.3) ...
Setting up libgtk-3-bin (3.4.2-0ubuntu0.3) ...
Setting up libgail-3-0 (3.4.2-0ubuntu0.3) ...
Setting up libglade2-0 (1:2.6.4-1ubuntu1.1) ...
Setting up libgutenprint2 (5.2.8~pre1-0ubuntu2.1) ...
Setting up libmtp-common (1.1.3-1ubuntu0.1) ...
Setting up libmtp9 (1.1.3-1ubuntu0.1) ...
Setting up mysql-common (5.5.24-0ubuntu0.12.04.1) ...
Setting up libmysqlclient18 (5.5.24-0ubuntu0.12.04.1) ...
Setting up libpulse0 (1:1.1-0ubuntu15.1) ...
Setting up libpulse-mainloop-glib0 (1:1.1-0ubuntu15.1) ...
Setting up libtiff4 (3.9.5-2ubuntu1.1) ...
Setting up libv4lconvert0 (0.8.6-1ubuntu2) ...
Setting up libv4l-0 (0.8.6-1ubuntu2) ...
Setting up libwbclient0 (2:3.6.3-2ubuntu2.3) ...
Setting up libxkbfile1 (1:1.0.7-1ubuntu0.1) ...
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-26-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-26-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Writing config for Windows 7 (loader) on /dev/sda1...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Debian GNU/Linux (wheezy/sid) on /dev/sda5
done
Setting up linux-image-3.2.0-26-generic-pae (3.2.0-26.41) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-26-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-26-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Writing config for Windows 7 (loader) on /dev/sda1...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-24-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Debian GNU/Linux (wheezy/sid) on /dev/sda5
done
Setting up ntp (1:4.2.6.p3+dfsg-1ubuntu3.1) ...
 * Starting NTP server ntpd        
[ OK ]
Setting up libsmbclient (2:3.6.3-2ubuntu2.3) ...
Setting up apt-utils (0.8.16~exp12ubuntu10.2) ...
Setting up isc-dhcp-common (4.1.ESV-R4-0ubuntu5.1) ...
Setting up isc-dhcp-client (4.1.ESV-R4-0ubuntu5.1) ...
Setting up sudo (1.8.3p1-1ubuntu3.3) ...
Installing new version of config file /etc/pam.d/sudo ...
Setting up libaccountsservice0 (0.6.15-2ubuntu9.1) ...
Setting up accountsservice (0.6.15-2ubuntu9.1) ...
Setting up apt-transport-https (0.8.16~exp12ubuntu10.2) ...
Setting up printer-driver-gutenprint (5.2.8~pre1-0ubuntu2.1) ...
Setting up cups-driver-gutenprint (5.2.8~pre1-0ubuntu2.1) ...
Setting up desktop-file-utils (0.20-0ubuntu3) ...

Configuration file `/etc/gnome/defaults.list'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** defaults.list (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/gnome/defaults.list ...
Setting up firefox-locale-en (13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-sv (13.0.1+build1-0ubuntu0.12.04.1) ...
Setting up gir1.2-pango-1.0 (1.30.0-0ubuntu3) ...
Setting up gir1.2-gtk-3.0 (3.4.2-0ubuntu0.3) ...
Setting up libgrip0 (0.3.4-0ubuntu2~ubuntu12.04.1) ...
Setting up libnautilus-extension1a (1:3.4.2-0ubuntu3) ...
Setting up linux-image-generic (3.2.0.26.28) ...
Setting up linux-generic (3.2.0.26.28) ...
Setting up linux-image-generic-pae (3.2.0.26.28) ...
Setting up linux-generic-pae (3.2.0.26.28) ...
Setting up linux-headers-3.2.0-26 (3.2.0-26.41) ...
Setting up linux-headers-3.2.0-26-generic (3.2.0-26.41) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic
Setting up linux-headers-3.2.0-26-generic-pae (3.2.0-26.41) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-26-generic-pae /boot/vmlinuz-3.2.0-26-generic-pae
Setting up linux-headers-generic (3.2.0.26.28) ...
Setting up linux-headers-generic-pae (3.2.0.26.28) ...
Setting up linux-libc-dev (3.2.0-26.41) ...
Setting up nautilus-data (1:3.4.2-0ubuntu3) ...
Setting up python-cupshelpers (1.3.8+20120201-0ubuntu8.1) ...
Setting up system-config-printer-common (1.3.8+20120201-0ubuntu8.1) ...
Setting up system-config-printer-gnome (1.3.8+20120201-0ubuntu8.1) ...
Setting up virtualbox (4.1.12-dfsg-2ubuntu0.1) ...
 * Stopping VirtualBox kernel modules        
[ OK ]
 * Starting VirtualBox kernel modules         * No suitable module for running kernel found

[fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Setting up xserver-common (2:1.11.4-0ubuntu10.3) ...
Setting up xserver-xorg-core (2:1.11.4-0ubuntu10.3) ...
Setting up xserver-xorg-input-evdev (1:2.7.0-0ubuntu1.2) ...
Setting up xserver-xorg-input-vmmouse (1:12.9.0-0ubuntu0.1) ...
Setting up lxkeymap (0.7.99+dfsg-0ubuntu1.1) ...
Setting up spotify-client (1:0.8.4.103.g9cb177b.260-1) ...
Processing triggers for python-central ...
Setting up virtualbox-qt (4.1.12-dfsg-2ubuntu0.1) ...
Setting up virtualbox-dkms (4.1.12-dfsg-2ubuntu0.1) ...
Loading new virtualbox-4.1.12 DKMS files...
Building for 3.2.0-24-generic-pae and 3.2.0-26-generic
Building initial module for 3.2.0-24-generic-pae
Done.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic-pae/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic-pae/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic-pae/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
Building initial module for 3.2.0-26-generic
Done.

vboxdrv:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic/updates/dkms/

depmod....

DKMS: install completed.
 * Stopping VirtualBox kernel modules        
[ OK ]
 * Starting VirtualBox kernel modules        
[ OK ]
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 foomatic-filters
Error in function: 
Setting up foomatic-filters (4.0.16-0ubuntu0.1) ...
debconf: varning: databasen kan vara trasig. Frsker reparera genom att lgga tillbaka den saknade frgan foomatic-filters.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN2> line 3.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN2> line 3.
Can't call method "description" on an undefined value at /usr/share/perl5/Debconf/Question.pm line 93, <GEN2> line 3.
dpkg: error processing foomatic-filters (--configure):
 subprocess installed post-installation script returned error exit status 255
```

---

### Post by Lyfang on 2012-07-08
Restoring backed up files after deleting, reminder: Is done at your own risk (as usual)!: [http://kmandla.wordpress.com/2007/04/01/damaged-varlibdpkgavailable/](http://kmandla.wordpress.com/2007/04/01/damaged-varlibdpkgavailable/)

```
gksudo pcmanfm 
```
Cannot create the folder 'available' in /var/lib/dpkg

It says "Skapa ny..." again & again. Creating a folder with a different name & attempting to rename the folder results in: "Målfilen finns".

---

### Post by Lyfang on 2012-07-10
> **Lyfang said:**
> Restoring backed up files after deleting, reminder: Is done at your own risk (as usual)!: [http://kmandla.wordpress.com/2007/04/01/damaged-varlibdpkgavailable/](http://kmandla.wordpress.com/2007/04/01/damaged-varlibdpkgavailable/)

```
gksudo pcmanfm 
```
Cannot create the folder 'available' in /var/lib/dpkg

It says "Skapa ny..." again & again. Creating a folder with a different name & attempting to rename the folder results in: "Målfilen finns".

USERNAME@USERNAME-lubuntu:~$ cd /var/lib/dpkg
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ ls
alternatives   available.oldBusted  diversions-old  parts         status-old
available      cmethopt             info            statoverride  triggers
available-old  diversions           lock            status        updates
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ sudo mkdir available
mkdir: kan inte skapa katalog ”available”: Filen existerar
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ cd available 
bash: cd: available: Inte en katalog
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ rm available
rm: ta bort skrivskyddad normal fil ”available”? 
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ ls
alternatives   available.oldBusted  diversions-old  parts         status-old
available      cmethopt             info            statoverride  triggers
available-old  diversions           lock            status        updates
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ rm available
rm: ta bort skrivskyddad normal fil ”available”? y
rm: kan inte ta bort ”available”: Åtkomst nekas
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ sudo rm available
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ ls
alternatives         cmethopt        info   statoverride  triggers
available-old        diversions      lock   status        updates
available.oldBusted  diversions-old  parts  status-old
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ sudo mkdir available 
USERNAME@USERNAME-lubuntu:/var/lib/dpkg$ ls
alternatives   available.oldBusted  diversions-old  parts         status-old
available      cmethopt             info            statoverride  triggers
available-old  diversions           lock            status        updates

USERNAME@USERNAME-lubuntu:~$ cd /var/lib/dpkg
USERNAME@USERNAME-lubuntu:/var/lib/dpkg/available$ ls
conffiles  control  md5sums  postinst  postrm  preinst

USERNAME@USERNAME-lubuntu:~$ sudo dpkg-reconfigure debconf
[sudo] password for USERNAME: 
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
/usr/sbin/dpkg-reconfigure: debconf är trasigt eller inte helt installerat
USERNAME@USERNAME-lubuntu:~$ sudo apt-get install debconf
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
debconf är redan den senaste versionen.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 4 att inte uppgradera.
2 är inte helt installerade eller borttagna.
Efter denna åtgärd kommer ytterligare 0 B utrymme användas på disken.
Vill du fortsätta [J/n]? j
Ställer in debconf (1.5.42ubuntu1) ...
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
debconf: varning: databasen kan vara trasig. Försöker reparera genom att lägga tillbaka den saknade frågan debconf.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 4.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 4.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 5.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 5.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 7.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 7.
Can't call method "i18n" on an undefined value at /usr/share/perl5/Debconf/Element/Noninteractive/Select.pm line 13, <GEN1> line 7.
dpkg: fel vid hantering av debconf (--configure):
 underprocessen installerade post-installation-skript gav felkod 255
dpkg: beroendeproblem förhindrar konfigurering av foomatic-filters:
 foomatic-filters är beroende av debconf (>= 0.5) | debconf-2.0, men:
  Paketet debconf har inte konfigurerats ännu.
  Paketet debconf-2.0 är ej installerat.
  Paketet debconf, som tillhandahåller debconf-2.0, har inte konfigurerats ännu.
dpkg: fel vid hantering av foomatic-filters (--configure):
 beroendeproblem - lämnar okonfigurerad
Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                           Fel uppstod vid hantering:
 debconf
 foomatic-filters
E: Sub-process /usr/bin/dpkg returned an error code (1)
USERNAME@USERNAME-lubuntu:~$ sudo apt-get install foomatic-filters 
Display all 38350 possibilities? (y or n)
USERNAME@USERNAME-lubuntu:~$ sudo apt-get install foomatic-filters 
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
foomatic-filters är redan den senaste versionen.
0 att uppgradera, 0 att nyinstallera, 0 att ta bort och 4 att inte uppgradera.
2 är inte helt installerade eller borttagna.
Efter denna åtgärd kommer ytterligare 0 B utrymme användas på disken.
Vill du fortsätta [J/n]? j
Ställer in debconf (1.5.42ubuntu1) ...
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39.
debconf: varning: databasen kan vara trasig. Försöker reparera genom att lägga tillbaka den saknade frågan debconf.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 4.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 4.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 5.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 5.
Use of uninitialized value $template in exists at /usr/share/perl5/Debconf/Template.pm line 81, <GEN1> line 7.
Use of uninitialized value $item in exists at /usr/share/perl5/Debconf/DbDriver/Cache.pm line 39, <GEN1> line 7.
Can't call method "i18n" on an undefined value at /usr/share/perl5/Debconf/Element/Noninteractive/Select.pm line 13, <GEN1> line 7.
dpkg: fel vid hantering av debconf (--configure):
 underprocessen installerade post-installation-skript gav felkod 255
dpkg: beroendeproblem förhindrar konfigurering av foomatic-filters:
 foomatic-filters är beroende av debconf (>= 0.5) | debconf-2.0, men:
  Paketet debconf har inte konfigurerats ännu.
  Paketet debconf-2.0 är ej installerat.
  Paketet debconf, som tillhandahåller debconf-2.0, har inte konfigurerats ännu.
dpkg: fel vid hantering av foomatic-filters (--configure):
 beroendeproblem - lämnar okonfigurerad
Ingen apport-rapport skrevs därför att felmeddelandet indikerar att det är ett efterföljande fel från ett tidigare problem.
                                           Fel uppstod vid hantering:
 debconf
 foomatic-filters
E: Sub-process /usr/bin/dpkg returned an error code (1)

See also: package debconf 1.5.42ubuntu1 failed to install/upgrade: underprocessen installerade post-installation-skript gav felkod 255 [https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/1023096](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/1023096)
package foomatic-filters 4.0.16-0ubuntu0.1 failed to install/upgrade: underprocessen installerade post-installation-skript gav felkod 255 [https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/1022398](https://bugs.launchpad.net/ubuntu/+source/debconf/+bug/1022398)

I will reinstall another Linux distribution for a less buggy experience than of Lubuntu 12.04 LTS. Why not Debian 7 "Wheezy" testing with LXDE? [http://ubuntuforums.org/showthread.php?t=2016082](http://ubuntuforums.org/showthread.php?t=2016082) or Debian 6 "squeeze" stable with GNOME 2.30?

---

### Post by Lyfang on 2012-07-15
> **Lyfang said:**
> I know that running the ext4 file system without a journal can cause problems.

[QUOTE=Ramesh Natarajan]When the system crashes, the possibility of file system corruption is less because of journaling.[/QUOTE]
Source: [http://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/](http://www.thegeekstuff.com/2011/05/ext2-ext3-ext4/)

Terminal output:
```
EXT-fs error (device sdc1): ext4 find entry:935: inode
```

---

### Post by Lyfang on 2012-10-09
If this were to occur again, is there a way to debug apt (or dpkg)?

---

### Post by Lyfang on 2012-10-18
ext4 file system without a journal: Maybe one should enable and run the built-in tune2fs that runs e2fsck on a scheduled basis and here is how: [Disk Check]("http://ubuntuforums.org/showthread.php?t=2072400") or check with Disk Utility (gnome-disk-utility) on a regular basis?

---

