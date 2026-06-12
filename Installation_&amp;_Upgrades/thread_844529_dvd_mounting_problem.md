---
title: "dvd mounting problem"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by utab on 2008-06-29
Dear all,

To recover my backup, I am trying to mount a dvd. But it is not working as intended. I can mount cds, that is not a problem fortunately...

The output from dmesg | grep CD is
[http://pastebin.com/d387e2dc3](http://pastebin.com/d387e2dc3)

The output of sudo hdparm -I /dev/scd0
[http://pastebin.com/m2834c77a](http://pastebin.com/m2834c77a)

The output of cat /etc/fstab
[http://pastebin.com/m612e1ec0](http://pastebin.com/m612e1ec0)

A similar thread I found was this but it was not concluded :/

Any help is appreciated.

Umut

---

### Post by didac on 2008-06-30
Can you mount any other dvd, or is the problem only with your backup?

Your line:

```
/dev/scd0  /media/cdrom0  udf,iso9660 user,noauto,exec,utf8 0 0
```

should be enough. No need to change it to:

```
/dev/scd0  /media/cdrom0  auto user,noauto,exec,utf8 0 0
```

Insert the dvd and post the output of

```
dmesg | tail
```

---

