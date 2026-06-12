---
title: "kernel update failure"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by frank_n on 2011-07-16
ubuntu 11.04 32-bit.

An update from kernel 2.6.38-8-generic to kernel 2.6.38-10-generic
has failed with a kernel panic at reboot:

/init: exec: line 331: run-init: Permission denied.

Using an old (distinct) install, I have set all permissions in 11.04

/etc/init
/etc/init.d
/etc/initramfs-tools

to 777 and still it wouldn't help. Also no clue in the log files.

As a workaround, I have now pointed the symlinks /vmlinuz and 
/initrd.img to the 2.6.38-8 version and so 11.04 does boot. But synaptics is in a mess and I would like to clean it up and complete the update.

How?

Thanks!

frank

---

### Post by dino99 on 2011-07-16
tweaking permissions is the best way to have a broken system, and undoing its a nightmare.

Ready for a clean install :)

---

### Post by frank_n on 2011-07-16
> **dino99 said:**
> tweaking permissions is the best way to have a broken system, and undoing its a nightmare.


You sound encouraging. Maybe you know what the death message

/init: exec: line 331: run-init: Permission denied.

refers to?

Thanks.

frank

---

### Post by dino99 on 2011-07-16
dont want to discourage but trying to find and restore settings to finally get an instable system, its not the way i choose.

---

### Post by frank_n on 2011-07-17
While hoping for positive feedback, I unpacked initrd and looked at init (which resides in /sbin in binary form but is a script).

Its line 331 is the last one and reads

exec run-init ${rootmnt} ${init} "$@" <${rootmnt}/dev/console >${rootmnt}/dev/console 2>&1

translating to

exec run-init /root /sbin/init </root/dev/console >/root/dev/console

The line is just preparing the death message to the console, real problems came before during script execution, but where? The only sure thing is, the update did generate an invalid initrd.

So I booted into my alternate (kitchen & workshop) 11.04 and initiated there a kernel update. Reboot went ok, so next step. I copied initrd from the alternate install into the main install (that wouldn't boot) replacing the invalid initrd.

Allah is great and Mohamed is her prophet! The update is done, the (main) install is booting. And I'm not marking the issue [SOLVED] because it isn't.

You can find tons of posts on the net about failing update reboots, all stuck in the init script. About time for the maintainers to give some more information and support to users.

---

