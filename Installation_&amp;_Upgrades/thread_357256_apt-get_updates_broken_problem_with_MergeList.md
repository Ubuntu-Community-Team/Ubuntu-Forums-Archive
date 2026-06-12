---
title: "apt-get updates broken? problem with MergeList?"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by krantix on 2007-02-09
I cannot update anymore... this is what i get...

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I've tryed to substitute status with status.old but nothing changes...

my /var/lib/dpkg/status file is as follows...

```

root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:christian
tty:x:5:
disk:x:6:
lp:x:7:cupsys
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:cupsys,christian
fax:x:21:
voice:x:22:
cdrom:x:24:haldaemon,christian
floppy:x:25:haldaemon,christian
tape:x:26:
sudo:x:27:
audio:x:29:christian
dip:x:30:christian
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:christian
sasl:x:45:
plugdev:x:46:haldaemon,christian
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
dhcp:x:101:
syslog:x:102:
klog:x:103:
ssl-cert:x:104:cupsys
crontab:x:105:
ssh:x:106:
messagebus:x:107:
avahi:x:108:
lpadmin:x:109:christian
haldaemon:x:110:
scanner:x:111:cupsys,hplip,christian
slocate:x:112:
gdm:x:113:
christian:x:1000:
admin:x:114:christian
fuse:x:115:christian

```


please, help!!!

---

### Post by STREETURCHINE on 2007-03-10
yep having the same problem here  cant update ,


```
free/binary-i386/Packages.gz  504 Gateway Timeout
Reading package lists... Error!
E: Malformed Status line, no 3rd word
E: Error occurred while processing language-pack-be-base (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
rex@rex-desktop:~$
```

---

### Post by STREETURCHINE on 2007-03-10
ok i seem to have mine sorted by

       ```
dpkg --configure -a
```

       ```
apt-get -f install
``` 

if that does not work look in 

        ```
/var/lib/dpkg/info
```

The above location stores what are called post-installation (.postinst) and post-removal (.postrm) scripts from deb packages which include them. Sometimes, packagers do not do a good job of packaging software and these scripts (which are NOT present in all debs) error out (during installation or uninstallation) and prevent apt from doing anything further (in terms of installing or uninstalling other packages).
What you need to do then is delete the faulty scripts from the above location and then apt-get remove the package.
That will fix apt.

and then manually go and repir anything else that shows up

---

### Post by geakMonkey on 2007-03-21
> **STREETURCHINE said:**
> yep having the same problem here  cant update ,


```
free/binary-i386/Packages.gz  504 Gateway Timeout
Reading package lists... Error!
E: Malformed Status line, no 3rd word
E: Error occurred while processing language-pack-be-base (UsePackage1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
rex@rex-desktop:~$
```

# apt-get check
Reading package lists... Error!
E: Malformed 1st word in the Status line
E: Error occurred while processing xserver-xorg-driver-glint (UsePackage2)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I did look into the /var/lib/dpkg/status and output it. What needs to be done to fix the Malformed 1st word in Status line?

---

### Post by geakMonkey on 2007-03-21
ok, I found this solution and it worked for me:


cd /var/lib/dpkg
mv status status-bad
cp status-old status

apt-get update

from: [http://www.oclug.on.ca/archives/linux/2007-February/001056.html](http://www.oclug.on.ca/archives/linux/2007-February/001056.html)

---

### Post by ceixeoida on 2007-04-07
> **geakMonkey said:**
> ok, I found this solution and it worked for me:


cd /var/lib/dpkg
mv status status-bad
cp status-old status

apt-get update

from: [http://www.oclug.on.ca/archives/linux/2007-February/001056.html](http://www.oclug.on.ca/archives/linux/2007-February/001056.html)
This worked for me too... thanx!

---

### Post by veugelenw on 2007-04-17
hmm, it doesn't work for me :S

---

### Post by Norway26 on 2008-02-14
This worked for me as well, but  I needed to remove the lock before I could run the update.

```
sudo rm -f /var/lib/dpkg/lock
```

---

### Post by doublet on 2008-02-18
After doing all that it is not working for me :(

E: Dynamic MMap ran out of room
E: Error ehile processing language-pack-kde-uz-base (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_dapper-updates_main_binary-i386_Packages
E: Could not open packet list or status file

(translated to english)

---

