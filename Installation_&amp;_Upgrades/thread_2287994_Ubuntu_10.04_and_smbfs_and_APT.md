---
title: "Ubuntu 10.04 and smbfs and APT"
date: 2015-07-23
forum: Installation &amp; Upgrades
---

### Post by cm1375 on 2015-07-23
Not sure if this is the correct way and place to post this, and apologies if this is wrong.

I seem to have come across a possible problem with Ubuntu 10.04, synaptic and apt in general when used in conjunction with a repository located on a shared windows directory mounted using smbfs.  

ENVIRONMENT
-----------
The shared directory is mounted after installing smbfs (2:3.4.7~dfsg-1ubuntu3) and issuing the following command:
    mount //192.100.100.1/u$ /media/nfsmount/UBU-REPO -t cifs -o user=administrator,password=XXX 

/etc/apt/sources.list contains the repository link:
    deb file:///media/nfsmount/UBU-REPO/Repository_Lucid lucid main universe multiverse restricted

PROBLEMS
--------
When I try to "Reload" the repository information or run an install from within synaptic I get errors of which 
a typical example is shown below:

    "Failed to fetch file:/media/nfsmount/UBU-REPO/Repository_Lucid/dists/lucid/main/binary-i386/Packages.gz  File not found"

If I try to install a program, for example hexedit with apt-get install hexedit
I get:
    <<
    Err file:/media/nfsmount/UBU-REPO/Repository_Lucid/ lucid/universe hexedit 1.2.12-4
      File not found
    Failed to fetch file:///media/nfsmount/UBU-REPO/Repository_Lucid/pool/universe/h/hexedit/hexedit_1.2.12-4_i386.deb  File not found
    E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
    >>

POINTS:
 1)  I can browse /media/nfsmount/UBU-REPO from within nautilus as any user on my system and see all the files and directory
     structure as expected.
     Also if as root or any user I issue the command:
          ls -l /media/nfsmount/UBU-REPO/Repository_Lucid/pool/universe/h/hexedit/hexedit_1.2.12-4_i386.deb
     I get 
         -rwxr-xr-x 1 root root 28294 2010-02-02 09:05 /media/nfsmount/UBU-REPO/Repository_Lucid/pool/universe/h/hexedit/hexedit_1.2.12-4_i386.deb
     so the file is there, and I can list it.

 2)  The nfsmount in the mount path is there because I initially setup the repository to be accessible via a mount to an nfs
      share of the repository on a ubuntu box, and that all worked fine.  When trying to learn how to set up access 
      via smb I wanted to initially keep the original structures the same until everything was working.

 3)  I installed Ubuntu 12.01 on the same client machine in another partition and installed cifs-utils to see if it was a problem in 10.04 specifically.
      And indeed everything works as expected with 12.01 with cifs-utils.   apt-get and synaptic (reload etc) worked fine.


CONCLUSIONS
-----------
The fact that I can list repository files on the command line or using nautilus would suggest some sort of problem with the
way smbfs (2:3.4.7~dfsg-1ubuntu3) offers mounted files?  Particularly as the newer version cifs-utils appears to
offer mounted files correctly.

I initially thought it was a problem synaptic might have with ubuntu permissions but I have tried logging in as 
root and the problem persisted.  I ran (ps -U root|grep synaptic) which confirms that synaptic runs as root.

I have tried looking for answers without luck.

Has anybody else had problems with Ubuntu 10.04 accessing a repository via smbfs?

Thanks.

---

### Post by flocculant on 2015-07-23
>  Has anybody else had problems with Ubuntu 10.04 accessing a repository via smbfs?

I would expect so.

10.04 for desktop was EOL in 2013
10.04 for server was EOL in April.

---

### Post by Bucky Ball on 2015-07-23
> **flocculant said:**
> 

10.04 for desktop was EOL in 2013
10.04 for server was EOL in April.

^^^
This. Welcome. Suggest heading to the current LTS, 14.04 LTS.

[This]("https://help.ubuntu.com/community/EOLUpgrades") might help or you'll need to back up and do a clean install.

Although not sure if this has anything to do with your issue as you are trying to access a repo of your own making on a local device by the sounds of it. Better to upgrade anyway as chances of user support diminishes quickly for end-of-life releases.

---

### Post by cm1375 on 2015-07-24
Yes 10.04 is going back a bit but have reasons for using it for now.  In part because I have slow and intermittent links to internet.  Thanks for replies in any case.   Just so strange that accessing the smbfs mount works via "ls" and nautilus but not through any ATP related software?  I thought that file system calls would be abstracted and the same independent of what type of software was making the calls.  So either all access to the mount would work or none.  Ah well.

---

