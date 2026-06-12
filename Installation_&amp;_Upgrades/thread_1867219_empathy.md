---
title: "empathy"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by btek on 2011-10-22
Hellow 
I have problem with empathy. I recive messages but I can't send.
I have kubuntu and gnome 3 with empathy 3.2.0

Log
```


empathy/(null)-DEBUG: 21.10.2011 17:58:49.261715: empathy_tp_chat_send: Sending message: erfews
empathy/(null)-DEBUG: 21.10.2011 17:58:49.268049: message_send_cb: Error: org.freedesktop.DBus.Python.NotImplementedError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/telepathy/_generated/Channel_Interface_Messages.py", line 117, in SendMessage
    raise NotImplementedError
NotImplementedError

```

---

