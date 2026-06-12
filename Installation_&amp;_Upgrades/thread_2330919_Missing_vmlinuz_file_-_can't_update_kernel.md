---
title: "Missing vmlinuz file - can't update kernel"
date: 2016-07-16
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2016-07-16
This is the error I got when trying the latest update on 16.04.

E: linux-image-4.2.0-41-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-extra-4.2.0-41-generic: dependency problems - leaving unconfigured

How this happened - when in 15.10 I was deleting excess files in /boot.  I deleted the current one. The one mentioned above.  A big whoops - to say the least.  Tried to fix with synaptic, no luck, then moved on to 16.04 and some more fix with synaptic and it still wants the old image.

What can I do to remedy this?  At least I now discovered the best way to clean out /boot and it's in a file on my desktop.

Ron

---

### Post by Bashing-om on 2016-07-16
Alligator; Hello;

These things do happen. Let's see what it is going to take to put things back aright.
Post back - Between Code Tags - the outputs of terminal commands:
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]if the package manager is not happy
[INDENT][INDENT][INDENT]nobody is happy
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-16
Here it is.  Thanks
uname -r
4.4.0-28-generic

___________________________________________________________

```
ls -al /usr/src
total 500
drwxrwsr-x 123 root src  12288 Jul 16 07:59 .
drwxr-xr-x  13 root root  4096 Jul  9 02:07 ..
drwxr-xr-x   2 root root  4096 Jul  9 01:56 bbswitch-0.8
drwxr-xr-x  24 root root  4096 Aug 30  2014 linux-headers-3.13.0-35
drwxr-xr-x   7 root root  4096 Aug 30  2014 linux-headers-3.13.0-35-generic
drwxr-xr-x  24 root root  4096 Sep 24  2014 linux-headers-3.13.0-36
drwxr-xr-x   7 root root  4096 Sep 24  2014 linux-headers-3.13.0-36-generic
drwxr-xr-x  24 root root  4096 Oct 10  2014 linux-headers-3.13.0-37
drwxr-xr-x   7 root root  4096 Oct 10  2014 linux-headers-3.13.0-37-generic
drwxr-xr-x  24 root root  4096 Oct 29  2014 linux-headers-3.13.0-39
drwxr-xr-x   7 root root  4096 Oct 29  2014 linux-headers-3.13.0-39-generic
drwxr-xr-x  24 root root  4096 Nov 26  2014 linux-headers-3.13.0-40
drwxr-xr-x   7 root root  4096 Nov 26  2014 linux-headers-3.13.0-40-generic
drwxr-xr-x  24 root root  4096 Dec 12  2014 linux-headers-3.13.0-43
drwxr-xr-x   7 root root  4096 Dec 12  2014 linux-headers-3.13.0-43-generic
drwxr-xr-x  24 root root  4096 Jan 12  2015 linux-headers-3.13.0-44
drwxr-xr-x   7 root root  4096 Jan 12  2015 linux-headers-3.13.0-44-generic
drwxr-xr-x  24 root root  4096 Feb  3  2015 linux-headers-3.13.0-45
drwxr-xr-x   7 root root  4096 Feb  3  2015 linux-headers-3.13.0-45-generic
drwxr-xr-x  24 root root  4096 Mar 13  2015 linux-headers-3.13.0-46
drwxr-xr-x   7 root root  4096 Mar 13  2015 linux-headers-3.13.0-46-generic
drwxr-xr-x  24 root root  4096 Apr 15  2015 linux-headers-3.13.0-49
drwxr-xr-x   7 root root  4096 Apr 15  2015 linux-headers-3.13.0-49-generic
drwxr-xr-x  24 root root  4096 May  2  2015 linux-headers-3.13.0-51
drwxr-xr-x   7 root root  4096 May  2  2015 linux-headers-3.13.0-51-generic
drwxr-xr-x  24 root root  4096 May  9  2015 linux-headers-3.13.0-52
drwxr-xr-x   7 root root  4096 May  9  2015 linux-headers-3.13.0-52-generic
drwxr-xr-x  24 root root  4096 May 21  2015 linux-headers-3.13.0-53
drwxr-xr-x   7 root root  4096 May 21  2015 linux-headers-3.13.0-53-generic
drwxr-xr-x  24 root root  4096 Jun 11  2015 linux-headers-3.13.0-54
drwxr-xr-x   7 root root  4096 Jun 11  2015 linux-headers-3.13.0-54-generic
drwxr-xr-x  24 root root  4096 Jun 21  2015 linux-headers-3.13.0-55
drwxr-xr-x   7 root root  4096 Jun 21  2015 linux-headers-3.13.0-55-generic
drwxr-xr-x  24 root root  4096 Jul 11  2015 linux-headers-3.13.0-57
drwxr-xr-x   7 root root  4096 Jul 11  2015 linux-headers-3.13.0-57-generic
drwxr-xr-x  24 root root  4096 Jul 23  2015 linux-headers-3.13.0-58
drwxr-xr-x   7 root root  4096 Jul 23  2015 linux-headers-3.13.0-58-generic
drwxr-xr-x  24 root root  4096 Jul 29  2015 linux-headers-3.13.0-59
drwxr-xr-x   7 root root  4096 Jul 29  2015 linux-headers-3.13.0-59-generic
drwxr-xr-x  24 root root  4096 Jul 31  2015 linux-headers-3.13.0-61
drwxr-xr-x   7 root root  4096 Jul 31  2015 linux-headers-3.13.0-61-generic
drwxr-xr-x  24 root root  4096 Aug 21  2015 linux-headers-3.13.0-62
drwxr-xr-x   7 root root  4096 Aug 21  2015 linux-headers-3.13.0-62-generic
drwxr-xr-x  24 root root  4096 Sep  7  2015 linux-headers-3.13.0-63
drwxr-xr-x   7 root root  4096 Sep  7  2015 linux-headers-3.13.0-63-generic
drwxr-xr-x  24 root root  4096 Oct  7  2015 linux-headers-3.13.0-65
drwxr-xr-x   7 root root  4096 Oct  7  2015 linux-headers-3.13.0-65-generic
drwxr-xr-x  24 root root  4096 Oct 20  2015 linux-headers-3.13.0-66
drwxr-xr-x   7 root root  4096 Oct 20  2015 linux-headers-3.13.0-66-generic
drwxr-xr-x  24 root root  4096 Nov  7  2015 linux-headers-3.13.0-67
drwxr-xr-x   7 root root  4096 Nov  7  2015 linux-headers-3.13.0-67-generic
drwxr-xr-x  24 root root  4096 Nov 12  2015 linux-headers-3.13.0-68
drwxr-xr-x   7 root root  4096 Nov 12  2015 linux-headers-3.13.0-68-generic
drwxr-xr-x  24 root root  4096 Dec 20  2015 linux-headers-3.13.0-74
drwxr-xr-x   7 root root  4096 Dec 20  2015 linux-headers-3.13.0-74-generic
drwxr-xr-x  24 root root  4096 Jan 22 09:04 linux-headers-3.13.0-76
drwxr-xr-x   7 root root  4096 Jan 22 09:04 linux-headers-3.13.0-76-generic
drwxr-xr-x  24 root root  4096 Feb  4 01:47 linux-headers-3.13.0-77
drwxr-xr-x   7 root root  4096 Feb  4 01:47 linux-headers-3.13.0-77-generic
drwxr-xr-x  24 root root  4096 Feb 24 18:15 linux-headers-3.13.0-79
drwxr-xr-x   7 root root  4096 Feb 24 18:15 linux-headers-3.13.0-79-generic
drwxr-xr-x  24 root root  4096 Mar 16 08:10 linux-headers-3.13.0-83
drwxr-xr-x   7 root root  4096 Mar 16 08:11 linux-headers-3.13.0-83-generic
drwxr-xr-x  24 root root  4096 Apr  9  2013 linux-headers-3.2.0-40
drwxr-xr-x   7 root root  4096 Apr  9  2013 linux-headers-3.2.0-40-generic
drwxr-xr-x  24 root root  4096 May  2  2013 linux-headers-3.2.0-41
drwxr-xr-x   7 root root  4096 May  2  2013 linux-headers-3.2.0-41-generic
drwxr-xr-x  24 root root  4096 May 17  2013 linux-headers-3.2.0-43
drwxr-xr-x   7 root root  4096 May 17  2013 linux-headers-3.2.0-43-generic
drwxr-xr-x  24 root root  4096 May 24  2013 linux-headers-3.2.0-44
drwxr-xr-x   7 root root  4096 May 24  2013 linux-headers-3.2.0-44-generic
drwxr-xr-x  24 root root  4096 Jun  3  2013 linux-headers-3.2.0-45
drwxr-xr-x   7 root root  4096 Jun  3  2013 linux-headers-3.2.0-45-generic
drwxr-xr-x  24 root root  4096 Jun 18  2013 linux-headers-3.2.0-48
drwxr-xr-x   7 root root  4096 Jun 18  2013 linux-headers-3.2.0-48-generic
drwxr-xr-x  24 root root  4096 Jul  9  2013 linux-headers-3.2.0-49
drwxr-xr-x   7 root root  4096 Jul  9  2013 linux-headers-3.2.0-49-generic
drwxr-xr-x  24 root root  4096 Aug  3  2013 linux-headers-3.2.0-51
drwxr-xr-x   7 root root  4096 Aug  3  2013 linux-headers-3.2.0-51-generic
drwxr-xr-x  24 root root  4096 Aug 20  2013 linux-headers-3.2.0-52
drwxr-xr-x   7 root root  4096 Aug 20  2013 linux-headers-3.2.0-52-generic
drwxr-xr-x  24 root root  4096 Sep 10  2013 linux-headers-3.2.0-53
drwxr-xr-x   7 root root  4096 Sep 10  2013 linux-headers-3.2.0-53-generic
drwxr-xr-x  24 root root  4096 Sep 30  2013 linux-headers-3.2.0-54
drwxr-xr-x   7 root root  4096 Sep 30  2013 linux-headers-3.2.0-54-generic
drwxr-xr-x  24 root root  4096 Oct 22  2013 linux-headers-3.2.0-55
drwxr-xr-x   7 root root  4096 Oct 22  2013 linux-headers-3.2.0-55-generic
drwxr-xr-x  24 root root  4096 Nov 17  2013 linux-headers-3.2.0-56
drwxr-xr-x   7 root root  4096 Nov 17  2013 linux-headers-3.2.0-56-generic
drwxr-xr-x  24 root root  4096 Dec  5  2013 linux-headers-3.2.0-57
drwxr-xr-x   7 root root  4096 Dec  5  2013 linux-headers-3.2.0-57-generic
drwxr-xr-x  24 root root  4096 Jan  3  2014 linux-headers-3.2.0-58
drwxr-xr-x   7 root root  4096 Jan  3  2014 linux-headers-3.2.0-58-generic
drwxr-xr-x  24 root root  4096 Feb 20  2014 linux-headers-3.2.0-59
drwxr-xr-x   7 root root  4096 Feb 20  2014 linux-headers-3.2.0-59-generic
drwxr-xr-x  24 root root  4096 Mar  7  2014 linux-headers-3.2.0-60
drwxr-xr-x   7 root root  4096 Mar  7  2014 linux-headers-3.2.0-60-generic
drwxr-xr-x  24 root root  4096 May 22  2014 linux-headers-3.2.0-61
drwxr-xr-x   7 root root  4096 May 22  2014 linux-headers-3.2.0-61-generic
drwxr-xr-x  24 root root  4096 May 27  2014 linux-headers-3.2.0-63
drwxr-xr-x   7 root root  4096 May 27  2014 linux-headers-3.2.0-63-generic
drwxr-xr-x  24 root root  4096 Jun  6  2014 linux-headers-3.2.0-64
drwxr-xr-x   7 root root  4096 Jun  6  2014 linux-headers-3.2.0-64-generic
drwxr-xr-x  24 root root  4096 Jul  6  2014 linux-headers-3.2.0-65
drwxr-xr-x   7 root root  4096 Jul  6  2014 linux-headers-3.2.0-65-generic
drwxr-xr-x  24 root root  4096 Jul 17  2014 linux-headers-3.2.0-67
drwxr-xr-x   7 root root  4096 Jul 17  2014 linux-headers-3.2.0-67-generic
drwxr-xr-x  24 root root  4096 Apr  3 00:56 linux-headers-4.2.0-34
drwxr-xr-x   7 root root  4096 Apr  3 00:56 linux-headers-4.2.0-34-generic
drwxr-xr-x  24 root root  4096 Apr 10 01:39 linux-headers-4.2.0-35
drwxr-xr-x   7 root root  4096 Apr 10 01:39 linux-headers-4.2.0-35-generic
drwxr-xr-x  24 root root  4096 May 18 03:26 linux-headers-4.2.0-36
drwxr-xr-x   7 root root  4096 May 18 03:26 linux-headers-4.2.0-36-generic
drwxr-xr-x  24 root root  4096 Jul  7 14:13 linux-headers-4.2.0-41
drwxr-xr-x   7 root root  4096 Jul  7 14:13 linux-headers-4.2.0-41-generic
drwxr-xr-x  27 root root  4096 Jul  9 01:44 linux-headers-4.4.0-21
drwxr-xr-x   7 root root  4096 Jul  9 01:44 linux-headers-4.4.0-21-generic
drwxr-xr-x  27 root root  4096 Jul 10 02:54 linux-headers-4.4.0-28
drwxr-xr-x   7 root root  4096 Jul 10 02:54 linux-headers-4.4.0-28-generic
drwxr-xr-x  27 root root  4096 Jul 16 07:59 linux-headers-4.4.0-31
drwxr-xr-x   7 root root  4096 Jul 16 07:59 linux-headers-4.4.0-31-generic
drwxr-xr-x   4 root root  4096 Jul  9 01:39 nvidia-340-340.96
drwxr-xr-x   6 root root  4096 Mar 25 19:21 oem-audio-hda-daily-0.201603240932~ubuntu14.04.1
```

_____________________________________________________________________________________

```
ls -al /lib/modules/
total 272
drwxr-xr-x 68 root root 4096 Jul 16 07:58 .
drwxr-xr-x 26 root root 4096 Jul  9 02:00 ..
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-10-generic
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-11-generic
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-12-generic
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-13-generic
drwxr-xr-x  5 root root 4096 Apr 13  2012 2.6.38-8-generic
drwxr-xr-x  5 root root 4096 Apr 10  2013 3.0.0-32-generic
drwxr-xr-x  5 root root 4096 Dec 12  2014 3.13.0-35-generic
drwxr-xr-x  5 root root 4096 Dec 12  2014 3.13.0-36-generic
drwxr-xr-x  5 root root 4096 Dec 12  2014 3.13.0-37-generic
drwxr-xr-x  5 root root 4096 Dec 12  2014 3.13.0-39-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-40-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-43-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-44-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-45-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-46-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-49-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-51-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-52-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-53-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-54-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-55-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-57-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-58-generic
drwxr-xr-x  5 root root 4096 Aug  6  2015 3.13.0-59-generic
drwxr-xr-x  5 root root 4096 Sep 30  2015 3.13.0-61-generic
drwxr-xr-x  5 root root 4096 Sep 30  2015 3.13.0-62-generic
drwxr-xr-x  5 root root 4096 Nov 23  2015 3.13.0-63-generic
drwxr-xr-x  5 root root 4096 Nov 23  2015 3.13.0-65-generic
drwxr-xr-x  5 root root 4096 Nov 23  2015 3.13.0-66-generic
drwxr-xr-x  5 root root 4096 Nov 23  2015 3.13.0-67-generic
drwxr-xr-x  5 root root 4096 Apr  2 23:02 3.13.0-68-generic
drwxr-xr-x  5 root root 4096 Apr  2 23:03 3.13.0-74-generic
drwxr-xr-x  5 root root 4096 Apr  2 23:04 3.13.0-76-generic
drwxr-xr-x  5 root root 4096 Apr  2 23:04 3.13.0-77-generic
drwxr-xr-x  5 root root 4096 Apr  2 23:05 3.13.0-79-generic
drwxr-xr-x  6 root root 4096 Apr  4 13:54 3.13.0-83-generic
drwxr-xr-x  5 root root 4096 Jun  3  2015 3.2.0-39-generic
drwxr-xr-x  5 root root 4096 Aug 20  2013 3.2.0-40-generic
drwxr-xr-x  5 root root 4096 Aug 20  2013 3.2.0-41-generic
drwxr-xr-x  5 root root 4096 Aug 20  2013 3.2.0-43-generic
drwxr-xr-x  5 root root 4096 Aug 20  2013 3.2.0-44-generic
drwxr-xr-x  5 root root 4096 Aug 20  2013 3.2.0-45-generic
drwxr-xr-x  5 root root 4096 Aug 20  2013 3.2.0-48-generic
drwxr-xr-x  5 root root 4096 Aug 20  2013 3.2.0-49-generic
drwxr-xr-x  5 root root 4096 Feb  4  2014 3.2.0-51-generic
drwxr-xr-x  5 root root 4096 Feb  4  2014 3.2.0-52-generic
drwxr-xr-x  5 root root 4096 Feb  4  2014 3.2.0-53-generic
drwxr-xr-x  5 root root 4096 Feb  4  2014 3.2.0-54-generic
drwxr-xr-x  5 root root 4096 Feb  4  2014 3.2.0-55-generic
drwxr-xr-x  5 root root 4096 Feb  4  2014 3.2.0-56-generic
drwxr-xr-x  5 root root 4096 Feb  4  2014 3.2.0-57-generic
drwxr-xr-x  5 root root 4096 Aug 12  2014 3.2.0-58-generic
drwxr-xr-x  5 root root 4096 Aug 12  2014 3.2.0-59-generic
drwxr-xr-x  5 root root 4096 Aug 12  2014 3.2.0-60-generic
drwxr-xr-x  5 root root 4096 Aug 12  2014 3.2.0-61-generic
drwxr-xr-x  5 root root 4096 Aug 12  2014 3.2.0-63-generic
drwxr-xr-x  5 root root 4096 Aug 12  2014 3.2.0-64-generic
drwxr-xr-x  5 root root 4096 Aug 12  2014 3.2.0-65-generic
drwxr-xr-x  4 root root 4096 Dec 12  2014 3.2.0-67-generic
drwxr-xr-x  5 root root 4096 Jul  9 01:55 4.2.0-34-generic
drwxr-xr-x  5 root root 4096 Jul  9 01:56 4.2.0-35-generic
drwxr-xr-x  6 root root 4096 Jul  9 03:24 4.2.0-36-generic
drwxr-xr-x  5 root root 4096 Jul  9 01:56 4.2.0-41-generic
drwxr-xr-x  6 root root 4096 Jul  9 03:25 4.4.0-21-generic
drwxr-xr-x  6 root root 4096 Jul 10 03:06 4.4.0-28-generic
drwxr-xr-x  6 root root 4096 Jul 16 08:01 4.4.0-31-generic
```

_____________________________________________________

```
ls -al /boot/
total 272189
drwxr-xr-x  4 root root     6144 Jul 16 08:02 .
drwxr-xr-x 25 root root     4096 Jul 16 08:00 ..
-rw-r--r--  1 root root  1165578 Mar 10 19:35 abi-3.13.0-83-generic
-rw-r--r--  1 root root  1312645 Mar 10 18:11 abi-4.2.0-34-generic
-rw-r--r--  1 root root  1313407 May 12 19:58 abi-4.2.0-36-generic
-rw-r--r--  1 root root  1239577 Apr 18 16:21 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1240018 Jun 24 06:03 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12 19:59 abi-4.4.0-31-generic
-rw-r--r--  1 root root   165918 Mar 10 19:35 config-3.13.0-83-generic
-rw-r--r--  1 root root   184888 Mar 10 18:11 config-4.2.0-34-generic
-rw-r--r--  1 root root   184888 May 12 19:58 config-4.2.0-36-generic
-rw-r--r--  1 root root   189412 Apr 18 16:21 config-4.4.0-21-generic
-rw-r--r--  1 root root   189533 Jun 24 06:03 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12 19:59 config-4.4.0-31-generic
drwxr-xr-x  5 root root     8192 Jul 16 08:10 grub
-rw-r--r--  1 root root 29618704 Apr  3 10:13 initrd.img-3.13.0-83-generic
-rw-r--r--  1 root root 33579846 Apr  4 13:57 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root 33898697 Jul  9 03:23 initrd.img-4.2.0-36-generic
-rw-r--r--  1 root root 36088793 Jul  9 03:37 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 36103081 Jul 10 03:08 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 36076647 Jul 16 08:02 initrd.img-4.4.0-31-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3393725 Mar 10 19:35 System.map-3.13.0-83-generic
-rw-------  1 root root  3744589 Mar 10 18:11 System.map-4.2.0-34-generic
-rw-------  1 root root  3745958 May 12 19:58 System.map-4.2.0-36-generic
-rw-------  1 root root  3853719 Apr 18 16:21 System.map-4.4.0-21-generic
-rw-------  1 root root  3859655 Jun 24 06:03 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12 19:59 System.map-4.4.0-31-generic
-rw-------  1 root root  5827776 Mar 10 19:35 vmlinuz-3.13.0-83-generic
-rw-------  1 root root  6808528 Mar 10 18:11 vmlinuz-4.2.0-34-generic
-rw-------  1 root root  6830352 May 12 19:58 vmlinuz-4.2.0-36-generic
-rw-------  1 root root  7013968 Apr 18 16:21 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7026864 Jun 24 06:03 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12 19:59 vmlinuz-4.4.0-31-generic
```

___________________________________________________________________

```
dpkg -l | grep linux-
ii  linux-base                                           4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                       1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                        4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-35                              3.13.0-35.62                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                      3.13.0-35.62                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                              3.13.0-36.63                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                      3.13.0-36.63                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                              3.13.0-37.64                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                      3.13.0-37.64                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                              3.13.0-39.66                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                      3.13.0-39.66                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-40                              3.13.0-40.69                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                      3.13.0-40.69                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                              3.13.0-43.72                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                      3.13.0-43.72                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                              3.13.0-44.73                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                      3.13.0-44.73                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                              3.13.0-45.74                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                      3.13.0-45.74                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                              3.13.0-46.79                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                      3.13.0-46.79                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                              3.13.0-49.83                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                      3.13.0-49.83                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-51                              3.13.0-51.84                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                      3.13.0-51.84                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                              3.13.0-52.86                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                      3.13.0-52.86                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                              3.13.0-53.89                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                      3.13.0-53.89                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-54                              3.13.0-54.91                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                      3.13.0-54.91                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-55                              3.13.0-55.94                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                      3.13.0-55.94                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                              3.13.0-57.95                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                      3.13.0-57.95                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                              3.13.0-58.97                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                      3.13.0-58.97                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                              3.13.0-59.98                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                      3.13.0-59.98                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-61                              3.13.0-61.100                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                      3.13.0-61.100                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                              3.13.0-62.102                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                      3.13.0-62.102                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                              3.13.0-63.103                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                      3.13.0-63.103                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                              3.13.0-65.106                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                      3.13.0-65.106                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                              3.13.0-66.108                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                      3.13.0-66.108                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                              3.13.0-67.110                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                      3.13.0-67.110                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-68                              3.13.0-68.111                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                      3.13.0-68.111                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-74                              3.13.0-74.118                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                      3.13.0-74.118                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-76                              3.13.0-76.120                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                      3.13.0-76.120                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-77                              3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                      3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                              3.13.0-79.123                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                      3.13.0-79.123                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-83                              3.13.0-83.127                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                      3.13.0-83.127                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-40                               3.2.0-40.64                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic                       3.2.0-40.64                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-41                               3.2.0-41.66                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic                       3.2.0-41.66                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-43                               3.2.0-43.68                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic                       3.2.0-43.68                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-44                               3.2.0-44.69                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic                       3.2.0-44.69                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-45                               3.2.0-45.70                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic                       3.2.0-45.70                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48                               3.2.0-48.74                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic                       3.2.0-48.74                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-49                               3.2.0-49.75                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic                       3.2.0-49.75                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-51                               3.2.0-51.77                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic                       3.2.0-51.77                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                               3.2.0-52.78                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic                       3.2.0-52.78                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                               3.2.0-53.81                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic                       3.2.0-53.81                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-54                               3.2.0-54.82                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic                       3.2.0-54.82                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-55                               3.2.0-55.85                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic                       3.2.0-55.85                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-56                               3.2.0-56.86                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic                       3.2.0-56.86                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-57                               3.2.0-57.87                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic                       3.2.0-57.87                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-58                               3.2.0-58.88                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic                       3.2.0-58.88                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-59                               3.2.0-59.90                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic                       3.2.0-59.90                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-60                               3.2.0-60.91                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic                       3.2.0-60.91                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-61                               3.2.0-61.93                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic                       3.2.0-61.93                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-63                               3.2.0-63.95                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic                       3.2.0-63.95                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-64                               3.2.0-64.97                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-64-generic                       3.2.0-64.97                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-65                               3.2.0-65.99                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-65-generic                       3.2.0-65.99                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-67                               3.2.0-67.101                                                all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic                       3.2.0-67.101                                                amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                               4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                       4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-35                               4.2.0-35.40                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-35-generic                       4.2.0-35.40                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-36                               4.2.0-36.42                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-36-generic                       4.2.0-36.42                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-41                               4.2.0-41.48                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic                       4.2.0-41.48                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-21                               4.4.0-21.37                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic                       4.4.0-21.37                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                               4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                       4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                               4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                       4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-2.6.38-8-generic                         2.6.38-8.42                                                 amd64        Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-15-generic                         3.0.0-15.26                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic                         3.0.0-16.29                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic                         3.0.0-17.30                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic                         3.0.0-19.33                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic                         3.0.0-20.34                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-21-generic                         3.0.0-21.35                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-22-generic                         3.0.0-22.36                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-23-generic                         3.0.0-23.39                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-24-generic                         3.0.0-24.40                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-25-generic                         3.0.0-25.41                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-26-generic                         3.0.0-26.43                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-27-generic                         3.0.0-27.44                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-28-generic                         3.0.0-28.45                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-29-generic                         3.0.0-29.46                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-30-generic                         3.0.0-30.47                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-31-generic                         3.0.0-31.49                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-32-generic                         3.0.0-32.50                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.13.0-33-generic                        3.13.0-33.58                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-34-generic                        3.13.0-34.60                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                        3.13.0-35.62                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                        3.13.0-36.63                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                        3.13.0-37.64                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                        3.13.0-39.66                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                        3.13.0-40.69                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                        3.13.0-43.72                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                        3.13.0-44.73                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                        3.13.0-45.74                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                        3.13.0-46.79                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                        3.13.0-48.80                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                        3.13.0-49.83                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic                        3.13.0-51.84                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                        3.13.0-52.86                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                        3.13.0-53.89                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                        3.13.0-54.91                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                        3.13.0-55.94                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                        3.13.0-57.95                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                        3.13.0-58.97                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-59-generic                        3.13.0-59.98                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                        3.13.0-61.100                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic                        3.13.0-62.102                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                        3.13.0-63.103                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                        3.13.0-65.106                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-generic                        3.13.0-66.108                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-generic                        3.13.0-67.110                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic                        3.13.0-68.111                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-71-generic                        3.13.0-71.114                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic                        3.13.0-74.118                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-76-generic                        3.13.0-76.120                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                        3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-79-generic                        3.13.0-79.123                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-83-generic                        3.13.0-83.127                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-39-generic                         3.2.0-39.62                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-40-generic                         3.2.0-40.64                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-41-generic                         3.2.0-41.66                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-43-generic                         3.2.0-43.68                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-44-generic                         3.2.0-44.69                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-45-generic                         3.2.0-45.70                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-48-generic                         3.2.0-48.74                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-49-generic                         3.2.0-49.75                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-51-generic                         3.2.0-51.77                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic                         3.2.0-52.78                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-53-generic                         3.2.0-53.81                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-54-generic                         3.2.0-54.82                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-55-generic                         3.2.0-55.85                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-56-generic                         3.2.0-56.86                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-57-generic                         3.2.0-57.87                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-58-generic                         3.2.0-58.88                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-59-generic                         3.2.0-59.90                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-60-generic                         3.2.0-60.91                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-61-generic                         3.2.0-61.93                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-63-generic                         3.2.0-63.95                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-64-generic                         3.2.0-64.97                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-65-generic                         3.2.0-65.99                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-67-generic                         3.2.0-67.101                                                amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                         4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-35-generic                         4.2.0-35.40                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-36-generic                         4.2.0-36.42                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
iF  linux-image-4.2.0-41-generic                         4.2.0-41.48                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-21-generic                         4.4.0-21.37                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                         4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                         4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-33-generic                  3.13.0-33.58                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                  3.13.0-34.60                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                  3.13.0-35.62                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                  3.13.0-36.63                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                  3.13.0-37.64                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                  3.13.0-39.66                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                  3.13.0-40.69                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                  3.13.0-43.72                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                  3.13.0-44.73                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                  3.13.0-45.74                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                  3.13.0-46.79                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                  3.13.0-48.80                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                  3.13.0-49.83                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                  3.13.0-51.84                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                  3.13.0-52.86                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                  3.13.0-53.89                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                  3.13.0-54.91                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                  3.13.0-55.94                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                  3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                  3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                  3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                  3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                  3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                  3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                  3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                  3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                  3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                  3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-71-generic                  3.13.0-71.114                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                  3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic                  3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                  3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                  3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-35-generic                   4.2.0-35.40                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-36-generic                   4.2.0-36.42                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
iU  linux-image-extra-4.2.0-41-generic                   4.2.0-41.48                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic                   4.4.0-21.37                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies
```





BootNOT.txt

---

### Post by Bashing-om on 2016-07-16
Alligator; Ouch ...

We may have our work cut out for us, huh ?

Let's see if we have operational overhead; and see if the system then will do our work for us.
Presently, what returns:
```

df -h
df -i

```

Depending the overhead room, is what we do next.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-16
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M  9.8M  775M   2% /run
/dev/md0        720G  315G  369G  47% /
tmpfs           3.9G   38M  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  273M   41M  88% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M   48K  785M   1% /run/user/1001
tmpfs           785M   76K  785M   1% /run/user/1000
/dev/sdb2       661G  139G  522G  22% /media/ron/Data

df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             999171     584   998587    1% /dev
tmpfs           1004017     953  1003064    1% /run
/dev/md0       47947776 4123141 43824635    9% /
tmpfs           1004017      50  1003967    1% /dev/shm
tmpfs           1004017       6  1004011    1% /run/lock
tmpfs           1004017      18  1003999    1% /sys/fs/cgroup
/dev/sdb1         88352     327    88025    1% /boot
cgmfs           1004017      14  1004003    1% /run/cgmanager/fs
tmpfs           1004017      28  1003989    1% /run/user/1001
tmpfs           1004017      35  1003982    1% /run/user/1000
/dev/sdb2             0       0        0     - /media/ron/Data

---

### Post by Bashing-om on 2016-07-16
Alligator; Hey;

Look'n good ! We do have the operating head room available.
Code tags, please .. to maintain and promote readability of the outputs:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Let's see if the system will work for us.
```

sudo apt update
sudo apt upgrade
sudo apt-get autoremove

```

else, we roll our sleeves up and go to work .. 

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-17
The autoremove remove a lot of files,  still looking for 4.2.0-41  Following that I checked the cmds initially used, output looks similar.  I did another update and upgrade with the following error, which has been happening since the whoops.

> sudo apt update && sudo apt upgrade
[sudo] password for ron: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]
Hit:2 [http://mirrors.accretive-networks.net/ubuntu](http://mirrors.accretive-networks.net/ubuntu) xenial InRelease                                                          
Hit:3 [http://mirrors.accretive-networks.net/ubuntu](http://mirrors.accretive-networks.net/ubuntu) xenial-updates InRelease                                                                             
Ign:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                                                                                            
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease          
Hit:7 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release               
Get:6 [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease [2,592 B]
Err:6 [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
Reading package lists... Done
W: GPG error: [http://deb.opera.com/opera](http://deb.opera.com/opera) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 63F7D4AFF6D61D45
E: The repository 'http://deb.opera.com/opera stable InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by Bashing-om on 2016-07-17
Alligator; Hey;

Looking good. thus far .
-IF- the major cause of concern is the public key, that we can deal with easily by importing the signing key.
However. I do have a great amount of concern, in that:
The Opera web browser:
[http://deb.opera.com/opera/dists/](http://deb.opera.com/opera/dists/)
is built for the debian release .. I do not know opera, thus I do not know how this install of opera applies to our ubuntu install !
Did you install Opera from their web site for linux ?
[http://www.opera.com/computer/linux](http://www.opera.com/computer/linux)

The brakes are applied on this resolution as if there is a mix of distributions here, we do have a problem.

[INDENT][INDENT]maybe yes
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-17
The computer requested a reboot.  The result is 
uname -r  =>  4.4.0-31-generic

Which is something new image, so is this the lasted kernel, and therefore, you've fixed my problem??

The opera thing, I don't use, so I can probably delete from the repository file.

---

### Post by Bashing-om on 2016-07-17
Alligator; Well ..

That is good news that the new kernel installed ..

If you do not use it .. yes, remove it .. keep it clean behind you is my motto.
Depending on how Opera was installed is how it is removed ..

At this rime .. do we need to focus on removing the old no longer needed kernels ?
what have you still installed :
```

dpkg -l | grep linux- 

```

[INDENT][INDENT]clean system
[INDENT][INDENT][INDENT]is a clean mind
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-17
```

ii  linux-base                                           4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                       1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                        4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-35                              3.13.0-35.62                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                      3.13.0-35.62                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                              3.13.0-36.63                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                      3.13.0-36.63                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                              3.13.0-37.64                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                      3.13.0-37.64                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                              3.13.0-39.66                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                      3.13.0-39.66                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-40                              3.13.0-40.69                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                      3.13.0-40.69                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                              3.13.0-43.72                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                      3.13.0-43.72                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                              3.13.0-44.73                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                      3.13.0-44.73                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                              3.13.0-45.74                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                      3.13.0-45.74                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                              3.13.0-46.79                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                      3.13.0-46.79                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                              3.13.0-49.83                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                      3.13.0-49.83                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-51                              3.13.0-51.84                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                      3.13.0-51.84                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                              3.13.0-52.86                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                      3.13.0-52.86                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                              3.13.0-53.89                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                      3.13.0-53.89                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-54                              3.13.0-54.91                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                      3.13.0-54.91                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-55                              3.13.0-55.94                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                      3.13.0-55.94                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                              3.13.0-57.95                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                      3.13.0-57.95                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                              3.13.0-58.97                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                      3.13.0-58.97                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                              3.13.0-59.98                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                      3.13.0-59.98                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-61                              3.13.0-61.100                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                      3.13.0-61.100                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                              3.13.0-62.102                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                      3.13.0-62.102                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                              3.13.0-63.103                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                      3.13.0-63.103                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                              3.13.0-65.106                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                      3.13.0-65.106                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                              3.13.0-66.108                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                      3.13.0-66.108                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                              3.13.0-67.110                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                      3.13.0-67.110                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-68                              3.13.0-68.111                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                      3.13.0-68.111                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-74                              3.13.0-74.118                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                      3.13.0-74.118                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-76                              3.13.0-76.120                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                      3.13.0-76.120                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-77                              3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                      3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                              3.13.0-79.123                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                      3.13.0-79.123                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-83                              3.13.0-83.127                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                      3.13.0-83.127                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-40                               3.2.0-40.64                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic                       3.2.0-40.64                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-41                               3.2.0-41.66                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic                       3.2.0-41.66                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-43                               3.2.0-43.68                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-43-generic                       3.2.0-43.68                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-44                               3.2.0-44.69                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic                       3.2.0-44.69                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-45                               3.2.0-45.70                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-45-generic                       3.2.0-45.70                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48                               3.2.0-48.74                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic                       3.2.0-48.74                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-49                               3.2.0-49.75                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic                       3.2.0-49.75                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-51                               3.2.0-51.77                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-51-generic                       3.2.0-51.77                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-52                               3.2.0-52.78                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-52-generic                       3.2.0-52.78                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-53                               3.2.0-53.81                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-53-generic                       3.2.0-53.81                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-54                               3.2.0-54.82                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-54-generic                       3.2.0-54.82                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-55                               3.2.0-55.85                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-55-generic                       3.2.0-55.85                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-56                               3.2.0-56.86                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-56-generic                       3.2.0-56.86                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-57                               3.2.0-57.87                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-57-generic                       3.2.0-57.87                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-58                               3.2.0-58.88                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-58-generic                       3.2.0-58.88                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-59                               3.2.0-59.90                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-59-generic                       3.2.0-59.90                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-60                               3.2.0-60.91                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-60-generic                       3.2.0-60.91                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-61                               3.2.0-61.93                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-61-generic                       3.2.0-61.93                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-63                               3.2.0-63.95                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-63-generic                       3.2.0-63.95                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-64                               3.2.0-64.97                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-64-generic                       3.2.0-64.97                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-65                               3.2.0-65.99                                                 all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-65-generic                       3.2.0-65.99                                                 amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-67                               3.2.0-67.101                                                all          Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-67-generic                       3.2.0-67.101                                                amd64        Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                               4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                       4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                               4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                       4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                               4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                       4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-2.6.38-8-generic                         2.6.38-8.42                                                 amd64        Linux kernel image for version 2.6.38 on x86/x86_64
rc  linux-image-3.0.0-15-generic                         3.0.0-15.26                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-16-generic                         3.0.0-16.29                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-17-generic                         3.0.0-17.30                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-19-generic                         3.0.0-19.33                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-20-generic                         3.0.0-20.34                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-21-generic                         3.0.0-21.35                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-22-generic                         3.0.0-22.36                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-23-generic                         3.0.0-23.39                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-24-generic                         3.0.0-24.40                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-25-generic                         3.0.0-25.41                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-26-generic                         3.0.0-26.43                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-27-generic                         3.0.0-27.44                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-28-generic                         3.0.0-28.45                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-29-generic                         3.0.0-29.46                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-30-generic                         3.0.0-30.47                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.0.0-31-generic                         3.0.0-31.49                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-32-generic                         3.0.0-32.50                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
rc  linux-image-3.13.0-33-generic                        3.13.0-33.58                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-34-generic                        3.13.0-34.60                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                        3.13.0-35.62                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                        3.13.0-36.63                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                        3.13.0-37.64                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                        3.13.0-39.66                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                        3.13.0-40.69                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                        3.13.0-43.72                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                        3.13.0-44.73                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                        3.13.0-45.74                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                        3.13.0-46.79                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                        3.13.0-48.80                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                        3.13.0-49.83                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic                        3.13.0-51.84                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                        3.13.0-52.86                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                        3.13.0-53.89                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                        3.13.0-54.91                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                        3.13.0-55.94                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                        3.13.0-57.95                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                        3.13.0-58.97                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-59-generic                        3.13.0-59.98                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                        3.13.0-61.100                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic                        3.13.0-62.102                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                        3.13.0-63.103                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                        3.13.0-65.106                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-generic                        3.13.0-66.108                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-generic                        3.13.0-67.110                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic                        3.13.0-68.111                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-71-generic                        3.13.0-71.114                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic                        3.13.0-74.118                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-76-generic                        3.13.0-76.120                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                        3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-79-generic                        3.13.0-79.123                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-83-generic                        3.13.0-83.127                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-39-generic                         3.2.0-39.62                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-40-generic                         3.2.0-40.64                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-41-generic                         3.2.0-41.66                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-43-generic                         3.2.0-43.68                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-44-generic                         3.2.0-44.69                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-45-generic                         3.2.0-45.70                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-48-generic                         3.2.0-48.74                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-49-generic                         3.2.0-49.75                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-51-generic                         3.2.0-51.77                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-52-generic                         3.2.0-52.78                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-53-generic                         3.2.0-53.81                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-54-generic                         3.2.0-54.82                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-55-generic                         3.2.0-55.85                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-56-generic                         3.2.0-56.86                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-57-generic                         3.2.0-57.87                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-58-generic                         3.2.0-58.88                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-59-generic                         3.2.0-59.90                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-60-generic                         3.2.0-60.91                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-61-generic                         3.2.0-61.93                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-63-generic                         3.2.0-63.95                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-64-generic                         3.2.0-64.97                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-65-generic                         3.2.0-65.99                                                 amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-67-generic                         3.2.0-67.101                                                amd64        Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                         4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-35-generic                         4.2.0-35.40                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-36-generic                         4.2.0-36.42                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.2.0-41-generic                         4.2.0-41.48                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-21-generic                         4.4.0-21.37                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                         4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                         4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-33-generic                  3.13.0-33.58                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                  3.13.0-34.60                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                  3.13.0-35.62                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                  3.13.0-36.63                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                  3.13.0-37.64                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                  3.13.0-39.66                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                  3.13.0-40.69                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                  3.13.0-43.72                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                  3.13.0-44.73                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                  3.13.0-45.74                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                  3.13.0-46.79                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                  3.13.0-48.80                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                  3.13.0-49.83                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic                  3.13.0-51.84                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                  3.13.0-52.86                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                  3.13.0-53.89                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                  3.13.0-54.91                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                  3.13.0-55.94                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                  3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                  3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                  3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                  3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                  3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                  3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                  3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                  3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                  3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                  3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-71-generic                  3.13.0-71.114                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                  3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic                  3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                  3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                  3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-35-generic                   4.2.0-35.40                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-36-generic                   4.2.0-36.42                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-41-generic                   4.2.0-41.48                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-21-generic                   4.4.0-21.37                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

Thank you very much for your help.  Everything seems to work just fine.

Ron

---

### Post by Bashing-om on 2016-07-17
Alligator; OK;

I see now why "autoremove" did not remove the old kernels, there exist kernel images from before "autoremove" had this ability.

So we handle this ourselves .
As the 1st stab at removing these old kernels, run terminal commands:
Copy and paste for best results, please look and verify the sequence that I have is right for only the 3.2.0 series of kernels in this 1st stab. Hey, I can make mistakes ! But I have double checked my intent here .
```

sudo dpkg -P linux-image-3.2.0-{39,40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,65,67}-generic
sudo dpkg -P linux-headers-3.2.0-{40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,65,67}-generic
sudo dpkg -P linux-headers-3.2.0-{40,41,43,44,45,48,49,51,52,53,54,55,56,57,58,59,60,61,63,64,65,67}
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
If there are reported errors, and there is that possibility .. please post the command and the errors ..

Else we continue with removing the next series of old kernels .
Post back a new list of what is now installed after the above removal procedure completes:
Show me:
```

dpkg -l | grep linux-

```



[INDENT][INDENT]slow process
[INDENT][INDENT]but, we getter done
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-17
```

ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-35                        3.13.0-35.62                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                3.13.0-35.62                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                        3.13.0-36.63                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                3.13.0-36.63                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                        3.13.0-37.64                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                3.13.0-37.64                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                        3.13.0-39.66                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                3.13.0-39.66                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-40                        3.13.0-40.69                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                3.13.0-40.69                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                        3.13.0-43.72                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                3.13.0-43.72                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                        3.13.0-44.73                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                3.13.0-44.73                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                        3.13.0-45.74                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                3.13.0-45.74                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                        3.13.0-46.79                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                3.13.0-46.79                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                        3.13.0-49.83                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                3.13.0-49.83                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-51                        3.13.0-51.84                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                3.13.0-51.84                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                        3.13.0-52.86                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                3.13.0-52.86                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                        3.13.0-53.89                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                3.13.0-53.89                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-54                        3.13.0-54.91                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                3.13.0-54.91                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-55                        3.13.0-55.94                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                3.13.0-55.94                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                        3.13.0-57.95                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                3.13.0-57.95                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                        3.13.0-58.97                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                3.13.0-58.97                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                        3.13.0-59.98                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                3.13.0-59.98                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-61                        3.13.0-61.100                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                3.13.0-61.100                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                        3.13.0-62.102                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                3.13.0-62.102                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                        3.13.0-63.103                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                3.13.0-63.103                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                        3.13.0-65.106                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                3.13.0-65.106                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                        3.13.0-66.108                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                3.13.0-66.108                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                        3.13.0-67.110                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                3.13.0-67.110                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-68                        3.13.0-68.111                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                3.13.0-68.111                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-74                        3.13.0-74.118                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                3.13.0-74.118                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-76                        3.13.0-76.120                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                3.13.0-76.120                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                        3.13.0-79.123                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                3.13.0-79.123                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-83                        3.13.0-83.127                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                3.13.0-83.127                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-2.6.38-8-generic                   2.6.38-8.42                                                 amd64        Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-3.0.0-32-generic                   3.0.0-32.50                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.13.0-35-generic                  3.13.0-35.62                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                  3.13.0-36.63                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                  3.13.0-37.64                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                  3.13.0-39.66                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                  3.13.0-40.69                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                  3.13.0-43.72                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                  3.13.0-44.73                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                  3.13.0-45.74                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                  3.13.0-46.79                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                  3.13.0-49.83                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic                  3.13.0-51.84                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                  3.13.0-52.86                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                  3.13.0-53.89                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                  3.13.0-54.91                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                  3.13.0-55.94                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                  3.13.0-57.95                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                  3.13.0-58.97                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-59-generic                  3.13.0-59.98                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                  3.13.0-61.100                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic                  3.13.0-62.102                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                  3.13.0-63.103                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                  3.13.0-65.106                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-generic                  3.13.0-66.108                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-generic                  3.13.0-67.110                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic                  3.13.0-68.111                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic                  3.13.0-74.118                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-76-generic                  3.13.0-76.120                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-79-generic                  3.13.0-79.123                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-83-generic                  3.13.0-83.127                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic            3.13.0-35.62                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic            3.13.0-36.63                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic            3.13.0-37.64                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic            3.13.0-39.66                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic            3.13.0-40.69                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic            3.13.0-43.72                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic            3.13.0-44.73                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic            3.13.0-45.74                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic            3.13.0-46.79                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic            3.13.0-49.83                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic            3.13.0-51.84                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic            3.13.0-52.86                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic            3.13.0-53.89                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic            3.13.0-54.91                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic            3.13.0-55.94                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic            3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic            3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic            3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic            3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic            3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic            3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic            3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic            3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic            3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic            3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic            3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic            3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic            3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic            3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-07-17
Alligator; Hey hey ...

Looking better, we are doing something right, huh ?

Ok, a double check that we do not mess with the booting kernel.
show me:
```

uname -r

```
And we knock out the next kernel series .

[INDENT][INDENT]progress made
[INDENT][INDENT]even in small steps
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
4.4.0-31-generic

---

### Post by Alligator on 2016-07-18
/boot  ls -al
```

/boot$ ls -al
total 179663
drwxr-xr-x  4 root root     6144 Jul 17 20:33 .
drwxr-xr-x 25 root root     4096 Jul 16 08:00 ..
-rw-r--r--  1 root root  1165578 Mar 10 19:35 abi-3.13.0-83-generic
-rw-r--r--  1 root root  1312645 Mar 10 18:11 abi-4.2.0-34-generic
-rw-r--r--  1 root root  1240018 Jun 24 06:03 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12 19:59 abi-4.4.0-31-generic
-rw-r--r--  1 root root   165918 Mar 10 19:35 config-3.13.0-83-generic
-rw-r--r--  1 root root   184888 Mar 10 18:11 config-4.2.0-34-generic
-rw-r--r--  1 root root   189533 Jun 24 06:03 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12 19:59 config-4.4.0-31-generic
drwxr-xr-x  5 root root     8192 Jul 17 20:01 grub
-rw-r--r--  1 root root 29618704 Apr  3 10:13 initrd.img-3.13.0-83-generic
-rw-r--r--  1 root root 33579846 Apr  4 13:57 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root 36103081 Jul 10 03:08 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 36075447 Jul 17 20:33 initrd.img-4.4.0-31-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3393725 Mar 10 19:35 System.map-3.13.0-83-generic
-rw-------  1 root root  3744589 Mar 10 18:11 System.map-4.2.0-34-generic
-rw-------  1 root root  3859655 Jun 24 06:03 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12 19:59 System.map-4.4.0-31-generic
-rw-------  1 root root  5827776 Mar 10 19:35 vmlinuz-3.13.0-83-generic
-rw-------  1 root root  6808528 Mar 10 18:11 vmlinuz-4.2.0-34-generic
-rw-------  1 root root  7026864 Jun 24 06:03 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12 19:59 vmlinuz-4.4.0-31-generic

```

---

### Post by Bashing-om on 2016-07-18
Alligator; Hey, look'n great ...

I am a bit concerned that the contents of /boot is not what I expected .

For verification of what I next had in mind show me a new:
```

dpkg -l | grep linux-

```

see if we are now ready for cleanup.

[INDENT][INDENT]slowly, but surely
[INDENT][INDENT]getting there
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-35                        3.13.0-35.62                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                3.13.0-35.62                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                        3.13.0-36.63                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                3.13.0-36.63                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                        3.13.0-37.64                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                3.13.0-37.64                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                        3.13.0-39.66                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                3.13.0-39.66                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-40                        3.13.0-40.69                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                3.13.0-40.69                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                        3.13.0-43.72                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                3.13.0-43.72                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                        3.13.0-44.73                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                3.13.0-44.73                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                        3.13.0-45.74                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                3.13.0-45.74                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                        3.13.0-46.79                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                3.13.0-46.79                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                        3.13.0-49.83                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                3.13.0-49.83                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-51                        3.13.0-51.84                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                3.13.0-51.84                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                        3.13.0-52.86                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                3.13.0-52.86                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                        3.13.0-53.89                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                3.13.0-53.89                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-54                        3.13.0-54.91                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                3.13.0-54.91                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-55                        3.13.0-55.94                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                3.13.0-55.94                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                        3.13.0-57.95                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                3.13.0-57.95                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                        3.13.0-58.97                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                3.13.0-58.97                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                        3.13.0-59.98                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                3.13.0-59.98                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-61                        3.13.0-61.100                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                3.13.0-61.100                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                        3.13.0-62.102                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                3.13.0-62.102                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                        3.13.0-63.103                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                3.13.0-63.103                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                        3.13.0-65.106                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                3.13.0-65.106                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                        3.13.0-66.108                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                3.13.0-66.108                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                        3.13.0-67.110                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                3.13.0-67.110                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-68                        3.13.0-68.111                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                3.13.0-68.111                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-74                        3.13.0-74.118                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                3.13.0-74.118                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-76                        3.13.0-76.120                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                3.13.0-76.120                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                        3.13.0-79.123                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                3.13.0-79.123                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-83                        3.13.0-83.127                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                3.13.0-83.127                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-2.6.38-8-generic                   2.6.38-8.42                                                 amd64        Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-3.0.0-32-generic                   3.0.0-32.50                                                 amd64        Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.13.0-35-generic                  3.13.0-35.62                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                  3.13.0-36.63                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                  3.13.0-37.64                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                  3.13.0-39.66                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                  3.13.0-40.69                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                  3.13.0-43.72                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                  3.13.0-44.73                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                  3.13.0-45.74                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                  3.13.0-46.79                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                  3.13.0-49.83                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic                  3.13.0-51.84                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                  3.13.0-52.86                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                  3.13.0-53.89                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                  3.13.0-54.91                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                  3.13.0-55.94                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                  3.13.0-57.95                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                  3.13.0-58.97                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-59-generic                  3.13.0-59.98                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                  3.13.0-61.100                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic                  3.13.0-62.102                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                  3.13.0-63.103                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                  3.13.0-65.106                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-generic                  3.13.0-66.108                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-generic                  3.13.0-67.110                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic                  3.13.0-68.111                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic                  3.13.0-74.118                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-76-generic                  3.13.0-76.120                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-79-generic                  3.13.0-79.123                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-83-generic                  3.13.0-83.127                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic            3.13.0-35.62                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic            3.13.0-36.63                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic            3.13.0-37.64                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic            3.13.0-39.66                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic            3.13.0-40.69                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic            3.13.0-43.72                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic            3.13.0-44.73                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic            3.13.0-45.74                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic            3.13.0-46.79                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic            3.13.0-49.83                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic            3.13.0-51.84                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic            3.13.0-52.86                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic            3.13.0-53.89                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic            3.13.0-54.91                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic            3.13.0-55.94                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic            3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic            3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic            3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic            3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic            3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic            3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic            3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic            3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic            3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic            3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic            3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic            3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic            3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic            3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-07-18
Alligator; Ho Kay ...

Continue on our merry way.
```

sudo dpkg -P linux-image-2.6.38-8-generic
sudo dpkg -P linux-image-3.0.0-32-generic 

```

I want to know that the above commands complete before we move on .
If these run clean;
Then we see if the package manager will now pick up our slack and do our work for us.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
All is well - no errors

---

### Post by Bashing-om on 2016-07-18
Alligator; K;

Now that we have the obsolete kernels off the system; let's see if the package manager will work it's magic:
```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```

If these above run clean .. let's get a status:
run:
```

sudo apt update
sudo apt upgrade

```

and show me what :
```

sudo apt -f install
sudo dpkg -C

```
results in.

[INDENT][INDENT]maybe all YES
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

 sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

ron@Cronluath:~$ sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 medibuntu-keyring    GnuPG key of the Medibuntu repository


```

---

### Post by Bashing-om on 2016-07-18
Alligator; Hey ! Looks great to me ...

Prove it !
```

dpkg -l | grep linux-

```
Let's know now what is .

a bit more clean up " medibuntu-keyring " ; that repo has been dead for ages .. remove that source from the source(s) list .


[INDENT][INDENT]nothing like
[INDENT][INDENT][INDENT]a clean house
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

 dpkg -l | grep linux-
ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-35                        3.13.0-35.62                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                3.13.0-35.62                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                        3.13.0-36.63                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                3.13.0-36.63                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                        3.13.0-37.64                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                3.13.0-37.64                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                        3.13.0-39.66                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                3.13.0-39.66                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-40                        3.13.0-40.69                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                3.13.0-40.69                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                        3.13.0-43.72                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                3.13.0-43.72                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                        3.13.0-44.73                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                3.13.0-44.73                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                        3.13.0-45.74                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                3.13.0-45.74                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                        3.13.0-46.79                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                3.13.0-46.79                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                        3.13.0-49.83                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                3.13.0-49.83                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-51                        3.13.0-51.84                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                3.13.0-51.84                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                        3.13.0-52.86                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                3.13.0-52.86                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                        3.13.0-53.89                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                3.13.0-53.89                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-54                        3.13.0-54.91                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                3.13.0-54.91                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-55                        3.13.0-55.94                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                3.13.0-55.94                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                        3.13.0-57.95                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                3.13.0-57.95                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                        3.13.0-58.97                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                3.13.0-58.97                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                        3.13.0-59.98                                                all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                3.13.0-59.98                                                amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-61                        3.13.0-61.100                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                3.13.0-61.100                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                        3.13.0-62.102                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                3.13.0-62.102                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                        3.13.0-63.103                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                3.13.0-63.103                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                        3.13.0-65.106                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                3.13.0-65.106                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                        3.13.0-66.108                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                3.13.0-66.108                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                        3.13.0-67.110                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                3.13.0-67.110                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-68                        3.13.0-68.111                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                3.13.0-68.111                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-74                        3.13.0-74.118                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                3.13.0-74.118                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-76                        3.13.0-76.120                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                3.13.0-76.120                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                        3.13.0-79.123                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                3.13.0-79.123                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-83                        3.13.0-83.127                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                3.13.0-83.127                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-35-generic                  3.13.0-35.62                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                  3.13.0-36.63                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                  3.13.0-37.64                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                  3.13.0-39.66                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                  3.13.0-40.69                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                  3.13.0-43.72                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                  3.13.0-44.73                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                  3.13.0-45.74                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                  3.13.0-46.79                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                  3.13.0-49.83                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-51-generic                  3.13.0-51.84                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                  3.13.0-52.86                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                  3.13.0-53.89                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                  3.13.0-54.91                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                  3.13.0-55.94                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                  3.13.0-57.95                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                  3.13.0-58.97                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-59-generic                  3.13.0-59.98                                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                  3.13.0-61.100                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic                  3.13.0-62.102                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                  3.13.0-63.103                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                  3.13.0-65.106                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-generic                  3.13.0-66.108                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-generic                  3.13.0-67.110                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic                  3.13.0-68.111                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic                  3.13.0-74.118                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-76-generic                  3.13.0-76.120                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-79-generic                  3.13.0-79.123                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-83-generic                  3.13.0-83.127                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic            3.13.0-35.62                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic            3.13.0-36.63                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic            3.13.0-37.64                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic            3.13.0-39.66                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic            3.13.0-40.69                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic            3.13.0-43.72                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic            3.13.0-44.73                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic            3.13.0-45.74                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic            3.13.0-46.79                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic            3.13.0-49.83                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-51-generic            3.13.0-51.84                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic            3.13.0-52.86                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic            3.13.0-53.89                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic            3.13.0-54.91                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic            3.13.0-55.94                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic            3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic            3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic            3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic            3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic            3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic            3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic            3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic            3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic            3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic            3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic            3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic            3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic            3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic            3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-07-18
Alligator; Well ....

Did not work out as I had hoped .. OK, we do it ourselves:
```

sudo dpkg -P linux-image-extra-3.13.0-{35,36,37,39,40,43,44,45,46,49,51,52,53,54,55,57,58,59,61,62,63,65,66,67,68,74,76,79,83}-generic
sudo dpkg -P linux-image-3.13.0-{35,36,37,39,40,43,44,45,46,49,51,52,53,54,55,57,58,59,61,62,63,65,66,67,68,74,76,79,83}-generic
sudo dpkg -P linux-headers-3.13.0-{35,36,37,39,40,43,44,45,46,49,51,52,53,54,55,57,58,59,61,62,63,65,66,67,68,74,76,79,83}-generic
sudo dpkg -P linux-headers-3.13.0-{35,36,37,39,40,43,44,45,46,49,51,52,53,54,55,57,58,59,61,62,63,65,66,67,68,74,76,79,83}

```

And again, what is the status then when completed ?
show:
```

sudo apt -f install
sudo dpkg -C

```

---

### Post by Alligator on 2016-07-18
```

sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-extra-3.13.0-57-generic linux-image-extra-3.13.0-58-generic linux-image-extra-3.13.0-59-generic linux-image-extra-3.13.0-61-generic linux-image-extra-3.13.0-62-generic
  linux-image-extra-3.13.0-63-generic linux-image-extra-3.13.0-65-generic linux-image-extra-3.13.0-66-generic linux-image-extra-3.13.0-67-generic linux-image-extra-3.13.0-68-generic
  linux-image-extra-3.13.0-74-generic linux-image-extra-3.13.0-76-generic linux-image-extra-3.13.0-79-generic linux-image-extra-3.13.0-83-generic
0 upgraded, 0 newly installed, 14 to remove and 0 not upgraded.
14 not fully installed or removed.
After this operation, 2,126 MB disk space will be freed.
Do you want to continue? [Y/n] YY
(Reading database ... 363869 files and directories currently installed.)
Removing linux-image-extra-3.13.0-57-generic (3.13.0-57.95) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-57-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Error! Your kernel headers for kernel 3.13.0-57-generic cannot be found.
Please install the linux-headers-3.13.0-57-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-57-generic cannot be found.
Please install the linux-headers-3.13.0-57-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-57-generic
WARNING: missing /lib/modules/3.13.0-57-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-57-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_qsj9LG/lib/modules/3.13.0-57-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_qsj9LG/lib/modules/3.13.0-57-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-57-generic /boot/vmlinuz-3.13.0-57-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-58-generic (3.13.0-58.97) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-58-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
Error! Your kernel headers for kernel 3.13.0-58-generic cannot be found.
Please install the linux-headers-3.13.0-58-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-58-generic cannot be found.
Please install the linux-headers-3.13.0-58-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-58-generic
WARNING: missing /lib/modules/3.13.0-58-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-58-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_MciQDK/lib/modules/3.13.0-58-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_MciQDK/lib/modules/3.13.0-58-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-58-generic /boot/vmlinuz-3.13.0-58-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-59-generic (3.13.0-59.98) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-59-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
Error! Your kernel headers for kernel 3.13.0-59-generic cannot be found.
Please install the linux-headers-3.13.0-59-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-59-generic cannot be found.
Please install the linux-headers-3.13.0-59-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-59-generic
WARNING: missing /lib/modules/3.13.0-59-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-59-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_NIz7w4/lib/modules/3.13.0-59-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_NIz7w4/lib/modules/3.13.0-59-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-59-generic /boot/vmlinuz-3.13.0-59-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-61-generic (3.13.0-61.100) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-61-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
Error! Your kernel headers for kernel 3.13.0-61-generic cannot be found.
Please install the linux-headers-3.13.0-61-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-61-generic cannot be found.
Please install the linux-headers-3.13.0-61-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-61-generic
WARNING: missing /lib/modules/3.13.0-61-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-61-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_s0bYAa/lib/modules/3.13.0-61-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_s0bYAa/lib/modules/3.13.0-61-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-61-generic /boot/vmlinuz-3.13.0-61-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-62-generic (3.13.0-62.102) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-62-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Error! Your kernel headers for kernel 3.13.0-62-generic cannot be found.
Please install the linux-headers-3.13.0-62-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-62-generic cannot be found.
Please install the linux-headers-3.13.0-62-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-62-generic
WARNING: missing /lib/modules/3.13.0-62-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-62-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_slDfU0/lib/modules/3.13.0-62-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_slDfU0/lib/modules/3.13.0-62-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-63-generic (3.13.0-63.103) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-63-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Error! Your kernel headers for kernel 3.13.0-63-generic cannot be found.
Please install the linux-headers-3.13.0-63-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-63-generic cannot be found.
Please install the linux-headers-3.13.0-63-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-63-generic
WARNING: missing /lib/modules/3.13.0-63-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-63-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_PrVliS/lib/modules/3.13.0-63-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_PrVliS/lib/modules/3.13.0-63-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-63-generic /boot/vmlinuz-3.13.0-63-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-65-generic (3.13.0-65.106) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-65-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Error! Your kernel headers for kernel 3.13.0-65-generic cannot be found.
Please install the linux-headers-3.13.0-65-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-65-generic cannot be found.
Please install the linux-headers-3.13.0-65-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-65-generic
WARNING: missing /lib/modules/3.13.0-65-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-65-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Bci54c/lib/modules/3.13.0-65-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Bci54c/lib/modules/3.13.0-65-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-66-generic (3.13.0-66.108) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-66-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
Error! Your kernel headers for kernel 3.13.0-66-generic cannot be found.
Please install the linux-headers-3.13.0-66-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-66-generic cannot be found.
Please install the linux-headers-3.13.0-66-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-66-generic
WARNING: missing /lib/modules/3.13.0-66-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-66-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_UcX7Dy/lib/modules/3.13.0-66-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_UcX7Dy/lib/modules/3.13.0-66-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-66-generic /boot/vmlinuz-3.13.0-66-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-67-generic (3.13.0-67.110) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-67-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Error! Your kernel headers for kernel 3.13.0-67-generic cannot be found.
Please install the linux-headers-3.13.0-67-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-67-generic cannot be found.
Please install the linux-headers-3.13.0-67-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-67-generic
WARNING: missing /lib/modules/3.13.0-67-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-67-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_thtfBX/lib/modules/3.13.0-67-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_thtfBX/lib/modules/3.13.0-67-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-67-generic /boot/vmlinuz-3.13.0-67-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-68-generic (3.13.0-68.111) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-68-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
Error! Your kernel headers for kernel 3.13.0-68-generic cannot be found.
Please install the linux-headers-3.13.0-68-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-68-generic cannot be found.
Please install the linux-headers-3.13.0-68-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-68-generic
WARNING: missing /lib/modules/3.13.0-68-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-68-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ZFko0Y/lib/modules/3.13.0-68-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ZFko0Y/lib/modules/3.13.0-68-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-68-generic /boot/vmlinuz-3.13.0-68-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-74-generic (3.13.0-74.118) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-74-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Error! Error! Your kernel headers for kernel 3.13.0-74-generic cannot be found.
Please install the linux-headers-3.13.0-74-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Your kernel headers for kernel 3.13.0-74-generic cannot be found.
Please install the linux-headers-3.13.0-74-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-74-generic
WARNING: missing /lib/modules/3.13.0-74-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-74-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_bwcMXw/lib/modules/3.13.0-74-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_bwcMXw/lib/modules/3.13.0-74-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-76-generic (3.13.0-76.120) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-76-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
Error! Your kernel headers for kernel 3.13.0-76-generic cannot be found.
Please install the linux-headers-3.13.0-76-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-76-generic cannot be found.
Please install the linux-headers-3.13.0-76-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-76-generic
WARNING: missing /lib/modules/3.13.0-76-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-76-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_AlhyYN/lib/modules/3.13.0-76-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_AlhyYN/lib/modules/3.13.0-76-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-76-generic /boot/vmlinuz-3.13.0-76-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-79-generic (3.13.0-79.123) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-79-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Error! Your kernel headers for kernel 3.13.0-79-generic cannot be found.
Please install the linux-headers-3.13.0-79-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-79-generic cannot be found.
Please install the linux-headers-3.13.0-79-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-79-generic
WARNING: missing /lib/modules/3.13.0-79-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-79-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Auf64q/lib/modules/3.13.0-79-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Auf64q/lib/modules/3.13.0-79-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-79-generic /boot/vmlinuz-3.13.0-79-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Removing linux-image-extra-3.13.0-83-generic (3.13.0-83.127) ...
depmod: FATAL: could not load /boot/System.map-3.13.0-83-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
Error! Your kernel headers for kernel 3.13.0-83-generic cannot be found.
Please install the linux-headers-3.13.0-83-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.13.0-83-generic cannot be found.
Please install the linux-headers-3.13.0-83-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-83-generic
WARNING: missing /lib/modules/3.13.0-83-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/3.13.0-83-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_bLyGBW/lib/modules/3.13.0-83-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_bLyGBW/lib/modules/3.13.0-83-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-83-generic /boot/vmlinuz-3.13.0-83-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.2.0-34-generic
Found initrd image: /boot/initrd.img-4.2.0-34-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

```

```

sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 medibuntu-keyring    GnuPG key of the Medibuntu repository

```

```

dpkg -l | grep linux-
ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic            3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic            3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic            3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic            3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic            3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic            3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic            3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic            3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic            3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-68-generic            3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-74-generic            3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-76-generic            3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic            3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-83-generic            3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

uname -r
4.4.0-31-generic

---

### Post by Bashing-om on 2016-07-18
Alligator; well .....

That was an interesting turn of events, but looks like 'dpkg' handled it well.
However, let's make sure we are clean behind us:
show me:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot

```

still to be dealt with is the medibuntu-keyring .

[INDENT][INDENT]all in all,
[INDENT][INDENT]look'n good
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

ls -al /usr/src
total 64
drwxrwsr-x 14 root src  12288 Jul 18 15:46 .
drwxr-xr-x 13 root root  4096 Jul  9 02:07 ..
drwxr-xr-x  2 root root  4096 Jul  9 01:56 bbswitch-0.8
drwxr-xr-x 24 root root  4096 Feb  4 01:47 linux-headers-3.13.0-77
drwxr-xr-x  7 root root  4096 Feb  4 01:47 linux-headers-3.13.0-77-generic
drwxr-xr-x 24 root root  4096 Apr  3 00:56 linux-headers-4.2.0-34
drwxr-xr-x  7 root root  4096 Apr  3 00:56 linux-headers-4.2.0-34-generic
drwxr-xr-x 27 root root  4096 Jul 10 02:54 linux-headers-4.4.0-28
drwxr-xr-x  7 root root  4096 Jul 10 02:54 linux-headers-4.4.0-28-generic
drwxr-xr-x 27 root root  4096 Jul 16 07:59 linux-headers-4.4.0-31
drwxr-xr-x  7 root root  4096 Jul 16 07:59 linux-headers-4.4.0-31-generic
drwxr-xr-x  4 root root  4096 Jul  9 01:39 nvidia-340-340.96
drwxr-xr-x  6 root root  4096 Mar 25 19:21 oem-audio-hda-daily-0.201603240932~ubuntu14.04.1
drwxr-sr-x  2 root src   4096 Jul 18 14:59 .tmp_versions

```

```

ls -al /lib/modules/
total 40
drwxr-xr-x 10 root root 4096 Jul 18 15:42 .
drwxr-xr-x 26 root root 4096 Jul 18 13:59 ..
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-10-generic
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-11-generic
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-12-generic
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-13-generic
drwxr-xr-x  5 root root 4096 Apr  2 23:04 3.13.0-77-generic
drwxr-xr-x  5 root root 4096 Jul  9 01:55 4.2.0-34-generic
drwxr-xr-x  6 root root 4096 Jul 10 03:06 4.4.0-28-generic
drwxr-xr-x  6 root root 4096 Jul 16 08:01 4.4.0-31-generic

```

```

ls -al /boot
total 259676
drwxr-xr-x  4 root root     6144 Jul 18 15:50 .
drwxr-xr-x 25 root root     4096 Jul 16 08:00 ..
-rw-r--r--  1 root root  1312645 Mar 10 18:11 abi-4.2.0-34-generic
-rw-r--r--  1 root root  1240018 Jun 24 06:03 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12 19:59 abi-4.4.0-31-generic
-rw-r--r--  1 root root   184888 Mar 10 18:11 config-4.2.0-34-generic
-rw-r--r--  1 root root   189533 Jun 24 06:03 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12 19:59 config-4.4.0-31-generic
drwxr-xr-x  5 root root     8192 Jul 18 15:50 grub
-rw-r--r--  1 root root  8697762 Jul 18 15:46 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root  8697769 Jul 18 15:47 initrd.img-3.13.0-58-generic
-rw-r--r--  1 root root  8697753 Jul 18 15:47 initrd.img-3.13.0-59-generic
-rw-r--r--  1 root root  8697752 Jul 18 15:47 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root  8697791 Jul 18 15:47 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root  8697653 Jul 18 15:48 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root  8697755 Jul 18 15:48 initrd.img-3.13.0-65-generic
-rw-r--r--  1 root root  8697756 Jul 18 15:48 initrd.img-3.13.0-66-generic
-rw-r--r--  1 root root  8697734 Jul 18 15:48 initrd.img-3.13.0-67-generic
-rw-r--r--  1 root root  8697733 Jul 18 15:49 initrd.img-3.13.0-68-generic
-rw-r--r--  1 root root  8697755 Jul 18 15:49 initrd.img-3.13.0-74-generic
-rw-r--r--  1 root root  8697723 Jul 18 15:49 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root  8697805 Jul 18 15:49 initrd.img-3.13.0-79-generic
-rw-r--r--  1 root root  8697713 Jul 18 15:50 initrd.img-3.13.0-83-generic
-rw-r--r--  1 root root 33579846 Apr  4 13:57 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root 36103081 Jul 10 03:08 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 36075447 Jul 17 20:33 initrd.img-4.4.0-31-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3744589 Mar 10 18:11 System.map-4.2.0-34-generic
-rw-------  1 root root  3859655 Jun 24 06:03 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12 19:59 System.map-4.4.0-31-generic
-rw-------  1 root root  6808528 Mar 10 18:11 vmlinuz-4.2.0-34-generic
-rw-------  1 root root  7026864 Jun 24 06:03 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12 19:59 vmlinuz-4.4.0-31-generic

```

---

### Post by Bashing-om on 2016-07-18
Alligator; welp;

Glad we looked, there is some clean up of the old kernels we will have to do manually .
```

sudo rm -rf /usr/src/linux-headers-3.13.0-77{,-generic}
sudo rm -rf /lib/modules/2.6.38-{10,12,13}*
sudo rm -rf /lib/modules/3.13.0-77-generic
sudo rm /boot/*-3.13.0-{57,58,59,61,62,63,65,66,67,68,74,79,83}-generic
sudo apt -f install

```

And we know now why "autoremove" has such a struggle .

And a new look to see if we have missed anything:
```

dpkg -l | grep linux-
ls -al /boot/

```


still pending is medibuntu-keyring ; least it slips my mind.

[INDENT][INDENT]making good progress
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

 dpkg -l | grep linux-
ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic            3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic            3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic            3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic            3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic            3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic            3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic            3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic            3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic            3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-68-generic            3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-74-generic            3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-76-generic            3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic            3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-83-generic            3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

```

ls -al /boot/
total 148799
drwxr-xr-x  4 root root     6144 Jul 18 17:11 .
drwxr-xr-x 25 root root     4096 Jul 16 08:00 ..
-rw-r--r--  1 root root  1312645 Mar 10 18:11 abi-4.2.0-34-generic
-rw-r--r--  1 root root  1240018 Jun 24 06:03 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12 19:59 abi-4.4.0-31-generic
-rw-r--r--  1 root root   184888 Mar 10 18:11 config-4.2.0-34-generic
-rw-r--r--  1 root root   189533 Jun 24 06:03 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12 19:59 config-4.4.0-31-generic
drwxr-xr-x  5 root root     8192 Jul 18 15:50 grub
-rw-r--r--  1 root root  8697723 Jul 18 15:49 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root 33579846 Apr  4 13:57 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root 36103081 Jul 10 03:08 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 36075447 Jul 17 20:33 initrd.img-4.4.0-31-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3744589 Mar 10 18:11 System.map-4.2.0-34-generic
-rw-------  1 root root  3859655 Jun 24 06:03 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12 19:59 System.map-4.4.0-31-generic
-rw-------  1 root root  6808528 Mar 10 18:11 vmlinuz-4.2.0-34-generic
-rw-------  1 root root  7026864 Jun 24 06:03 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12 19:59 vmlinuz-4.4.0-31-generic

```

---

### Post by Bashing-om on 2016-07-18
Alligator; Huh ??

Now why would " ii  linux-headers-3.13.0-77 " and " initrd.img-3.13.0-76-generic" raise it's heads ... was not formerly in the equation, were they ?

Once more with feeling:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot
dpkg -l | grep linux-

```
try and make sure this mess is all cleaned up . That we get all our ducks in one row .

[INDENT][INDENT]much closer to the goal
[INDENT][INDENT][INDENT]than when we started .[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

dpkg -l | grep linux-
ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic            3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic            3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic            3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic            3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic            3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic            3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic            3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic            3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic            3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-68-generic            3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-74-generic            3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-76-generic            3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic            3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-83-generic            3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                       

```

```

 ls -al /boot/
total 148799
drwxr-xr-x  4 root root     6144 Jul 18 17:11 .
drwxr-xr-x 25 root root     4096 Jul 16 08:00 ..
-rw-r--r--  1 root root  1312645 Mar 10 18:11 abi-4.2.0-34-generic
-rw-r--r--  1 root root  1240018 Jun 24 06:03 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12 19:59 abi-4.4.0-31-generic
-rw-r--r--  1 root root   184888 Mar 10 18:11 config-4.2.0-34-generic
-rw-r--r--  1 root root   189533 Jun 24 06:03 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12 19:59 config-4.4.0-31-generic
drwxr-xr-x  5 root root     8192 Jul 18 15:50 grub
-rw-r--r--  1 root root  8697723 Jul 18 15:49 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root 33579846 Apr  4 13:57 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root 36103081 Jul 10 03:08 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 36075447 Jul 17 20:33 initrd.img-4.4.0-31-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3744589 Mar 10 18:11 System.map-4.2.0-34-generic
-rw-------  1 root root  3859655 Jun 24 06:03 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12 19:59 System.map-4.4.0-31-generic
-rw-------  1 root root  6808528 Mar 10 18:11 vmlinuz-4.2.0-34-generic
-rw-------  1 root root  7026864 Jun 24 06:03 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12 19:59 vmlinuz-4.4.0-31-generic

```

---

### Post by Alligator on 2016-07-18
ls -al /lib/modules
total 24
drwxr-xr-x  6 root root 4096 Jul 18 17:10 .
drwxr-xr-x 26 root root 4096 Jul 18 13:59 ..
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-11-generic
drwxr-xr-x  5 root root 4096 Jul  9 01:55 4.2.0-34-generic
drwxr-xr-x  6 root root 4096 Jul 10 03:06 4.4.0-28-generic
drwxr-xr-x  6 root root 4096 Jul 16 08:01 4.4.0-31-generic

---

### Post by Alligator on 2016-07-18
I think I'm behind
```

ls -al /usr/src
total 56
drwxrwsr-x 12 root src  12288 Jul 18 17:10 .
drwxr-xr-x 13 root root  4096 Jul  9 02:07 ..
drwxr-xr-x  2 root root  4096 Jul  9 01:56 bbswitch-0.8
drwxr-xr-x 24 root root  4096 Apr  3 00:56 linux-headers-4.2.0-34
drwxr-xr-x  7 root root  4096 Apr  3 00:56 linux-headers-4.2.0-34-generic
drwxr-xr-x 27 root root  4096 Jul 10 02:54 linux-headers-4.4.0-28
drwxr-xr-x  7 root root  4096 Jul 10 02:54 linux-headers-4.4.0-28-generic
drwxr-xr-x 27 root root  4096 Jul 16 07:59 linux-headers-4.4.0-31
drwxr-xr-x  7 root root  4096 Jul 16 07:59 linux-headers-4.4.0-31-generic
drwxr-xr-x  4 root root  4096 Jul  9 01:39 nvidia-340-340.96
drwxr-xr-x  6 root root  4096 Mar 25 19:21 oem-audio-hda-daily-0.201603240932~ubuntu14.04.1
drwxr-sr-x  2 root src   4096 Jul 18 14:59 .tmp_versions

```

```

t src   4096 Jul 18 14:59 .tmp_versions
ron@Cronluath:~$ ls -al /lib/modules
total 24
drwxr-xr-x  6 root root 4096 Jul 18 17:10 .
drwxr-xr-x 26 root root 4096 Jul 18 13:59 ..
drwxr-xr-x  3 root root 4096 Feb 13  2012 2.6.38-11-generic
drwxr-xr-x  5 root root 4096 Jul  9 01:55 4.2.0-34-generic
drwxr-xr-x  6 root root 4096 Jul 10 03:06 4.4.0-28-generic
drwxr-xr-x  6 root root 4096 Jul 16 08:01 4.4.0-31-generic

```

```

ls -al /boot
total 148799
drwxr-xr-x  4 root root     6144 Jul 18 17:11 .
drwxr-xr-x 25 root root     4096 Jul 16 08:00 ..
-rw-r--r--  1 root root  1312645 Mar 10 18:11 abi-4.2.0-34-generic
-rw-r--r--  1 root root  1240018 Jun 24 06:03 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12 19:59 abi-4.4.0-31-generic
-rw-r--r--  1 root root   184888 Mar 10 18:11 config-4.2.0-34-generic
-rw-r--r--  1 root root   189533 Jun 24 06:03 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12 19:59 config-4.4.0-31-generic
drwxr-xr-x  5 root root     8192 Jul 18 15:50 grub
-rw-r--r--  1 root root  8697723 Jul 18 15:49 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root 33579846 Apr  4 13:57 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root 36103081 Jul 10 03:08 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 36075447 Jul 17 20:33 initrd.img-4.4.0-31-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3744589 Mar 10 18:11 System.map-4.2.0-34-generic
-rw-------  1 root root  3859655 Jun 24 06:03 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12 19:59 System.map-4.4.0-31-generic
-rw-------  1 root root  6808528 Mar 10 18:11 vmlinuz-4.2.0-34-generic
-rw-------  1 root root  7026864 Jun 24 06:03 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12 19:59 vmlinuz-4.4.0-31-generic

```

```

dpkg -l | grep linux-
ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic            3.13.0-57.95                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic            3.13.0-58.97                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-59-generic            3.13.0-59.98                                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic            3.13.0-61.100                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic            3.13.0-62.102                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic            3.13.0-63.103                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic            3.13.0-65.106                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic            3.13.0-66.108                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic            3.13.0-67.110                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-68-generic            3.13.0-68.111                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-74-generic            3.13.0-74.118                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-76-generic            3.13.0-76.120                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic            3.13.0-79.123                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-83-generic            3.13.0-83.127                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-07-18
Alligator; OK;

Let's try this again:
```

sudo rm -rf /lib/modules/2.6.38-11-generic
sudo rm /boot/initrd.img-3.13.0-76-generic
sudo rm /boot/linux-image-3.13.0-77-generic 
sudo rm /boot/linux-headers-3.13.0-77-generic 
sudo rm /boot/linux-headers-3.13.0-77
sudo rm /boot/linux-image-extra-3.13.0-77-generic 
sudo apt -f install

```

And clean up the debris:
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
Where what is happening here is that any package that the package manager sees as 'rc' ( removed but config files remain) then purge those packages.


Now how do we stand ?
```

sudo apt update
sudo apt upgrade

```
where the only thing I expect for the package manager to holler about is the medibuntu-keyring .

[INDENT][INDENT]maybe now YES ?
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

dpkg -l | grep linux-
ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

No complaints about the keyring

---

### Post by Bashing-om on 2016-07-18
Alligator; I goofed;

See the edit to my last post .
I missed the /boot files !

[INDENT][INDENT]Ouch
I hate when that happens
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

ls -al /boot
total 140270
drwxr-xr-x  4 root root     6144 Jul 18 17:58 .
drwxr-xr-x 25 root root     4096 Jul 16 08:00 ..
-rw-r--r--  1 root root  1312645 Mar 10 18:11 abi-4.2.0-34-generic
-rw-r--r--  1 root root  1240018 Jun 24 06:03 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12 19:59 abi-4.4.0-31-generic
-rw-r--r--  1 root root   184888 Mar 10 18:11 config-4.2.0-34-generic
-rw-r--r--  1 root root   189533 Jun 24 06:03 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12 19:59 config-4.4.0-31-generic
drwxr-xr-x  5 root root     8192 Jul 18 15:50 grub
-rw-r--r--  1 root root 33579846 Apr  4 13:57 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root 36103081 Jul 10 03:08 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 36075447 Jul 17 20:33 initrd.img-4.4.0-31-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3744589 Mar 10 18:11 System.map-4.2.0-34-generic
-rw-------  1 root root  3859655 Jun 24 06:03 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12 19:59 System.map-4.4.0-31-generic
-rw-------  1 root root  6808528 Mar 10 18:11 vmlinuz-4.2.0-34-generic
-rw-------  1 root root  7026864 Jun 24 06:03 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12 19:59 vmlinuz-4.4.0-31-generic

```

---

### Post by Bashing-om on 2016-07-18
Alligator; Uh Huh !

That looks clean .. does the package manager agree ?
```

sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT]are we there yet ?
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
sudo apt -f install

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


sudo dpkg -C
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 medibuntu-keyring    GnuPG key of the Medibuntu repository

---

### Post by Bashing-om on 2016-07-18
Alligator; Outstanding !

Ok .. now to finalize all this and remove that no longer needed key.

Let's try and find that key so we can delete it.

What returns:
```

for r in /var/lib/apt/lists/*Release; do if ! gpgv --keyring /etc/apt/trusted.gpg $r.gpg $r; then echo "error: $? Problem with $r"; fi; done

```
That will check the gpg signatures of the Release files.... any errors it's say "error: X Problem with ...."

see where we go from here .

[INDENT][INDENT]we too can do this
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-18
```

gpgv: can't open `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_xenial_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_xenial_InRelease
gpgv: Signature made Wed 13 Jul 2016 02:45:26 PM CST using DSA key ID 7FAC5991
gpgv: Good signature from "Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>"
gpgv: Signature made Wed 13 Jul 2016 02:45:26 PM CST using RSA key ID 640DB551
gpgv: Good signature from "Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>"
gpgv: can't open `/var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_xenial_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_xenial_InRelease
gpgv: can't open `/var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_xenial-updates_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/mirrors.accretive-networks.net_ubuntu_dists_xenial-updates_InRelease
gpgv: can't open `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_InRelease.gpg'
gpgv: verify signatures failed: file open error
error: 0 Problem with /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_xenial-security_InRelease

```

---

### Post by Bashing-om on 2016-07-18
Alligator; Nope,

Do not see the key in that output ...

what about:
```

sudo apt-key finger

```

As I am done try'n to think for this session, we continue this hunt on my AM.

[INDENT][INDENT]all in for a days work
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-19
```

/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
      Key fingerprint = 6302 39CC 130E 1A7F D81A  27B1 4097 6EAF 437D 05B5
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
      Key fingerprint = C598 6B4F 1257 FFA8 6632  CBA7 4618 1433 FBB7 5451
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024D/3E5C1192 2010-09-20
      Key fingerprint = C474 15DF F48C 0964 5B78  6094 1612 6D3A 3E5C 1192
uid                  Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

pub   1024R/0624A220 2009-01-19
      Key fingerprint = FE85 409E EAB4 0ECC B657  4081 6AF0 E194 0624 A220
uid                  Launchpad PPA for TualatriX

pub   1024R/61E46227 2009-09-20
      Key fingerprint = 454F EDB2 28E1 455D 687C  9CBE 35DA 01C2 61E4 6227
uid                  Launchpad Default PPA

pub   1024D/0C5A2783 2006-11-23
      Key fingerprint = 64D1 5ADA FA81 B2C5 619B  3297 2EBC 26B6 0C5A 2783
uid                  Medibuntu Packaging Team <admin@lists.medibuntu.org>
uid                  The Medibuntu Team <medibuntu@sos-sts.com>
sub   2048g/16C7105A 2006-11-23

pub   1024R/569113AE 2009-08-24
      Key fingerprint = DC28 8793 6B41 53CA 9AFB  151B 0F67 8A01 5691 13AE
uid                  Launchpad Caffeine

pub   1024R/EEA14886 2010-05-04
      Key fingerprint = 7B2C 3B08 89BF 5709 A105  D03A C251 8248 EEA1 4886
uid                  Launchpad VLC

pub   1024R/5139BD61 2010-08-06
      Key fingerprint = DCD5 E6AE 989F 3D6B 1E8B  1553 7759 E0D6 5139 BD61
uid                  Launchpad rec-applet

pub   4096R/C0B21F32 2012-05-11
      Key fingerprint = 790B C727 7767 219C 42C8  6F93 3B4F E6AC C0B2 1F32
uid                  Ubuntu Archive Automatic Signing Key (2012) <ftpmaster@ubuntu.com>

pub   4096R/EFE21092 2012-05-11
      Key fingerprint = 8439 38DF 228D 22F7 B374  2BC0 D94A A3F0 EFE2 1092
uid                  Ubuntu CD Image Automatic Signing Key (2012) <cdimage@ubuntu.com>

pub   1024D/7FAC5991 2007-03-08
      Key fingerprint = 4CCA 1EAF 950C EE4A B839  76DC A040 830F 7FAC 5991
uid                  Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
sub   2048g/C07CB649 2007-03-08

pub   1024R/8EEBB0CA 2009-11-29
      Key fingerprint = 4496 BE64 A6BE E4CD 4BEE  E744 D8AD 4DE7 8EEB B0CA
uid                  Launchpad ClipGrab PPA

pub   1024R/DAD80779 2010-10-23
      Key fingerprint = 6D43 9625 4B22 84D9 AD9F  AE8F AE6D FF70 DAD8 0779
uid                  Launchpad PPA for ubun-Tor

pub   4096R/D38B4796 2016-04-12
      Key fingerprint = EB4C 1BFD 4F04 2F6D DDCC  EC91 7721 F63B D38B 4796
uid                  Google Inc. (Linux Packages Signing Authority) <linux-packages-keymaster@google.com>
sub   4096R/640DB551 2016-04-12 [expires: 2019-04-12]

/etc/apt/trusted.gpg.d/dhor-myway.gpg
-------------------------------------
pub   1024R/93330B78 2011-02-13
      Key fingerprint = B7A8 ED84 DF6A FA37 B620  BFB2 E2B7 D64D 9333 0B78
uid                  Launchpad PPA for Dariusz Duma

/etc/apt/trusted.gpg.d/klaus-vormweg-awesome.gpg
------------------------------------------------
pub   1024R/D36FE61D 2009-01-22
      Key fingerprint = 343F C747 0ABA 9C92 3C49  7A4E 8938 CE95 D36F E61D
uid                  Launchpad PPA for Klaus Vormweg

/etc/apt/trusted.gpg.d/libreoffice-ppa.gpg
------------------------------------------
pub   1024R/1378B444 2010-12-29
      Key fingerprint = 36E8 1C92 67FD 1383 FCC4  4909 83FB A175 1378 B444
uid                  Launchpad PPA for LibreOffice Packaging

/etc/apt/trusted.gpg.d/osmoma-audio-recorder.gpg
------------------------------------------------
pub   1024R/5139BD61 2010-08-06
      Key fingerprint = DCD5 E6AE 989F 3D6B 1E8B  1553 7759 E0D6 5139 BD61
uid                  Launchpad rec-applet

/etc/apt/trusted.gpg.d/plushuang-tw_ubuntu_uget-stable.gpg
----------------------------------------------------------
pub   1024R/EBE14A20 2011-03-17
      Key fingerprint = B6BA 898C B0A1 1CD9 F5EB  AF33 8BE3 EAB5 EBE1 4A20
uid                  Launchpad PPA for plushuang.tw

/etc/apt/trusted.gpg.d/ubuntu-audio-dev-alsa-daily.gpg
------------------------------------------------------
pub   1024R/72B194E5 2009-07-01
      Key fingerprint = 4E9F 485B F943 EF0E ABA1  0B5B D225 991A 72B1 94E5
uid                  Launchpad Ubuntu Audio Dev team PPA

/etc/apt/trusted.gpg.d/ubuntu-wine-ppa.gpg
------------------------------------------
pub   1024R/F9CB8DB0 2009-01-20
      Key fingerprint = 883E 8688 3975 76B6 C509  DF49 5A9A 06AE F9CB 8DB0
uid                  Launchpad PPA for Ubuntu Wine Team


```

Now getting an error message stated /boot has only 16M left.  This directory hasn't changed only three images in it.

---

### Post by Bashing-om on 2016-07-19
Alligator; Ouch !

I am also a bit disconcerted at:
> 
Now getting an error message stated /boot has only 16M left.

As I thought we were well past that ,

OK, from the top .. let's look and see:
```

df -h
df -i
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot
dpkg -l | grep linux-

```

---

### Post by Alligator on 2016-07-19
During the removal and rebuilding of many kernel files I only got this error message, I chose to ignore it and when another user logged (the wife) in it was there.  It hasn't come back and as I stated /boot has only 3 different images and associated files.  So, I don't think this is a problem; however, I know longer remember much about Unix/linux.   The key is the problem?

```

df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M  9.8M  775M   2% /run
/dev/md0        720G  299G  385G  44% /
tmpfs           3.9G   83M  3.8G   3% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  144M  170M  46% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M   60K  785M   1% /run/user/1001
tmpfs           785M   60K  785M   1% /run/user/1000

```

```

df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
udev             999175     583   998592    1% /dev
tmpfs           1004013     928  1003085    1% /run
/dev/md0       47947776 2525053 45422723    6% /
tmpfs           1004013      84  1003929    1% /dev/shm
tmpfs           1004013       6  1004007    1% /run/lock
tmpfs           1004013      18  1003995    1% /sys/fs/cgroup
/dev/sdb1         88352     312    88040    1% /boot
cgmfs           1004013      14  1003999    1% /run/cgmanager/fs
tmpfs           1004013      31  1003982    1% /run/user/1001
tmpfs           1004013      31  1003982    1% /run/user/1000

```

```

ls -al /usr/src/
total 56
drwxrwsr-x 12 root src  12288 Jul 18 17:10 .
drwxr-xr-x 13 root root  4096 Jul  9 02:07 ..
drwxr-xr-x  2 root root  4096 Jul  9 01:56 bbswitch-0.8
drwxr-xr-x 24 root root  4096 Apr  3 00:56 linux-headers-4.2.0-34
drwxr-xr-x  7 root root  4096 Apr  3 00:56 linux-headers-4.2.0-34-generic
drwxr-xr-x 27 root root  4096 Jul 10 02:54 linux-headers-4.4.0-28
drwxr-xr-x  7 root root  4096 Jul 10 02:54 linux-headers-4.4.0-28-generic
drwxr-xr-x 27 root root  4096 Jul 16 07:59 linux-headers-4.4.0-31
drwxr-xr-x  7 root root  4096 Jul 16 07:59 linux-headers-4.4.0-31-generic
drwxr-xr-x  4 root root  4096 Jul  9 01:39 nvidia-340-340.96
drwxr-xr-x  6 root root  4096 Mar 25 19:21 oem-audio-hda-daily-0.201603240932~ubuntu14.04.1
drwxr-sr-x  2 root src   4096 Jul 18 14:59 .tmp_versions

```

```

ls -al /lib/modules/
total 20
drwxr-xr-x  5 root root 4096 Jul 18 17:58 .
drwxr-xr-x 26 root root 4096 Jul 18 13:59 ..
drwxr-xr-x  5 root root 4096 Jul  9 01:55 4.2.0-34-generic
drwxr-xr-x  6 root root 4096 Jul 10 03:06 4.4.0-28-generic
drwxr-xr-x  6 root root 4096 Jul 16 08:01 4.4.0-31-generic

```

```

ls -al /boot
total 140270
drwxr-xr-x  4 root root     6144 Jul 18 17:58 .
drwxr-xr-x 25 root root     4096 Jul 16 08:00 ..
-rw-r--r--  1 root root  1312645 Mar 10 18:11 abi-4.2.0-34-generic
-rw-r--r--  1 root root  1240018 Jun 24 06:03 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12 19:59 abi-4.4.0-31-generic
-rw-r--r--  1 root root   184888 Mar 10 18:11 config-4.2.0-34-generic
-rw-r--r--  1 root root   189533 Jun 24 06:03 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12 19:59 config-4.4.0-31-generic
drwxr-xr-x  5 root root     8192 Jul 18 15:50 grub
-rw-r--r--  1 root root 33579846 Apr  4 13:57 initrd.img-4.2.0-34-generic
-rw-r--r--  1 root root 36103081 Jul 10 03:08 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 36075447 Jul 17 20:33 initrd.img-4.4.0-31-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28 06:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 06:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 06:44 memtest86+_multiboot.bin
-rw-------  1 root root  3744589 Mar 10 18:11 System.map-4.2.0-34-generic
-rw-------  1 root root  3859655 Jun 24 06:03 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12 19:59 System.map-4.4.0-31-generic
-rw-------  1 root root  6808528 Mar 10 18:11 vmlinuz-4.2.0-34-generic
-rw-------  1 root root  7026864 Jun 24 06:03 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12 19:59 vmlinuz-4.4.0-31-generic

```

```

dpkg -l | grep linix-

```

This last cmd returned with nothing - looking good

---

### Post by Bashing-om on 2016-07-19
Alligator; Humm ...

A typo:
> 
dpkg -l | grep linix-
This last cmd returned with nothing - looking good

on my part .. correct(ed) to be:
```

dpkg -l | grep linux-

```

And honestly, I am so confused as to what we do have here .. as you have a small boot partition:
> 
/dev/sdb1       331M  144M  170M  46% /boot

How in the world could it have contained all those kernels we have removed ??
It is currently at close to half capacity with 3 kernels installed ! Some kind of fancy dandy LVM ??

I honestly presently just do not see the source of a problem.
Let's await and see what " dpkg -l | grep linux- " reports .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-19
```

dpkg -l | grep linux-
ii  linux-base                                     4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                 1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                  4.4.0.31.33                                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-77                        3.13.0-77.121                                               all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                3.13.0-77.121                                               amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34                         4.2.0-34.39                                                 all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic                 4.2.0-34.39                                                 amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28                         4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic                 4.4.0-28.47                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31                         4.4.0-31.50                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic                 4.4.0-31.50                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                          4.4.0.31.33                                                 amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-77-generic                  3.13.0-77.121                                               amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic                   4.2.0-34.39                                                 amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-28-generic                   4.4.0-28.47                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-31-generic                   4.4.0-31.50                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic            3.13.0-77.121                                               amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic             4.2.0-34.39                                                 amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic             4.4.0-28.47                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic             4.4.0-31.50                                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                            4.4.0.31.33                                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                           4.4.0-31.50                                                 amd64        Linux Kernel Headers for development
ii  linux-sound-base                               1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                                3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                                2:3.63+dfsg-2ubuntu8                                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2016-07-19
Alligator; Humm ...

Not enough here to be of concern, however, I thought we had removed the 3.13.0-77  image.
Once more:
```

sudo apt purge linux-image-3.13.0-77-generic 
sudo apt purge linux-headers-3.13.0-77-generic
sudo apt purge linux-headers-3.13.0-77
sudo apt purge linux-image-extra-3.13.0-77-generic
sudo apt -f install
sudo apt-get autoremove

```

Still pending is removing medibuntu-keyring.

[INDENT][INDENT]still a wonder, how such a small space could operate
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-19
It's gone.  The /boot size was determined by the choice of letting the software setup the partitions.

---

### Post by Bashing-om on 2016-07-19
Alligator; Ho Kay ..
Some things I just will never understand.

All good now ?

Moving on along .
```

sudo apt purge medibuntu-keyring
sudo rm -rf /etc/apt/sources.list.d/medibuntu.list
sudo apt update
sudo apt upgrade

```

All now
[INDENT][INDENT][INDENT]finer than a frog's hair
[/INDENT][/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-19
Looks like another {solved}  Thank you.  Should purr like a kitten now.

---

### Post by Bashing-om on 2016-07-19
Alligator; Hey hey !

Dirty Jobs done Dirt Cheap :)

> 
Looks like another {solved} Thank you. Should purr like a kitten now.

Only you can say when we are done for sure.
However, if we are then:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Telling the world that this odyssey is ended.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by Alligator on 2016-07-19
Thanks again for your patience and your attention to detail in bringing a solution.  May the road always rise up to meet you.

---

### Post by Bashing-om on 2016-07-19
Alligator; :)

Many thanks for the thanks .. Appreciate the sentiment .

I do look forward to our next adventure.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

