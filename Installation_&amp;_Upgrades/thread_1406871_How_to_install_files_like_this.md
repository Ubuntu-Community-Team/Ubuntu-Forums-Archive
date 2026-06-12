---
title: "How to install files like this"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by KevzJD on 2010-02-14
Right i just downloaded avant window navigator and in the folder i have the files in the below screenshot, now what i run to install this? please help.

---

### Post by darkod on 2010-02-14
That README file will usually have the procedure for you. It's not like windows readme files with unnecessary information. :)
Most probably it would be the INSTALL file, but read the README first.

---

### Post by KevzJD on 2010-02-14
thanks for the reply, yeah i got the install text file but makes no sense to me, i only just installed ubuntu abt an hour ago heres what the file says



> The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

---

### Post by pirateghost on 2010-02-14
why dont you just install avant-window-navigator from synaptic??

---

### Post by darkod on 2010-02-14
> **KevzJD said:**
> thanks for the reply, yeah i got the install text file but makes no sense to me, i only just installed ubuntu abt an hour ago heres what the file says

OK. Open terminal (Applications-Accessories) and navigate to where you have the files you downloaded and unpacked. Terminal starts in your home folder, and you change folders/directories with 'cd'. So, if your downloaded software is in Downloads, type:

cd Downloads (linux makes difference between capital and small letters in files and folders)

Then if the software unpacked in specific folder:

cd nameoffolder

Wher ever you are, you can check the content of current folder with:

ls (small LS, as in list)

After you reach the folder where the unpacked files are, as per the instructions execute one by one:

./configure
make
make install (not sure of this should be sudo make install, if it complains try that)

According to those instructions, it should be installed after that. Take note of any possible error messages.

---

### Post by darkod on 2010-02-14
> **pirateghost said:**
> why dont you just install avant-window-navigator from synaptic??

In case it is available there, it is recommended you install it from there. System-Administration-Synaptic Package Manager. In the search/filter box just type avant-window-navigator (or part of the name) and it will find it for you. Click on the checkbox and from the list select Mark For complete install. That will install any needed additional files. Click on the green button in the toolbar to execute this.

---

### Post by KevzJD on 2010-02-14
Wow it worked, thanks guys!

---

