---
title: "Can't upgrade to Intrepid"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sipickles on 2008-10-06
Hi,

When I do this:

upgrade-manager -d

I hoped to be able to upgrade to intrepid beta.

No distro upgrade is shown tho.

Heres the output:

```
simon@simon-linux:~$ sudo update-manager -d
[sudo] password for simon: 
Unhandled exception in thread started by <bound method MetaRelease.download of <MetaRelease object at 0x856561c (UpdateManager+MetaReleaseGObject+MetaRelease at 0x8812010)>>
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/MetaRelease.py", line 229, in download
    self.parse()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/MetaRelease.py", line 139, in parse
    current_dist_name = self.get_dist()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/MetaRelease.py", line 129, in get_dist
    p = Popen(["lsb_release","-c","-s"],stdout=PIPE)
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
sh: lsb_release: not found

```

I am seeing few errors with python-libxml2 and python-gtkhtml2 in the update manager in case that is related. Not sure how to reinstall these are suggested by update manager.

Thanks for any advice

Simon

---

### Post by sipickles on 2008-10-06
Ok, my python install is corrupt.

'lsb_release -c' spits out errors.

I'll see to that first!

---

