---
title: "Dropbox - can't download daemon - not a gzip file"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by DavetheDude on 2010-08-23
Using lucid LTS, I have no problem installing dropbox using either the website download .deb, or adding it to my repositories.

The problem comes when I try and run the software. At this point it unsuccessfully tries to download the required proprietary daemon.

In the terminal, running:

'sudo dropbox start -i'

Gives:

Starting Dropbox...Traceback (most recent call last):
  File "/usr/bin/dropbox", line 242, in handle_data_waiting
    self.unpack_dropbox()
  File "/usr/bin/dropbox", line 252, in unpack_dropbox
    name, i, total = one_member.next()
  File "/usr/bin/dropbox", line 148, in unpack
    archive = tarfile.open(self.local_path, 'r:gz')
  File "/usr/lib/python2.6/tarfile.py", line 1671, in open
    return func(name, filemode, fileobj, **kwargs)
  File "/usr/lib/python2.6/tarfile.py", line 1722, in gzopen
    raise ReadError("not a gzip file")
tarfile.ReadError: not a gzip file


Any ideas? Thanks troops.

---

### Post by DavetheDude on 2010-08-25
Bump. Anyone?

---

### Post by olmecnz on 2010-12-12
Same issue for me.... any ideas people?

---

### Post by malleeblue on 2010-12-30
Does the info at this link help you out?

[http://forums.dropbox.com/topic.php?id=22209](http://forums.dropbox.com/topic.php?id=22209)

---

