---
title: "Dying for help after 9.10 upgrade"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by ssdt on 2009-12-11
I just upgraded to 9.10 and it told me to reboot my system and after the reboot i get this error message:
```

init: unreadahead main process (2051) terminated with status 5
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2052) terminated with status 1
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@dell-desktop:~#
```


please help me as soon as possible
i am using dell inspiron 530N
thank you

---

### Post by Fafler on 2009-12-12
Unfortunately upgrading from 9.04 to 9.10 seems to give more problems than usual. If you possible can, backup any important data and reinstall. Even though it's not the Linux way of doing upgrades ;-)

---

### Post by ssdt on 2009-12-12
Fixed it with Dell's given Backup DVD which took me back to LTS 8.04. They told me not to upgrade much until another LTS comes by which will soon be in April 2010.

Thanks everyone.

---

