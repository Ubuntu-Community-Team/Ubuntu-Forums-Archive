---
title: "GTKRadiant fails to build on AMD 64bit Proc, 32bit OS"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by Rhemat on 2008-10-07
Hello again,

  I'm attempting to run GTKRadiant 1.4.0 on an AMD Athlon 3200+ 64bit machine, using the 32bit version of Kubuntu 8.04.  I keep getting this error message:

setup.gtk failed to start?
DISPLAY: :0.0
Do you need to issue an xhost + command to let root access X11?
The setup program seems to have failed on x86/glibc-2.1

I've google searched the problem, but I never get anything that helps.  I have downloaded glibc-2.1, but I don't know where to move the file, and if there are any other steps beyond putting it in a particular directory.

Thanks in advance for any help

---

### Post by Yellow Pasque on 2008-10-08
> using the 32bit version of Kubuntu 8.04
This is the wrong sub-forum then.

BTW, how did you install the program? From a .deb or from source?

> I have downloaded glibc-2.1, but I don't know where to move the file
glibc is also called libc6. Install the appropriate libc6 packages through Synaptic.

---

### Post by bapoumba on 2008-10-08
Moved to "Installation & Upgrades".

---

### Post by Rhemat on 2008-10-08
I use the source directly from id's FTP site (linux-radiant-1.4.0.run).  I've downloaded libdb1-compat, which if I read it correctly is supposed to offer compatibility for programs using the 2.1 version, but it still does not work.  Is there any way I can target the program to that particular directory?  Right now I try to install it with the following command:

./linux-radiant-1.4.0.run

Thanks for the help

---

### Post by Rhemat on 2008-10-08
Sorry I didn't read all of your post Temüjin, but it appears that I already have that package, and it still didn't work.  I know I must have had problems installing this program before, but I always got passed it.

Thanks for your help

---

### Post by Yellow Pasque on 2008-10-08
I tried compiling the last version (1.5) from source, but I get errors when running it (maybe because I don't have the games installed or it's not meant for 64-bit?)

Anyway,, there's a .deb available here: [http://alientrap.org/forum/viewtopic.php?t=3093](http://alientrap.org/forum/viewtopic.php?t=3093)

---

### Post by Rhemat on 2008-10-08
Okay, I downloaded that, and then tried to run it the same way I did with v1.4, and I got this message:
./gtkradiant_1.5-svn20080512-1_i386.deb: line 1: syntax error near unexpected token `newline'
./gtkradiant_1.5-svn20080512-1_i386.deb: line 1: `!<arch>'

Am I not doing it right?

---

### Post by Rhemat on 2008-10-13
Okay, the only thing I can think of to do is install the glibc-2.1 codec I downloaded, I just don't know how to do it.  If any one knows how, or where to find a proper guide, let me know.

Thanks in advance.

---

### Post by Partyboi2 on 2008-10-13
> **Rhemat said:**
> Okay, I downloaded that, and then tried to run it the same way I did with v1.4, and I got this message:
./gtkradiant_1.5-svn20080512-1_i386.deb: line 1: syntax error near unexpected token `newline'
./gtkradiant_1.5-svn20080512-1_i386.deb: line 1: `!<arch>'

Am I not doing it right?
How are you trying to install the downloaded deb?  You should be able to install it by 
```
sudo dpkg -i package
``` Change package to actually name. Or another way is to double click on the deb file you downloaded to start installing it.

---

### Post by Rhemat on 2008-10-14
Okay, I think that did it.  It gave a few errors at first, but one of the errors suggested I run:

sudo apt-get install -f

That seemed to fix some dependency problems.  Now I just have to figure out how to start the program.  Thanks!

---

### Post by Rhemat on 2008-10-14
Okay, it was right in the menus.  I'm used to typing radiant into the terminal.  Problem is now, it gives no option for Quake 3; there are options for Quake, Quake 2, Quake 4, and just about any other id game or game based on id tech, but no Quake 3....  Well, I might be able to fix this on my own.
Once again, thanks for the help, you have been most.... helpful.

---

### Post by Rhemat on 2008-10-24
Okay, I found a fix that will install GTKRadiant 1.4, you just have to download the glibc-2.1 from the net.  Then you install that in:

/usr/lib

---

### Post by Rhemat on 2009-02-28
Okay, not certain what changed since then and now, but I put in a new hard drive, and installed Ubuntu 8.10 on it, and I get this error message when I attempt to install:

radiant/main.cpp:186
runtime error: GTK+ error: Gtk-Warning **; GtkSpinButton: setting an adjustment with non-zero page size is deprecated
/usr/lib/gtkradiant/radiant.x86 [skipping to the end of the error message]

Would you like to break into the debugger? [Yes] [No]

Yes terminates the program, no just pops up that error message again.
I truncated the error message because it seemed to be address spaces for radiant.x86, and a few libs.  If needed, I can take a screen shot of it later.

---

