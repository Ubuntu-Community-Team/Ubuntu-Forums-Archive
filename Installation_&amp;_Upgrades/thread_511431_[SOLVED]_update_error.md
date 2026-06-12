---
title: "[SOLVED] update error"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by Peregrine88 on 2007-07-27
I tried updating ubuntu fiesty with the automatic updater on the top right of my screen and got this error.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Would someone help me with this? It seems to be affecting all of my updating capabilities.

---

### Post by Pumalite on 2007-07-27
Did you try 'dpkg --configure -a'?

---

### Post by Peregrine88 on 2007-07-27
I tried but don't know what to do with it. I'm pretty knew.

elliot@elliot-laptop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
elliot@elliot-laptop:~$ su dpkg --configure -a
su: unrecognized option `--configure'
Usage: su [options] [LOGIN]

Options:
  -c, --command COMMAND         pass COMMAND to the invoked shell
  -h, --help                    display this help message and exit
  -, -l, --login                make the shell a login shell
  -m, -p,
  --preserve-environment        do not reset environment variables, and keep
                                the same shell
  -s, --shell SHELL             use SHELL instead of the default in passwd

elliot@elliot-laptop:~$

EDIT: mistyped su instead of sudo, I tried sudo this time and it's working. I'll update once it's done.

---

### Post by Pumalite on 2007-07-27
Try: sudo dpkg --configure -a

---

### Post by Peregrine88 on 2007-07-27
It's working now. Thanks for the help!

---

