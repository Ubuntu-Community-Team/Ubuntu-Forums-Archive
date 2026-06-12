---
title: "sync gparted to gnome svn"
date: 2009-01-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-17
Hi all, 
 We should sync gparted with gnome svn. 

[http://svn.gnome.org/viewvc/gparted](http://svn.gnome.org/viewvc/gparted)

The changelog of the latest head (with specific excerpts)

[http://svn.gnome.org/viewvc/gparted/trunk/ChangeLog?revision=1031&view=markup](http://svn.gnome.org/viewvc/gparted/trunk/ChangeLog?revision=1031&view=markup)

> 

2008-12-31 Curtis Gedak <gedakc@gmail.com>

38     
39     * src/Utils.cc: Added e2fsprogs version required for ext4 support. 



as well as 

> 

008-12-20 Curtis Gedak <gedakc@gmail.com>
47     
48     * src/ext4.cc: Add flags to create journal and use extent option.
49     
50     2008-12-18 Curtis Gedak <gedakc@gmail.com>
51     
52     * include/Utils.h,
53     src/GParted_Core.cc,
54     src/Utils.cc: Added support for ext4 file systems.
55     - Closes GParted bug #503112
56     
57     * include/ext4.h,
58     include/Makefile.am,
59     src/ext4.cc,
60     src/Makefile.am: Created 2 files to support ext4 operations.
61     - Support for ext4 is planned for version 2.6.28 of the Linux kernel.
62     - e2fsprogs version 1.41.0 or higher is required.
63     
64     * include/FS_Info.h,
65     src/FS_Info.cc: Added get_fs_type() method



---

### Post by autocrosser on 2009-01-17
There is a bug report about ext4 support in gparted:  [https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872)

I'm adding the thread to the report--Colin has a bit of a load right now, but that "might" make it easier.......

---

### Post by plun on 2009-01-23
Well, svn builds ok after a little challenges.

build-dep, gnome-common and libdevmapper-dev  are needed as deps

Seems to be OK and EXt4 partitions are recognised

ver 4.2 should be stable release for EXT4.

---

### Post by Eclipse. on 2009-01-23
> **plun said:**
> Well, svn builds ok after a little challenges.

build-dep, gnome-common and libdevmapper-dev  are needed as deps

Seems to be OK and EXt4 partitions are recognised

ver 4.2 should be stable release for EXT4.

Its been done already.;)

---

### Post by plun on 2009-01-23
> **Eclipse. said:**
> Its been done already.;)

Its Ok.....?  ;)

I just compiled it and it looks OK....:D

---

### Post by Starks on 2009-01-23
I think at the very least a ppa is in order.

---

### Post by MacUntu on 2009-01-23
Just resized an EXT4 partition, seems to work fine:

```

GParted 0.4.1-svn

Libparted 1.8.8
Move /dev/sda5 to the left and grow it from 13.11 GiB to 21.11 GiB  00:13:38    ( SUCCESS ) 
```

---

### Post by Starks on 2009-01-23
I like.

[[IMG]http://img172.imageshack.us/img172/3974/smexyvh6.th.png[/IMG]](http://img172.imageshack.us/my.php?image=smexyvh6.png)

---

### Post by Starks on 2009-01-25
I'd like to remind everyone that the lack of synchronization is absurd.

What's the point of ext4 if we can't even put an ext4-enabled build of Gparted on a livecd or liveusb of Ubuntu short of creating a custom iso. In addition to this, neither a ext4-enabled bootable livecd or liveusb image of Gparted Live even exists yet.

Why was ext4 implemented if there is no meaningful way of altering the partitions after the installation of Ubuntu?

---

### Post by Gourgi on 2009-01-25
[QUOTE=Starks]I'd like to remind everyone that the lack of synchronization is absurd.

What's the point of ext4 if we can't even put an ext4-enabled build of Gparted on a livecd or liveusb of Ubuntu short of creating a custom iso. In addition to this, neither a ext4-enabled bootable livecd or liveusb image of Gparted Live even exists yet.

Why was ext4 implemented if there is no meaningful way of altering the partitions after the installation of Ubuntu? [/QUOTE]

i totally agree with that and i also think that devs would agree too.
patience  :)
i'm sure devs put their best on it and i hope it will be ready soon enough.

just give them some space and time.

---

### Post by bruce89 on 2009-01-25
Usually (especially with programs like this), SVN snapshots aren't packaged. Wait until there's a new official release.

---

### Post by MacUntu on 2009-01-25
Yeah, just be patient or compile it yourself. There's no way we'll have EXT4-support without such an important tool. :)

---

### Post by amano on 2009-01-26
Is there a bug filed for syncronizing with the current gparted SVN? That bug should get a pretty high priority then...

---

### Post by plun on 2009-01-26
> **amano said:**
> Is there a bug filed for syncronizing with the current gparted SVN? That bug should get a pretty high priority then...

Yup this one

[https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872](https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/137872)

"Waiting for Debian".....;)

---

### Post by ronacc on 2009-01-26
I'm trying to checkout the sources from svn but I get this response.

ron@rondesktopb:~/tmp/build/gparted$ svn checkout [http://svn.gnome.org/viewvc/gparted/trunk/](http://svn.gnome.org/viewvc/gparted/trunk/) gparted
svn: Repository moved temporarily to '/viewvc/gparted/trunk/'; please relocate


what am I doing wrong ?

---

### Post by MacUntu on 2009-01-26
[http://live.gnome.org/Subversion](http://live.gnome.org/Subversion)

If you want to checkout via subversion you need to contact the subversion server, not the http server. ;)

* svn checkout svn://svn.gnome.org/svn/gparted
* cd gparted
* Install gparted build-deps, gnome-common and libdevmapper-dev 
* sh autogen.sh
* make
* sudo make install

Good to go.

---

### Post by Eclipse. on 2009-01-26
EXT4 support is already in (g)pated, no need to compile from SVN.

---

### Post by ronacc on 2009-01-26
@ macuntu thanks , I see where I went wrong .

---

### Post by ronacc on 2009-01-26
@ Eclipse  not on my sys (64bit) and I am uptodate as of 9 AM this morning . see screenshot . Did you mean the standalone gparted ?

---

### Post by MacUntu on 2009-01-26
> **Eclipse. said:**
> EXT4 support is already in (g)pated, no need to compile from SVN.

```
gparted:
  Installed: 0.3.9-3ubuntu1
  Candidate: 0.3.9-3ubuntu1
  Version table:
 *** 0.3.9-3ubuntu1 0
        500 http://archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status

```

Gparted 0.3.9 does not recognize EXT4 partitions.

---

