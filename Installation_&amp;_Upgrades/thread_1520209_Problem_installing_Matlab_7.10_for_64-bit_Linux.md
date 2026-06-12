---
title: "Problem installing Matlab 7.10 for 64-bit Linux"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by aSpareName on 2010-06-29
I am trying to install Matlab v. 7.10 on my Ubuntu machine. I was able to successfully download the necessary files. However, when I attempt to install using ' ./install ', I get the following error message:

...
Finished extracting ftp files.
Starting installer ...
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /home/user1/mathworks_downloads/update/install/main.sh: 178: /home/user1/mathworks_downloads/update/bin/glnxa64/xsetup: not found

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .

I tried using the command instal* -t, as recommended by the program, but then I get this error message:

Finished extracting ftp files.
Starting installer ...
awk: cmd. line:2:     BEGIN { found = 0; extra = 9; min = 24; default = 24 }
awk: cmd. line:2:                                             ^ syntax error
awk: cmd. line:6:             if (nrows < min) nrows = default
awk: cmd. line:6:                                      ^ syntax error
awk: cmd. line:12:     END { if (found == 0) print (default - extra) }
awk: cmd. line:12:                                  ^ syntax error
awk: cmd. line:12:     END { if (found == 0) print (default - extra) }
awk: cmd. line:12:                                                   ^ syntax error
awk: cmd. line:2: (FILENAME=- FNR=1) fatal: division by zero attempted in `%'
/tmp/2367d: 3: cannot create /1: Permission denied
[: 582: -le: argument expected
/home/Finished extracting ftp files.
Starting installer ...
awk: cmd. line:2:     BEGIN { found = 0; extra = 9; min = 24; default = 24 }
awk: cmd. line:2:                                             ^ syntax error
awk: cmd. line:6:             if (nrows < min) nrows = default
awk: cmd. line:6:                                      ^ syntax error
awk: cmd. line:12:     END { if (found == 0) print (default - extra) }
awk: cmd. line:12:                                  ^ syntax error
awk: cmd. line:12:     END { if (found == 0) print (default - extra) }
awk: cmd. line:12:                                                   ^ syntax error
awk: cmd. line:2: (FILENAME=- FNR=1) fatal: division by zero attempted in `%'
/tmp/2367d: 3: cannot create /1: Permission denied
[: 582: -le: argument expected
/home/user1/mathworks_downloads/update/install/main.sh: 582: /home/user1/mathworks_downloads/update/bin/glnxa64/xsetup: not found
user1/mathworks_downloads/update/install/main.sh: 582: /home/user1/mathworks_downloads/update/bin/glnxa64/xsetup: not found

any ideas on how I can resolve this issue?

Thanks in advance.

---

### Post by dino99 on 2010-06-29
[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

---

### Post by aSpareName on 2010-06-29
Thanks! That link had everything I needed. Essentially I was using ./install* -t, but it worked when I used ' sudo sh ./install* -t -glnx86 ' instead.

---

### Post by jugad on 2010-08-20
glnxa64/xsetup might not have its execute bit set by default.
chmod 755 xsetup should do it.

---

