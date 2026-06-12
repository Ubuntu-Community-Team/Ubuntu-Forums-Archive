---
title: "Installing ncview"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by sherlockmz on 2010-04-13
Dear Ubuntu users 
I am trying to install ncview and I get this 

root@XXXX:/usr/local/ncview-2.0beta4# ./configure 
checking for nc-config... no
-----------------------------------------------------------------------------------
Error, nc-config not found or not executable.  This is a script that comes with the
netcdf library, version 4.1-beta2 or later, and must be present for configuration
to succeed.
 
If you installed the netcdf library (and nc-config) in a standard location, nc-config
should be found automatically.  Otherwise, you can specify the full path and name of
the nc-config script by passing the --with-nc-config=/full/path/nc-config argument
flag to the configure script.  For example:
 
./configure --with-nc-config=/sw/dist/netcdf4/nc-config
 
Special note for R users:
-------------------------
To pass the configure flag to R, use something like this:
 
R CMD INSTALL --configure-args="--with-nc-config=/home/joe/bin/nc-config" ncdf4
 
where you should replace /home/joe/bin etc. with the location where you have
installed the nc-config script that came with the netcdf 4 distribution.

I am using
2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

Does anyone have any idea on how to solve this?
thanks in advance

---

### Post by geoguy on 2011-02-10
You should be able to install it after installing netcdf-bin from the repositories

---

