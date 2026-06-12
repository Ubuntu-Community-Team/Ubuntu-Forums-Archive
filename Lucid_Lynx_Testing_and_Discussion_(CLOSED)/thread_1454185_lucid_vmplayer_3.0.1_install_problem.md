---
title: "lucid vmplayer 3.0.1 install problem"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by quiricada on 2010-04-14
hi,

was trying to install vmplayer 3.0.1, it bombs at 57%, anyone else?

sudo ./VMware-Player-3.0.1-227600.i386.bundle --console
Extracting VMware Installer...done.
The product is ready to be installed.  Press Enter to begin
installation or Ctrl-C to cancel.

Installing VMware Player Application 3.0.1
    Copying files...
[#######################################                               ]  57%*** glibc detected *** /tmp/vmis.elT2uY/install/vmware-installer/vmis-launcher: double free or corruption (out): 0xb64fc008 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b581)[0xbfc581]
/lib/tls/i686/cmov/libc.so.6(+0x6cdd8)[0xbfddd8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xc00ebd]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyObject_Free+0x5c)[0xd6e41c]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x6353c)[0xd7553c]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x55049)[0xd67049]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyDict_SetItem+0x7e)[0xd6905e]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x2b290)[0xd3d290]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyObject_SetAttr+0xaf)[0xd6c49f]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x1edb)[0xdb44ab]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x44eb0)[0xd56eb0]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0xd354b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x2ac32)[0xd3cc32]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0xd354b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_CallObjectWithKeywords+0x7b)[0xdb18cb]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x2c8b3)[0xd3e8b3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0xa1e)[0xdb2fee]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x3b9ff)[0xd4d9ff]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0xa1e)[0xdb2fee]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x44eb0)[0xd56eb0]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0xd354b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(+0x2ac32)[0xd3cc32]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0xd354b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/_functools.so(+0xe1d)[0x271e1d]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0xd354b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x1383)[0xdb3953]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xdb76b7]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x62f8)[0xdb88c8]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xdb96e3]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyEval_EvalCode+0x55)[0xdb9755]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyRun_FileExFlags+0xb4)[0xddb7e4]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyRun_SimpleFileExFlags+0x1a6)[0xddbad6]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(PyRun_AnyFileExFlags+0x7a)[0xddbdba]
/tmp/vmis.elT2uY/install/vmware-installer/python/libpython.so(Py_Main+0xa24)[0xde5204]
/tmp/vmis.elT2uY/install/vmware-installer/sopython/libpy25.so(RunInstaller+0xed)[0x13a62d]
/tmp/vmis.elT2uY/install/vmware-installer/vmis-launcher[0x804fb56]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xba7bd6]
/tmp/vmis.elT2uY/install/vmware-installer/vmis-launcher[0x804f631]
======= Memory map: ========
00110000-001ef000 r-xp 00000000 08:01 1311773    /tmp/vmis.elT2uY/install/vmware-installer/sopython/libpy25.so
001ef000-00205000 rw-p 000df000 08:01 1311773    /tmp/vmis.elT2uY/install/vmware-installer/sopython/libpy25.so
00205000-0020d000 rw-p 00000000 00:00 0 
0020d000-00210000 r-xp 00000000 08:01 1311160    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/time.so
00210000-00212000 rw-p 00002000 08:01 1311160    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/time.so
00212000-00214000 r-xp 00000000 08:01 1311153    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/fcntl.so
00214000-00215000 rw-p 00002000 08:01 1311153    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/fcntl.so
00215000-00224000 r-xp 00000000 08:01 1311166    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/datetime.so
00224000-00227000 rw-p 0000e000 08:01 1311166    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/datetime.so
00227000-0022b000 r-xp 00000000 08:01 1311167    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/binascii.so
0022b000-0022c000 rw-p 00003000 08:01 1311167    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/binascii.so
0022c000-0022d000 r-xp 00000000 08:01 1311158    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/_weakref.so
0022d000-0022e000 rw-p 00000000 08:01 1311158    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/_weakref.so
00271000-00273000 r-xp 00000000 08:01 1311154    /tmp/vmis.elT2uY/install/vmware-installer/python/lib/lib-dynload/_functools.so/tmp/vmis.elT2uY/install/vmware-installer/vmware-installer: line 22:  6261 Aborted                 (core dumped) VMWARE_INSTALLER="$VMWARE_INSTALLER" VMISPYVERSION="$VMISPYVERSION" "$VMWARE_INSTALLER"/vmis-launcher "$VMWARE_INSTALLER"/vmware-installer.py "$@"

---

### Post by tad1073 on 2010-04-14
working fine here on 64 bit

---

### Post by Astenorh on 2010-04-14
Doesn't seem to an common problem according to google. Try to give us some information about your system. Try commands such as uname -a, ...

Also your file might be corrupt check md5sum of it. Vmware provides the md5sums.

---

### Post by quiricada on 2010-04-14
md5 checked.

uname -a
Linux apple 2.6.32-20-generic #30-Ubuntu SMP Mon Apr 12 15:19:41 UTC 2010 i686 GNU/Linux

---

### Post by quiricada on 2010-04-14
updated/upgraded lucid to

Linux apple 2.6.32-21-generic #31-Ubuntu SMP Tue Apr 13 20:34:00 UTC 2010 i686 GNU/Linux

vmplayer 3.0.1 still bombs during install.

this thread
[http://ubuntuforums.org/showthread.php?t=1447951](http://ubuntuforums.org/showthread.php?t=1447951)
pointed to vmplayer 3.1 beta, it install fine, so i don't know whose problem it is now?

---

