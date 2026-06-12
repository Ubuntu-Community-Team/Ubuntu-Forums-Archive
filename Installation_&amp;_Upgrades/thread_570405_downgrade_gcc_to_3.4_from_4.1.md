---
title: "downgrade gcc to 3.4 from 4.1"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by karmo on 2007-10-08
hello everyone
i'm trying to install Trustedgrub (an extension of Grub to use the TPM chip) , i'm using Kubuntu and i have already installed grub 0.97..
the notes tell that 
* Trusted GRUB will not compile with GCC 4.x, so you have to use GCC 3.3.x or 3.4.x

infact i executed ./buildtgrub.sh and it tells
"Wrong gcc-version, please use GCC 3.x"

i tried to do this:
apt-get install gcc-3.4
apt-get install g++-3.4
export CC=/usr/bin/gcc-3.4
./buildtgrub.sh

but it tells again
"Wrong gcc-version, please use GCC 3.x"

so....what i have to do to use gcc 3.4??

---

### Post by ddrichardson on 2007-10-09
There appears to be a patch for GCC 4.x on [sourceforge]("http://sourceforge.net/project/showfiles.php?group_id=165379").

---

