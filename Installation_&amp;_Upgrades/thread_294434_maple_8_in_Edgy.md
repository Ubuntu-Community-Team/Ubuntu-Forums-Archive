---
title: "maple 8 in Edgy"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by fofenk on 2006-11-06
hi
i've managed to install maple 8 in dapper with the help of [this post]("http://ubuntuforums.org/showthread.php?t=38126")
but after i ugraded to edgy the program begin to give this error message

/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

to check whether it was due to a possible upgrade error, i've installed maple8 to my home pc, with a clean install of edgy, it gave the same error.

for further info, this is the result of
$ ldd /bin/sh
        linux-gate.so.1 =>  (0xffffe000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7dc2000)
        /lib/ld-linux.so.2 (0xb7f04000)

any ideas?
thanks in advance

**edit**
ok, i give up
going back to dapper...
](*,)

---

