---
title: "UnRar!"
date: 2005-06-04
forum: Installation &amp; Upgrades
---

### Post by karmah on 2005-06-04
I'm trying to install UnRar. But i can't :D. I downloaded it from [http://www.rarlab.com/rar_add.htm](http://www.rarlab.com/rar_add.htm)
Ive tried different programs from that page but there's always something stopping me. Like one of them: I can't use the 'make' command to install anything, there's just lots of cpp source code files but nothing I can do to install them.
Any sort of help appreciated! :P

---

### Post by lakcaj on 2005-06-04
apt-get install rar
man rar
/Extract files with full path

---

### Post by karmah on 2005-06-04
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

:O

---

### Post by FluffyElmo on 2005-06-04
If you add the Non-Free 'Multiverse' Repository in Synaptic you should find a package for unrar. Works perfectly for me.

Also, Ubuntu by default doesn't install any development tools. You can install them (make, gcc, g++, etc) from Synaptic so you can build from source in future.

---

### Post by karmah on 2005-06-04
I have them dev tools installed...non-free multiverse? :O ill check it out.

---

### Post by lotusleaf on 2005-06-05
[QUOTE=karmah]I'm trying to install UnRar. But i can't :D. I downloaded it from [http://www.rarlab.com/rar_add.htm](http://www.rarlab.com/rar_add.htm)
Ive tried different programs from that page but there's always something stopping me. Like one of them: I can't use the 'make' command to install anything, there's just lots of cpp source code files but nothing I can do to install them.
Any sort of help appreciated! :P[/QUOTE]

I downloaded the Linux version from [here](http://www.rarlab.com/download.htm), uncompressed it, and ran sudo make and that was all that was required AFAIK. It works great after this by typing rar from the command line with options.

---

### Post by karmah on 2005-06-05
Oh lol, i allready had it downloaded, forgot to install it and then got the idea that that one wasn't working either. Thx guyz!  :grin:

---

