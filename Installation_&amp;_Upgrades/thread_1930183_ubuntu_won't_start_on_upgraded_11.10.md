---
title: "ubuntu won't start on upgraded 11.10"
date: 2012-02-23
forum: Installation &amp; Upgrades
---

### Post by elephantgod on 2012-02-23
Hi

I just upgraded to 11.10 but the software center won't start when i click the icon.
Type "sudo software-center" in terminal i got :

```
2012-02-23 12:57:10,748 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2012-02-23 12:57:35,906 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 406, '_introspect_error_handler')'
2012-02-23 12:57:35,905 - dbus.proxies - ERROR - Introspect error on :1.0:/com/ubuntu/Softwarecenter: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
2012-02-23 12:58:01,560 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-02-23 12:58:01,633 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for ambiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2012-02-23 12:58:02,435 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/update-software-center-agent', 92, '<module>')'
2012-02-23 12:58:02,435 - root - WARNING - Another instance of the update agent already holds a write lock on /root/.cache/software-center/software-center-agent.db.tmp
2012-02-23 12:58:05,741 - softwarecenter.ui.gtk3.app - INFO - software-center-agent finished with status 1
*** buffer overflow detected ***: /usr/bin/python terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x37)[0x7fc3545777f7]
/lib/x86_64-linux-gnu/libc.so.6(+0xf7710)[0x7fc354576710]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgr8add_wordEPKciiPtiS1_b+0x7b)[0x7fc336ee63bb]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgr11load_tablesEPKcS1_+0x268)[0x7fc336ee6be8]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN7HashMgrC1EPKcS1_S1_+0xb2)[0x7fc336ee6d82]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN8HunspellC2EPKcS1_S1_+0x8a)[0x7fc336ee70ba]
/usr/local/lib/enchant/libenchant_myspell.so(_ZN14MySpellChecker17requestDictionaryEPKc+0x39d)[0x7fc336ef44ed]
/usr/local/lib/enchant/libenchant_myspell.so(+0x29656)[0x7fc336ef4656]
/usr/local/lib/libenchant.so.1(+0x41b8)[0x7fc345afe1b8]
/usr/local/lib/libenchant.so.1(enchant_broker_request_dict+0xc3)[0x7fc345aff5b3]
/usr/lib/libwebkitgtk-3.0.so.0(+0x48cf53)[0x7fc346192f53]
/usr/lib/libwebkitgtk-3.0.so.0(+0x4c4bbe)[0x7fc3461cabbe]
/usr/lib/libwebkitgtk-3.0.so.0(+0x4c546d)[0x7fc3461cb46d]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_type_create_instance+0x513)[0x7fc3530f3373]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(+0x125ac)[0x7fc3530d35ac]
/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0(g_object_newv+0x294)[0x7fc3530d5e94]
/usr/lib/python2.7/dist-packages/gi/_gobject/_gobject.so(+0xbcea)[0x7fc351589cea]
/usr/lib/python2.7/dist-packages/gi/_gobject/_gobject.so(+0x14371)[0x7fc351592371]
/usr/bin/python[0x47c1d1]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_EvalFrameEx+0x92e)[0x4b6b9e]
/usr/bin/python(PyEval_EvalCodeEx+0x13d)[0x4bcd2d]
/usr/bin/python[0x448edf]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x43074e]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x480c73]
/usr/bin/python[0x47c1d1]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_EvalFrameEx+0x92e)[0x4b6b9e]
/usr/bin/python(PyEval_EvalCodeEx+0x13d)[0x4bcd2d]
/usr/bin/python[0x448edf]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x43074e]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python[0x480c73]
/usr/bin/python[0x47c1d1]
/usr/bin/python(PyObject_Call+0x3a)[0x41ad2a]
/usr/bin/python(PyEval_EvalFrameEx+0x92e)[0x4b6b9e]
/usr/bin/python(PyEval_EvalCodeEx+0x735)[0x4bd325]
/usr/bin/python(PyEval_EvalFrameEx+0x7eb)[0x4b6a5b]
/usr/bin/python(PyEval_EvalFrameEx+0xb07)[0x4b6d77]
```
followed by Memory Map.

How can i fix this ? Thanks

"sudo apt-get update" & "sudo apt-get upgrade" seems work fine.

---

### Post by elephantgod on 2012-03-01
Anyone ?

---

