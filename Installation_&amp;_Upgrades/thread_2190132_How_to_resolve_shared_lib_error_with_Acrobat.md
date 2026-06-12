---
title: "How to resolve shared lib error with Acrobat"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by Thund3rstruck on 2013-11-25
On Kubuntu 13.10 (X64), I downloaded and installed Reader 9.5.5 from Adobe's website using the provided *.run file. 

On execution the following error occurs:
```

acroread 
/opt/Adobe/Reader9/Reader/intellinux/bin/acroread: 
  error while loading shared libraries: libgdk_pixbuf_xlib-2.0.so.0: cannot open shared object file: No such file or directory

```

Locate what package contains the required shared so.0 library:

```

sudo apt-file search libgdk_pixbuf_xlib-2.0.so.0
libgdk-pixbuf2.0-0: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf_xlib-2.0.so.0
libgdk-pixbuf2.0-0: /usr/lib/x86_64-linux-gnu/libgdk_pixbuf_xlib-2.0.so.0.2800.1

```

Install the required pkg:

```

sudo apt-get install libgdk-pixbuf2.0-0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgdk-pixbuf2.0-0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 67 not upgraded.

```

I'm at a loss. The package manager is telling me the dependency is already installed but acrobat cannot identify it. What do I need to do to get Adobe Acrobat Reader working?

---

### Post by drmrgd on 2013-11-26
I wonder if it's an architecture issue.  You have a 64-bit system, but according to the requirements, Reader is only 32-bit for Linux (or so I assume).  From their system requirements for Reader 9:

[h=3]Linux[/h]
[LIST]
[*]32-bit Intel Pentium® processor or equivalent
[*]Red Hat® Linux® WS 5, SUSE® Linux Enterprise Desktop (SLED) 10 with Service Pack 2, or Ubuntu 7.10; GNOME or KDE Desktop Environment
[*]512MB of RAM (1GB recommended)
[*]150MB of available hard-disk space (additional 75MB required for all supported font packs)
[*]GTK+ (GIMP Toolkit) user interface library, version 2.6 or later
[*]Firefox 2.x or 3.0
[*]OpenLDAP and CUPS libraries
[/LIST]
[FONT=inherit]
It could be that it's looking for a 32-bit library instead of the 64-bit library you have.  You could try to add this package to add capability to run 32-bit apps under your architecture:

```

sudo apt-get install ia32-libs

```

But the problem might be a bit more difficult to solve than that to solve.[/FONT]

---

### Post by palani2 on 2014-04-30
[FONT=inherit]'sudo apt-get install ia32-libs'[/FONT]
Very good solution. It works!
Thank you drmrgd!

---

### Post by garibaldy on 2014-05-22
> **palani2 said:**
> [FONT=inherit]'sudo apt-get install ia32-libs'[/FONT]
Very good solution. It works!
Thank you drmrgd!

Unfortunately didn't work for me. Output from the terminal as follows:

sudo apt-get install ia32-libs

Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0
E: Package 'ia32-libs' has no installation candidate

I downloaded and installed lib32z1 lib32ncurses5 lib32bz2-1.0 but have not as yet found where they are located, so I have not set the "path" as below.

I found a file - libgdk_pixbuf_xlib-2.0.so.0, using the grep command in /usr/lib/x86_64-linux-gnu and executed "export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH" based on information provided at [https://forums.adobe.com/message/1784813](https://forums.adobe.com/message/1784813), and got the following: acroread: error while loading shared libraries: libgdk_pixbuf_xlib-2.0.so.0: wrong ELF class: ELFCLASS64. 

OS is Kubuntu 14.04LTS 64bit.

---

### Post by LastDino on 2014-05-22
> **garibaldy said:**
> Unfortunately didn't work for me. Output from the terminal as follows:

sudo apt-get install ia32-libs

Package ia32-libs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  lib32z1 lib32ncurses5 lib32bz2-1.0

E: Package 'ia32-libs' has no installation candidate

I found a 64 bit version of this file using the grep command in /usr/lib/x86_64-linux-gnu and executed "export LD_LIBRARY_PATH=/usr/lib/x86_64-linux-gnu:$LD_LIBRARY_PATH" based on information provided at [https://forums.adobe.com/message/1784813](https://forums.adobe.com/message/1784813), and got the following: acroread: error while loading shared libraries: libgdk_pixbuf_xlib-2.0.so.0: wrong ELF class: ELFCLASS64. 

OS is Kubuntu 14.04LTS

I could be horribly wrong, but you probably need to add i386 architecture.

---

### Post by garibaldy on 2014-05-22
> **LastDino said:**
> I could be horribly wrong, but you probably need to add i386 architecture.

Thanks for your reply. Sorry about my ignorance but would you please elaborate? I've just edited my original post to add some more information.

---

### Post by westie457 on 2014-05-22
This should work ```
sudo dpkg --add-architecture i386
```

---

### Post by garibaldy on 2014-05-23
> **westie457 said:**
> This should work ```
sudo dpkg --add-architecture i386
```

@Westie Thank you for that. I executed the command and did not get any failure messages so I am assuming it was successful, but when I run acroread I still get the error message:

error while loading shared libraries: libgdk_pixbuf_xlib-2.0.so.0: cannot open shared object file: No such file or directory

Do I need to set PATH to the directory where it is installed? I have no idea where it installed, assuming it did.

---

### Post by westie457 on 2014-05-23
How did you install 'Acroread'? Was it from the Adobe web site using the .bin file?

There is a version in the repos that works and it installs the missing file.

---

### Post by Luke M on 2014-05-23
You have to install the 32-bit versions the libraries, e.g.:
sudo apt-get install xxx:i386

where xxx is the missing library.

---

### Post by LastDino on 2014-05-24
> **Luke M said:**
> You have to install the 32-bit versions the libraries, e.g.:
sudo apt-get install xxx:i386

where xxx is the missing library.

+ 1
From what I've noticed, latest x64 14.04 doesn't come with those by default, you need to install them.

---

### Post by garibaldy on 2014-05-27
A sincere thank you to everyone who helped with this issue. What a fantastic community!  I eventually managed to get a working Adobe Reader 9 after pursuing suggestions  on this thread which led me to this page:

[http://askubuntu.com/questions/455135/how-do-i-install-adobe-acrobat-reader-in-ubuntu-14-04](http://askubuntu.com/questions/455135/how-do-i-install-adobe-acrobat-reader-in-ubuntu-14-04)

I followed the instructions in this post:

[http://askubuntu.com/a/460448](http://askubuntu.com/a/460448)

I uninstalled the original .bin from Adobe and installed the .deb instead. Works now! :)

---

