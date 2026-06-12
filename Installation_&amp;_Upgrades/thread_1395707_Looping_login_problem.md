---
title: "Looping login problem"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by espressobeanie on 2010-02-01
Hi all.

I have a problem logging in with my new Ubuntu Karmic install. Every time I do so, the screen turns black and a grey box in the middle of the screen or something of that nature, briefly flashes. Expecting God, I get psyched. However, disappointed, I get dumped back into the login screen again. I notice that under Session, nothing is listed. After CTRL+ALT+F1, I tried some commands:

sudo gdm

Output:
** (gdm-binary:1898 ) : WARNING **: Failed to acquire  org.gnome.DisplayManager: Connection ":1.99" is not allowed to own the  service "org.gnome.DisplayManger" due to security polices in the  configuration file
 
** (gdm-binary:1898 ) : WARNING **: Could not acquire name; bailing out        

So, I tried the instructions posted here:  [http://ubuntuforums.org/showthread.php?t=1335435&page=2](http://ubuntuforums.org/showthread.php?t=1335435&page=2)

2.) sudo stop gdm (or sudo /etc/init.d/gdm stop)
 
3.) sudo apt-get purge gdm
 
4.) sudo apt-get install wdm

and instead of 'sudo install wdm' I did 'sudo install gdm'. I am connected thru wifi, not ethernet. It did some weird stuff and now I have the option to boot into KDE or x 'something' which leads to a command prompt. 

A funny thing also happened. The way my computer is setup, I have Vista, Backtrack, and Ubuntu 9, with a swap space and 200 Gigs set aside as a formatted D:\ for Vista. A .tar.bz2 file I downloaded thru my Vista setup not only contained it's normal files, but also a 'root' folder from Ubuntu with all of my settings inside. It extracts and I get an error message:

!   V:\zd1211-firmware-1.4.tar.bz2: Cannot open \tmp\kde-root (root\.kde\tmp-bt --> \tmp\kde-root)
!   V:\zd1211-firmware-1.4.tar.bz2: Symbolic link points to missing file
!   V:\zd1211-firmware-1.4.tar.bz2: Cannot open \tmp\ksocket-root (root\.kde\socket-bt --> \tmp\ksocket-root)
!   V:\zd1211-firmware-1.4.tar.bz2: Symbolic link points to missing file
!   V:\zd1211-firmware-1.4.tar.bz2: Cannot open \var\tmp\kdecache-root (root\.kde\cache-bt --> \var\tmp\kdecache-root)
!   V:\zd1211-firmware-1.4.tar.bz2: Symbolic link points to missing file
!   V:\zd1211-firmware-1.4.tar.bz2: Cannot open \root\.DCOPserver_bt__0 (root\.DCOPserver_bt__0 --> \root\.DCOPserver_bt__0)
!   V:\zd1211-firmware-1.4.tar.bz2: Symbolic link points to missing file
!   V:\zd1211-firmware-1.4.tar.bz2: Cannot open \tmp\kde-root (root\.kde3\tmp-bt --> \tmp\kde-root)
!   V:\zd1211-firmware-1.4.tar.bz2: Symbolic link points to missing file
!   V:\zd1211-firmware-1.4.tar.bz2: Cannot open \tmp\ksocket-root (root\.kde3\socket-bt --> \tmp\ksocket-root)
!   V:\zd1211-firmware-1.4.tar.bz2: Symbolic link points to missing file
!   V:\zd1211-firmware-1.4.tar.bz2: Cannot open \var\tmp\kdecache-root (root\.kde3\cache-bt --> \var\tmp\kdecache-root)
!   V:\zd1211-firmware-1.4.tar.bz2: Symbolic link points to missing file

V:\ is the 200 Gig D:\ and the the zd1211-firmware-1.4.tar.bz2 is the file I was extracting from.

---

### Post by djdan2k8 on 2010-02-01
I did have this a while ago and not sure if it is the same problem your having mine was a faulty RAM Memory stick.

---

### Post by espressobeanie on 2010-02-01
I did a memory test. It came back clean.

---

