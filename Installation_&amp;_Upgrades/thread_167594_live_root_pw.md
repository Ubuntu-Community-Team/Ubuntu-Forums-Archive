---
title: "live root pw"
date: 2006-04-28
forum: Installation &amp; Upgrades
---

### Post by ron kaye on 2006-04-28
dont remember being root setup or password

want to mount a floppy

su root
password?

ron

---

### Post by Jagot on 2006-04-28
Ubuntu uses sudo:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Just run any tasks that would require root with sudo preceeding it.

---

### Post by yomoenco on 2006-04-28
Ron,

You should use `sudo` to run a command as root (sudo mount ......), and give your own password when it replies for one.
and if need a root shell you can give a `sudo su -`, then you have a "root" session you can end with `exit`

Regards,
   Andre

---

