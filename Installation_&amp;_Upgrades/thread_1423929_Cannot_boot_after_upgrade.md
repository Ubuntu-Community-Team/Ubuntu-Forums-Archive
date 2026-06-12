---
title: "Cannot boot after upgrade"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by James Goode on 2010-03-07
I have just upgraded my server to 9.10, and I cannot boot.  Here is the error message I get:

```

init: ureadahead main process (2492) terminated with status 5
mountall start/spawned, process 2493
mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
init: mountall main process (2493) terminated with status 1
General error mounting filesystems

```

Then a root maintenance shell is started.

Typing:
mountall --debug | grep proc
results in:
```

mountall:/proc: unable to mount: Device or resource busy
mountall:/proc/self/mountinfo: No such file or directory
mountall: root filesystem isn't mounted
parse_filesystems: proc (udev)
new_mount: /proc: - proc nodev,noexec,nosuid
new_mount: /proc/sys/fs/binfmt_misc: - binfmt_misc nodev,noexec,nosuid,optional
update_mount: /proc: proc proc defaults
mount_proc: mounting /proc
mount_policy: /proc/sys/fs/binfmt_misc: dropping unknown filesystem
mount_policy: /proc can be mounted while root readonly
mount_policy: /proc prior fstab entry /
mount_policy: /proc is virtual

```

Please help, I need to get this server back online.

Thanks,

--James.

---

### Post by AgentZ86 on 2010-03-07
can you boot to a 9.10 CD and recover/repair ?

---

### Post by James Goode on 2010-03-07
I can't write a CD, because the only CD writer is in the server.  I have access to a 7.10 CD, if that helps.

---

### Post by James Goode on 2010-03-07
Ah!

Grub didn't update, probably my absent-mindedness.

Sorry for the panic-posting.

---

