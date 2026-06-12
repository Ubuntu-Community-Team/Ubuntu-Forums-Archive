---
title: "apt-get severely damaged my system installing g++"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by studout on 2009-04-01
I used ``sudo apt-get install g++'' to install the gnu c++ compiler on my (Ubuntu Intrepid 8.10) machine.
Now, the system that was installed and working nicely is heavily damaged.
It is was not possible to open a Nautilus window, or a shell window.  After logging out, it is now not possible to use the gui login, to log back in.  (no big deal, I can ssh in remotely)

How do I go about cleaning up this huge mess that apt-get made for me?
I have a log of what packages were installed before apt-get damaged my system, and I also have the scrollback that contains apt-get's output as it was damaging my system.
My first thought, would be to simply diff the before and after, remove the new, and "downgrade" the changed packages.
...but perhaps there is a better way of cleaning up one of apt-get's messes.. I doubt I'm the first victim.
In the past, I have used ``apt-get autoremove'' to remove a whole group of packages that were installed, but the packages it said it would [auto]remove are not all of the packages that it installed.

Secondly, since apt-get doesn't seem to be able to install g++ and maintain a working system for me, am I forced to hit gnu.org, download the relevant tarballs, and then Make it myself?

Here's apt-get's output.

```
The following extra packages will be installed:
  binutils cpp cpp-4.3 g++-4.3 gcc gcc-4.3 gcc-4.3-base lib32gcc1 lib32stdc++6
  libgcc1 libgomp1 libstdc++6 libstdc++6-4.3-dev
Suggested packages:
  binutils-doc cpp-doc gcc-4.3-locales g++-multilib g++-4.3-multilib
  gcc-4.3-doc libstdc++6-4.3-dbg gcc-multilib manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-4.3-multilib libmudflap0-4.3-dev
  libgcc1-dbg libgomp1-dbg libmudflap0-dbg libstdc++6-4.3-doc
The following NEW packages will be installed:
  g++ g++-4.3 libstdc++6-4.3-dev
The following packages will be upgraded:
  binutils cpp cpp-4.3 gcc gcc-4.3 gcc-4.3-base lib32gcc1 lib32stdc++6 libgcc1
  libgomp1 libstdc++6
11 upgraded, 3 newly installed, 0 to remove and 965 not upgraded.
Need to get 14.9MB of archives.
After this operation, 21.1MB of additional disk space will be used.
```

---

### Post by dcstar on 2009-04-02
> **studout said:**
> I used ``sudo apt-get install g++'' to install the gnu c++ compiler on my (Ubuntu Intrepid 8.10) machine.
........
Here's apt-get's output.

```
The following extra packages will be installed:
  binutils cpp cpp-4.3 g++-4.3 gcc gcc-4.3 gcc-4.3-base lib32gcc1 lib32stdc++6
  libgcc1 libgomp1 libstdc++6 libstdc++6-4.3-dev
Suggested packages:
  binutils-doc cpp-doc gcc-4.3-locales g++-multilib g++-4.3-multilib
  gcc-4.3-doc libstdc++6-4.3-dbg gcc-multilib manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-4.3-multilib libmudflap0-4.3-dev
  libgcc1-dbg libgomp1-dbg libmudflap0-dbg libstdc++6-4.3-doc
The following NEW packages will be installed:
  g++ g++-4.3 libstdc++6-4.3-dev
The following packages will be upgraded:
  binutils cpp cpp-4.3 gcc gcc-4.3 gcc-4.3-base lib32gcc1 lib32stdc++6 libgcc1
  libgomp1 libstdc++6
11 upgraded, 3 newly installed, 0 to remove and 965 not upgraded.
Need to get 14.9MB of archives.
After this operation, 21.1MB of additional disk space will be used.
```

Fairly pointless just showing what it was going to do, you need to show what it **actually** did.

---

### Post by studout on 2009-04-02
How convenient, I JUST FINISHED producing such a list. :)

Top is list of what it downloaded
bottom...
Left is what was, tabbed right is what is.
```
gcc-4.3-base	    4.3.3-5ubuntu4
libstdc++6	    4.3.3-5ubuntu4
libgomp1	    4.3.3-5ubuntu4
lib32stdc++6	    4.3.3-5ubuntu4
lib32gcc1	    1:4.3.3-5ubuntu4
cpp-4.3		    4.3.3-5ubuntu4
binutils	    2.19.1-0ubuntu3
gcc-4.3		    4.3.3-5ubuntu4
libgcc1		    1:4.3.3-5ubuntu4
cpp		    4:4.3.3-1ubuntu1
gcc		    4:4.3.3-1ubuntu1
libstdc++6-4.3-dev  4.3.3-5ubuntu4
g++-4.3		    4.3.3-5ubuntu4
g++		    4:4.3.3-1ubuntu1


< ii  binutils                                  2.18.93.20081009-0ubuntu1
	> ii  binutils                                  2.19.1-0ubuntu3
< ii  cpp                                       4:4.3.1-1ubuntu2
< ii  cpp-4.3                                   4.3.2-1ubuntu11
	> ii  cpp                                       4:4.3.3-1ubuntu1
	> ii  cpp-4.3                                   4.3.3-5ubuntu4
	> ii  g++                                       4:4.3.3-1ubuntu1
	> ii  g++-4.3                                   4.3.3-5ubuntu4
< ii  gcc                                       4:4.3.1-1ubuntu2
< ii  gcc-4.3                                   4.3.2-1ubuntu11
< ii  gcc-4.3-base                              4.3.2-1ubuntu11
	> ii  gcc                                       4:4.3.3-1ubuntu1
	> ii  gcc-4.3                                   4.3.3-5ubuntu4
	> ii  gcc-4.3-base                              4.3.3-5ubuntu4
< ii  lib32gcc1                                 1:4.3.2-1ubuntu11
	> ii  lib32gcc1                                 1:4.3.3-5ubuntu4
< ii  lib32stdc++6                              4.3.2-1ubuntu11
	> ii  lib32stdc++6                              4.3.3-5ubuntu4
< ii  libc6                                     2.8~20080505-0ubuntu7
< ii  libc6-dev                                 2.8~20080505-0ubuntu7
< ii  libc6-i386                                2.8~20080505-0ubuntu7
	> ii  libc6                                     2.9-0ubuntu5
	> ii  libc6-dev                                 2.9-0ubuntu5
	> ii  libc6-i386                                2.9-0ubuntu5
< ii  libgcc1                                   1:4.3.2-1ubuntu11
	> ii  libgcc1                                   1:4.3.3-5ubuntu4
< ii  libglib2.0-0                              2.18.2-0ubuntu2
	> ii  libglib2.0-0                              2.20.0-1build1
	> ii  libglib2.0-dev                            2.20.0-1build1
< ii  libstdc++6                                4.3.2-1ubuntu11
	> ii  libstdc++6                                4.3.3-5ubuntu4
	> ii  libstdc++6-4.3-dev                        4.3.3-5ubuntu4
< ii  libgomp1                                  4.3.2-1ubuntu11
	> ii  libgomp1                                  4.3.3-5ubuntu4
```

---

### Post by studout on 2009-04-02
Here's the full output from apt-get.

```
$ sudo apt-get install g++
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  binutils cpp cpp-4.3 g++-4.3 gcc gcc-4.3 gcc-4.3-base lib32gcc1 lib32stdc++6
  libgcc1 libgomp1 libstdc++6 libstdc++6-4.3-dev
Suggested packages:
  binutils-doc cpp-doc gcc-4.3-locales g++-multilib g++-4.3-multilib
  gcc-4.3-doc libstdc++6-4.3-dbg gcc-multilib manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-4.3-multilib libmudflap0-4.3-dev
  libgcc1-dbg libgomp1-dbg libmudflap0-dbg libstdc++6-4.3-doc
The following NEW packages will be installed:
  g++ g++-4.3 libstdc++6-4.3-dev
The following packages will be upgraded:
  binutils cpp cpp-4.3 gcc gcc-4.3 gcc-4.3-base lib32gcc1 lib32stdc++6 libgcc1
  libgomp1 libstdc++6
11 upgraded, 3 newly installed, 0 to remove and 965 not upgraded.
Need to get 14.9MB of archives.
After this operation, 21.1MB of additional disk space will be used.
Do you want to continue [Y/n]?
Get:1 http://us.archive.ubuntu.com jaunty/main gcc-4.3-base 4.3.3-5ubuntu4 [107kB]
Get:2 http://us.archive.ubuntu.com jaunty/main libstdc++6 4.3.3-5ubuntu4 [336kB]
Get:3 http://us.archive.ubuntu.com jaunty/main libgomp1 4.3.3-5ubuntu4 [15.6kB]
Get:4 http://us.archive.ubuntu.com jaunty/main lib32stdc++6 4.3.3-5ubuntu4 [334kB]
Get:5 http://us.archive.ubuntu.com jaunty/main lib32gcc1 1:4.3.3-5ubuntu4 [26.1kB]
Get:6 http://us.archive.ubuntu.com jaunty/main cpp-4.3 4.3.3-5ubuntu4 [3392kB]
Get:7 http://us.archive.ubuntu.com jaunty/main binutils 2.19.1-0ubuntu3 [1609kB]
Get:8 http://us.archive.ubuntu.com jaunty/main gcc-4.3 4.3.3-5ubuntu4 [2799kB]
Get:9 http://us.archive.ubuntu.com jaunty/main libgcc1 1:4.3.3-5ubuntu4 [44.6kB]
Get:10 http://us.archive.ubuntu.com jaunty/main cpp 4:4.3.3-1ubuntu1 [35.6kB]
Get:11 http://us.archive.ubuntu.com jaunty/main gcc 4:4.3.3-1ubuntu1 [5106B]
Get:12 http://us.archive.ubuntu.com jaunty/main libstdc++6-4.3-dev 4.3.3-5ubuntu4 [1394kB]
Get:13 http://us.archive.ubuntu.com jaunty/main g++-4.3 4.3.3-5ubuntu4 [4826kB]
Get:14 http://us.archive.ubuntu.com jaunty/main g++ 4:4.3.3-1ubuntu1 [1450B]
Fetched 14.9MB in 16s (880kB/s)

(Reading database ... 124239 files and directories currently installed.)
Preparing to replace gcc-4.3-base 4.3.2-1ubuntu11 (using .../gcc-4.3-base_4.3.3-5ubuntu4_amd64.deb) ...
Unpacking replacement gcc-4.3-base ...
Setting up gcc-4.3-base (4.3.3-5ubuntu4) ...

(Reading database ... 124238 files and directories currently installed.)
Preparing to replace libstdc++6 4.3.2-1ubuntu11 (using .../libstdc++6_4.3.3-5ubuntu4_amd64.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.3.3-5ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 124238 files and directories currently installed.)
Preparing to replace libgomp1 4.3.2-1ubuntu11 (using .../libgomp1_4.3.3-5ubuntu4_amd64.deb) ...
Unpacking replacement libgomp1 ...
Preparing to replace lib32stdc++6 4.3.2-1ubuntu11 (using .../lib32stdc++6_4.3.3-5ubuntu4_amd64.deb) ...
Unpacking replacement lib32stdc++6 ...
Preparing to replace lib32gcc1 1:4.3.2-1ubuntu11 (using .../lib32gcc1_1%3a4.3.3-5ubuntu4_amd64.deb) ...
Unpacking replacement lib32gcc1 ...
Preparing to replace cpp-4.3 4.3.2-1ubuntu11 (using .../cpp-4.3_4.3.3-5ubuntu4_amd64.deb) ...
Unpacking replacement cpp-4.3 ...
Preparing to replace binutils 2.18.93.20081009-0ubuntu1 (using .../binutils_2.19.1-0ubuntu3_amd64.deb) ...
Unpacking replacement binutils ...
Preparing to replace gcc-4.3 4.3.2-1ubuntu11 (using .../gcc-4.3_4.3.3-5ubuntu4_amd64.deb) ...
Unpacking replacement gcc-4.3 ...
Preparing to replace libgcc1 1:4.3.2-1ubuntu11 (using .../libgcc1_1%3a4.3.3-5ubuntu4_amd64.deb) ...
Unpacking replacement libgcc1 ...
Processing triggers for man-db ...
Setting up libgcc1 (1:4.3.3-5ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
(Reading database ... 124239 files and directories currently installed.)
Preparing to replace cpp 4:4.3.1-1ubuntu2 (using .../cpp_4%3a4.3.3-1ubuntu1_amd64.deb) ...
Unpacking replacement cpp ...
Preparing to replace gcc 4:4.3.1-1ubuntu2 (using .../gcc_4%3a4.3.3-1ubuntu1_amd64.deb) ...
Removing old gcc doc directory.
Unpacking replacement gcc ...
Selecting previously deselected package libstdc++6-4.3-dev.
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.3-5ubuntu4_amd64.deb) ...
Selecting previously deselected package g++-4.3.
Unpacking g++-4.3 (from .../g++-4.3_4.3.3-5ubuntu4_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.3.3-1ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up libgomp1 (4.3.3-5ubuntu4) ...

Setting up lib32gcc1 (1:4.3.3-5ubuntu4) ...

Setting up lib32stdc++6 (4.3.3-5ubuntu4) ...

Setting up cpp-4.3 (4.3.3-5ubuntu4) ...
Setting up binutils (2.19.1-0ubuntu3) ...

Setting up gcc-4.3 (4.3.3-5ubuntu4) ...
Setting up cpp (4:4.3.3-1ubuntu1) ...

Setting up gcc (4:4.3.3-1ubuntu1) ...

Setting up libstdc++6-4.3-dev (4.3.3-5ubuntu4) ...
Setting up g++-4.3 (4.3.3-5ubuntu4) ...
Setting up g++ (4:4.3.3-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

---

### Post by studout on 2009-04-02
Looking at the output, it is possible to see what order they were installed in.  My best guess is to use a command of the form
```
apt-get install <package name>=<version>
```
to tell it to install the correct version, and do this in the reverse order of how it installed the packages.

For example, I tried installing the correct version of libgomp1, and it said that it could not because of unmet dependencies.
That is why I thought fixing in the reverse order is best.

I am a bit reluctant to simply try what seems like the logical sulution on this because of the severity of the problem, and not wanting to make it worse

-Thanks.

---

### Post by lloyd_b on 2009-04-02
> 11 upgraded, 3 newly installed, 0 to remove and **965 not upgraded.**
It looks like you've changed sources.list to point to Jaunty, but you've never completed the upgrade process.  This is probably the source of your problems - some of your packages have been upgraded to that version, while others have not.

Lloyd B.

---

### Post by studout on 2009-04-02
Gah!

```
~/$ grep -i Jaunty /etc/apt/sources.list
deb http://us.archive.ubuntu.com/ubuntu/ jaunty main universe
~/$
```

I did... I remember doing it.
I did that so that I could install the latest version of Seamonkey.

Ok, at least now I have a presumed path for getting g++ installed once I clean up this mess that *I* made.

That all being the case, my best guess is still to tell it to install the specific versions that I had, in the reverse order they were upgraded.  Thoughts?

-Thanks.

---

### Post by studout on 2009-04-02
I was able to get these packages removed... that was no problem.
```

remove	> ii  libstdc++6-4.3-dev                        4.3.3-5ubuntu4
remove	> ii  g++-4.3                                   4.3.3-5ubuntu4
remove	> ii  g++      
```

These packages, I managed to "downgrade" to the correct version using "sudo apt-get install package=version"
```

< ii  cpp                                       4:4.3.1-1ubuntu2
	> ii  cpp                                       4:4.3.3-1ubuntu1
< ii  gcc                                       4:4.3.1-1ubuntu2
	> ii  gcc                                       4:4.3.3-1ubuntu1
```


Several of these rely on gcc-4.3-base, and apt-get wants to uninstall my whole system to swap that out.
It was willing to "upgrade" gcc-4.3-base to the wrong version, but it's not willing to "downgrade" to the correct verion w/o swapping out pretty much everything else?
I commented out the reference in my sources.list file to the Jaunty repository, and then ask it to reinstall g++, but that didn't work.
--- I'm pretty much stuck.
Any ideas?  Thanks.
```
< ii  libc6                                     2.8~20080505-0ubuntu7
	> ii  libc6                                     2.9-0ubuntu5
< ii  libc6-dev                                 2.8~20080505-0ubuntu7
	> ii  libc6-dev                                 2.9-0ubuntu5
< ii  libc6-i386                                2.8~20080505-0ubuntu7
	> ii  libc6-i386                                2.9-0ubuntu5
< ii  libglib2.0-0                              2.18.2-0ubuntu2
	> ii  libglib2.0-0                              2.20.0-1build1
	> ii  libglib2.0-dev                            2.20.0-1build1

< ii  gcc-4.3-base                              4.3.2-1ubuntu11
	> ii  gcc-4.3-base                              4.3.3-5ubuntu4
< ii  libstdc++6                                4.3.2-1ubuntu11
	> ii  libstdc++6                                4.3.3-5ubuntu4
< ii  libgomp1                                  4.3.2-1ubuntu11
	> ii  libgomp1                                  4.3.3-5ubuntu4
< ii  lib32stdc++6                              4.3.2-1ubuntu11
	> ii  lib32stdc++6                              4.3.3-5ubuntu4
< ii  lib32gcc1                                 1:4.3.2-1ubuntu11
	> ii  lib32gcc1                                 1:4.3.3-5ubuntu4
< ii  cpp-4.3                                   4.3.2-1ubuntu11
	> ii  cpp-4.3                                   4.3.3-5ubuntu4
< ii  binutils                                  2.18.93.20081009-0ubuntu1
	> ii  binutils                                  2.19.1-0ubuntu3
< ii  gcc-4.3                                   4.3.2-1ubuntu11
	> ii  gcc-4.3                                   4.3.3-5ubuntu4
< ii  libgcc1                                   1:4.3.2-1ubuntu11
	> ii  libgcc1                                   1:4.3.3-5ubuntu4

```

---

### Post by unutbu on 2009-04-02
Perhaps this will help:
[http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html)

Backing up your data before beginning this adventure would be wise.
Of course, if you've backed-up your data, you could always just reinstall...

---

### Post by studout on 2009-04-02
Thanks for the link.
Is that assuming I've "upgraded" to Jaunty?  Because I've not, I'm running Intrepid, a copy that has been contaminated with 14 or so Jaunty packages.. the worst offender of which is probably libc6.  apt-get is sadly unwilling to remove the said contamination.

Interesting to know, would be why apt-get was willing to "upgrade" these packages while leaving everything else alone, but is unwilling to "downgrade" these packages while leaving everything else alone.  I understand the dependencies, and having to do it in the correct order, but ... how did this affect the other packages?  A bug?  A design flaw?

---

### Post by unutbu on 2009-04-02
The link discusses how to downgrade packages from the testing repo to packages in the stable repo on a Debian system.

It will take some thinking to reformulate what they are doing to apply it to your situation. The commands used there apply (in some form) to your situation, and do not require that you have completely upgraded to Jaunty.

Unfortunately, I don't have experience doing this myself, nor a virtual machine on which to test it. So I'm not confident enough to tell you exactly what to do.
This is why I suggested backing up and maybe even just reinstalling.

However, if you want to pursue this, here is another link discussing downgrading for Ubuntu users: [https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

I think the second method is what you want to look at. 

If we are lucky, that might solve the problem. If we are not, it will take a closer study of [http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html). To my very limited understanding, fixing the remaining packages seems to involve some banging around with

```

dpkg -i --force-overwrite PACKAGE.deb
```

to force the installation of particular .debs regardless of dependencies

and
```

dpkg --force-depends -r PACKAGE
```

to force the removal of packages regardless of dependencies.

Be careful about removing packages like libc6 because without it your system will be severely crippled if not inoperable.

According to [http://linuxmafia.com/faq/Debian/downgrade.html](http://linuxmafia.com/faq/Debian/downgrade.html), they were able to downgrade libc6 with a simple
```

apt-get install libc6/stable
```

(after setting up the /etc/apt/preferences first). 
For you, I imagine the equivalent command would be
```

sudo apt-get install libc6/intrepid
```

So maybe there is hope without doing the dpkg commands... but I don't know for sure.

---

### Post by studout on 2009-04-02
lloyd_b; thank you for realizing the situation with Jaunty.

unutbu; thank you for the highly informative and thoughtful responses.

I will thoroughly backup, try the downgrade, and if that does not go well, I will just reinstall.

Thanks again for the thoughtful replies and consideration.

---

### Post by zekopeko on 2009-04-02
wouldn't it be best to simply upgrade to jaunty using the offical method?
it's fairly stable.

---

### Post by studout on 2009-04-02
I'd say that the most significant reason I do not want to upgrade is that the usb tv tuner I am using, is only precariously working with the default kernel in Intrepid.  A very helpful person patched various codes to make it work.  Jaunty uses a different kernel .'. I'm sunk.

Intrepid uses 2.6.27-7-generic, and Jaunty 2.6.28-something or other.

If you're interested, you can read about it here.. [http://ubuntuforums.org/showthread.php?t=791842&page=4](http://ubuntuforums.org/showthread.php?t=791842&page=4)

Though, what is the prescribed upgrade method of which you speak?

Thank you for the reply :)

---

