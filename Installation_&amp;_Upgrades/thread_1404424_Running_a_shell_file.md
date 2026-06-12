---
title: "Running a shell file"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Sikandar on 2010-02-11
Hello,
I have to run one shell file in order to check its working. File is part of a project.
file name is **autogen.sh. **Earlier when i wrote ./autogen.sh, i got the error that autoreconf is not installed. So i installed autoconf;by using **sudo apt-get install autoconf.** 
Later i got the error as :line.188 of autoreconfig is not having libtool...sth like that.
i installed **sudo apt-get install libtool**.
Am still getting error when i write the same command as,
./autogen.sh
It's as follows:
>  
./autogen.sh
+ autoreconf -i -f -v
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal --force 
autoreconf: configure.ac: tracing
autoreconf: running: libtoolize --install --copy --force
libtoolize: putting auxiliary files in `.'.
libtoolize: copying file `./config.guess'
libtoolize: copying file `./config.sub'
libtoolize: copying file `./install-sh'
libtoolize: copying file `./ltmain.sh'
libtoolize: Consider adding `AC_CONFIG_MACRO_DIR([m4])' to configure.ac and
libtoolize: rerunning libtoolize, to keep the correct libtool macros in-tree.
libtoolize: Consider adding `-I m4' to ACLOCAL_AMFLAGS in Makefile.am.
autoreconf: running: /usr/bin/autoconf --force
autoreconf: running: /usr/bin/autoheader --force
autoreconf: running: automake --add-missing --copy --force-missing
autoreconf: Leaving directory `.'
 

 
Another thing i want to ask; which may be related to this, is regarding **root**
I had installed root some days before with same command as;
**sudo apt-get install root**
but when i write any command in root
like reboot, it says that :command is not defined in current scope.Why is that happening?
Are the two things related?
I run root simply by typing root.
Do reply.

---

### Post by Sikandar on 2010-02-11
I tried installing autoconf once again, but it was of no use..as the output was:
You already have latest version installed!..Let me know what am i supposed to do.

---

### Post by Sikandar on 2010-02-11
This is really urgent and important for me.
Please reply soon.

---

### Post by Sikandar on 2010-02-11
Why nobody is replying?

---

### Post by Sikandar on 2010-02-15
Am still stuck on the same problem.

---

### Post by giammy on 2010-02-15
> **Sikandar said:**
> Why nobody is replying?

hi,

personally, I read your post, but do not understand which is the error:
which is the output you expect?
why is it different?
(but I'm not an auto-tools guru :-( 

bye
giammy

---

### Post by Sikandar on 2010-02-15
Last two lines stating that something is missing and exiting with error is the error.
It should not occur and file should get opened as normal shell file.

---

### Post by giammy on 2010-02-15
> **Sikandar said:**
> Last two lines stating that something is missing and exiting with error is the error.
It should not occur and file should get opened as normal shell file.


Do you mean this lines?

autoreconf: running: automake --add-missing --copy --force-missing
autoreconf: Leaving directory `.'

Here there's no error
--add-missing is an option of automake command
see the manual page of automake
bye

---

### Post by Sikandar on 2010-02-15
hey giammy; thanks a lot, you are right --add-missing is one of the options in automake.
It adds some coomonly needed files in the package.

---

