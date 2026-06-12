---
title: "keyboard problem after upgrading to feisty 7.04"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by mcewen98 on 2007-04-20
Hello,

I used the update manager to update edgy 6.10 to feisty 7.04.  After it was done and restarted my keyboard is no longer working correctly.  Typing the letters asdfghjk results in abfhjk;' being printed to the screen.  I tried adding acpi=off (after seeing what sounded like a related post) to the grub boot options but that didn't help.  Also, I'm accessing the desktop through VNC.  Anybody else have this problem?

Thanks,

---

### Post by ryanc on 2007-04-20
I am experiencing this same issue. The keyboard works fine from the real keyboard but when connecting via vnc the keys are all wrong.

---

### Post by mcewen98 on 2007-04-20
> **ryanc said:**
> I am experiencing this same issue. The keyboard works fine from the real keyboard but when connecting via vnc the keys are all wrong.

Well this sucks.  I use ubuntu as my home server without a keyboard mouse or display directly attached.  I only occasionally access it with VNC, but when I do, I need it to work.  I wonder if this has already been reported as a bug?

---

### Post by ryanc on 2007-04-20
I noticed if I login to gdm on the local display then enable remote desktop through gnome I can connect to the :0 display and use the keyboard just fine. You may be able to start gdm without a local keyboard + display... use x11vnc to login to gdm... and go from there.

I will search launchpad in a few minutes and see if this has been reported.

---

### Post by mcewen98 on 2007-04-20
> **ryanc said:**
> I noticed if I login to gdm on the local display then enable remote desktop through gnome I can connect to the :0 display and use the keyboard just fine. You may be able to start gdm without a local keyboard + display... use x11vnc to login to gdm... and go from there.

I will search launchpad in a few minutes and see if this has been reported.

Yeah this is weird.  If I log into desktop :0 it's fine.  It's only a problem when I'm using the vncserver command to start up another desktop, and connect to :1.  When I connect to :1, the shift key does not work, and the number keys aren't right either.

---

### Post by fourthirtysix on 2007-04-24
i'm having this vnc keyboard problem after upgrading to feisty as well. has anyone figured out what the problem is?

---

### Post by fourthirtysix on 2007-04-26
i've been following this issue since i am having the same problem. it seems to be referred to as the "abfh" problem since that is what people get when they type "asdf"

i upgraded two computers to feisty at the same time, and i only have the gnome keyboard abfh problem on a headless machine that I use tightvnc to connect to.  i never had a problem running the exact same configuration with edgy.

i tried playing around with keyboard and language settings in gnome a little bit, but nothing seemed to help.

i hope someone can track this problem down. i will attempt to look into more this weekend.

if anyone solves the problem, please post the answer here. i am tracking what appears to be the same problem in a number of threads/posts:

[http://ubuntuforums.org/showthread.php?p=2523097](http://ubuntuforums.org/showthread.php?p=2523097)

[http://ubuntuforums.org/showthread.php?p=2517629](http://ubuntuforums.org/showthread.php?p=2517629)

[http://ubuntuforums.org/showthread.php?t=233613](http://ubuntuforums.org/showthread.php?t=233613)

[http://ubuntuforums.org/showthread.php?t=420179](http://ubuntuforums.org/showthread.php?t=420179)

---

### Post by Labanana on 2007-04-26
.

---

### Post by davidpk on 2007-04-30
Check out [https://bugs.launchpad.net/ubuntu/feisty/+source/vnc4/+bug/78282](https://bugs.launchpad.net/ubuntu/feisty/+source/vnc4/+bug/78282)

The "-extension XFIXES" switch appears to have corrected the problem for me. I haven't tested all apps, but Mozilla and synaptic work AND the keyboard issue appears to be resolved.

I'm not sure this is a solution, but I'm able to bring up Gnome and type correctly now!


David

---

### Post by ryanc on 2007-04-30
Thank works for me as well.

---

