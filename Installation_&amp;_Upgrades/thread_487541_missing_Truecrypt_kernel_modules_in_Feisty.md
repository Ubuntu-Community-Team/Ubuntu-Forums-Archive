---
title: "missing Truecrypt kernel modules in Feisty"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by rafalr on 2007-06-29
I have had  Truecrypt 4.02a running on Dapper from terminal flawlessly.

After upgrading from 6.06 (via 6.10) to Feisty (all 32 bit running on AMD 64), I had problem to run 4.02a so I uninstalled this and replaced with 4.03a via Automatix2.

```

rafal@Ubuntu-AMD-64:~$ truecrypt -V
truecrypt 4.3a

Copyright (C) 2003-2007 TrueCrypt Foundation. All Rights Reserved.
Copyright (C) 1998-2000 Paul Le Roux. All Rights Reserved.
Copyright (C) 1999-2006 Dr. Brian Gladman. All Rights Reserved.
Copyright (C) 1995-1997 Eric Young. All Rights Reserved.
Copyright (C) 2001 Markus Friedl. All Rights Reserved.

Released under the TrueCrypt Collective License 1.2

```

Now when I launch truecrypt mounting command (I wrote a short script) I am requested for password, but later on truecrypt dies and the mount point is empty (I guess simply not mounted). The same when I go via Forcefield (Truecrypt GUI supplied via Automatix2). 

Note that the encrypted volume and mounting points did not change from the situation while operating Dapper.

When I do the same from command line I get the following:

```

rafal@Ubuntu-AMD-64:~$ truecrypt -u /home/rafal/.RMC_crypto /home/rafal/RMC
Enter password for '/home/rafal/.RMC_crypto': 
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.20.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
Failed to load TrueCrypt kernel module

```

It does not seem to be very well know issue (not on this Forum) - any ideas ?

rafal

---

