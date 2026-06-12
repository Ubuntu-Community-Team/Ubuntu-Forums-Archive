---
title: "Howto install &quot;minimal&quot; from desktop ISO"
date: 2017-01-01
forum: Installation &amp; Upgrades
---

### Post by porlockos on 2017-01-01
Hi,

I want to use Ubuntu on some intel atom device, unfortunately standard Ubuntu editions does not work, it stuck on boot, some kernel patches are needed to work fine.
I find a project that provide this patches to Ubuntu desktop ISO, but I do not need an GUI and other software that desktop ISO provides, is there a way to install minimal version by using a desktop ISO version ?
I can’t just download the minimal iso because it does not have that kernel patches I mentioned earlier I must use a special desktop version ISO.

regards
Tomek

---

### Post by Irihapeti on 2017-01-01
If your disk is a standard Ubuntu disk with a few patches, you should be able to do a command-line install by choosing expert mode and then replacing "ubuntu.seed" (or similar) in the command string with "cli.seed".

This is assuming that the disk has a preseed directory containing a cli.seed file. Note that I haven't actually tried this myself.

---

### Post by Irihapeti on 2017-01-01
Update: I've tried this in a virtual machine and unfortunately it doesn't do what I thought it would.

We need to keep looking.

---

### Post by ian-weisser on 2017-01-01
It's not easy, but Debian Live ([https://www.debian.org/devel/debian-live/](https://www.debian.org/devel/debian-live/)) will create an installer using software -including patched kernel- that you provide.

---

