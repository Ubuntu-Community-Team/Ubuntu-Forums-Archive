---
title: "Error message when scanning 7.10 CD"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by rwnz on 2007-10-20
I receive the following error message from Synaptic Package Manager when trying to open both the  ubuntu-7.10-alternate-i386.iso and  ubuntu-7.10-desktop-i386.iso cd's:


Sub-process gpgv returned an error code (2)

W: Signature verification failed for: /media/cdrom0/dists/gutsy/Release.gpg


I've tried running them on a P3 850MHz laptop with 256MB RAM running 7.04 by first inserting the alternate disc into the CD drive with the 7.04 operating system fully loaded, and then trying the desktop disc to see if it acted differently. The desktop CD started OK on a Windows XP machine.

I note that at [https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes](https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes) there is the statement "The minimum memory requirement for Ubuntu 7.10 is 384MB of memory for desktop CDs, and 256MB for other installation methods. (Note that some of your system's memory may be unavailable due to being used for the graphics card.)" I assumed that the alternate cd is an "other" method so my 256MB should be enough, but could this be the reason for my problem and can I install 7.110 on my system? The System Monitor tells me I have 242MB RAM so maybe the graphics may be using 14MB of it.

---

### Post by Pumalite on 2007-10-20
256 MB RAM or less> Xubuntu Alternate CD:[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by rwnz on 2007-10-21
Thanks. I expected that Ubuntu 7.10 would work on this laptop as 7.04 did OK. Also, I had tried Xubuntu 7.04 a while back (before I tried Unbuntu 7.04) but couldn't get my display resolution right with it, which is why I then tried Ubuntu 7.04.. I'll download Xubuntu 7.10 and try it. I hope that it's display, wireless network and printer capabilities are at the same level as Ubuntu.

---

### Post by tsmets on 2007-11-06
my laptop has 2 GB of RAM and also indicates the same error :

> Can't check signature : public key not found
...
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for : /cdrom/dists/gutsy/Release.gpg


Please note that I booted the live cd and asked it to check itself & it did successfully !!!
Any idea ... ?

\T,

---

### Post by lacis_alfredo on 2008-04-01
Hi,
HELP! I have similar problems with trying to add a 7.10 CD:
```

homer@krusty:~$ sudo bash
root@krusty:~# apt-cdrom add 
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [b23710d0071ddbf904b10cfe355c13af-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
This disc is called: 
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
Copying package lists...gpgv: Signature made Tue 16 Oct 2007 09:53:09 EST using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/gutsy/Release.gpg
root@krusty:~# 

```
Thanks in advance,
Alfredo

---

### Post by zvacet on 2008-04-01
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by lacis_alfredo on 2008-04-01
> **zvacet said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```

I'm sorry, but how does this help get the CD running?

---

### Post by zvacet on 2008-04-01
You said 

> I receive the following error message from Synaptic Package Manager 

so refreshing your source list can help.Sorry if I misunderstand you.

---

### Post by lacis_alfredo on 2008-04-08
Hi, someone on freenode #ubuntu suggested that I should be using the "alternate" CD, not the "live" CD, although I did not think the difference would be important.

So I downloaded the "alternate" CD.  I inserted the CD & I got a dialog box:
```

Error scanning the CD 
E:Sub-process gpgv returned an error code (2), W:Signature verification failed for: /cdrom/dists/gutsy/Release.gpg

```
Not giving me a lot of confidence.......  So I went to a bash prompt:
```

homer@krusty:~$ sudo apt-cdrom add 
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [f38417f7ed4311386f5496706aea66ed-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)'
This disc is called: 
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)'
Copying package lists...gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/gutsy/Release.gpg
homer@krusty:~$ 

```
Did it mean anything important when it said this?
```

Copying package lists...gpgv: Signature made Tue 16 Oct 2007 09:24:30 EST using DSA key ID FBB75451
gpgv: Can't check signature: public key not found

```
TIA,
Alf

---

### Post by lacis_alfredo on 2008-04-08
Does it have anything to do with, in the gui Synaptic Package Manager,  under Settings / Repositories.../ Authentication tab/
My "Trusted software providers" list is empty.

Should I be using the button "+Import Key File..."?

/Alf

---

### Post by Pumalite on 2008-04-08
Never heard of it. this could be a bad burn. Download from here:
[http://cdimage.ubuntu.com/xubuntu/re.../7.10/release/](http://cdimage.ubuntu.com/xubuntu/re.../7.10/release/)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on the iso, burn at 4x or less, on CD-R, check CD integrity after burn and before install.

---

### Post by AllanM on 2008-05-21
I am getting exactly the same error on xubuntu 8.04 on a new install completed a few minutes ago and downloaded yesterday. I installed from the alternate cd on a thinkpad that doesn't have an internet connection or much memory. The desktop cdrom seems to be recognised and brings up synaptic, which the alternate one doesn't, but the message about "E:Sub-process gpgv returned an error code (2)" and "W: Signature verificatiuon failed for: /mdeia/cdrom0/dists/hardy/Rlease.gpg" stops synaptic from working. No solution yet :(

---

