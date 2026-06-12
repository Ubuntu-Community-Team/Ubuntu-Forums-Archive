---
title: "help crack y old zip file?"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by spacemanps on 2008-05-27
okay so a while back i zipped some important documents, and i currently have forgotten the pass world. So i was looking online and found this:
[http://www.ubuntu-unleashed.com/2008/04/howto-crack-rar-7z-and-zip-files-with.html]("http://www.ubuntu-unleashed.com/2008/04/howto-crack-rar-7z-and-zip-files-with.html")

i did what ever it said but when i tried to put in 
make ; sudo make install i get that end about the release note...(boldede)





nishan@Nishan:~$ _wget [http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2](http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2)_
--01:36:16--  [http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2](http://superb-east.dl.sourceforge.net/sourceforge/rarcrack/rarcrack-0.2.tar.bz2)
           => `rarcrack-0.2.tar.bz2'
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34,964 (34K) [application/x-bzip2]

100%[====================================>] 34,964        13.82K/s             

01:36:21 (13.82 KB/s) - `rarcrack-0.2.tar.bz2' saved [34964/34964]

nishan@Nishan:~$ _tar xvjf rarcrack-0.2.tar.bz2_
rarcrack-0.2/
rarcrack-0.2/CHANGELOG
rarcrack-0.2/LICENSE
rarcrack-0.2/Makefile
rarcrack-0.2/rarcrack.c
rarcrack-0.2/README
rarcrack-0.2/RELEASE_NOTES
rarcrack-0.2/test.rar
rarcrack-0.2/rarcrack.h
rarcrack-0.2/test.zip
rarcrack-0.2/README.html
rarcrack-0.2/test.7z
nishan@Nishan:~$ _cd rarcrack-0.2_
nishan@Nishan:~/rarcrack-0.2$ _sudo apt-get install libxml2-dev_
[sudo] password for nishan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libc6-dev linux-libc-dev zlib1g-dev
Suggested packages:
  glibc-doc manpages-dev
The following NEW packages will be installed:
  libc6-dev libxml2-dev linux-libc-dev zlib1g-dev
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4874kB of archives.
After this operation, 19.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-libc-dev 2.6.24-17.31 [694kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libc6-dev 2.7-10ubuntu3 [3344kB] 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main zlib1g-dev 1:1.2.3.3.dfsg-7ubuntu1 [160kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libxml2-dev 2.6.31.dfsg-2ubuntu1 [676kB]
Fetched 4874kB in 1min9s (70.1kB/s)                                            
Selecting previously deselected package linux-libc-dev.
(Reading database ... 126471 files and directories currently installed.)
Unpacking linux-libc-dev (from .../linux-libc-dev_2.6.24-17.31_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.7-10ubuntu3_i386.deb) ...
Selecting previously deselected package zlib1g-dev.
Unpacking zlib1g-dev (from .../zlib1g-dev_1%3a1.2.3.3.dfsg-7ubuntu1_i386.deb) ...
Selecting previously deselected package libxml2-dev.
Unpacking libxml2-dev (from .../libxml2-dev_2.6.31.dfsg-2ubuntu1_i386.deb) ...
Setting up linux-libc-dev (2.6.24-17.31) ...
Setting up libc6-dev (2.7-10ubuntu3) ...
Setting up zlib1g-dev (1:1.2.3.3.dfsg-7ubuntu1) ...
Setting up libxml2-dev (2.6.31.dfsg-2ubuntu1) ...
nishan@Nishan:~/rarcrack-0.2$ _make ; sudo make install_
[B]gcc -pthread rarcrack.c `xml2-config --libs --cflags` -O2 -o rarcrack
rarcrack.c: In function ‘crack_thread’:
rarcrack.c:206: warning: comparison between pointer and integer
install -s rarcrack /usr/bin
mkdir -p /usr/share/doc/rarcrack
chmod 755 /usr/share/doc/rarcrack
install -m 644 -t /usr/share/doc/rarcrack CHANGELOG LICENSE README README.html RELEASE_NOTES
nishan@Nishan:~/rarcrack-0.2$[/B]

---

### Post by dstew on 2008-05-27
That is just a compiler warning. There seems to have been a bit of sloppy programming, but the program will probably work OK. Did you try it?

---

### Post by spacemanps on 2008-05-27
yeah i did try it, and all that is what i got... i cant get past the bolded part...thats why i posted it

---

### Post by dstew on 2008-05-28
What I mean is, did you try and execute the program? It looks to me like it compiled and installed correctly.

---

### Post by spacemanps on 2008-05-30
sorry doubled.... read below

---

### Post by spacemanps on 2008-05-30
nishan@Nishan:~$ rarcrack oldcrap.rar [12] [rar]
RarCrack! 0.2 by David Zoltan Kedves (kedazo@gmail.com)

ERROR: The specified file ([rar]) is not exists or 
       you don't have a right permissions!

---

### Post by galileon on 2008-05-30
heh, you just either don't have the file oldcrap.rar in your home folder or its permission is wrong

try this:

ls oldcrap.rar -lh

if it says ls: oldcrap.rar: No such file or directory, it means you don't have the file in your home directory. if so, copy/move it from where it is into your home directory.

if its there, it means the permission is wrong. in this case, try

chmod +rw oldcrap.rar

then try 

rarcrack oldcrap.rar [12] [rar]

again. 

btw, if you use AES on rar, it may be impossible to crack with a desktop computer in reasonable time!

---

### Post by Forbees on 2008-10-10
seems like it just isn't in his home folder

i too am having a little trouble . . . 

see i have a RAR with a script i wrote, and i know the password is 4 digits, only numbers and starts with " 1 " . . .

but when i run rarcrack on it, it continues trying to crack after it should have found it.... 

i checked the filename.rar.xml and this is what i get

```

<?xml version="1.0" encoding="UTF-8"?>
<rarcrack>
  <abc>0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ</abc>
  <current>5Voc</current>
  <good_password/>
</rarcrack>

```

obviosuly it's past the right password which would be 1***
and it didn't give me the password


what to do?

---

### Post by laplace/d on 2008-10-27
> **spacemanps said:**
> nishan@Nishan:~$ rarcrack oldcrap.rar [12] [rar]
RarCrack! 0.2 by David Zoltan Kedves (kedazo@gmail.com)

ERROR: The specified file ([rar]) is not exists or 
       you don't have a right permissions!

try the following:

rarcrack --12 --rar oldcrap.rar

for some reason that obscures me, that seems to be working for me.

---

