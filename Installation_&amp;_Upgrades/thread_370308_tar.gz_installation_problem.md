---
title: "tar.gz installation problem"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by tagu on 2007-02-25
Hi everyone, I'm new to ubuntu and I'm triying to install my mainboard driver. 
Firstly, I have my mainboard cd I take the driver file form cd which ends with tar.gz then I copy it to the drive then I extract it.

Like written in this forum I used ./configure command then I use "make" command then I wrote "sudo make install" to the terminal but I cant install the driver.
The problem that I got is:

make -C  nvnet install
make[1]: Entering directory `/home/tagu/nforce/nvnet'
mkdir -p //lib/modules/2.6.17-10-generic/kernel/drivers/net
install -b -m 644 -o root nvnet.o //lib/modules/2.6.17-10-generic/kernel/drivers/net
install: cannot stat `nvnet.o': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/tagu/nforce/nvnet'
make: *** [nvnet_install] Error 2

Please Help thank a lottt...

---

### Post by tagu on 2007-02-26
Anyone Help

---

### Post by energiya on 2007-02-26
In the tar.gz file it should be a README or INSTALL file that says what to do. Maybe you must do something else, not ./configure, make, make install.

---

