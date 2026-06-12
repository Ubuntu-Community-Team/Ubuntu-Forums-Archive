---
title: "Ubuntu 6.06 Not updating"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by muz1 on 2006-10-10
Hey all groovy linux peoples.
Glad to once again be in your awesome company.

I am running Ubuntu 6.06. Aint it awesome. So basically it tells me that I have 77 updates waiting and it scans my system to check and stops there when I click the update button. I think I am having duplicate repositories but maybe not. I was thinking that maybe if I go back to the original set of repositories it may fix the problem.

Any thoughts, suggestions, tall black coffees greatly appreciated.

Cheers
muz

---

### Post by Jussi Kukkonen on 2006-10-10
Duplicates shouldn't matter. Could you do a
> sudo apt-get update
sudo apt-get upgrade
on the command line and paste the output here?

---

### Post by muz1 on 2006-10-10
> **Jussi Kukkonen said:**
> Duplicates shouldn't matter. Could you do a

on the command line and paste the output here?

Hey Jussi.
Thanks for offering assistance.
I did  waht oyu said and it ca==gave me the following.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [189B]           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release                                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release                        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages                          
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages                    
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release [30.9kB]              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Sources                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages            
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages [74.1kB]        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Sources               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Sources             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages              
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages [6446B]   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources [13.3kB]         
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources [960B]     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [29.8kB]    
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2789B]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [3874B]     
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources [520B]    
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages [2789B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [29.8kB]   
Fetched 195kB in 22s (8744B/s)                                                 
Reading package lists... Done
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/multiverse Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper-updates_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_dapper-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

Hope this helps.
Cheers
muz

---

### Post by dannyboy79 on 2006-10-10
just paste the output of cat /etc/apt/sources.list. then i'll tel you what you should remove and what you should keep. i think the file is in /etc/apt/. if it's not, do a sudo find / -name source* and whatever it returns, then do a cat on that locations and file. your sources.list file is what contains the repos it is suppose to look at for updates etc.

well forget that, you should be able to figure this out yourself, just do a cp /etc/apt/sources.list /etc/apt/sources.list-backup

that makes a backup of the file.
then do a 
sudo gedit /etc/apt/sources.list
once you're inside gedit and hte file, just look for what the output told you were duplicates and delete that entire line. that should do  it. then do the sudo aptitude update and sudo aptitude upgrade again and you'll be set. i use aptitude because it keeps better track of dependencies than apt-get does.

---

### Post by muz1 on 2006-10-12
Hey dannyboy79.
Thanks heaps for your insight.

I found thisplace online that generated source.list files so I went through it and it ourputted some ource repositrories.
I put them in abut what I am getting after trying to do an manual update via console is (when hovering on the orange icon to tell yo uthat there are updtes). "An error occured. Please run package manager from the right click menyu or apt-get on a term,ainal to see waht is wrong. The error message was: 'Error : BrokenCount>0'

If it is of some use, It stopped while trying to update Clam AV and told me that there was a missing linkor support file. I tried to go into advanced and see  what is wrong but it just went dumb on me and after asking me for the password, just did nothing.

Strange things are afoot at circle K!!!!!

Cheers and propz
muz

---

### Post by muz1 on 2006-10-12
sudo apt-get install -f

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  clamav-freshclam
The following packages will be upgraded:
  clamav-freshclam
1 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
55 not fully installed or removed.
Need to get 0B/4297kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 126226 files and directories currently installed.)
Preparing to replace clamav-freshclam 0.88.2-1ubuntu1 (using .../clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb) ...
 * Stopping ClamAV virus database updater freshclam                      [ ok ] 
Unpacking replacement clamav-freshclam ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/clamav-freshclam/examples/daily.cvd')
Errors were encountered while processing:
 /var/cache/apt/archives/clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas???
Cheers

muz

---

### Post by dannyboy79 on 2006-10-12
> **muz1 said:**
> sudo apt-get install -f

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  clamav-freshclam
The following packages will be upgraded:
  clamav-freshclam
1 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
55 not fully installed or removed.
Need to get 0B/4297kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 126226 files and directories currently installed.)
Preparing to replace clamav-freshclam 0.88.2-1ubuntu1 (using .../clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb) ...
 * Stopping ClamAV virus database updater freshclam                      [ ok ] 
Unpacking replacement clamav-freshclam ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/clamav-freshclam/examples/daily.cvd')
Errors were encountered while processing:
 /var/cache/apt/archives/clamav-freshclam_0.88.2-1ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Any ideas???
Cheers

muz

BEFORE DOING ANYTHING READ THE WHOLE THING.

Well, it's not a good idea to go off and start adding repo's to your sources.list if they are not a well known repo. i myself only use the official dapper repos and have added the repo for opera and realplayer as well as the one for compiz and xgl but other than that nothing else. this is what can happen! did you ever back up your sources.list like i suggested? if so, make a backup of this new one just in case by doing cp /etc/apt/sources.list /etc/apt/sources.list-inetgen    (meaning internet generated)  once you do that, let's overwrite the current sources.list with the backup you made before (which hopefully is the one the stock one that came with dapper. that is done by doing mv /etc/apt/sources.list-backup /etc/apt/sources.list  (or whatever the name of the backup file was). once that is done, go in it and make sure that the multiverse and universe, security, and dapper update repos are all UNcommented. then let's run a sudo aptitude update and then a sudo aptitude upgrade because it appears that you never did a update or upgrade after installing because of this error, 55 not fully installed or removed. this is because the iso only has the base required packages of dapper and then when you install, they want you to do a upgrade after uncommenting your repos so that you're system gets all up to date. this is so that they don't have a 4.5gb iso file like knoppix does. anyway, once your system is all updated and upgraded then lets start installing stuff and whatnot.  also, prior to doing any updating or whatnot, i would suggest you do a complete removal of any programs that you tried installing and had problems with. like clamav-freshclam or whatever the package name was. if you had clamav installed for awhile and hav tons of rules setup and whatnot, you should gogle how you would be able to savbe your setting and whatnot prior to doing a complete removal. it probably has something to do with saving the hidden folder in your home directory named whatever the package is, maybe somwething like /home/username/.clamav.  The possible reason for errors is because if you add repos that contain a slightly different clam package than the real dapper package then you'll get conflicts and broken packages.  post back if you need more help.

---

