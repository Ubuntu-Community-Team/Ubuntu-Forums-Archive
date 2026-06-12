---
title: "devpts not started at boot?"
date: 2009-02-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tigerstripedcat on 2009-02-02
Whenever I opened any console (konsole, xterm, etc.) I couldn't get a prompt to type anything in.  This is resolved by:

sudo mount -t devpts devpts /dev/pts

However, why is this not started by default.  I've installed jaunty on two computer and neither have a listing in fstab to mount devpts.  Has anyone else ran into this problem?  Could you check your /etc/fstab and let me know if it shows a mount listing for /dev/pts?

Thanks,
TSC

---

### Post by marmuta on 2009-02-03
It's not in fstab here either, but the mount is still there.
I guess it's mounted by one of the init scripts.
Are there any errors during boot?

Edit: There is a bug report already, [#313947]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313947").

---

