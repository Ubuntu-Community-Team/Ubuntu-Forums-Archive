---
title: "the upgrade 8.04&gt;10.04 stops without upgrading the system"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by fabio61 on 2010-07-18
I was going to upgrade my 8.04LTS system to the new 10.04: I had done it in May on my notebook and now I was going to do it on my main desktop.
I followed the instruction found in:
[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

everything OK up to the start of the upgrade to the new release, the update-manager tells me that it is downloading the new "advanced update manager tool" (2 files) but then everything stops, NO UPGRADE 

In the console it appears the following:

Code:

root@compaq-desktop:~# update-manager --devel-release
extracting 'lucid.tar.gz'
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/UpdateManager/UpdateManager.py", line 959, in on_button_dist_upgrade_clicked
    fetcher.run()
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 202, in run
    if not self.extractDistUpgrader():
  File "/usr/lib/python2.5/site-packages/UpdateManager/Core/DistUpgradeFetcherCore.py", line 130, in extractDistUpgrader
    for tarinfo in tar:
  File "/usr/lib/python2.5/tarfile.py", line 2053, in next
    tarinfo = self.tarfile.next()
  File "/usr/lib/python2.5/tarfile.py", line 1806, in next
    self.fileobj.seek(self.offset)
  File "/usr/lib/python2.5/gzip.py", line 388, in seek
    self.read(1024)
  File "/usr/lib/python2.5/gzip.py", line 227, in read
    self._read(readsize)
  File "/usr/lib/python2.5/gzip.py", line 275, in _read
    self._read_eof()
  File "/usr/lib/python2.5/gzip.py", line 311, in _read_eof
    raise IOError, "CRC check failed"
IOError: CRC check failed
/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py:75: GtkWarning: gtk_scrolled_window_add: assertion `bin->child == NULL' failed
  self.parent.scrolled_notes.add(textview_release_notes)
extracting 'lucid.tar.gz'

---

