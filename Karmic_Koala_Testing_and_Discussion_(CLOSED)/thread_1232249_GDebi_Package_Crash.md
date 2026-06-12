---
title: "GDebi Package Crash"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-08-05
Trying to install google-chrome, and it crashed. I did file a bug report. Anyone else have this issue using Karmic. Jaunty worked ok.

======================================================
$ gdebi-gtk google-chrome-unstable_current_i386.deb
/usr/lib/python2.6/dist-packages/GDebi/SimpleGtkbuilderApp.py:34: RuntimeWarning: missing handler 'gtk_main_quit'
  self.builder.connect_signals(self)
WARNING: can not get name for '<gtk.TextBuffer object at 0xa29384c (GtkTextBuffer at 0xa5e59c0)>'
WARNING: can not get name for '<gtk.AccelGroup object at 0xa293964 (GtkAccelGroup at 0xa5e4600)>'
WARNING: can not get name for '<gtk.TextBuffer object at 0xa293f7c (GtkTextBuffer at 0xa5e5980)>'
WARNING: can not get name for '<gtk.TextBuffer object at 0xa297144 (GtkTextBuffer at 0xa5e5940)>'
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/GDebi/GDebi.py", line 343, in on_open_activate
    self.open(fs.get_filename())
  File "/usr/lib/python2.6/dist-packages/GDebi/GDebi.py", line 217, in open
    for name in self._deb.control_filelist:
  File "/usr/lib/python2.6/dist-packages/GDebi/DebPackage.py", line 438, in control_filelist
    for name in DebFile(self.file).control:
  File "/usr/lib/pymodules/python2.6/debian_bundle/debfile.py", line 234, in __init__
    compressed_part_name(DATA_PART)))
  File "/usr/lib/pymodules/python2.6/debian_bundle/debfile.py", line 219, in compressed_part_name
    " (expected one of: %s)" % candidates)
debian_bundle.debfile.DebError: missing required part in given .deb (expected one of: ['data.tar.gz', 'data.tar.bz2'])

---

### Post by DougieFresh4U on 2009-08-05
Yes there is a bug filed a few days ago. I was having the same exact issue installing Google Chrome.
Sorry I don't have bug#

---

### Post by VMC on 2009-08-05
I filed a bug report myself. I was just wondering if I was alone on this. I see a topic about Chrome and that got me thinking that no one else has an issue. 

Thanks for replying.

---

### Post by taavikko on 2009-08-05
> **VMC said:**
> I filed a bug report myself. I was just wondering if I was alone on this. I see a topic about Chrome and that got me thinking that no one else has an issue. 

Thanks for replying.

where's the bug #, in case somebody wants to chime in...?

---

### Post by WelshDragon on 2009-08-05
> **taavikko said:**
> where's the bug #, in case somebody wants to chime in...?
[https://bugs.edge.launchpad.net/ubuntu/+source/gdebi/+bug/407198](https://bugs.edge.launchpad.net/ubuntu/+source/gdebi/+bug/407198)

---

### Post by Detroit_Bad_Boy on 2009-10-04
I tried to install Frostwire in kUbuntu and this is the crash error message that came up:

 p, li { white-space: pre-wrap; }  Application: GDebi (gdebi-kde), signal SIGABRT
 
 Thread 1 (Thread 0xb7ded6c0 (LWP 6140)):
 [KCrash Handler]
 #5  0xb7fc5430 in __kernel_vsyscall ()
 #6  0xb7e1a6d0 in raise () from /lib/tls/i686/cmov/libc.so.6
 #7  0xb7e1c098 in abort () from /lib/tls/i686/cmov/libc.so.6
 #8  0xb7e135ce in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
 #9  0xb57dc7d7 in ?? () from /usr/lib/libX11.so.6
 #10 0xb57dd0e5 in _XEventsQueued () from /usr/lib/libX11.so.6
 #11 0xb57c57af in XEventsQueued () from /usr/lib/libX11.so.6
 #12 0xb5bc859a in ?? () from /usr/lib/libQtGui.so.4
 #13 0xb6db39c0 in g_main_context_prepare () from /usr/lib/libglib-2.0.so.0
 #14 0xb6db3dda in ?? () from /usr/lib/libglib-2.0.so.0
 #15 0xb6db4268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
 #16 0xb701a438 in QEventDispatcherGlib::processEvents () from /usr/lib/libQtCore.so.4
 #17 0xb5bc8365 in ?? () from /usr/lib/libQtGui.so.4
 #18 0xb6fefb06 in QCoreApplication::processEvents () from /usr/lib/libQtCore.so.4
 #19 0xb6b74f9a in ?? () from /usr/lib/python2.6/dist-packages/PyQt4/QtCore.so
 #20 0x080de562 in PyEval_EvalFrameEx ()
 #21 0x080df587 in PyEval_EvalFrameEx ()
 #22 0x080df587 in PyEval_EvalFrameEx ()
 #23 0x080df587 in PyEval_EvalFrameEx ()
 #24 0x080df587 in PyEval_EvalFrameEx ()
 #25 0x080e00b8 in PyEval_EvalCodeEx ()
 #26 0x080de5f8 in PyEval_EvalFrameEx ()
 #27 0x080df587 in PyEval_EvalFrameEx ()
 #28 0x080e00b8 in PyEval_EvalCodeEx ()
 #29 0x080e0217 in PyEval_EvalCode ()
 #30 0x080fe0e1 in PyRun_FileExFlags ()
 #31 0x080fe43a in PyRun_SimpleFileExFlags ()
 #32 0x0805c882 in Py_Main ()
 #33 0x0805b972 in main ()


Can anyone tell me exactly what the problem is and why I can't install Frostwire on Kubuntu 9.04 ? OR...can anyone tell me another way to install Frostwaire in .deb format with another program ?

---

### Post by nanog on 2009-10-04
Gdebi has been borked for days. Use:

```
dpkg -i *packagename*
```

---

### Post by Detroit_Bad_Boy on 2009-10-11
**[SOLVED]**I found the problem regarding Frostwire. It turns out that I had not yet installed java (which it needs as a dependency). After that, the install went through and Frostwire is working perfectly.

---

