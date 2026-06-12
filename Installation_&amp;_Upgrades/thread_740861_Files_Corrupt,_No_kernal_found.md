---
title: "Files Corrupt, No kernal found"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by tcity5 on 2008-03-31
I realize there are other topics about this, but I have tried burning the ISO to the CD at the lowest burn speed available on Alcohol 120%, 8x.  I am burning onto an HP Lightscribe disk.  The installation goes absolutely perfectly until the final installation, where I get to 6% and get several messages about files being corrupt and unable to be installed.  I continue through them to find that there is no installable kernal found.

I am using the Ubuntu 7.10 Server Edition downloaded straight from the Ubuntu website.  Should I try Ubuntu 6.06 LTS?  What is the difference?

---

### Post by dstew on 2008-03-31
Do the CD integrity check (on the first menu) and see if the CD is OK. It is possible that the .iso you used had errors in it (did you check the .iso MD5 checksum), or that the burn failed.

---

### Post by anantshri on 2008-03-31
do run a cd integrity check.

and if that fails you have only one option redownload of files.

as far as 6.06 LTS is concerned 

Its the long term support you get assurance from ubuntu that you get a life long support from them.

wereas other versions have limited support time.

well you can read more about LTS at ubuntu's official website.

---

### Post by tcity5 on 2008-04-02
Should I be installing the desktop version before the server edition?  I just realized that the desktop version is actually significantly bigger in file size.

---

### Post by dstew on 2008-04-03
The server edition is a command-line only system. If you want a graphical desktop, like Windows or Mac OSX, you need to install the desktop version.

If you install the server version, you can install the Desktop part over the internet by executing the command```
sudo apt-get install ubuntu-desktop
```You need at least 256 Mb memory, and about 10 Gb disk space to install the Desktop.

---

### Post by tcity5 on 2008-04-03
Yeah, I have 1GB memory and 210GB disk space on the computer to which I'm installing it.  My friend recommended that I try the ISO from a torrent download.  I'll give that a whirl and let you know how it turns out.

I assume if I install the desktop version, I can use it as a server in that order as well, right?

---

### Post by zvacet on 2008-04-03
I think it is too late,but I say it anyway.Download same iso with torrent and point download to the folder where is youe existing iso.That way you don have to download all,because torrent will check files on your iso and if find any corupted it will replace them with good ones.After that check [md5sum](https://help.ubuntu.com/community/HowToMD5SUM).If it is O.K. then burn it on lower possible speed and after that check disc integrity.If that is fine too,then go for install.

After installing go to the system>admin>software sources and check all boxes under Ubuntu software and updates tab.Reload.If you want to insall server go to the synaptic and I think under edit tab>mark packages by task>LAMP.

---

### Post by dstew on 2008-04-03
> I assume if I install the desktop version, I can use it as a server in that order as well, right?Sure, it does not interfere with the base (server) install, it just adds the desktop to it. And really, if you have internet access, try the apt-get command to install the desktop. It will take just as long to download the .iso and burn it. If you download the .iso, it will re-install the server part also, so if you have any programs or configuration there, you will have to re-do those.

---

### Post by tcity5 on 2008-04-03
Actually what I meant was, I already have the desktop version installed.  Can I use it as a server?

Clarification: I managed to get Ubuntu 7.10 desktop perfectly installed with the torrent ISO.  I want to use it as a server now.

---

### Post by zvacet on 2008-04-03
Here it is again

> After installing go to the system>admin>software sources and check all boxes under Ubuntu software and updates tab.Reload.If you want to insall server go to the synaptic and  under edit tab>mark packages by task>LAMP.

---

### Post by cferthorney on 2008-04-05
I had similar problems on the alternates CD, the MD5sum matched fine, although some of the .deb's on the CD were actually (worryingly) .de not .deb or .udeb so teh CD integirty check never worked.  Also the CD integrity check is not perfect I found.  The MD% may match but it appears (On the 4 CD's I burned, 2 on lowest speeds, using different media etc as suggested in my [similar topic here ](http://ubuntuforums.org/showthread.php?t=744982&highlight=md5sum) [ubuntuforums.org] and whilst the cd integ check was fine the CD was still finding problems with certain .deb files (Aptitude kept popping up as did some of the kernel .debs :( )

This is by no means a slating of Ubuntu I downloaded the desktop CD and had no problems - I just wanted to encrypt my disks as its on a laptop I take many places and also I like using LVM.

Slightly off topic and I am sorry for this - but if the alternatives CD is being downloaded with .de files instead of .deb and the MD5sum matches (I mounted the ISO on loopback to check this as I wasn't sure) who do we report this to? Does it get filed as a bug?  I ask only because I want to put Ubuntu on my servers when Hardy is officially released and obviously with the LTS agreement there extra checks will be made coz of its use on enterprise servers.

I'm glad the desktop cd worked for you too.

Sorry to have hijacked this slightly.
Dave

---

