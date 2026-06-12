---
title: "inotify_add_watch failed"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by YA0730 on 2010-06-03
On boot - I get the message udevd inotify_add_watch failed  no such file or directory for my LVM physical volumes...  volumes are mounted and appear to be usable...

Is this normal?

10.04 LTS Server

---

### Post by cmdupre on 2010-07-11
I have the same issue, I think... but the error message specifies /dev/sda3 and /dev/sdb1 which are actually physical volumes in my volume group. I think it's because the devices are only lvm partitions and don't actually have a file system. I'm looking around the web for more information but not much luck.

---

### Post by jursra on 2010-07-18
After installing 'cryptsetup' the message disappears.

---

### Post by Joe Momma on 2010-07-29
Thanks, I was having the same problem and cryptsetup fixed it for me too.

My problems started when I installed dmraid and setup a raid device.  After that the two drives in my raid triggered the inotify_add_watch error, but then bootup continued and I never saw any other issues.

So my questions are:

Does anyone know what the hell the error was trying to tell me?

And what does cryptsetup do? Why did I need to install it? And what have I changed about my system now?

---

### Post by cmdupre on 2010-08-09
> **Joe Momma said:**
> And what does cryptsetup do?

Check your man page for cryptsetup... or go here: [http://linux.die.net/man/8/cryptsetup]("http://linux.die.net/man/8/cryptsetup")

I'd like to know the answer to the other questions you have as well.

---

### Post by foxmulder881 on 2010-11-18
Thanks a million jursra. I was getting udev-work[79] and inotify_add_watch errors at boot on Maverick 10.10. So I just installed the cryptsetup package and it fixed all my boot errors also.

---

### Post by paolo.denti on 2010-12-28
thanks, cryptsetup fixed errors on logical volumes.

---

