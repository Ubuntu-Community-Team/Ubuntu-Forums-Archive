---
title: "Update manager crashing"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SpenceMakesSense on 2009-09-09
Update manager wont start heres the terminal output
```
spence@Metallica:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 103, in <module>
    app = UpdateManager(data_dir, options)
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 111, in __init__
    SimpleGtkbuilderApp.__init__(self, datadir+"glade/UpdateManager.ui")
  File "/usr/lib/python2.6/dist-packages/UpdateManager/SimpleGtkbuilderApp.py", line 33, in __init__
    self.builder.add_from_file(path)
glib.GError: Duplicate object id 'image15' on line 1088 (previously on line 957)
```

---

### Post by SpenceMakesSense on 2009-09-10
bump

---

### Post by dinxter on 2009-09-10
this should be fixed in version 1:0.124.9ubuntu1 of update-manager, is this the version (or later) you're using?
see
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/422249](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/422249)

---

