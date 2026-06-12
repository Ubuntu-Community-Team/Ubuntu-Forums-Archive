---
title: "&quot;cannot execute binary&quot; error in terminal after install of 10.04"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by charkear on 2010-05-14
After upgrading to 10.04 I can not execute any binaries I compile inside the terminal.  I compile a hello world program and try to run it I get the error.  This happens for any program I compile and try to run.

Note the permissions for this file permit execution.

```

gcc hello.c -o hello
. ./hello
bash: .: ./hello: cannot execute binary file

```

---

### Post by charkear on 2010-05-17
When I do "strace" on a compiled program I get the following errors.


access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)

access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)

access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)


EDIT: Apparently this isn't a problem.

---

### Post by charkear on 2010-05-25
I have a solution.


When I run a program like this:
> $ ./hello

There are no problems.

When I run a program like this:
> $ . ./hello

I get the error.

---

