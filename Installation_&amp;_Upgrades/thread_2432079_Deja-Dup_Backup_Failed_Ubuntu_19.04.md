---
title: "Deja-Dup Backup Failed Ubuntu 19.04"
date: 2019-11-26
forum: Installation &amp; Upgrades
---

### Post by saywot on 2019-11-26
I haven't been able to complete a back-up for weeks
I'm trying to use a formatted external HDD and the outout from the failure window is, to me, incomprehensible
the Failed Due To An Unknown Error has this in a window
```
Traceback (innermost last):
  File "/usr/bin/duplicity", line 1560, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1546, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1398, in main
    do_backup(action)
  File "/usr/bin/duplicity", line 1528, in do_backup
    incremental_backup(sig_chain)
  File "/usr/bin/duplicity", line 664, in incremental_backup
    bytes_written = dummy_backup(tarblock_iter)
  File "/usr/bin/duplicity", line 227, in dummy_backup
    while tarblock_iter.next():
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 523, in next
    result = self.process(self.input_iter.next())
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 195, in get_delta_iter
    for new_path, sig_path in collated:
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 280, in collate2iters
    for relem2 in riter2:
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 354, in combine_path_iters
    refresh_triple_list(triple_list)
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 341, in refresh_triple_list
    new_triple = get_triple(old_triple[1])
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 327, in get_triple
    path = path_iter_list[iter_index].next()
  File "/usr/lib/python2.7/dist-packages/duplicity/diffdir.py", line 239, in sigtar2path_iter
    for tarinfo in tf:
  File "/usr/lib/python2.7/tarfile.py", line 2510, in next
    tarinfo = self.tarfile.next()
  File "/usr/lib/python2.7/tarfile.py", line 2350, in next
    self.fileobj.seek(self.offset - 1)
  File "/usr/lib/python2.7/dist-packages/duplicity/dup_temp.py", line 221, in seek
    return self.fileobj.seek(offset)
  File "/usr/lib/python2.7/gzip.py", line 443, in seek
    self.read(count % 1024)
  File "/usr/lib/python2.7/gzip.py", line 267, in read
    self._read(readsize)
  File "/usr/lib/python2.7/gzip.py", line 331, in _read
    self._read_eof()
  File "/usr/lib/python2.7/gzip.py", line 353, in _read_eof
    hex(self.crc)))
 IOError: CRC check failed 0x940ae478 != 0x709c7d7fL
```

What am I supposed to make of that ?

---

### Post by saywot on 2019-11-26
So I uninstalled then re-installed tried a back-up to the same location, with the "snap' version I get 
[B][I]Back-Up Failed
Failed to read /tmp/duplicity-vc74him5-tempdir/mktemp-dafhu7iq-2: (<class 'OSError'>, OSError('CRC check failed 0x940ae478 != 0x84d0fc3f',), <traceback object at 0x7fef723e9048>)[/I][/B]

---

### Post by deadflowr on 2019-11-26
This bug is the closes  I've found on it: [https://bugs.launchpad.net/deja-dup/+bug/676767]("https://bugs.launchpad.net/deja-dup/+bug/676767")

The comments show that removing the cache for it can help.

---

### Post by saywot on 2019-11-27
For the third time 
[B][I]
[/I][/B]Failed to read /tmp/duplicity-yq19nvma-tempdir/mktemp-hm_o6lg0-2: (<class 'OSError'>, OSError('CRC check failed 0x940ae478 != 0x84d0fc3f',), <traceback object at 0x7f05d4723148>)

I think we can say that Deja-Dup is never going to create a back-up

---

### Post by saywot on 2019-11-27
Deleted .cache/Deja-Dup twice and ...
***Failed to read /tmp/duplicity-rs9mzb5u-tempdir/mktemp-zn6aj1xn-2: (<class 'OSError'>, OSError('CRC check failed 0x940ae478 != 0x84d0fc3f',), <traceback object at 0x7f4eb0a730c8>)***
so what else can I try ?

---

### Post by saywot on 2019-11-28
If deleting the cache doesn't work then what else can I try ?

---

### Post by saywot on 2019-11-28
[B][I]sudo deja-dup
[sudo] password for saywot: *************
Cannot load module /usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so: GModule (/usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)
/usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so does not export GTK+ IM module API: GModule (/usr/lib/x86_64-linux-gnu/gtk-3.0/3.0.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)[/I][/B]

Does this mean anything ?

---

### Post by maglin2 on 2019-11-29
It's a bit of an oblique response, but are you wedded to using deja-dup? Other backup solutions are available.

I recall having issues with it years ago. I switched to back in time and have had no problems.

---

