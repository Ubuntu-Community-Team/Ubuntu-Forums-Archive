---
title: "Can't install gimp after partial update"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by Grab&amp;Drop on 2012-03-01
Hi

I did a partial update that included removing gimp.
I thought I would be able to reinstall it.
when I try to install it via terminal, I got:
> The following packages have unmet dependencies:
 gimp : Depends: libgimp2.0 (>= 2.7.5) but it is not going to be installed
        Depends: libgimp2.0 (<= 2.7.5-z) but it is not going to be installed
        Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.


I tried to install libgimp2.0 and libglib2.0-0 but it also didn't success.

wot can I do? learn using Inkscape?

---

### Post by Lasall on 2012-03-01
Hi Grab&Drop,

do you have enabled any PPAs? If so just disable PPA that provides gimp.


Kind regards

Lasall

---

### Post by Grab&amp;Drop on 2012-03-02
I removed all my gimp PPAs. nothin.

---

### Post by Lasall on 2012-03-02
Please show:

```

apt-cache policy gimp libgimp2.0 libgimp2.0 libglib2.0-0

```

---

### Post by Grab&amp;Drop on 2012-03-02
```
libglib2.0-0:
  Installed: 2.30.0-0ubuntu4
  Candidate: 2.30.0-0ubuntu4
  Version table:
 *** 2.30.0-0ubuntu4 0
        500 http://cy.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages
        100 /var/lib/dpkg/status
gimp:
  Installed: (none)
  Candidate: 2.6.11-2ubuntu4
  Version table:
     2.7.4-2011102201~oo 0
        100 /var/lib/dpkg/status
     2.6.11-2ubuntu4 0
        500 http://cy.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages
libgimp2.0:
  Installed: (none)
  Candidate: 2.6.11-2ubuntu4
  Version table:
     2.6.11-2ubuntu4 0
        500 http://cy.archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages

```

thanks

---

### Post by Lasall on 2012-03-02
Easiest solution is to use apt-pinning. Open (or create) **/etc/apt/preferences** and insert following lines:

```

Package: *
Pin: release a=oneiric*
Pin-Priority: 1001

```

Then run installation again:
```

sudo apt-get install gimp

```

---

### Post by picciottino on 2012-03-02
> **Lasall said:**
> Easiest solution is to use apt-pinning. Open (or create) **/etc/apt/preferences** and insert following lines:

```

Package: *
Pin: release a=oneiric
Pin-Priority: 1001

```

Then run installation again:
```

sudo apt-get install gimp

```

It worked for me but I also had to re-install some libraries (I launched gimp on the terminal and read the errors)

---

### Post by Grab&amp;Drop on 2012-03-02
> **Lasall said:**
> Easiest solution is to use apt-pinning. Open (or create) **/etc/apt/preferences** and insert following lines:

```

Package: *
Pin: release a=oneiric
Pin-Priority: 1001

```

Then run installation again:
```

sudo apt-get install gimp

```

```
maor@victor-M61PME-S2P:~$ Package: *
Package:: command not found
maor@victor-M61PME-S2P:~$ Pin: release a=oneiric
Pin:: command not found
maor@victor-M61PME-S2P:~$ Pin-Priority: 1001
Pin-Priority:: command not found

```

I don't think it should happen...
edit: oh sorry I didn't see the first line
I will check now

another edit: yea dude! it worked! woohoo!
a guide for who didn't understand: first I created the file like he said via root user.
then I went to synaptic, searched for libgegl-0.0 and it gave me three packages. I installed them all, runned gimp and... designed.

---

### Post by Lasall on 2012-03-02
Nice :) . When it's working now, you should remove these lines (because they are no longer required for anything).

---

### Post by whitepixel on 2012-03-04
Hello ive got the same error:

I'm using ubuntu 11.10 AMD64

> gimp : Depends: libgimp2.0 (>= 2.7.5) but it is not going to be installed
        Depends: libgimp2.0 (<= 2.7.5-z) but it is not going to be installed
        Depends: libglib2.0-0 (>= 2.31.2) but 2.30.0-0ubuntu4 is to be installed
E: Unable to correct problems, you have held broken packages.

i tried Lasall solution but doesnt work.

here's the output of the command:

apt-cache policy gimp libgimp2.0 libgimp2.0 libglib2.0-0

> libglib2.0-0:
  Installed: 2.30.0-0ubuntu4
  Candidate: 2.30.0-0ubuntu4
  Version table:
 *** 2.30.0-0ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
gimp:
  Installed: (none)
  Candidate: 2.7.5-2012020902~oo
  Version table:
     2.7.5-2012020902~oo 0
        500 [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/) oneiric/main amd64 Packages
     2.6.11-2ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages
libgimp2.0:
  Installed: (none)
  Candidate: 2.7.5-2012020902~oo
  Version table:
     2.7.5-2012020902~oo 0
        500 [http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/](http://ppa.launchpad.net/matthaeus123/mrw-gimp-svn/ubuntu/) oneiric/main amd64 Packages
     2.6.11-2ubuntu4 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) oneiric/main amd64 Packages
        100 /var/lib/dpkg/status


Any more work around? 
thanks in advance

---

### Post by Lasall on 2012-03-04
Hi whitepixel,

you have to disable your PPA first.

---

### Post by whitepixel on 2012-03-04
Hello Lasall, 
I really appreciate the quick reply.

Disabling the PPA definitely works, but it installed the stable release of Gimp, What i would like to accomplish is to install the Development version of Gimp 2.7.4 is this possible in ubuntu 11.10 AMD64?

Sorry for the noob question, I'm new to linux only 2 months old from windows os. And I'm really liking the way how linux works specially ubuntu:).

---

### Post by Lasall on 2012-03-04
> **whitepixel said:**
> Hello Lasall, 
I really appreciate the quick reply.

Disabling the PPA definitely works, but it installed the stable release of Gimp, What i would like to accomplish is to install the Development version of Gimp 2.7.4 is this possible in ubuntu 11.10 AMD64?

Sorry for the noob question, I'm new to linux only 2 months old from windows os. And I'm really liking the way how linux works specially ubuntu:).

First of all: That's not a "noob" question (if they exist at all).

There is some GNOME stuff you have to upgrade to get new GIMP 2.7.5 running (or even building). I do not recommend to upgrade such essential stuff partially, but if you want so, do some backups and read PPA description of mrw-gimp-svn. Matt Walker points to two other PPAs you have to enable (which should contain that stuff)...

If there are no essential features in GIMP 2.7.X for you, I think best way is to wait for Precise release. Then you can enable GIMP PPA (or just rebuild it for your own ;) ).
Alternatively you can use Natty version GIMP 2.7.3 which should install and work ootb.

---

### Post by whitepixel on 2012-03-05
> **Lasall said:**
> First of all: That's not a "noob" question (if they exist at all).

There is some GNOME stuff you have to upgrade to get new GIMP 2.7.5 running (or even building). I do not recommend to upgrade such essential stuff partially, but if you want so, do some backups and read PPA description of mrw-gimp-svn. Matt Walker points to two other PPAs you have to enable (which should contain that stuff)...

If there are no essential features in GIMP 2.7.X for you, I think best way is to wait for Precise release. Then you can enable GIMP PPA (or just rebuild it for your own ;) ).
Alternatively you can use Natty version GIMP 2.7.3 which should install and work ootb.

Hello Lasall,

Thanks for the info, I think ill just stick with oneirick for the time being to be familiarize with the OS. 

I found a binary if GIMP 2.7.4 which you just download and run it. here's the link ([http://alcides-mp.com/software/gimp-2-7-4-binaries-for-ubuntu/](http://alcides-mp.com/software/gimp-2-7-4-binaries-for-ubuntu/)) incase someone wants to use it. You don't need to remove your current gimp version by doing this. A bit buggy but you can test it.

Thanks Lasall

---

