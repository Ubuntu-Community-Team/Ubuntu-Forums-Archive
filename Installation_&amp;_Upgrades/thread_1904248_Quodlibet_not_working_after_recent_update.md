---
title: "Quodlibet not working after recent update"
date: 2012-01-04
forum: Installation &amp; Upgrades
---

### Post by tlee on 2012-01-04
Greetings--

After the most recent round of system updates, quodlibet no longer works.  Starting it from the command line produces the following:

```
Traceback (most recent call last):
  File "/usr/bin/quodlibet", line 289, in <module>
    main()
  File "/usr/bin/quodlibet", line 36, in main
    library=const.LIBRARY,
  File "/usr/lib/pymodules/python2.7/quodlibet/__init__.py", line 160, in init
    _gtk_init(icon)
  File "/usr/lib/pymodules/python2.7/quodlibet/__init__.py", line 30, in _gtk_init
    import gtk
  File "/usr/lib/pymodules/python2.7/quodlibet/__init__.py", line 132, in import_ql
    try: return old_import(module, *args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
  File "/usr/lib/pymodules/python2.7/quodlibet/__init__.py", line 132, in import_ql
    try: return old_import(module, *args, **kwargs)
ImportError: /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1: undefined symbol: xcb_glx_set_client_info_2arb
```


This is Oneiric on a Macbook Air (4-2).

Any ideas?

---

### Post by silpablo on 2012-01-04
I'm having the same problem in linux mint lisa (oneiric)

[COLOR=RoyalBlue]/usr/lib/linuxmint/mintInstall/mintinstall.py:252: SyntaxWarning: import * only allowed at module level
  def get_status_description(self, transaction):
/usr/lib/linuxmint/mintInstall/mintinstall.py:260: SyntaxWarning: import * only allowed at module level
  def get_role_description(self, transaction):
Traceback (most recent call last):
  File "/usr/lib/linuxmint/mintInstall/mintinstall.py", line 6, in <module>
    import gtk
  File "/usr/lib/python2.7/dist-packages/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: /usr/lib/i386-linux-gnu/mesa/libGL.so.1: undefined symbol: xcb_glx_set_client_info_2arb
[COLOR=Black]
I guess it is a bug on python or maybe in the xorg ppa (I'm using it)

see this [https://answers.launchpad.net/ubuntu/+question/183731](https://answers.launchpad.net/ubuntu/+question/183731)[/COLOR]
[/COLOR]

---

### Post by tlee on 2012-01-04
Thanks.  I found the solution on that page.

---

