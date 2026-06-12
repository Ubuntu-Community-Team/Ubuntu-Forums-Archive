---
title: "kernel update error"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by pradeepadapa on 2006-09-18
hi,

  i tried to update my kernel to 2.6.17 by looking at the instructions given in the thread 

        
         [http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.17](http://ubuntuforums.org/showthread.php?t=217657&highlight=2.6.17)

in that, it worked fine till the 6th step, but after executing the second command in the 6th step i get an error while compiling the kernel like this,



fs/xfs/linux-2.6/xfs_buf.c:1855: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-4.0/README.Bugs>.
make[3]: *** [fs/xfs/linux-2.6/xfs_buf.o] Error 1
make[2]: *** [fs/xfs] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.17.7'
make: *** [stamp-build] Error 2


now my question is 

why has this occured nd how to recompile the kernel without any errors nd how to overcome this problem,

plse help me by giving commands to do this to update my kernel to the latest one 2.6.17.

---

