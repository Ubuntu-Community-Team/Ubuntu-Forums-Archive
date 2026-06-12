---
title: "Matlab Installation"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by bikewrecker on 2011-10-27
Hi all, I'm working on switching most of my work/school related stuff to my ubuntu partition; however, I am having trouble installing matlab version R2010a student version. The error is this
```

-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /usr/local/temp/update/install/main.sh: 178: /usr/local/temp/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

```

I looked up the problem in the mathworks site and they say, "Although it is not required to have XServer be running on the machine,  our installer relies on XServer libraries located in /etc/X11/lib (or  /etc/X11/lib64).  Once XServer is installed, the installer should run  without giving this error"
... doesn't make a whole lot of change to me, but I got that I should install XServer. I tried a few things to install it, but I really have no idea what I'm doing and ubuntu assumes that I do. Any help would be greatly apprectiated. 

Oh ps. Im running ubuntu 11.10 64-bit and matlab is a 32-bit program, so that might have something to do with my problem. Also I think I remember that in order to run it I will have to use a -l command or something after it to let it know I'm trying to run a 32-bit program. 

Thanks in advance!!!

---

### Post by bikewrecker on 2011-10-28
bump.

I think I must have XServer installed because a bunch of things like my graphics card uses it. Anybody know what else could be causing this error?

---

