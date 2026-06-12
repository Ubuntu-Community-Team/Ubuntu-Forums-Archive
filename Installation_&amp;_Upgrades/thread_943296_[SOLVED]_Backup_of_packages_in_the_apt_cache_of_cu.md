---
title: "[SOLVED] Backup of packages in the apt cache of currently installed software only"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by Dre8927354 on 2008-10-10
Hi,

I want to backup all the packages in my “/var/cache/apt/archives”. Nevertheless, I only want the packages of software currently installed on my computer. I used APTonCD, however, it creates backups of all the packages and some of these packages causes errors in Synaptic when I add the created disk to my repositories. 

Other considerations are that I pay R80/$8.48 per 1gB for internet and that I want to install these packages on a computer of a friend that I only see once a year and whom does not have any internet access whatsoever. 

Thank you

---

### Post by Partyboi2 on 2008-10-10
Have you tried this
[http://ubuntuforums.org/showthread.php?t=819396](http://ubuntuforums.org/showthread.php?t=819396)

---

### Post by iaculallad on 2008-10-10
On your terminal:

```
sudo apt-cdrom add
```

and place your AptOnCD media on your CD/DVDROM drive then:

```
sudo apt-get update && sudo apt-get upgrade
```

Does it still show an error message?

---

### Post by Dre8927354 on 2008-10-10
Thanks for the quick reply!

After “sudo apt-cdrom add” I got these messages:
[COLOR="Blue"]
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [f0a1a540c35772db30bf4297a4d0af13-2]
Scanning disc for index files..
Found 1 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
Found label 'APTonCD for ubuntu hardy - i386 (2008-10-09 22:01) DVD1'
This disc is called: 
'APTonCD for ubuntu hardy - i386 (2008-10-09 22:01) DVD1'
Reading Package Indexes... Error!
E: Cannot find filename or size tag[/COLOR]

My computer was busy for a long time with:

[COLOR="Blue"]$ sudo apt-get install dpkg-repack fakeroot
$ mkdir ~/dpkg-repack; cd ~/dpkg-repack
$ fakeroot -u dpkg-repack `dpkg --get-selections | grep install | cut -f1`[/COLOR]

And I got a few messages that concerned me... Examples are:
[COLOR="Blue"]
warning, `./dpkg-repack-7137/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `xcursor-themes' in `./xcursor-themes_1.0.1-5ubuntu1_i386.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)

dpkg-repack: File not found: /usr/share/locale/be@latin/LC_MESSAGES/xdg-user-dirs.mo[/COLOR]

After that I cleared my apt cache because that seems to be the first place where APTonCD looks for packages then I told APTonCD to add the previously created folder “~/dpkg-repack”. I burned the disk and added it to the repositories and everything seems to work fine. 

I will try to open my eyes wider the next time I have a problem!

Thank you both and [http://ubuntuforums.org/showthread.php?t=819396]("http://ubuntuforums.org/showthread.php?t=819396") for the help!

---

