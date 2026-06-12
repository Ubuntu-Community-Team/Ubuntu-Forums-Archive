---
title: "Boot-repair unable to install"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2014-07-29
My dual boot Ubuntu 12.10, Win 8 computer won't boot.  I have booted from a liveCD and I am attempting to install boot-repair to no avail.

I used many different iterations of the following commands, but get the same error messages each time.....  In the past when I had boot issues I would just run boot-repair and it would work and fix the issue, now I can't even install boot-repair.  (I can't even boot into win or ubuntu)
[INDENT] **sudo add-apt-repository ppa:yannubuntu/boot-repair** 
[/INDENT]
[INDENT] **sudo apt-get update** 
[/INDENT]
[INDENT] **sudo apt-get install boot-repair boot-sav**


It states these can't be authenticated....
libsigsegv2 gawk python-configobj pastebinit







This is the output of the terminal......




```
ubuntu@ubuntu:~$      sudo add-apt-repository ppa:yannubuntu/boot-repair 
You are about to add the following PPA to your system:
 Simple tool to repair frequent boot problems.

Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpcm43ki/secring.gpg' created
gpg: keyring `/tmp/tmpcm43ki/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpcm43ki/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal InRelease
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main Translation-en_US                             
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/main Translation-en         
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted Translation-en_US
Ign cdrom://Ubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.5) quantal/restricted Translation-en   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security InRelease                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release.gpg                                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release                                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal InRelease                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release.gpg                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Sources                                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main amd64 Packages                   
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main amd64 Packages                              
  404  Not Found [IP: 91.189.91.14 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted amd64 Packages                        
  404  Not Found [IP: 91.189.91.14 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en_US                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal InRelease                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/main Translation-en
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal-updates/restricted Translation-en
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) quantal/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages](http://security.ubuntu.com/ubuntu/dists/quantal-security/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.14 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal-updates/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/quantal/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.91.13 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
ubuntu@ubuntu:~$ sudo apt-get install boot-repair boot-sav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  boot-sav-extra gawk glade2script libsigsegv2 pastebinit python-configobj
Suggested packages:
  mbr mdadm clean-ubiquity os-uninstaller gawk-doc
The following NEW packages will be installed:
  boot-repair boot-sav boot-sav-extra gawk glade2script libsigsegv2 pastebinit python-configobj
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,042 kB/1,705 kB of archives.
After this operation, 6,581 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  libsigsegv2 gawk python-configobj pastebinit
Install these packages without verification [y/N]? y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main libsigsegv2 amd64 2.9-4ubuntu3
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main gawk amd64 1:4.0.1+dfsg-2
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main python-configobj all 4.7.2+ds-4
  404  Not Found [IP: 91.189.92.201 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main pastebinit all 1.3-2ubuntu3
  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libs/libsigsegv/libsigsegv2_2.9-4ubuntu3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libs/libsigsegv/libsigsegv2_2.9-4ubuntu3_amd64.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gawk/gawk_4.0.1+dfsg-2_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gawk/gawk_4.0.1+dfsg-2_amd64.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/configobj/python-configobj_4.7.2+ds-4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/configobj/python-configobj_4.7.2+ds-4_all.deb)  404  Not Found [IP: 91.189.92.201 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pastebinit/pastebinit_1.3-2ubuntu3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pastebinit/pastebinit_1.3-2ubuntu3_all.deb)  404  Not Found [IP: 91.189.92.201 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ 
```


[/INDENT]

---

### Post by grahammechanical on 2014-07-29
Ubuntu 12.10 has reached end of life. So, if you are trying to install Boot Repair on the 12.10 live session then reason why it is failing is because the 12.10 repositories are now closed.

You could download Ubuntu 14.04 and run that as a live session and install Boot Repair then. An alternative would be to download and burn the Linux Secure Remix ISO image. It is Ubuntu 13.04 with Boot Repair; OS-Uninstaller and Clean Ubiquity already installed.

[http://sourceforge.net/projects/linux-secure/](http://sourceforge.net/projects/linux-secure/)

[http://sourceforge.net/p/linux-secure/wiki/Home/](http://sourceforge.net/p/linux-secure/wiki/Home/)

Regards.

---

### Post by claven123 on 2014-07-30
So, I would do the same as I did in the past with the 12.10 liveCD, only this time download create the 14.04 liveCD and then install Boot-repair.  I've seen quite a bit on the net about 14.04 causing lots of issues with boot-repair or vica versa ....

I have a liveCD of 13.10 at home I could just use that one, yes?

Thanks,

D

---

### Post by oldfred on 2014-07-30
Only 12.04 or 14.04.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Boot-Repair has not been updated for 14.04, but install instruction have you change it to download last version which still works.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by claven123 on 2014-07-31
I thought I would try the 13.10 LiveCD before I went thru the hassle of making a LiveCD for 14.04 and the 13.10 CD worked.  I was able to quickly install and use the boot repair from the 13.10 disk.

d

---

