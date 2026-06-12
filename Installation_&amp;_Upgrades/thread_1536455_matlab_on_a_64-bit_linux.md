---
title: "matlab on a 64-bit linux"
date: 2010-07-22
forum: Installation &amp; Upgrades
---

### Post by ddmn on 2010-07-22
I've been trying to install Matlab r2008b but with no sucess.

here are the commands i ran.
sudo mkdir  /usr/local/matlabR2008b

cd /usr/local/matlabR2008b/

copied  my files to tmp folder and run

sudo sh  /tmp/MATHWORKS_R2008B/install

here is what i get at the terminal
```

-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:

        /tmp/MATHWORKS_R2008B/update/install/main.sh: 178: /tmp/MATHWORKS_R2008B/update/bin/glnxa64/xsetup: Permission denied

    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------

    Sorry! Setup aborted . . .

```when i run install* -t i get 
```

awk: cmd. line:2:     BEGIN { found = 0; extra = 9; min = 24; default = 24 }
awk: cmd. line:2:                                             ^ syntax error
awk: cmd. line:6:             if (nrows < min) nrows = default
awk: cmd. line:6:                                      ^ syntax error
awk: cmd. line:12:     END { if (found == 0) print (default - extra) }
awk: cmd. line:12:                                  ^ syntax error
awk: cmd. line:12:     END { if (found == 0) print (default - extra) }
awk: cmd. line:12:                                                   ^ syntax error
awk: cmd. line:2: (FILENAME=- FNR=1) fatal: division by zero attempted in `%'
/tmp/4274d: 3: cannot create /1: Permission denied
[: 582: -le: argument expected
/tmp/MATHWORKS_R2008B/update/install/main.sh: 582: /tmp/MATHWORKS_R2008B/update/bin/glnxa64/xsetup: Permission denied


```any way i can fix this?

---

### Post by lechien73 on 2010-07-22
This link seemed to fix it, the last time it was asked here on the forums:

[https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

Hope it helps you too :)

---

