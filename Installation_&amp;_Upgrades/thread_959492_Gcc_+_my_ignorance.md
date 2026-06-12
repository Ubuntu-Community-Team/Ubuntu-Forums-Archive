---
title: "Gcc + my ignorance"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by fit_gurl on 2008-10-26
Hi, 

I am very new to Ubuntu and gcc and programming in general. 
I'm doing a course in which i need gcc 3.4.6. 
So i downloaded Ubuntu and looked at the gcc version which was 4.2. 
I was trying to install gcc-3.4.6 and in the process deleted 4.2
I am in complete ignorance. I went into the package manager and reinstalled 4.2. I did the sudo apt-get install build essential command and when i do a gcc -v command now it is telling me: 

The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder


I really need someone to help me and explain it to me like i'm a two year old! 
HELP!!!!

---

### Post by brianfreytag on 2008-10-26
```
sudo apt-get install gcc pentium-builder
```

It sounds to me that the actual gcc package is not properly installed.  Give that code above a try.

Welcome to the Ubuntu forums :)

---

### Post by fit_gurl on 2008-10-26
Thanks for the welcome! ;) 

I did that and got this diatribe: 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
gcc is already the newest version.
gcc set to manually installed.
The following NEW packages will be installed:
  pentium-builder
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7178B of archives.
After this operation, 81.9kB of additional disk space will be used.
(Reading database ... 101355 files and directories currently installed.)
Unpacking pentium-builder (from .../pentium-builder_0.19_all.deb) ...
dpkg-divert: Cannot divert directories

Usage: dpkg-divert [<option> ...] <command>

Commands:
  [--add] <file>           add a diversion.
  --remove <file>          remove the diversion.
  --list [<glob-pattern>]  show file diversions.
  --truename <file>        return the diverted file.

Options:
  --package <package>      name of the package whose copy of <file> will not
                             be diverted.
  --local                  all packages' versions are diverted.
  --divert <divert-to>     the name used by other packages' versions.
  --rename                 actually move the file aside (or back).
  --admindir <directory>   set the directory with the diversions file.
  --test                   don't do anything, just demonstrate.
  --quiet                  quiet operation, minimal output.
  --help                   show this help message.
  --version                show the version.

When adding, default is --local and --divert <original>.distrib.
When removing, --package or --local and --divert must match if specified.
Package preinst/postrm scripts should always specify --package and --divert.
dpkg: error processing /var/cache/apt/archives/pentium-builder_0.19_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/pentium-builder_0.19_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I've been following instructions on that many sites today i honestly don't know how many wronk turns i've taken. Very very lost... :-/

---

### Post by brianfreytag on 2008-10-26
That's an interesting error.

Have you checked in Synaptic Package Manager and done a search for gcc?

Go to System -> Administration -> Synaptic Package Manager

If you have Ubuntu Hardy Heron (8.04), click the Search button and type gcc and press search.  If you have Ubuntu Intrepid Ibex, in the Quick Search box, type gcc.

There is an option there for gcc-3.4.  Right click it and select "Mark for Installation."

Then press the Apply.

This should go ahead and install 3.4.6 and all dependencies  for you.

Then run in terminal:

```
gcc -v
```I did this and this is what I got:

```

brian@brian-ubuntu:~$ gcc -v
Using built-in specs.
Target: x86_64-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu11' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-checking=release --build=x86_64-linux-gnu --host=x86_64-linux-gnu --target=x86_64-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11)

```

So it only shows the most up-to-date version installed, but you do have gcc 3.4.6 installed.  You should be able to do things with that version.  Just make sure when you're doing your project, you specify that you want to use 3.4.6.

BTW... "diatribe"... Nice word usage :)

---

### Post by fit_gurl on 2008-10-26
Yeah i've done this already and now just again. 
I get the error again: 
The program 'gcc' can be found in the following packages:
 * gcc
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: gcc: command not found

I've been at this since 8am this morning so i'm gonna walk away before my mac becomes a casualty! 
Thanks for your help. 
I think i might uninstall ubuntu and start again tomorrow. (Another wasted day)

Thanks agian! :)

---

