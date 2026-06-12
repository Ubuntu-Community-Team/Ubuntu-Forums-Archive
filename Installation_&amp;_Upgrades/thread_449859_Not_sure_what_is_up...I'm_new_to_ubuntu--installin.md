---
title: "Not sure what is up...I'm new to ubuntu--installing Dnews"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Cr0n_J0b on 2007-05-20
So I just moved over to Ubuntu from Fedora Core4 and I'm having some trouble gettings things back to normal.

In this episode, I'm trying to load DNews on the system.

I have Dnews in a directory, and permissions are fine...there is a file called "dnews_setup" which kicks off the install script.

In FC4 i would just do:

#/>./dnews_setup

and the script would run fine.  In Ubuntu I get...-bash: ./dnews_setup: No such file or directory
 But I know it's there...I can see it...it's really there.  and I'm in the right directory.

Is there something about Ubuntu, that I need to know when Installing applications?

thanks

---

### Post by taurus on 2007-05-20
What's the output of this command, assuming you are in the directory where that file is?

```
ls -la
```

---

### Post by Cr0n_J0b on 2007-05-20
This is the output from "ls -la dnews_setup"

-rwxrwxr-x 1 root root   66703 2004-04-27 23:56 dnews_setup

---

### Post by taurus on 2007-05-20
What does the first few lines look like?

```
more dnews_setup
```
If it's a script file, then make sure the first line says

```
#!/bin/bash
```

---

### Post by Cr0n_J0b on 2007-05-20
I thought it was a script, but it appears to be a binary, though it doesn't end in bin.

I have sinced changed the perms to 777 and I still get 

-bash: ./dnews_setup: No such file or directory

---

### Post by taurus on 2007-05-20
What's the output of these two commands then?

```
file dnews_setup
ldd dnews_setup
```

---

### Post by Cr0n_J0b on 2007-05-20
file dnews_setup
dnews_setup: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.0.0, dynamically linked (uses shared libs), not stripped

ldd dnews_setup
 not a dynamic executable

---

### Post by taurus on 2007-05-20
Are you runnng x86 or x86_64?

```
uname -a
```
Where did you download that dnew_setup (or dnews) anyway?

---

### Post by Cr0n_J0b on 2007-05-21
the 64-bit version...but I thought that it would run 32bit apps just fine... :-( does this mean I have to reinstall?

Linux Ubuntu-Venice 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

---

