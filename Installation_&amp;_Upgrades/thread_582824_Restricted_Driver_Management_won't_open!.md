---
title: "Restricted Driver Management won't open!"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by apricot on 2007-10-20
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/154786](https://bugs.launchpad.net/ubuntu/+source/restricted-manager/+bug/154786) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Bug description

Binary package hint: restricted-manager

After upgrading to Gutsy, my restricted manager won't open. This is what i get from sudo restricted-manager:

gorski@mashina:~$ sudo restricted-manager
```
Traceback (most recent call last):
  File "/usr/bin/restricted-manager", line 42, in <module>
    rm = RestrictedManager()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 53, in __init__
    RestrictedManagerCommon.__init__(self,args,opts)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerCommon.py", line 197, in __init__
    self.launch_manager()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 151, in launch_manager
    self.ManagerWindow(self.xml, self.handlers, self)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 209, in __init__
    self.reset_model()
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 262, in reset_model
    self.parent.set_title_label(self.xml.get_widget('label_heading'), any_enabled)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerGtk.py", line 122, in set_title_label
    (bold, normal) = RestrictedManagerCommon.title_label(self, in_use)
  File "/usr/lib/python2.5/site-packages/RestrictedManager/RestrictedManagerCommon.py", line 242, in title_label
    'these drivers.') % {'os': get_os_name()}
ValueError: unsupported format character 'n' (0x6e) at index 287

```

---

### Post by apricot on 2007-10-20
Problem in translation package. Solved!

---

### Post by th_11 on 2007-10-23
I have a same problem, except when I run restricted-manager from console, I get the same error as you, but the last line is:
ValueError: unsupported format character 'k' (0x6b) at index 82

Could you explain what you had to do to get it fixed? I really don't know what to do with a "translation package" (or where it is at all).

---

### Post by apricot on 2007-10-23
At this page you can find the solution!
[http://www.ubuntu-hr.org/forum/index.php?topic=2908.0]("http://www.ubuntu-hr.org/forum/index.php?topic=2908.0")

---

### Post by th_11 on 2007-10-24
Thanks apricot!

From the url you gave, I managed to figure out what language file was incorrect.

Then I just replaced the /fi/LC_MESSAGES/restricted-manager.mo with restricted-manager.mo from en_GB folder (I now have restricted-manager in english, but thats not a problem :D)

Good community work!

Oh yeah, I'll copy the path here where restricted-manager.mo can be found if anyone other have same kind of issues:
/usr/share/locale-langpack/ and there choose your system language, in my case the full path was:
/usr/share/locale-langpack/fi/LC_MESSAGES/restricted-manager.mo

---

