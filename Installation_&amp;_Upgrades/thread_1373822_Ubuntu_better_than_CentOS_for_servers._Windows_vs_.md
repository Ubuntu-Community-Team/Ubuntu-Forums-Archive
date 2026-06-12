---
title: "Ubuntu better than CentOS for servers. Windows vs Linux, .deb vs .exe"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by xbaez on 2010-01-06
Hello. I am enjoying using Ubuntu but I have one question.

I recently rented a CentOS for around 6 months, and the glibc package was broken

Therefore, every now and then, apache would say 
********  glibc detected ***************

and apache would leak memory like crazy and in 30 seconds the load would go from 4 to 120

so I developed a program that checks the load every 30 second and stops/starts apache, mysql, lighttpd... based on the load

Anyway, I did some research and finally found that glibc was a faulty package on Red Hat, and since CentOS is a RedHat clone, yum updated this faulty glibc (automatically or when I installed a package, I don't remember)

The 'solution' was to download CentOS 5.2, and install the glibc package in a 'forced' mode.

Now, I tried to download CentOS 5.2 and they are not allowing people to download that version anymore (since they want you to download CentOS 5.4) 

So the solution was complicated

find a new server (I requested Ubuntu 9.10)
rsync all the files

Now, I can say I am happier with Ubuntu and my new server, installing the latest versions of httpd, Zend library, MySQL, php5, lighttpd... were easier

However, one time I checked the error in apache logs, and I saw that 
**** glibc detected ******** 
error

I checked the load and nothing happened, and the rest of the httpd process continue to work normally (I'm using the standard httpd with prefork)

in CentOS, when the 
**** glibc detected ********  
error happened, apache would 'hang' and start consuming memory like crazy


So my question is:
1) what causes this glibc detected error?
2) how can I make sure Ubuntu runs without any automatic software update that might break the current software?
3) for the benefit of the Linux community, do you think we're over complicating things by having packages for every distribution?

for example
if I want to download WinRAR for Windows I choose 32bit or 64bit, and then I download that


Now, in linux, I have to chose
Debian
Ubuntu 
Mandriva
Fedora
openSUSE
Gentoo
Slackware
FreeBSD
Arch

and it gets confusing
for example Skype, I can download it for Linux debian, since it comes already in .deb

Now, I can install that .deb file in Ubuntu (or Debian, if I'm using Debian)

However, I can't use a Debian repository in Ubuntu (even though they are .deb files)

So Debian and Ubuntu both use .deb files, however some files are compatible, some files are not (and adding a Debian repository to Ubuntu is not recommended)

So in Windows, you usually download the EXE file, and that's about it

so is there any way in which we could all make an 'official' way in which Linux installs software?

I changed distributions because of this, because Ubuntu has better repositories and better software than CentOS (CentOS is a clone of RedHat, so if RedHat fails, CentOs fails), so it should be more stable

Now, if all Linux distributions will use a unified system

glibc will be good, for any Linux distributions

Anyway, if you can read this post and just answer my 3 questions, I'll appreciate it :)

---

### Post by xbaez on 2010-01-06
I am reading Linux Mint PDF (as this distro seems pretty good with out of the box play of multimedia files), and it says:

[B]In summary, the distribution of static software
results in the unnecessary duplication of a lot of work.[/B]


I think Ubuntu software
1) is awesome thanks to apt-get, repositories, automatic installation of required libraries...

However, I think that Linux software is static
1) the software is not static, however, with so many distributions, the distributions themselves are 'static'

So we haven't solved this problem
**unnecessary duplication of a lot of work**

Anyway, my decision to use Ubuntu 9.10 in my new server is good right?

Is Ubuntu the best distro for a LAMP server?

---

### Post by theDaveTheRave on 2010-01-06
The answers to some of your questions are many, and complicated!

for the ones I feel able to answer

I'll start with the easiest

> 
Is Ubuntu the best distro for a LAMP server?


The best distro is the one that you (and your colleagues) find easiest to administer.

You may decide to have a different distro as a 'backup' (for instance debian is supposedly more "stable"). So using a "clone" of all your stuff onto a debian system should give you fault tolerance, how this would work in practice however I don't know?? It may be more "confusing" than helpfull?

HOWEVER again I say - The best distro is the one that you (and your colleagues) find easiest to administer
and best meets your requirements of course

>  for the benefit of the Linux community, do you think we're over complicating things by having packages for every distribution?


If only!

Most of the software available for the various distros is available in "source" format.
You would then download, compile, install, etc, etc, etc,....
The only difference would be for packages written in different languages using different compilers / interpreters.

So in effect all the software is the same for all the distro's.

However (and here is the catch), some make use of specific parts of certain distributions (I'm thinking specifically for kernel modules that may be specific to a certain distro - someone please correct me if I am incorrect ??).

If you have a particular peice of software that you need to use, and it doesn't work on your distro. Change the code, that is the beauty of open source - if you don't like a certain part of the ingredents in your dinner, you can easily take them out, and stir in something different.

David

---

### Post by xbaez on 2010-01-06
> **theDaveTheRave said:**
> The answers to some of your questions are many, and complicated!

for the ones I feel able to answer

I'll start with the easiest



The best distro is the one that you (and your colleagues) find easiest to administer.

You may decide to have a different distro as a 'backup' (for instance debian is supposedly more "stable"). So using a "clone" of all your stuff onto a debian system should give you fault tolerance, how this would work in practice however I don't know?? It may be more "confusing" than helpfull?

HOWEVER again I say - The best distro is the one that you (and your colleagues) find easiest to administer
and best meets your requirements of course



If only!

Most of the software available for the various distros is available in "source" format.
You would then download, compile, install, etc, etc, etc,....
The only difference would be for packages written in different languages using different compilers / interpreters.

So in effect all the software is the same for all the distro's.

However (and here is the catch), some make use of specific parts of certain distributions (I'm thinking specifically for kernel modules that may be specific to a certain distro - someone please correct me if I am incorrect ??).

If you have a particular peice of software that you need to use, and it doesn't work on your distro. Change the code, that is the beauty of open source - if you don't like a certain part of the ingredents in your dinner, you can easily take them out, and stir in something different.

David

I would rate CentOS 1/10
and I would rate Ubuntu, let's say, for sake only, 9/10

Linux is not Linux
as Apple is Apple 
or Microsoft is Microsoft

Linux, is basically, the distro that I am using

some people might differ

but in Ubuntu I disabled /etc/cron.daily/apt /etc/cron.daily/aptitude

because I am not going to do this moving servers crap over and over again

that said, I don't even consider CentOS a distro

it is RedHat, without the logo

so RedHat makes a faulty glibc, and boom, CentOS brakes

---

