---
title: "[SOLVED] Problems with glibc when launch skype in ubuntu 8.10 Intrepid Ibex 64-bit"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rj123 on 2008-10-22
I already tried this solution: [http://ubuntuforums.org/showthread.php?t=925211](http://ubuntuforums.org/showthread.php?t=925211) but still having the same problem, I have the last ia32 package installed.

when I try to start skype it returns this errors:
```
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/bin/skype.real)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.7' not found (required by /usr/lib32/libasound.so.2)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libasound.so.2)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib32/libasound.so.2)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libasound.so.2)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.2' not found (required by /lib32/librt.so.1)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_PRIVATE' not found (required by /lib32/librt.so.1)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtDBus.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libpng12.so.0: no version information available (required by /usr/lib32/libQtGui.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libQtGui.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtGui.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtNetwork.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib32/libQtNetwork.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libQtNetwork.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtCore.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libQtCore.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.2' not found (required by /lib32/libpthread.so.0)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_PRIVATE' not found (required by /lib32/libpthread.so.0)
/usr/bin/skype.real: /emul/ia32-linux/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib32/libstdc++.so.6)
/usr/bin/skype.real: /emul/ia32-linux/lib/libgcc_s.so.1: version `GCC_3.3' not found (required by /usr/lib32/libstdc++.so.6)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libstdc++.so.6)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libstdc++.so.6)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib32/libstdc++.so.6)
/usr/bin/skype.real: /lib/ld-linux.so.2: version `GLIBC_2.1.1' not found (required by /emul/ia32-linux/lib/libc.so.6)
/usr/bin/skype.real: /lib/ld-linux.so.2: version `GLIBC_2.2.3' not found (required by /emul/ia32-linux/lib/libc.so.6)
/usr/bin/skype.real: /lib/ld-linux.so.2: version `GLIBC_2.2' not found (required by /emul/ia32-linux/lib/libc.so.6)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libv4l1.so.0)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libv4l1.so.0)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_PRIVATE' not found (required by /lib32/libdl.so.2)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libQtXml.so.4)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libaudio.so.2)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3' not found (required by /usr/lib32/libaudio.so.2)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libaudio.so.2)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libfontconfig.so.1)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libfontconfig.so.1)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libv4l2.so.0)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libv4l2.so.0)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libexpat.so.1)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib32/libv4lconvert.so.0)
/usr/bin/skype.real: /emul/ia32-linux/lib/libc.so.6: version `GLIBC_2.3.4' not found (required by /usr/lib32/libv4lconvert.so.0)

```


Any ideas?

---

### Post by rj123 on 2008-10-23
No one can help me?

---

### Post by rj123 on 2008-10-23
Solved:
The problem was that I had installed glibc via sources compilation on ubuntu hardy. 
So to fixe I only deleted the folder /emul
sudo rm -Rf /emul

:)

---

### Post by bapoumba on 2008-10-23
Moved to Intrepid Ibex.

---

