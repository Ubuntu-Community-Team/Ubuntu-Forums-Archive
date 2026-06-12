---
title: "Can't remove package"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by inf1nity on 2013-06-22
I have a ZTE USB modem. It came with its dialer software for various platforms. It also had one .deb file. I copied that file to my /home and ran sudo dpkg -i <filename>.

Although there was an error, it installed and was available in the dash, but didn't work.
Now i tried to remove it using sudo apt-get remove --purge crossplatformui

I got a message saying that removing crossplatformui required removal of various other packages including vlc, i hit yes and it removed vlc, but when it tried to remove the modem software it gave me this error.

```

(Reading database ... 141977 files and directories currently installed.)
Removing crossplatformui ...
ztemtvcdromd: no process found
dpkg: error processing crossplatformui (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 crossplatformui
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Now i can't install anymore packages. No updates, nothing. whenever i try to install new packages i get the above error code. What do i do?

---

### Post by dentaku65 on 2013-06-22
Try
```
sudo dpkg --force-all -P crossplatformui
```

---

### Post by inf1nity on 2013-06-22
This is what i get

```

root@945GCM2SA2-6H:~# dpkg --force-all -P crossplatformui
(Reading database ... 141977 files and directories currently installed.)
Removing crossplatformui ...
ztemtvcdromd: no process found
dpkg: error processing crossplatformui (--purge):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 crossplatformui


```

---

### Post by inf1nity on 2013-06-22
while waiting for replies i've done a few things, here they are-
ran autoclean and autoremove.
ran dpkg --configure -a.
deleted files from /var/crash since i was also getting the message "No apport report written because MaxReports is reached already"

No use.. i lost 11MB worth of downloaded packages and still that package crossplatformui is there. Because of it i can't remove any other packes or intall new ones since before every such operation apt tries to remove croossplatformui and fails.

What do i do? Should i reinstall ubuntu? But then i'll lose 200MB worth of updates and this is costly since my internet is very slow... Please help..

---

### Post by dentaku65 on 2013-06-22
```
sudo rm -f /var/cache/apt/archives/[COLOR="#FF0000"]<filename>[/COLOR]
```
```
sudo apt-get clean
```

---

### Post by diesch on 2013-06-22
Please post the contents of the file  /var/lib/dpkg/info/crossplatformui.postrm

---

### Post by inf1nity on 2013-06-23
dentaku and diesch, thanks for your r[FONT=arial][/FONT]eplies. But my problem is fixed. I went to the directory 

[FONT=arial]/var/lib/dpkg/status (or maybe it was info)[/FONT]

[FONT=arial]and i saw a file that had an entry[/FONT]

```

Package: crossplatformui
Status: deinstall ok half-installed
Priority: extra
Section: non-free/net
Maintainer: ztemt
Architecture: i386
Version: 1.0.38
Conffiles:
 /etc/acpi/events/ztemtEVDO-lidbtn 20fe0e769bea115150fed0715b78737f
 /etc/acpi/events/ztemtEVDO-powerbtn 48f6cf0bf3e7694c24ae8afbf2ff8714
 /etc/acpi/events/ztemtEVDO-sleepbtn 39e022399f624095fffe5102e5a2eaa3
 /etc/ld.so.conf.d/ztemtApp.conf 354d2849fbfb769a38425ae304d5b9ce
 /etc/udev/rules.d/10-ztemtEVDO.rules aa924f3f8b9ac35a9adcd0abad07e529
Description: Reliance Netconnect - Broadband+

```

[FONT=arial]I removed this text from the file, (sorry i don't remember that filename) and my problem is now fixed.[/FONT]

---

### Post by nicandris on 2014-03-28
> **inf1nity said:**
> dentaku and diesch, thanks for your r[FONT=arial][/FONT]eplies. But my problem is fixed. I went to the directory 

[FONT=arial]/var/lib/dpkg/status (or maybe it was info)[/FONT]

[FONT=arial]and i saw a file that had an entry[/FONT]

```

Package: crossplatformui
Status: deinstall ok half-installed
Priority: extra
Section: non-free/net
Maintainer: ztemt
Architecture: i386
Version: 1.0.38
Conffiles:
 /etc/acpi/events/ztemtEVDO-lidbtn 20fe0e769bea115150fed0715b78737f
 /etc/acpi/events/ztemtEVDO-powerbtn 48f6cf0bf3e7694c24ae8afbf2ff8714
 /etc/acpi/events/ztemtEVDO-sleepbtn 39e022399f624095fffe5102e5a2eaa3
 /etc/ld.so.conf.d/ztemtApp.conf 354d2849fbfb769a38425ae304d5b9ce
 /etc/udev/rules.d/10-ztemtEVDO.rules aa924f3f8b9ac35a9adcd0abad07e529
Description: Reliance Netconnect - Broadband+

```

[FONT=arial]I removed this text from the file, (sorry i don't remember that filename) and my problem is now fixed.[/FONT]

many thanx. Yes the correct file is status. I deleted those lines and it worked. 
PS. my problem was not with this package, it was with musica, but the solution is the same.

---

