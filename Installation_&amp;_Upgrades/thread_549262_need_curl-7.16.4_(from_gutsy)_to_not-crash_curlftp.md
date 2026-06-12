---
title: "need curl-7.16.4 (from gutsy) to not-crash curlftpfs on feisty"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Rene7705 on 2007-09-12
Hi. i'm having a major problem mounting FTPS shares..
FTPS (TLSv1) is all my hoster allows me to use.

It seems that curlftpfs cannot deal with the feisty-provided curl-7.15.5

[http://curlftpfs.sourceforge.net/](http://curlftpfs.sourceforge.net/)
22-Jan-2007 - Bad libcurl versions

A lot of users are reporting problems with CurlFtpFS. We tracked this problems to bugs in libcurl versions 7.15.5 and 7.16.0. Since we depend on 7.15.2 or later and versions 7.15.2 and 7.15.3 have a bug that makes CurlFtpFS do not reuse the connection all the time, the current recommended version of libcurl is either 7.15.4 or the development branch. 




So how do I upgrade curl?

One option, to dnload the latest curl package from [http://curl.haxx.se/dlwiz/?type=bin&os=Linux&flav=Ubuntu&ver=gutsy](http://curl.haxx.se/dlwiz/?type=bin&os=Linux&flav=Ubuntu&ver=gutsy) gave me the error (when ran) that "Error: Dependency is not satisfiable: libc6"



Gutsy has curl 7.16.4, which might be OK.. 
However when running 

 gksudo "update-manager -c"

I get no option to upgrade to Gutsy..

---

### Post by Rene7705 on 2007-09-12
changing all "feisty" to "gutsy" in /etc/apt/source.list, and then running "gksudo "update-manager -d" (click "check"); I get a list of 56 possible upgrades and something about a "partial upgrade"..
Decided not to do that yet; not sure if i'll end up with a stable system.


more info at [http://ubuntuforums.org/showthread.php?t=549054](http://ubuntuforums.org/showthread.php?t=549054)

---

### Post by Rene7705 on 2007-09-12
update: after doing a reboot with "gutsy" instead of "feisty" in my /etc/apt/sources.lst, I got offered 700+ updates including the correct curl version.. So I did that, and threw in the "partial upgrade" that the upgrade manager proposed aswell..

rene@goose:~$ dpkg -l | grep curl
ii  curlftpfs                                  0.9.1-1                       filesystem to access FTP hosts based on FUSE
ii  libcurl3                                   7.16.4-2ubuntu1               Multi-protocol file transfer library (OpenSS
ii  libcurl3-gnutls                            7.16.4-2ubuntu1               Multi-protocol file transfer library (GnuTLS

This is able to setup a FTPS TLSv1 connection to my hoster.
However permissions are still a nightmare, as is reliability of the connection. I see many reconnects in the debug log, but no reason as to why it reconnects all the time..

rene@goose:~/LIVE_WEBSITES_MOUNTED$ sudo chown rene:fuse s.net
rene@goose:~/LIVE_WEBSITES_MOUNTED$ ls -al
total 12
drwxr-xr-x  3 rene rene 4096 2007-09-12 20:23 .
drwxr-xr-x 38 rene rene 4096 2007-09-12 20:33 ..
drwxr-xr-x  2 rene fuse 4096 2007-09-11 22:11 s.net


And after I connect using this:
rene@goose:~$ cat connect_to_servage.sh 
#!
sudo umount /home/rene/LIVE_WEBSITES_MOUNTED/servage.net/
curlftpfs -v -d -o debug,ciphers=TLSv1,user=x:y ftp.s.net /home/rene/LIVE_WEBSITES_MOUNTED/s.net/

rene@goose:~/LIVE_WEBSITES_MOUNTED$ ls -al
total 8
drwxr-xr-x  3 rene rene 4096 2007-09-12 20:23 .
drwxr-xr-x 38 rene rene 4096 2007-09-12 20:33 ..
drwxr-xr-x  1 root root 1024 1970-01-01 01:00 s.net

curlftpfs changes the permissions to root:root

anyways, the connection succeeds and in nautilus i can browse directories.
opening (txt) files in editors from nautilus didnt work at all for me, and from the commandline this happens:


```

rene@goose:~/LIVE_WEBSITES_MOUNTED/s.net/m-themes-0.9p/PT$ ls
ajax_get_stuff.php                   index.php
m_theme.css
.........
rene@goose:~/LIVE_WEBSITES_MOUNTED/snet/m-themes-0.9p/PT$ cat m_theme.css 
cat: mediaBeez_theme.css: Permission denied
rene@goose:~/LIVE_WEBSITES_MOUNTED/s.net/m-themes-0.9p/PT$ cat m_theme.css 
cat: mediaBeez_theme.css: Permission denied
rene@goose:~/LIVE_WEBSITES_MOUNTED/s.net/m-themes-0.9p/PT$ cat m_theme.css 
cat: mediaBeez_theme.css: Permission denied
rene@goose:~/LIVE_WEBSITES_MOUNTED/s.net/m-themes-0.9p/PT$ cat m_theme.css 
/* --- popular makeup in HTML land --- */
body {
        font-family : verdana, arial;
        font-size : 80%;
}
/*

```

---

### Post by Rene7705 on 2007-09-12
Update:
Doing a complete upgrade to gutsy caused all ppl in any of my movies to turn smurf-blue :D
Funniest bug i've seen in a long time..

So i did a reinstall of feisty, then changed all "feisty" to "gutsy" in /etc/apt/sources.list, and after a reboot i upgraded only libcurl, nautilus and firefox..

other apps may need to get upgraded too..

in this environment, curlftpfs at least browses correctly, and doesnt do erratic reconnects anymore..

but accessing files is still very erratic..
I need 4-5 retries to cat a file, and opening in Text Editor is equally prone to failure..

curlftpfs logging shows that connections to the clustered ftp server of my hoster is often either dropped or refused and shifted to a new IP...
here's a sample that shows 2 attempts to open a textfile in Text Editor, first failing second succeeding:
```

* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||50993|)
*   Trying xxx.yyy.67.28... * Connecting to ftp.s.net (xxx.yyy.67.28) port 50993
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 81, error: -13 (Permission denied), outsize: 16
unique: 82, opcode: LOOKUP (1), nodeid: 18, insize: 62
LOOKUP /m-themes-0.9p/PT/doNotPanic.normal.png
   NODEID: 25
   unique: 82, error: 0 (Success), outsize: 136
unique: 83, opcode: OPEN (14), nodeid: 25, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||55555|)
*   Trying xxx.yyy.76.11... * Connecting to ftp.s.net (xxx.yyy.76.11) port 55555
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 83, error: -13 (Permission denied), outsize: 16
unique: 84, opcode: LOOKUP (1), nodeid: 18, insize: 64
LOOKUP /m-themes-0.9p/PT/doNotPanic.selected.png
   NODEID: 26
   unique: 84, error: 0 (Success), outsize: 136
unique: 85, opcode: OPEN (14), nodeid: 26, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||50137|)
*   Trying xxx.yyy.67.29... * Connecting to ftp.s.net (xxx.yyy.67.29) port 50137
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 85, error: -13 (Permission denied), outsize: 16
unique: 86, opcode: LOOKUP (1), nodeid: 18, insize: 69
LOOKUP /m-themes-0.9p/PT/mCMS_dark.normal.png
   NODEID: 32
   unique: 86, error: 0 (Success), outsize: 136
unique: 87, opcode: OPEN (14), nodeid: 32, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||50556|)
*   Trying xxx.yyy.67.28... * Connecting to ftp.s.net (xxx.yyy.67.28) port 50556
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 87, error: -13 (Permission denied), outsize: 16
unique: 88, opcode: LOOKUP (1), nodeid: 18, insize: 71
LOOKUP /m-themes-0.9p/PT/mCMS_dark.selected.png
   NODEID: 33
   unique: 88, error: 0 (Success), outsize: 136
unique: 89, opcode: OPEN (14), nodeid: 33, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||60393|)
*   Trying xxx.yyy.76.12... * Connecting to ftp.s.net (xxx.yyy.76.12) port 60393
> SIZE mCMS_dark.selected.png
< 213 16557
> RETR mCMS_dark.selected.png
< 150 Opening BINARY mode data connection for mCMS_dark.selected.png (16557 bytes)
* Maxdownload = -1
* Getting file with size: 16557
   unique: 89, error: 0 (Success), outsize: 32
OPEN[134788272] flags: 0x8000 /m-themes-0.9p/PT/mCMS_dark.selected.png
unique: 90, opcode: READ (15), nodeid: 33, insize: 64
READ[134788272] 20480 bytes from 0
* Remembering we are in dir m-themes-0.9p/PT/
< 226 Transfer complete.
* Connection #0 to host ftp.s.net left intact
   READ[134788272] 16557 bytes
   unique: 90, error: 0 (Success), outsize: 16573
unique: 91, opcode: FLUSH (25), nodeid: 33, insize: 64
FLUSH[134788272]
   unique: 91, error: 0 (Success), outsize: 16
unique: 92, opcode: RELEASE (18), nodeid: 33, insize: 64
RELEASE[134788272] flags: 0x8000
   unique: 92, error: 0 (Success), outsize: 16
unique: 93, opcode: STATFS (17), nodeid: 18, insize: 40
   unique: 93, error: 0 (Success), outsize: 96
unique: 94, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 94, error: 0 (Success), outsize: 112
unique: 95, opcode: LOOKUP (1), nodeid: 18, insize: 65
LOOKUP /m-themes-0.9p/PT/bleeding_edge.normal.png
   NODEID: 23
   unique: 95, error: 0 (Success), outsize: 136
unique: 96, opcode: OPEN (14), nodeid: 24, insize: 48
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||54128|)
*   Trying xxx.yyy.76.11... * Connecting to ftp.s.net (xxx.yyy.76.11) port 54128
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 96, error: -13 (Permission denied), outsize: 16
unique: 97, opcode: OPEN (14), nodeid: 25, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||58124|)
*   Trying xxx.yyy.67.29... * Connecting to ftp.s.net (xxx.yyy.67.29) port 58124
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 97, error: -13 (Permission denied), outsize: 16
unique: 98, opcode: OPEN (14), nodeid: 26, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||53291|)
*   Trying xxx.yyy.67.28... * Connecting to ftp.s.net (xxx.yyy.67.28) port 53291
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 98, error: -13 (Permission denied), outsize: 16
unique: 99, opcode: OPEN (14), nodeid: 32, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56567|)
*   Trying xxx.yyy.76.12... * Connecting to ftp.s.net (xxx.yyy.76.12) port 56567
> SIZE mCMS_dark.normal.png
< 213 12808
> RETR mCMS_dark.normal.png
< 150 Opening BINARY mode data connection for mCMS_dark.normal.png (12808 bytes)
* Maxdownload = -1
* Getting file with size: 12808
   unique: 99, error: 0 (Success), outsize: 32
OPEN[134788272] flags: 0x8000 /m-themes-0.9p/PT/mCMS_dark.normal.png
unique: 100, opcode: READ (15), nodeid: 32, insize: 64
READ[134788272] 16384 bytes from 0
* Remembering we are in dir m-themes-0.9p/PT/
< 226 Transfer complete.
* Connection #0 to host ftp.s.net left intact
   READ[134788272] 12808 bytes
   unique: 100, error: 0 (Success), outsize: 12824
unique: 101, opcode: FLUSH (25), nodeid: 32, insize: 64
FLUSH[134788272]
   unique: 101, error: 0 (Success), outsize: 16
unique: 102, opcode: RELEASE (18), nodeid: 32, insize: 64
RELEASE[134788272] flags: 0x8000
   unique: 102, error: 0 (Success), outsize: 16
unique: 103, opcode: GETATTR (3), nodeid: 33, insize: 40
   unique: 103, error: 0 (Success), outsize: 112
unique: 104, opcode: LOOKUP (1), nodeid: 18, insize: 65
LOOKUP /m-themes-0.9p/PT/editor_articles_css3.css
   NODEID: 27
   unique: 104, error: 0 (Success), outsize: 136
unique: 105, opcode: OPEN (14), nodeid: 27, insize: 48
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
unique: 106, opcode: STATFS (17), nodeid: 18, insize: 40
   unique: 106, error: 0 (Success), outsize: 96
unique: 107, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 107, error: 0 (Success), outsize: 112
< 229 Entering Extended Passive Mode (|||58256|)
*   Trying xxx.yyy.76.11... * Connecting to ftp.s.net (xxx.yyy.76.11) port 58256
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 105, error: -13 (Permission denied), outsize: 16
unique: 108, opcode: LOOKUP (1), nodeid: 18, insize: 64
LOOKUP /m-themes-0.9p/PT/editor_articles_ie5.css
   NODEID: 28
   unique: 108, error: 0 (Success), outsize: 136
unique: 109, opcode: OPEN (14), nodeid: 28, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
unique: 110, opcode: STATFS (17), nodeid: 18, insize: 40
   unique: 110, error: 0 (Success), outsize: 96
unique: 111, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 111, error: 0 (Success), outsize: 112
< 229 Entering Extended Passive Mode (|||54335|)
*   Trying xxx.yyy.67.29... * Connecting to ftp.s.net (xxx.yyy.67.29) port 54335
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 109, error: -13 (Permission denied), outsize: 16
unique: 112, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /m-themes-0.9p
   NODEID: 8
   unique: 112, error: 0 (Success), outsize: 136
unique: 113, opcode: LOOKUP (1), nodeid: 8, insize: 43
LOOKUP /m-themes-0.9p/PT
   NODEID: 18
   unique: 113, error: 0 (Success), outsize: 136
unique: 114, opcode: LOOKUP (1), nodeid: 8, insize: 43
LOOKUP /m-themes-0.9p/PT
   NODEID: 18
   unique: 114, error: 0 (Success), outsize: 136
unique: 115, opcode: STATFS (17), nodeid: 18, insize: 40
   unique: 115, error: 0 (Success), outsize: 96
unique: 116, opcode: LOOKUP (1), nodeid: 18, insize: 51
LOOKUP /m-themes-0.9p/PT/latest.css
   NODEID: 31
   unique: 116, error: 0 (Success), outsize: 136
unique: 117, opcode: OPEN (14), nodeid: 31, insize: 48
* Expire cleared
* Closing connection #0
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* About to connect() to ftp.s.net port 21 (#0)
*   Trying xxx.yyy.76.12... unique: 118, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 118, error: 0 (Success), outsize: 112
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
< 220 FTP Server #2
> USER rveerman
< 331 Password required for rveerman.
> PASS rev3dace
< 230 User rveerman logged in.
> PWD
< 257 "/" is current directory.
* Entry path is '/'
> CWD m-themes-0.9p
< 250 CWD command successful
> CWD PT
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||60845|)
*   Trying xxx.yyy.67.28... * Connecting to ftp.s.net (xxx.yyy.67.28) port 60845
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 117, error: -13 (Permission denied), outsize: 16
unique: 119, opcode: LOOKUP (1), nodeid: 18, insize: 60
LOOKUP /m-themes-0.9p/PT/m_theme.css
   NODEID: 34
   unique: 119, error: 0 (Success), outsize: 136
unique: 120, opcode: OPEN (14), nodeid: 34, insize: 48
* Expire cleared
* Closing connection #0
unique: 121, opcode: STATFS (17), nodeid: 18, insize: 40
   unique: 121, error: 0 (Success), outsize: 96
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* About to connect() to ftp.s.net port 21 (#0)
*   Trying xxx.yyy.76.12... unique: 122, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 122, error: 0 (Success), outsize: 112
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
< 220 FTP Server #2
> USER rveerman
< 331 Password required for rveerman.
> PASS rev3dace
< 230 User rveerman logged in.
> PWD
< 257 "/" is current directory.
* Entry path is '/'
> CWD m-themes-0.9p
< 250 CWD command successful
> CWD PT
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||60845|)
*   Trying xxx.yyy.67.28... * Connecting to ftp.s.net (xxx.yyy.67.28) port 60845
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 120, error: -13 (Permission denied), outsize: 16
unique: 123, opcode: STATFS (17), nodeid: 18, insize: 40
   unique: 123, error: 0 (Success), outsize: 96
unique: 124, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 124, error: 0 (Success), outsize: 112
unique: 125, opcode: LOOKUP (1), nodeid: 18, insize: 65
LOOKUP /m-themes-0.9p/PT/m_theme_css3.css
   NODEID: 36
   unique: 125, error: 0 (Success), outsize: 136
unique: 126, opcode: OPEN (14), nodeid: 36, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
> CWD /
< 250 CWD command successful
> CWD m-themes-0.9p
< 250 CWD command successful
> CWD PT
< 250 CWD command successful
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||49620|)
*   Trying xxx.yyy.76.12... * Connecting to ftp.s.net (xxx.yyy.76.12) port 49620
> TYPE I
< 200 Type set to I
> SIZE m_theme_css3.css
< 213 3815
> RETR m_theme_css3.css
< 150 Opening BINARY mode data connection for m_theme_css3.css (3815 bytes)
* Maxdownload = -1
* Getting file with size: 3815
   unique: 126, error: 0 (Success), outsize: 32
OPEN[134788272] flags: 0x8000 /m-themes-0.9p/PT/m_theme_css3.css
unique: 127, opcode: READ (15), nodeid: 36, insize: 64
READ[134788272] 4096 bytes from 0
* Remembering we are in dir m-themes-0.9p/PT/
< 226 Transfer complete.
* Connection #0 to host ftp.s.net left intact
   READ[134788272] 3815 bytes
   unique: 127, error: 0 (Success), outsize: 3831
unique: 128, opcode: STATFS (17), nodeid: 18, insize: 40
   unique: 128, error: 0 (Success), outsize: 96
unique: 129, opcode: FLUSH (25), nodeid: 36, insize: 64
FLUSH[134788272]
   unique: 129, error: 0 (Success), outsize: 16
unique: 130, opcode: RELEASE (18), nodeid: 36, insize: 64
RELEASE[134788272] flags: 0x8000
   unique: 130, error: 0 (Success), outsize: 16
unique: 131, opcode: LOOKUP (1), nodeid: 18, insize: 64
LOOKUP /m-themes-0.9p/PT/m_theme_ie5.css
   NODEID: 37
   unique: 131, error: 0 (Success), outsize: 136
unique: 132, opcode: OPEN (14), nodeid: 37, insize: 48
unique: 133, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 133, error: 0 (Success), outsize: 112
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||56093|)
*   Trying xxx.yyy.76.11... * Connecting to ftp.s.net (xxx.yyy.76.11) port 56093
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 132, error: -13 (Permission denied), outsize: 16
unique: 134, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /m-themes-0.9p
   NODEID: 8
   unique: 134, error: 0 (Success), outsize: 136
unique: 135, opcode: LOOKUP (1), nodeid: 8, insize: 43
LOOKUP /m-themes-0.9p/PT
   NODEID: 18
   unique: 135, error: 0 (Success), outsize: 136
unique: 136, opcode: STATFS (17), nodeid: 18, insize: 40
   unique: 136, error: 0 (Success), outsize: 96
unique: 137, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 137, error: 0 (Success), outsize: 112
unique: 138, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 138, error: 0 (Success), outsize: 112
unique: 139, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /m-themes-0.9p
   NODEID: 8
   unique: 139, error: 0 (Success), outsize: 136
unique: 140, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /m-themes-0.9p
   NODEID: 8
   unique: 140, error: 0 (Success), outsize: 136
unique: 141, opcode: LOOKUP (1), nodeid: 8, insize: 43
LOOKUP /m-themes-0.9p/PT
   NODEID: 18
   unique: 141, error: 0 (Success), outsize: 136
unique: 142, opcode: LOOKUP (1), nodeid: 8, insize: 43
unique: 143, opcode: LOOKUP (1), nodeid: 18, insize: 64
LOOKUP /m-themes-0.9p/PT/editor_articles_ie5.css
   NODEID: 28
   unique: 143, error: 0 (Success), outsize: 136
LOOKUP /m-themes-0.9p/PT
   NODEID: 18
   unique: 142, error: 0 (Success), outsize: 136
unique: 144, opcode: LOOKUP (1), nodeid: 18, insize: 64
LOOKUP /m-themes-0.9p/PT/editor_articles_ie5.css
   NODEID: 28
   unique: 144, error: 0 (Success), outsize: 136
unique: 145, opcode: OPEN (14), nodeid: 28, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||49521|)
*   Trying xxx.yyy.67.29... * Connecting to ftp.s.net (xxx.yyy.67.29) port 49521
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 145, error: -13 (Permission denied), outsize: 16
unique: 146, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 146, error: 0 (Success), outsize: 112
unique: 147, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /m-themes-0.9p
   NODEID: 8
   unique: 147, error: 0 (Success), outsize: 136
unique: 148, opcode: LOOKUP (1), nodeid: 8, insize: 43
LOOKUP /m-themes-0.9p/PT
   NODEID: 18
   unique: 148, error: 0 (Success), outsize: 136
unique: 149, opcode: LOOKUP (1), nodeid: 18, insize: 64
LOOKUP /m-themes-0.9p/PT/editor_articles_ie5.css
   NODEID: 28
   unique: 149, error: 0 (Success), outsize: 136
unique: 150, opcode: OPEN (14), nodeid: 28, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||63982|)
*   Trying xxx.yyy.67.28... * Connecting to ftp.s.net (xxx.yyy.67.28) port 63982
* Connection refused
* Failed connect to ftp.s.net:21; Operation now in progress
   unique: 150, error: -13 (Permission denied), outsize: 16
unique: 151, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /m-themes-0.9p
   NODEID: 8
   unique: 151, error: 0 (Success), outsize: 136
unique: 152, opcode: LOOKUP (1), nodeid: 8, insize: 43
LOOKUP /m-themes-0.9p/PT
   NODEID: 18
   unique: 152, error: 0 (Success), outsize: 136
unique: 153, opcode: LOOKUP (1), nodeid: 18, insize: 64
LOOKUP /m-themes-0.9p/PT/editor_articles_ie5.css
   NODEID: 28
   unique: 153, error: 0 (Success), outsize: 136
unique: 154, opcode: OPEN (14), nodeid: 28, insize: 48
* Expire cleared
* Couldn't find host ftp.s.net in the .netrc file, using defaults
* Re-using existing connection! (#0) with host ftp.s.net
* Connected to ftp.s.net (xxx.yyy.76.12) port 21 (#0)
* Request has same path as previous transfer
> EPSV
* Connect data stream passively
< 229 Entering Extended Passive Mode (|||63709|)
*   Trying xxx.yyy.76.12... * Connecting to ftp.s.net (xxx.yyy.76.12) port 63709
> SIZE editor_articles_ie5.css
< 213 1409
> RETR editor_articles_ie5.css
< 150 Opening BINARY mode data connection for editor_articles_ie5.css (1409 bytes)
* Maxdownload = -1
* Getting file with size: 1409
   unique: 154, error: 0 (Success), outsize: 32
OPEN[134788272] flags: 0x0 /m-themes-0.9p/PT/editor_articles_ie5.css
unique: 155, opcode: READ (15), nodeid: 28, insize: 64
READ[134788272] 4096 bytes from 0
* Remembering we are in dir m-themes-0.9p/PT/
< 226 Transfer complete.
* Connection #0 to host ftp.s.net left intact
   READ[134788272] 1409 bytes
   unique: 155, error: 0 (Success), outsize: 1425
unique: 156, opcode: FLUSH (25), nodeid: 28, insize: 64
FLUSH[134788272]
   unique: 156, error: 0 (Success), outsize: 16
unique: 157, opcode: RELEASE (18), nodeid: 28, insize: 64
RELEASE[134788272] flags: 0x0
   unique: 157, error: 0 (Success), outsize: 16
unique: 158, opcode: GETATTR (3), nodeid: 28, insize: 40
   unique: 158, error: 0 (Success), outsize: 112
unique: 159, opcode: LOOKUP (1), nodeid: 1, insize: 62
LOOKUP /m-themes-0.9p
   NODEID: 8
   unique: 159, error: 0 (Success), outsize: 136
unique: 160, opcode: LOOKUP (1), nodeid: 8, insize: 43
LOOKUP /m-themes-0.9p/PT
   NODEID: 18
   unique: 160, error: 0 (Success), outsize: 136
unique: 161, opcode: LOOKUP (1), nodeid: 18, insize: 64
LOOKUP /m-themes-0.9p/PT/editor_articles_ie5.css
   NODEID: 28
   unique: 161, error: 0 (Success), outsize: 136

```

---

