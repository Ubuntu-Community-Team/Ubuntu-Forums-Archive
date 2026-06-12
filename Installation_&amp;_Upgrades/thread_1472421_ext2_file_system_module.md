---
title: "ext2 file system module"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by kubio on 2010-05-04
Hello all,
What do I need to do to configure ubuntu 2.6.31-14 to run ext2 as a module?

I've tried make menuconfig: the 
[*] square brackets indicate I can enable or disable ext2 external but does not allow modules.

modprobe ext2 results in the error: "FATAL: Module ext2 not found"

locate ext2 shows no ext2.ko files
but there is an ext2 dir under /usr/src/linux-source-2.6.31/fs/ with several .c .o .h files including ext2.o and ext2.h

I thought maybe it's already compiled in the kernel so I disabled Ext2 extended attributes in menuconfig under File systems.

I also read that the kernel can be configured to use modules for everything except the fs loaded as root. I ran mount -v to see what filesystems are loaded, the first line is
/dev/loop0 on /  type ext4 (rw,errors=remount-ro)
there are 14 more but none are type ext2.

This is a laptop installation, I downloaded ubuntu from their website.
TIA,
Keith

---

### Post by kubio on 2010-05-04
found this:
[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)
the Alternative Debian Old Fashioned way seems a good place for starters.

---

### Post by kubio on 2010-05-04
In make menuconfig:  use the "/" to open a search window, in this case searching for "ext2" returns several modules and explains their dependencies and what trees they are under.

Then use the "Help" button, to determine which one is the Ext2 filesystem.

Either make it a module <M> in makeconfig or 
disable it <> and use modprobe or insmod to add a module at the command line.

---

