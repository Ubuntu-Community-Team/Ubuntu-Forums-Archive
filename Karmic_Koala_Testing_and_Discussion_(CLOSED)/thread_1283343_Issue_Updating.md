---
title: "Issue Updating"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-10-05
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 103, in _process_transaction
    self.commit_packages(**self.trans.kwargs)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 146, in commit_packages
    self._commit_changes()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 418, in _commit_changes
    self._check_unauthenticated()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 176, in _check_unauthenticated
    raise UnauthenticatedPackageError(sorted(list(unauthenticated)))
UnauthenticatedPackageError: org.debian.apt.UnauthenticatedPackage: grub-common,klibc-utils,language-pack-en,language-pack-en-base,language-pack-gnome-en,language-pack-gnome-en-base,libffi5,libklibc,libpython2.6,libspectre1,libsqlite0,python2.6,python2.6-minimal

Did everyone get this?  The updates are there but cant update because of that error.

---

### Post by sports fan Matt on 2009-10-05
Was able to update it just took forever this morning.

---

### Post by jatinps on 2009-10-06
I have the same problem today morning - request to please take of the solved tag
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 103, in _process_transaction
    self.commit_packages(**self.trans.kwargs)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 146, in commit_packages
    self._commit_changes()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 418, in _commit_changes
    self._check_unauthenticated()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 176, in _check_unauthenticated
    raise UnauthenticatedPackageError(sorted(list(unauthenticated)))
UnauthenticatedPackageError: org.debian.apt.UnauthenticatedPackage: libatasmart4,libgtkhtml2-0

Attaching a screenshot.
Also can someone tell me why ubuntu-desktop cannot be checked (seen in screenshot)
[ATTACH]130942[/ATTACH]

---

