---
title: "post-8.04 update manager freezes"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by jmirick on 2008-05-06
8.04 upgraded successfully, works fine, now some days later I get the update glyph and I run update manager, it finds about 20 updates (applications) and I say, update me.  At that point it just freezes solid, the box greys out and I don't get even the password-request box.  I have to use system manager to kill the task.

Machine is a Dell 4600 that's been running Ubuntu for quite a while; another box (Compaq) has been upgraded to 8.04 and updates fine.

Synaptic works fine so I wouldn't think it's the repos.

I've tried this several times of the day, no dice.

---

### Post by Pumalite on 2008-05-06
Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
Post the output.

---

### Post by jmirick on 2008-05-06
Here's what I got:

jrm@Ubuntu-mini:~$ sudo dpkg --configure -a
sudo: unable to resolve host Ubuntu-mini
[sudo] password for jrm: 

jrm@Ubuntu-mini:~$ sudo apt-get -f install
sudo: unable to resolve host Ubuntu-mini
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.

jrm@Ubuntu-mini:~$ sudo apt-get update
sudo: unable to resolve host Ubuntu-mini
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources              
58% [Connecting to us.archive.ubuntu.com (91.189.88.45)]                      
jrm@Ubuntu-mini:~$ 

And at this point it hung -- I terminated it, finally.  So it can't get to the archive.  But I can ping 91.189.88.45 and it gives normal responses, so I'm not sure what to do next.

---

### Post by Pumalite on 2008-05-06
Try again later.

---

### Post by jmirick on 2008-05-06
I will, although I've tried it a couple of times over several days and I get the same result -- but I have another machine that's updated in the meantime with no problem.

---

### Post by brown705 on 2008-05-06
I was having the same problem myself, but I just found the answer at the bottom of this thread:

[https://answers.launchpad.net/ubuntu/+question/29446](https://answers.launchpad.net/ubuntu/+question/29446)

For your reference, I'll paste the post with the fix from the launchpad.net forum here:

> SwissMike  said on 2008-04-18:

Problem solved.

Turns out that the localhost setting in /etc/hosts was incorrect. The fix is going to menu ' System', then 'Administration', then 'Network'. Select the tab Hosts, enter password in dialog box, then change the localhost name:

127.0.0.1 PCName.networkName

to

127.0.0.1 PCName

and save it. Done. Whole problem gone. Interestingly, Bug #195308 confirms the same problem. Hope this small issue gets fixed before the Apr 21 release as it was nasty while it lasted.

Greetings from Switzerland,
Mike.

Worked for me! \\:D/

Michael

---

### Post by jmirick on 2008-05-06
Well, presto, it worked, although my hosts file said

127.0.0.1  localhost

Which I changed to:

127.0.0.1  PCName

However, then, won't I now have difficulty resolving localhost?  Or should it be 127.0.0.1  localhost  PCName    ?

---

### Post by brown705 on 2008-05-06
> **jmirick said:**
> Well, presto, it worked, although my hosts file said

127.0.0.1  localhost

Which I changed to:

127.0.0.1  PCName

However, then, won't I now have difficulty resolving localhost?  Or should it be 127.0.0.1  localhost  PCName    ?

OK, now that I looked closer at my hosts file, I see I used to have two lines that looked like this:

127.0.0.1   localhost
127.0.1.1   PCNAME.NETWORKNAME

and I simply removed the ".NETWORKNAME" part.  Note the second line has a different IP address than the first.  You should probably put the localhost line back and try making the second line like mine.  

Michael

---

### Post by davester on 2008-05-07
I also was experiencing the freeze-up of the update manager on 8.04, changed the host name etc and voila - works like a charm.  Many thanks for the information.

---

### Post by jmirick on 2008-05-07
So, isn't this a bug? My hosts file now contains:

127.0.0.1  localhost   PCName
127.0.1.1  PCName.networkid

And this configuration allows updates as it should.  So it would appear that the "rule" is, no networkid on the localhost line?  I don't this this is right, I thought that 127.0.0.1 should completely define the machine.

So I can update, for which I thank everyone who contributed, but it still seems like this is not as it should be.

---

### Post by brown705 on 2008-05-07
> **jmirick said:**
> So, isn't this a bug? My hosts file now contains:

127.0.0.1  localhost   PCName
127.0.1.1  PCName.networkid

And this configuration allows updates as it should.  So it would appear that the "rule" is, no networkid on the localhost line?  I don't this this is right, I thought that 127.0.0.1 should completely define the machine.

So I can update, for which I thank everyone who contributed, but it still seems like this is not as it should be.

I found this today:
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/188957](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/188957)

which also leads to this thread here:
[http://ubuntuforums.org/showthread.php?t=613521&page=2](http://ubuntuforums.org/showthread.php?t=613521&page=2)

that comes up with the same solution I found elsewhere.  

Michael

---

### Post by jmirick on 2008-05-08
Obviously an issue and it's fixed for me, but the second thread noted:

> I now have
127.0.0.1 localhost
127.0.1.1 laptop-hardy
etc.

PROBLEM SOLVED!

Thank you everyone for your help - you pointed me into the problem area. The line in question WAS required but should not have had .mshome on the end

But that's a little different from my solution, which has 127.0.0.1 with localhost aliased with the PCName, and then 127.0.1.1 seems to take the network ID in it just fine.  Oh well, maybe there's some interaction with the network ID parameter which is specified elsewhere!

Hope all this is useful to others, too . . .

jim

---

### Post by nxfs on 2008-05-08
did some messing around and got my that hostname changed to something like

myservername 127.0.0.1

and couldn't get update to work, but thanks to you guys, it now works

....now back to the pesky task of SSL...

---

### Post by Skip Da Shu on 2008-05-09
> **jmirick said:**
> So, isn't this a bug? My hosts file now contains:

127.0.0.1  localhost   PCName
127.0.1.1  PCName.networkid

And this configuration allows updates as it should.  So it would appear that the "rule" is, no networkid on the localhost line?  I don't this this is right, I thought that 127.0.0.1 should completely define the machine.

So I can update, for which I thank everyone who contributed, but it still seems like this is not as it should be.

Unencumbered by any actual knowledge...

All my machines are set up with:

127.0.0.1 PCName localhost
127.0.1.1 PCName
ur.192.168.ip.addr PCName

3rd line should **only** be added if you are using a static IP address.

This will allow 'PCName' to showup instead of 'localhost' in a couple places where I had been seeing "localhost".

---

### Post by lynns on 2008-05-10
Thanks! I had the problem with the 8.04 LTS release. This fixed it!

---

### Post by Evanmakundi on 2008-05-14
> **Pumalite said:**
> Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
Post the output.
Hi why dont you try the following commands.

sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude upgrade

They worked on my laptop. they might work on yours as well

Let me know if you are sorted out.

Cheers

---

### Post by truxntrax on 2008-05-17
Worked for me too - thank you all.

T

---

### Post by bnhrobotics on 2008-06-08
Worked for me too! Thanks!

---

### Post by carib909 on 2008-06-11
> **Pumalite said:**
> Try:
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
Post the output.

I have the same problem with the update manager freezing. I entered your commands and got the following results. Can you please explain waht each command does?


evan@ubuntu:~$ sudo dpkg --configure -a
sudo: unable to resolve host ubuntu
[sudo] password for evan: 
evan@ubuntu:~$ sudo dpkg --configure -a
sudo: unable to resolve host ubuntu
evan@ubuntu:~$ sudo apt-get -f install
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-17-generic linux-headers-2.6.24-17
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
evan@ubuntu:~$ sudo apt-get update
sudo: unable to resolve host ubuntu
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy Release.gpg
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/main Translation-en_US
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy Release
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/main Packages
Ign cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/restricted Packages
Err cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg                             
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
W: Failed to fetch cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu-Server 8.04 _Hardy Heron_ - Release i386 (20080423.2)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
evan@ubuntu:~$ sudo apt-get upgrade
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apache2 apache2-mpm-prefork apache2-utils apache2.2-common cpp firefox
  firefox-3.0 firefox-3.0-gnome-support firefox-gnome-support gcc gnome-about
  gnome-desktop-data initramfs-tools libgksu2-0 libgnome-desktop-2
  libldap-2.4-2 liblircclient0 libnspr4-0d libnss3-1d libntfs-3g23
  libpam-smbpass libparted1.7-1 libsmbclient ntfs-3g parted pciutils
  python-launchpad-bugs samba samba-common samba-doc smbclient smbfs tzdata
  tzdata-java ufw winbind xserver-xorg-video-cirrus xulrunner-1.9
  xulrunner-1.9-gnome-support yelp
40 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.7MB of archives.
After this operation, 328kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libntfs-3g23 1:1.2216-1ubuntu2 [101kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main ntfs-3g 1:1.2216-1ubuntu2 [29.4kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe tzdata-java 2008c-1ubuntu0.8.04 [140kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main tzdata 2008c-1ubuntu0.8.04 [656kB]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main initramfs-tools 0.85eubuntu39.1 [66.6kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libldap-2.4-2 2.4.7-6ubuntu4.2 [181kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main pciutils 1:2.2.4-1.1ubuntu4 [234kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main cpp 4:4.2.3-1ubuntu6 [34.6kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libparted1.7-1 1.7.1-5.1ubuntu9.1 [196kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main parted 1.7.1-5.1ubuntu9.1 [56.8kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main ufw 0.16.2.1 [23.0kB]   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2-utils 2.2.8-1ubuntu0.2 [139kB]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2-mpm-prefork 2.2.8-1ubuntu0.2 [230kB]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2.2-common 2.2.8-1ubuntu0.2 [753kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main apache2 2.2.8-1ubuntu0.2 [44.4kB]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libnspr4-0d 4.7.1+1.9-0ubuntu0.8.04.1 [121kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main yelp 2.22.1-0ubuntu2.8.04.1 [347kB]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libnss3-1d 3.12.0.2+1.9-0ubuntu0.8.04.1 [1016kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main xulrunner-1.9-gnome-support 1.9~rc1+nobinonly-0ubuntu1~8.04.2 [38.5kB]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox-3.0-gnome-support 3.0~rc1+nobinonly-0ubuntu0.8.04.1 [25.7kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox-3.0 3.0~rc1+nobinonly-0ubuntu0.8.04.1 [1063kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main xulrunner-1.9 1.9~rc1+nobinonly-0ubuntu1~8.04.2 [7741kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox 3.0~rc1+nobinonly-0ubuntu0.8.04.1 [65.4kB]
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main firefox-gnome-support 3.0~rc1+nobinonly-0ubuntu0.8.04.1 [65.3kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gcc 4:4.2.3-1ubuntu6 [5096B]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gnome-about 1:2.22.2-0ubuntu3 [160kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main gnome-desktop-data 1:2.22.2-0ubuntu3 [574kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libgksu2-0 2.0.5-1ubuntu5.1 [56.1kB]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libgnome-desktop-2 1:2.22.2-0ubuntu3 [94.8kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main python-launchpad-bugs 0.2.30.1 [63.0kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main winbind 3.0.28a-1ubuntu4.1 [2247kB]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main smbfs 3.0.28a-1ubuntu4.1 [93.5kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main smbclient 3.0.28a-1ubuntu4.1 [4862kB]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libpam-smbpass 3.0.28a-1ubuntu4.1 [471kB]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main samba 3.0.28a-1ubuntu4.1 [3839kB]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main samba-common 3.0.28a-1ubuntu4.1 [2839kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main samba-doc 3.0.28a-1ubuntu4.1 [7008kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main xserver-xorg-video-cirrus 1:1.1.0-8ubuntu1 [42.9kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main liblircclient0 0.8.3~pre1-0ubuntu7.1 [66.1kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main libsmbclient 3.0.28a-1ubuntu4.1 [886kB]
Fetched 36.7MB in 3min13s (190kB/s)                                            
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 127227 files and directories currently installed.)
Preparing to replace libntfs-3g23 1:1.2216-1ubuntu1 (using .../libntfs-3g23_1%3a1.2216-1ubuntu2_i386.deb) ...
Unpacking replacement libntfs-3g23 ...
Preparing to replace ntfs-3g 1:1.2216-1ubuntu1 (using .../ntfs-3g_1%3a1.2216-1ubuntu2_i386.deb) ...
Unpacking replacement ntfs-3g ...
Preparing to replace tzdata-java 2008b-1ubuntu1 (using .../tzdata-java_2008c-1ubuntu0.8.04_all.deb) ...
Unpacking replacement tzdata-java ...
Preparing to replace tzdata 2008b-1ubuntu1 (using .../tzdata_2008c-1ubuntu0.8.04_all.deb) ...
Unpacking replacement tzdata ...
Setting up tzdata (2008c-1ubuntu0.8.04) ...

Current default timezone: 'America/Los_Angeles'
Local time is now:      Tue Jun 10 23:18:34 PDT 2008.
Universal Time is now:  Wed Jun 11 06:18:34 UTC 2008.
Run 'dpkg-reconfigure tzdata' if you wish to change it.


(Reading database ... 127227 files and directories currently installed.)
Preparing to replace initramfs-tools 0.85eubuntu36 (using .../initramfs-tools_0.85eubuntu39.1_all.deb) ...
Unpacking replacement initramfs-tools ...
Preparing to replace libldap-2.4-2 2.4.7-6ubuntu4.1 (using .../libldap-2.4-2_2.4.7-6ubuntu4.2_i386.deb) ...
Unpacking replacement libldap-2.4-2 ...
Preparing to replace pciutils 1:2.2.4-1.1ubuntu3 (using .../pciutils_1%3a2.2.4-1.1ubuntu4_i386.deb) ...
Unpacking replacement pciutils ...
Preparing to replace cpp 4:4.2.3-1ubuntu5 (using .../cpp_4%3a4.2.3-1ubuntu6_i386.deb) ...
Unpacking replacement cpp ...
Preparing to replace libparted1.7-1 1.7.1-5.1ubuntu9 (using .../libparted1.7-1_1.7.1-5.1ubuntu9.1_i386.deb) ...
Unpacking replacement libparted1.7-1 ...
Preparing to replace parted 1.7.1-5.1ubuntu9 (using .../parted_1.7.1-5.1ubuntu9.1_i386.deb) ...
Unpacking replacement parted ...
Preparing to replace ufw 0.16.2 (using .../archives/ufw_0.16.2.1_all.deb) ...
Unpacking replacement ufw ...
Preparing to replace apache2-utils 2.2.8-1ubuntu0.1 (using .../apache2-utils_2.2.8-1ubuntu0.2_i386.deb) ...
Unpacking replacement apache2-utils ...
Preparing to replace apache2-mpm-prefork 2.2.8-1ubuntu0.1 (using .../apache2-mpm-prefork_2.2.8-1ubuntu0.2_i386.deb) ...
 * Stopping web server apache2                                                  apache2: apr_sockaddr_info_get() failed for ubuntu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]
Unpacking replacement apache2-mpm-prefork ...
Preparing to replace apache2.2-common 2.2.8-1ubuntu0.1 (using .../apache2.2-common_2.2.8-1ubuntu0.2_i386.deb) ...
Unpacking replacement apache2.2-common ...
Preparing to replace apache2 2.2.8-1ubuntu0.1 (using .../apache2_2.2.8-1ubuntu0.2_all.deb) ...
Unpacking replacement apache2 ...
Preparing to replace libnspr4-0d 4.7.1~beta2-0ubuntu1 (using .../libnspr4-0d_4.7.1+1.9-0ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement libnspr4-0d ...
Preparing to replace yelp 2.22.1-0ubuntu2 (using .../yelp_2.22.1-0ubuntu2.8.04.1_i386.deb) ...
Unpacking replacement yelp ...
Preparing to replace libnss3-1d 3.12.0~beta3-0ubuntu1 (using .../libnss3-1d_3.12.0.2+1.9-0ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement libnss3-1d ...
Preparing to replace xulrunner-1.9-gnome-support 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1 (using .../xulrunner-1.9-gnome-support_1.9~rc1+nobinonly-0ubuntu1~8.04.2_i386.deb) ...
Unpacking replacement xulrunner-1.9-gnome-support ...
Preparing to replace firefox-3.0-gnome-support 3.0~b5+nobinonly-0ubuntu3 (using .../firefox-3.0-gnome-support_3.0~rc1+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement firefox-3.0-gnome-support ...
Preparing to replace firefox-3.0 3.0~b5+nobinonly-0ubuntu3 (using .../firefox-3.0_3.0~rc1+nobinonly-0ubuntu0.8.04.1_i386.deb) ...
Unpacking replacement firefox-3.0 ...
Preparing to replace xulrunner-1.9 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1 (using .../xulrunner-1.9_1.9~rc1+nobinonly-0ubuntu1~8.04.2_i386.deb) ...
Unpacking replacement xulrunner-1.9 ...
Preparing to replace firefox 3.0~b5+nobinonly-0ubuntu3 (using .../firefox_3.0~rc1+nobinonly-0ubuntu0.8.04.1_all.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-gnome-support 3.0~b5+nobinonly-0ubuntu3 (using .../firefox-gnome-support_3.0~rc1+nobinonly-0ubuntu0.8.04.1_all.deb) ...
Unpacking replacement firefox-gnome-support ...
Preparing to replace gcc 4:4.2.3-1ubuntu5 (using .../gcc_4%3a4.2.3-1ubuntu6_i386.deb) ...
Removing old gcc doc directory.
Unpacking replacement gcc ...
Preparing to replace gnome-about 1:2.22.2-0ubuntu2 (using .../gnome-about_1%3a2.22.2-0ubuntu3_i386.deb) ...
Unpacking replacement gnome-about ...
Preparing to replace gnome-desktop-data 1:2.22.2-0ubuntu2 (using .../gnome-desktop-data_1%3a2.22.2-0ubuntu3_all.deb) ...
Unpacking replacement gnome-desktop-data ...
Preparing to replace libgksu2-0 2.0.5-1ubuntu5 (using .../libgksu2-0_2.0.5-1ubuntu5.1_i386.deb) ...
Unpacking replacement libgksu2-0 ...
Preparing to replace libgnome-desktop-2 1:2.22.2-0ubuntu2 (using .../libgnome-desktop-2_1%3a2.22.2-0ubuntu3_i386.deb) ...
Unpacking replacement libgnome-desktop-2 ...
Preparing to replace python-launchpad-bugs 0.2.30 (using .../python-launchpad-bugs_0.2.30.1_all.deb) ...
Unpacking replacement python-launchpad-bugs ...
Preparing to replace winbind 3.0.28a-1ubuntu4 (using .../winbind_3.0.28a-1ubuntu4.1_i386.deb) ...
 * Stopping the Winbind daemon winbind                                   [ OK ] 
Unpacking replacement winbind ...
Preparing to replace smbfs 3.0.28a-1ubuntu4 (using .../smbfs_3.0.28a-1ubuntu4.1_i386.deb) ...
Unpacking replacement smbfs ...
Preparing to replace smbclient 3.0.28a-1ubuntu4 (using .../smbclient_3.0.28a-1ubuntu4.1_i386.deb) ...
Unpacking replacement smbclient ...
Preparing to replace libpam-smbpass 3.0.28a-1ubuntu4 (using .../libpam-smbpass_3.0.28a-1ubuntu4.1_i386.deb) ...
Unpacking replacement libpam-smbpass ...
Preparing to replace samba 3.0.28a-1ubuntu4 (using .../samba_3.0.28a-1ubuntu4.1_i386.deb) ...
 * Stopping Samba daemons                                                [ OK ] 
Unpacking replacement samba ...
Preparing to replace samba-common 3.0.28a-1ubuntu4 (using .../samba-common_3.0.28a-1ubuntu4.1_i386.deb) ...
Unpacking replacement samba-common ...
Preparing to replace samba-doc 3.0.28a-1ubuntu4 (using .../samba-doc_3.0.28a-1ubuntu4.1_all.deb) ...
Ignoring nonregistered document `samba-by-example'
Ignoring nonregistered document `samba-developers-guide'
Ignoring nonregistered document `samba-using'
Ignoring nonregistered document `samba-howto'
Unpacking replacement samba-doc ...
Preparing to replace xserver-xorg-video-cirrus 1:1.1.0-8 (using .../xserver-xorg-video-cirrus_1%3a1.1.0-8ubuntu1_i386.deb) ...
Unpacking replacement xserver-xorg-video-cirrus ...
Preparing to replace liblircclient0 0.8.3~pre1-0ubuntu7 (using .../liblircclient0_0.8.3~pre1-0ubuntu7.1_i386.deb) ...
Unpacking replacement liblircclient0 ...
Preparing to replace libsmbclient 3.0.28a-1ubuntu4 (using .../libsmbclient_3.0.28a-1ubuntu4.1_i386.deb) ...
Unpacking replacement libsmbclient ...
Setting up libntfs-3g23 (1:1.2216-1ubuntu2) ...

Setting up ntfs-3g (1:1.2216-1ubuntu2) ...
update-initramfs: deferring update (trigger activated)

Setting up tzdata-java (2008c-1ubuntu0.8.04) ...
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up libldap-2.4-2 (2.4.7-6ubuntu4.2) ...

Setting up pciutils (1:2.2.4-1.1ubuntu4) ...

Setting up cpp (4:4.2.3-1ubuntu6) ...

Setting up libparted1.7-1 (1.7.1-5.1ubuntu9.1) ...

Setting up parted (1.7.1-5.1ubuntu9.1) ...
Setting up ufw (0.16.2.1) ...

Setting up apache2-utils (2.2.8-1ubuntu0.2) ...
Setting up apache2.2-common (2.2.8-1ubuntu0.2) ...

Setting up apache2-mpm-prefork (2.2.8-1ubuntu0.2) ...
 * Starting web server apache2                                                  apache2: apr_sockaddr_info_get() failed for ubuntu
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
                                                                         [ OK ]

Setting up apache2 (2.2.8-1ubuntu0.2) ...
Setting up libnspr4-0d (4.7.1+1.9-0ubuntu0.8.04.1) ...

Setting up libnss3-1d (3.12.0.2+1.9-0ubuntu0.8.04.1) ...

Setting up xulrunner-1.9 (1.9~rc1+nobinonly-0ubuntu1~8.04.2) ...

Setting up yelp (2.22.1-0ubuntu2.8.04.1) ...

Setting up xulrunner-1.9-gnome-support (1.9~rc1+nobinonly-0ubuntu1~8.04.2) ...

Setting up firefox-3.0 (3.0~rc1+nobinonly-0ubuntu0.8.04.1) ...
Installing new version of config file /etc/firefox-3.0/pref/firefox.js ...
Please restart all running instances of Firefox-3.0, or you will experience problems.

Setting up firefox-3.0-gnome-support (3.0~rc1+nobinonly-0ubuntu0.8.04.1) ...

Setting up firefox (3.0~rc1+nobinonly-0ubuntu0.8.04.1) ...
Setting up firefox-gnome-support (3.0~rc1+nobinonly-0ubuntu0.8.04.1) ...
Setting up gcc (4:4.2.3-1ubuntu6) ...

Setting up gnome-desktop-data (1:2.22.2-0ubuntu3) ...
Setting up gnome-about (1:2.22.2-0ubuntu3) ...
Setting up libgksu2-0 (2.0.5-1ubuntu5.1) ...

Setting up libgnome-desktop-2 (1:2.22.2-0ubuntu3) ...

Setting up python-launchpad-bugs (0.2.30.1) ...

Setting up samba-common (3.0.28a-1ubuntu4.1) ...

Setting up winbind (3.0.28a-1ubuntu4.1) ...
 * Starting the Winbind daemon winbind                                   [ OK ] 

Setting up smbfs (3.0.28a-1ubuntu4.1) ...
Setting up smbclient (3.0.28a-1ubuntu4.1) ...
Setting up libpam-smbpass (3.0.28a-1ubuntu4.1) ...
Setting up samba (3.0.28a-1ubuntu4.1) ...
 * Starting Samba daemons                                                [ OK ] 

Setting up samba-doc (3.0.28a-1ubuntu4.1) ...

Setting up xserver-xorg-video-cirrus (1:1.1.0-8ubuntu1) ...
Setting up liblircclient0 (0.8.3~pre1-0ubuntu7.1) ...

Setting up libsmbclient (3.0.28a-1ubuntu4.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-18-server

---

### Post by tabdelgawad on 2008-06-19
I had the same problem.  It seems something (an update/install? possibly the LAMP server package I added?) appended <.Domain> to every instance of <PCName> in the Hosts file.  This leads to the system being unable to resolve <PCName> by itself to 127.0.0.1 (e.g. if you're having this problem, open a terminal, type 'sudo', and you'll get an 'unable to resolve <PCName>' error)

The solution of updating the hosts file by adding <PCName> to the 127.0.0.1 line (and/or the 127.0.1.1 line) will work (you can leave <PCName.Domain> on the same line(s) if you want, it won't hurt).  The tricky part for me was that editing this through the GUI (System>Administration>Network>Hosts) didn't work.  Even though it seems that you can unlock the Hosts tab, it doesn't really unlock because of the system's inability to resolve <PCName> - the exact same reason why the Update Manager freezes in the first place. Of course, this doesn't generate any error messages in the GUI:  Instead of freezing like Update Manager, the edits are simply discarded when you exit the Network panel.

What worked for me was editing /etc/hosts by hand.  Of course, I couldn't do it by launching the text editor directly because saving the changes didn't work (it needs to resolve <PCName> to prompt for the password to allow saving, which of course it can't).  Instead, I had to open a terminal window and type:

sudo gedit /etc/hosts

While this still generated a 'can't resolve <PCName>' error, it did prompt me for my password, then opened /etc/hosts in gedit and allowed me to save the changes.

Nasty little bug.  I wonder how it would be resolvable if it became a total catch-22 situation where you needed to resolve <PCName> in order to edit hosts in order to be able to resolve <PCName>!

---

### Post by solidium on 2008-06-20
> **tabdelgawad said:**
> I had the same problem.  It seems something (an update/install? possibly the LAMP server package I added?) appended <.Domain> to every instance of <PCName> in the Hosts file.  This leads to the system being unable to resolve <PCName> by itself to 127.0.0.1 (e.g. if you're having this problem, open a terminal, type 'sudo', and you'll get an 'unable to resolve <PCName>' error)

The solution of updating the hosts file by adding <PCName> to the 127.0.0.1 line (and/or the 127.0.1.1 line) will work (you can leave <PCName.Domain> on the same line(s) if you want, it won't hurt).  The tricky part for me was that editing this through the GUI (System>Administration>Network>Hosts) didn't work.  Even though it seems that you can unlock the Hosts tab, it doesn't really unlock because of the system's inability to resolve <PCName> - the exact same reason why the Update Manager freezes in the first place. Of course, this doesn't generate any error messages in the GUI:  Instead of freezing like Update Manager, the edits are simply discarded when you exit the Network panel.

What worked for me was editing /etc/hosts by hand.  Of course, I couldn't do it by launching the text editor directly because saving the changes didn't work (it needs to resolve <PCName> to prompt for the password to allow saving, which of course it can't).  Instead, I had to open a terminal window and type:

sudo gedit /etc/hosts

While this still generated a 'can't resolve <PCName>' error, it did prompt me for my password, then opened /etc/hosts in gedit and allowed me to save the changes.

Nasty little bug.  I wonder how it would be resolvable if it became a total catch-22 situation where you needed to resolve <PCName> in order to edit hosts in order to be able to resolve <PCName>!

my situation is similar to you in the respect that I also keep getting the " cannot resolve" message when I type "sudo" in the terminal. However I am still able to operate after inputting my password. I was also able to edit my Hosts through the System>admn menu and also via the gedit in terminal. However I am still experiencing both problems a) unable to resolve b) update manager freezing. Here is what my hosts file looks like:

127.0.0.1 PCNAME localhost
127.0.1.1 PCNAME

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[B]
please can you help me out?[/B]

Also the update manager freezes when I click on "Install Updates", it has no problems checking for them.

---

