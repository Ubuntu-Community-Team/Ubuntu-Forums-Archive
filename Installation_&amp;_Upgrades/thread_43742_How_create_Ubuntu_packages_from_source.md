---
title: "How create Ubuntu packages from source?"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by peter07 on 2005-06-23
How create Ubuntu packages from source?

I have 1 archive with source. I want to create package - buy I don't know how. I read some manuals ( for example [http://www.debian.org/doc/maint-guide/ap-pkg-eg.en.html#s-pkg-simple)](http://www.debian.org/doc/maint-guide/ap-pkg-eg.en.html#s-pkg-simple)), but when I start to bulid my package - it doesn't work. 

Please help

---

### Post by Juergen on 2005-06-23
> it doesn't work I don't think anybody can help you with that little info on **what** doesn't work.

First look if this package is available in the Ubuntu-repositories. 
If it's there and you just want to change some compile-time settings, look at apt-build. 
[http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

Or, if you're just looking for a way to deinstall cleanly, look at 'checkinstall'

---

### Post by peter07 on 2005-06-23
> First look if this package is available in the Ubuntu-repositories. 

I want to install psi - psz ( jabber client). I can't find it in the Ubuntu-repositories. It is unofficial version. There isn't any Ubuntu ( Debian) package of this software.

>  I don't think anybody can help you with that little info on what doesn't work.

Ok, my misteake.

I have got psi-psz-src-2005.02.28.tar.bz2 file with source of psi-psz. I want to make package and then install this software. I've  read some manuals, but there are too 	complicated for me. I'm new Ubuntu user ( only 1 week with Linux ). Maybe somebody may help me and present ( step by step ) method of creating packages.

---

### Post by endy on 2005-06-23
I often use the program 'checkinstall'. All you do is configure and make the program as normal then 'sudo checkinstall' and you'll have a package built and installed. Very easy.

---

### Post by Juergen on 2005-06-24
> I'm new Ubuntu user ( only 1 week with Linux ).I, too, would recommend checkinstall then.

Or probably even better for the stability of your system: try to stay with official Ubuntu-packages until you reach the 'advanced user'-status ;-)
There are several jabber clients in the repositories.

---

### Post by peter07 on 2005-06-24
I have big problems:

1) First of all I entered to the directory, where software source is

cd path/to/file ...

2) Next, I configured the installation:

sudo auto-apt run ./configure --prefix=/usr

3) Next I tried to use make command.

sudo make

I recived message:

make[1]: *** [psi] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/XXXXX/MyDownloads/psi-psz/psi-psz-src-2005.02.28/psi/src'
make: *** [sub-src] B&#322;&#261;d 2

4) I tried cheskinstall:

sudo checkinstall

*****************************************
**** Debian package creation selected ***
*****************************************

Building Debian package... FAILED!

*** Failed to build the package

And the log file:

dpkg-deb - b&#322;&#261;d: (upstream) version (`psi') nie zawiera &#380;adnej cyfry ( in English - there is no digit/number)
dpkg-deb: 1 b&#322;&#281;dów w pliku kontrolnym ( In En 1 error in control file)

What I did wrong. How to reinstall this software ???

---

### Post by peter07 on 2005-06-24
[QUOTE=Juergen]I, too, would recommend checkinstall then.

Or probably even better for the stability of your system: try to stay with official Ubuntu-packages until you reach the 'advanced user'-status ;-)
There are several jabber clients in the repositories.[/QUOTE]
 But only **psi - psz** have options to work proprerly with Polish gadu-gadu ( the most popular in my country)

---

### Post by Juergen on 2005-06-24
> sudo auto-apt run ./configure --prefix=/usrThis ran without showing Errors?

> make[1]: *** [psi] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/XXXXX/MyDownloads/psi-psz/psi-psz-src-2005.02.28/psi/src'
make: *** [sub-src] B&#322;&#261;d 2The lines starting with (or containing) 'Error' that come before these are the interesting ones...

Oh, and BTW: try to translate the messages like you did for the log ;-)

---

### Post by peter07 on 2005-06-24
> Oh, and BTW: try to translate the messages like you did for the log 

You don't know Polish :)

Ok -  sudo auto-apt run ./configure --prefix=/usr

Entering auto-apt mode: ./configure --prefix=/usr
Exit the command to leave auto-apt mode.
Configuring Psi ...
Verifying Qt 3.x Multithreaded (MT) build environment ... ok
Checking for Qt >= 3.1 ... yes
Checking for QCA 1.0 ... yes
Checking for zlib ... yes
Checking for the XScreenSaver extension ... no
Checking for Linux Directory Notification ... yes
Checking for gethostbyname_r() ... yes
Checking for KDE ... no

Good, your configure finished. Now run 'make'.



 
Next make and errors:

make[1]: *** [psi] B&#322;&#261;d 1                            - Error 1
make[1]: Opuszczenie katalogu                      `/home/XXXXX/MyDownloads/psi-psz/psi-psz-src-2005.02.28/psi/src'    -  	leaving directory ( abandonment )
make: *** [sub-src] B&#322;&#261;d 2                         -  Error 2

What lines before??? Those are first lines with errors message.

How can I easly unistall this software????

My PC has crashed when I was installing psi first time - maybe that couses errors????

---

### Post by Juergen on 2005-06-24
> What lines before??? Those are first lines with errors message.Nothing like 'gcc: not found' or such? Make usually only stops if one of the tools it invokes throws an exception.

Have you installed the C(++)-compiler? If ./configure runs, probably yes, but:
Install package 'build-essential' and try again.

---

### Post by peter07 on 2005-06-24
[QUOTE=Juergen]Nothing like 'gcc: not found' or such? Make usually only stops if one of the tools it invokes throws an exception.

Have you installed the C(++)-compiler? If ./configure runs, probably yes, but:
Install package 'build-essential' and try again.[/QUOTE]

Yes i have c++ compiler. I'll try build-essential.

But - how I can uninstall psi - psz??? Make comand has made some new files???

---

### Post by Juergen on 2005-06-24
Until a 'make install' runs all the way through you only create files in the source-dir.
Nothing in the system should be changed.

You can remove this with just 'rm -rf path/to/source'

---

### Post by peter07 on 2005-06-25
I've just used: sudo make uninstall_subdirs && make uninstall

I have build-essential now.

I still don't have psi - psz installed. Maybe somebody else will try to create this package and then will tell me what I have done wrong ??

---

### Post by peter07 on 2005-06-30
I almost made the debian package. I've used  './configure' next 'sudo make' and next 'sudo checkinstall'. That time I haven't got any errors messages. But when I've ended compilation I started the aplication and I recived error messages: 

> 
QGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nno tabs\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nQGDict::hashKeyString: Invalid null key\nQGDict::hashKeyString: Invalid null key\nWARNING: IconsetFactory::icon("psi/statInd"): icon not found\nWARNING: IconsetFactory::icon("psi/statInd"): icon

(fragment)

I've tried:

> psi >/dev/null 2>&1&

What I have done wrong????????

---

