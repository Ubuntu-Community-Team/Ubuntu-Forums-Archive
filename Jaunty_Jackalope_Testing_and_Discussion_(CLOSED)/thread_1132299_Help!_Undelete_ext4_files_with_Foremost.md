---
title: "Help! Undelete ext4 files with Foremost?"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubu-for on 2009-04-21
Does anybody know if I can undelete files from an ext4 partition with Foremost?

Damn fast and unstable ext4!!!

Maybe I have the same problem like the following user?

[http://ubuntuforums.org/showthread.php?t=706500](http://ubuntuforums.org/showthread.php?t=706500)

```
~$ foremost -v -i /home/***/MyFiles -o /media/disk/FM
Foremost version 1.5.5 by Jesse Kornblum, Kris Kendall, and Nick Mikus
Audit File

Foremost started at Tue Apr 21 23:41:38 2009
Invocation: foremost -v -i /home/***/MyFiles -o /media/disk/FM 
Output directory: /media/disk/FM
Configuration file: /etc/foremost.conf
Processing: stdin
|------------------------------------------------------------------
File: stdin
Start: Tue Apr 21 23:41:38 2009
Length: Unknown
 
Num	 Name (bs=512)	       Size	 File Offset	 Comment 



```

Thanks in advance for every hint!

Please help!

---

### Post by psyke83 on 2009-04-22
> **ubu-for said:**
> Does anybody know if I can undelete files from an ext4 partition with Foremost?

Damn fast and unstable ext4!!!

Maybe I have the same problem like the following user?

[http://ubuntuforums.org/showthread.php?t=706500](http://ubuntuforums.org/showthread.php?t=706500)

```
~$ foremost -v -i /home/***/MyFiles -o /media/disk/FM
Foremost version 1.5.5 by Jesse Kornblum, Kris Kendall, and Nick Mikus
Audit File

Foremost started at Tue Apr 21 23:41:38 2009
Invocation: foremost -v -i /home/***/MyFiles -o /media/disk/FM 
Output directory: /media/disk/FM
Configuration file: /etc/foremost.conf
Processing: stdin
|------------------------------------------------------------------
File: stdin
Start: Tue Apr 21 23:41:38 2009
Length: Unknown
 
Num	 Name (bs=512)	       Size	 File Offset	 Comment 



```

Thanks in advance for every hint!

Please help!

The application would need to be patched to support EXT4 properly, and considering that the latest upstream release was in October 2008, I think you can guess the answer to your question.

---

### Post by alphacrucis2 on 2009-04-22
> **psyke83 said:**
> The application would need to be patched to support EXT4 properly, and considering that the latest upstream release was in October 2008, I think you can guess the answer to your question.

I read that a new version of testdisk (6.11) that supports ext4 is available. Doesn't appear to be in the Jaunty repos yet.

---

### Post by FredB on 2009-04-22
Why enabling ext4 ? Canonical won't enabled it until Karmic... So, if you lose data without doing backup, this is your fault, not ext4 one.

---

### Post by alphacrucis2 on 2009-04-22
> **FredB said:**
> Why enabling ext4 ? Canonical won't enabled it until Karmic... So, if you lose data without doing backup, this is your fault, not ext4 one.

Someones gotta test it.:). In the mean time, it does give a notable performance boost on file system operations. Apart from possible bugs it looks like a number of utilities don't support it yet.

---

### Post by ubu-for on 2009-04-22
> **FredB said:**
> So, if you lose data without doing backup, this is your fault, not ext4 one.
I haven't lost my whole partition. You can't backup every new folder!

Sure it's ext4's fault! Ask Linus! ;)

> **alphacrucis2 said:**
> I read that a new version of testdisk (6.11) that supports ext4 is available. Doesn't appear to be in the Jaunty repos yet.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I've downloaded a rpm of Testdisk and converted it to a deb file with Alien, but now which option allows me to undelete some folders and files?

---

### Post by ubu-for on 2009-04-22
Photorec, a part of Testdisk, is very easy to use, but quits always with the following error message after I've selected the folder where to store the recovered files.

```
Filesystem analysis, please wait...
*** glibc detected *** corrupted double-linked list: 0x0819faac ***
                                                                   Aborted

```

Any ideas?

---

### Post by alphacrucis2 on 2009-04-22
> **ubu-for said:**
> Photorec, a part of Testdisk, is very easy to use, but quits always with the following error message after I've selected the folder where to store the recovered files.

```
Filesystem analysis, please wait...
*** glibc detected *** corrupted double-linked list: 0x0819faac ***
                                                                   Aborted

```

Any ideas?

You could try sending a problem report to the dev:

[URL="http://www.cgsecurity.org/wiki/Support"]http://www.cgsecurity.org/wiki/Support
[/URL]

---

### Post by ubu-for on 2009-04-22
> **alphacrucis2 said:**
> You could try sending a problem report to the dev:

[URL="http://www.cgsecurity.org/wiki/Support"]http://www.cgsecurity.org/wiki/Support
[/URL]

If I google the error message, I think it's because I took the rpm which wasn't compiled for Ubuntu.

---

### Post by alphacrucis2 on 2009-04-22
> **ubu-for said:**
> If I google the error message, I think it's because I took the rpm which wasn't compiled for Ubuntu.


I just had a go at downloading the source from cgsecurity. I managed to successfully compile it and it seems to work. 

[Instructions]("http://www.cgsecurity.org/wiki/TestDisk_Compilation")

I had all the libs except uuid-dev zlib1g-dev which I installed via apt-get.

There seems to be a line missing from the compile of testdisk itself. They have:

```
./configure
make

```

I also did a 

```
sudo make install
```

---

### Post by ubu-for on 2009-04-22
Thank you very much alphacrucis2 for your great support!!!

I thought the Linux version of Testdisk have to be compiled but I only had to extract the tar.bz2 file and started Photorec with the following command.

```
***@***:/$ sudo /home/***/testdisk-6.11/linux/photorec_static
```

> This Linux version of TestDisk & PhotoRec should work on any 2.6 i386
or x86_64 kernel. It's a static version, the binary doesn't depend on
shared libraries.

Finally Photorec could recover most of my files and all the rest I'll get back soon or will be a warning from ext4 "Never move files! Copy only!".

P.S. Photorec found really old files, too. Here's one of them. :mrgreen:

---

