---
title: "Ubuntu One error in lucid 10.04"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by solitaire on 2010-03-21
I'm getting the following error when I try to set the prefrences for "Ubuntu One" 

```

2010-03-21 20:31:32,968 - ubuntuone.SyncDaemon.ActionQueue - ERROR - Upload                       share:''                                       node:marker:992622cd-687b-4dc6-8f81-a7fb6038bce4 Upload(share_id="''", hash="'sha1:da7daf3b41d187fdbb350a38577d52c67b5fc828'", fileobj_factory='<bound method FSKey.open_file of <ubuntuone.syncdaemon.sync.FSKey object at 0x1f78640>>', node_id='marker:992622cd-687b-4dc6-8f81-a7fb6038bce4', crc32='2213974092L', previous_hash="''", size='13396992') failure INTERNAL_ERROR
2010-03-21 20:32:42,479 - ubuntuone-preferences - ERROR - org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/ubuntuone/syncdaemon/dbus_interface.py", line 1093, in set_throttling_limits
    aq.readLimit = download
  File "/usr/lib/python2.6/dist-packages/ubuntuone/storageprotocol/client.py", line 1460, in _set_read_limit
    raise ValueError('Read limit must be greater than 0.')
ValueError: Read limit must be greater than 0.

```

I've tried manually changeing the entries in  "~/.config/ubuntuone/syncdaemon.conf"
but it's overwritten every time i open "System" "Prefrences" "Ubuntu One"

Any ideas on how to fix this?
Or will I post a Bug?

---

### Post by solitaire on 2010-03-22
*bump*

Anyone got any Ideas??

---

### Post by kyleabaker on 2010-03-22
Have you tried removing ubuntuone, clearing the profile and then reinstalling?

I run into this situation from time to time with other applications, so it may help.

---

### Post by autumnraine on 2010-03-22
I just went to try Ubuntu One for the first time, since it's supposedly able to sync multiple folders in their original position now, but it doesn't seem to do anything. The first time I pressed the button in Preferences it brought up a log in page, and so I logged in (didn't realize I already had an account :?) but then it wouldn't tie my computer to the account. The next time I pressed the button in preferences it acted like it would launch for a while and then nothing happened.

---

### Post by kyleabaker on 2010-03-22
> **autumnraine said:**
> I just went to try Ubuntu One for the first time, since it's supposedly able to sync multiple folders in their original position now, but it doesn't seem to do anything. The first time I pressed the button in Preferences it brought up a log in page, and so I logged in (didn't realize I already had an account :?) but then it wouldn't tie my computer to the account. The next time I pressed the button in preferences it acted like it would launch for a while and then nothing happened.
There are certainly problems with UbuntuOne still. I'm currently uploading a crash from right clicking the downloads folder and selecting to sync it with UbuntuOne...causing Nautilus to crash.

---

