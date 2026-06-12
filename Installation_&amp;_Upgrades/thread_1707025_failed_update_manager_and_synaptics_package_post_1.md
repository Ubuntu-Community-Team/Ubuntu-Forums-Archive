---
title: "failed update manager and synaptics package post 10.10 update"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by markwestwood on 2011-03-14
having had problems with getting grub2 to work  on dual  HDD setup...despite the most excellent advice on the forum;) i took the plunge and installed 10.10 from update manager within 10.04..... bingo fixed grub and now have dual boot again.  but the update manager and synaptic package don't work because of libedata-cal1.2-6 file that remains..

following other advice on the forum

So near yet so far....

Advice gratefully received, how can i force an unistall of this package

mark@studypc:~$ sudo apt-get -f remove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-evince kdesudo libgnomeprint2.2-data python-metacity python-rsvg python-mediaprofiles python-bugbuddy python-totem-plparser update-manager-kde
  libgnomeprint2.2-0 libgnomeprintui2.2-0 libgnomeprintui2.2-common python-gtop libgnomecups1.0-1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  libedata-cal1.2-6
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 319kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 189793 files and directories currently installed.)
Removing libedata-cal1.2-6 ...
dpkg (subprocess): unable to execute installed post-removal script (/var/lib/dpkg/info/libedata-cal1.2-6.postrm): Exec format error
dpkg: error processing libedata-cal1.2-6 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libedata-cal1.2-6
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by sikander3786 on 2011-03-15
Welcome to the forums :-)

Did you simply try

```
sudo apt-get remove --purge libedata-cal1.2-6
```

---

### Post by markwestwood on 2011-03-15
hi
tried and got
mark@studypc:~$ sudo apt-get remove --purge libedata-cal1.2-6
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libedata-cal1.2-6
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 319kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 189653 files and directories currently installed.)
Removing libedata-cal1.2-6 ...
dpkg (subprocess): unable to execute installed post-removal script (/var/lib/dpkg/info/libedata-cal1.2-6.postrm): Exec format error
dpkg: error processing libedata-cal1.2-6 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 libedata-cal1.2-6
E: Sub-process /usr/bin/dpkg returned an error code (1)


sudo apt-get remove --purge libedata-cal1.2-6

---

### Post by markwestwood on 2011-03-16
below = output after running update manager and  folowing instructions to remove package

---

### Post by markwestwood on 2011-03-18
Still  a package that refuses to go
tried

gedit /var/lib/dpkg/info/libedata-cal1.2-6.postrm

get
gedit has not been able to detect the character encoding.
Please check that you are not trying to open a binary file.
Select a character encoding from the menu and try again.*
 tried with Western (ISO-8859-15) character encoding. and Unicode (UTF-8)
character encoding.
 any way of finding how package is encoded?
 i have not installed any other language or locale other than what should be
default fo the uk


[http://img268.imageshack.us/img268/9003/libedatacal11.png](http://img268.imageshack.us/img268/9003/libedatacal11.png)


[http://img34.imageshack.us/img34/2753/screenshot1mh.png](http://img34.imageshack.us/img34/2753/screenshot1mh.png)




_A[U]ny other suggestions gratefully rec'd_[/U].

is there another way

---

### Post by sikander3786 on 2011-03-18
Try dpkg.

```
sudo dpkg --remove --force-remove-reinstreq libedata-cal1.2-6
```

If that still doesn't solve the issue, there is a manual way of getting rid of the install entries. See here if this one helps.

[http://ubuntuforums.org/showpost.php?p=10048487&postcount=6](http://ubuntuforums.org/showpost.php?p=10048487&postcount=6)

You will need to replace 'firmware-b43-installer' from that post with 'libedata-cal1.2-6'.

---

### Post by markwestwood on 2011-03-19
thanks your initial instructions did not work , followed second link

after finding all items with libedata-cal1.2.6.xxxx renamed all items by placing a in front of file name
ran the 
gksu gedit /var/lib/dpkg/status
deleted the paragraph referring to the libedata-cal1

ran 

sudo apt-get update

now have a working system that can access  the  ubuntu software centre.

a very happy person ....  a further convert to open source computing.... and a fix offered by someone in another continent:D

---

### Post by sikander3786 on 2011-03-19
Ubuntu brings us closer regardless of continents, countries and religions :-)

Glad to know that it worked for you. You can now mark the thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page.

Hope you enjoy your stay with Ubuntu!

---

### Post by markwestwood on 2011-03-19
famous last words about a fix...now have when downloading and attempting an install..

installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/status' near line 36097: 
 field name `' must be followed by colon

---

### Post by markwestwood on 2011-03-19
dpkg: parse error, in file '/var/lib/dpkg/status' near line 36097:
 field name `' must be followed by colon
mark@studypc:~$ gksu gedit /var/lib/dpkg/status
mark@studypc:~$ gksu gedit /var/lib/dpkg/status
^C
mark@studypc:~$ sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/status' near line 36096:
 newline in field name 


so near....

Is one oof the lines between "sourceforge.net" and "Package"  not needed

 This package contains the files necessary for running applications that
 use the libclucene library.
Original-Maintainer: Fathi Boudra <fabo@debian.org>
Homepage: [http://clucene.sourceforge.net](http://clucene.sourceforge.net)

 
Package: libedata-cal1.2-7
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 288
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: evolution-data-server
Version: 2.30.3-2ubuntu2.1
Depends: libc6 (>= 2.3.6-6~), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libebackend1.2-0 (>= 2.30.3), libecal1.2-7 (>= 2.30.3), libedataserver1.2-13 (>= 2.30.3), libgconf2-4 (>= 2.31.1), libglib2.0-0 (>= 2.24.0), libical0 (>= 0.42), libxml2 (>= 2.6.27)
Description: Backend library for evolution calendars
 Evolution is the integrated mail, calendar, task and address book
 distributed suite from Novell, Inc.

---

### Post by sikander3786 on 2011-03-20
You can either edit your /var/lib/dpkg/status file and see what is wrong there in line 36097.

```
gksudo gedit /var/lib/dpkg/status
```

Or if you can't find the offensive something in line 36097, try using an older status file.

Backup your existing one:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Setup the older one:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Then run update again.

```
sudo apt-get update
```

---

### Post by markwestwood on 2011-03-22
fixed it by removing a blank line..

all happily updating again....
:D

---

### Post by n.williams0440 on 2011-03-22
Thanks for the sharing guys.....

---

