---
title: "Noob failing to install Ubuntu 11.10 x64 on SSD from CD/USB"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by Becks21 on 2012-02-03
Hi there,

I am trying to install Ubuntu 11.10 x64 on a SSD from CD/USB but it looks like the boot-routine is crashing..

The last lines are like:

.../sbin/modprobe -bv pci:v000......
udevd[117]: inotify_add_watch(6, /dev/dm-0, 10) failed: No such file or directory

After that nothing happens and Ctrl-Alt-Del triggers the reboot..

Any help please? THX


System:
Intel i7-920
Gigabyte X58 UD5 (latest bios F13u)
SSD OCZ Revodrive x2 240gb in Raid0
Graphics: EVGA GTX580

---

### Post by darkod on 2012-02-03
Did you try with the Alternate Install CD? For raid you should use the alternate.

Also, the Revo drive is a raid itself and I am not sure it is supported. I remember reading about some issues if you want to install ubuntu because Revo is specific. Try googling for more info and also the alternate installer.

---

### Post by Becks21 on 2012-02-04
Thx Darko for your reply..

Finally I have been able to boot into Ubuntu via the Live-USB, but only if I disable acpi via the Boot-Options (F6 --> "acpi=off).. is this a bug?

Also you are right.. Revodrives are special "Raids".. "Fake Raids" to be precise..
Creating partitions and installing Ubuntu on it was no problem until the grub installer failed..
So I tried to start the installation via the Ubuntu-USB.. but this ended with Kernel Panic..

I had a good read over here at the OCZ forums.. I will try it
([http://www.ocztechnologyforum.com/forum/showthread.php?76486-Revodrive-Ubuntu-10.04-install-issues](http://www.ocztechnologyforum.com/forum/showthread.php?76486-Revodrive-Ubuntu-10.04-install-issues))

---

### Post by darkod on 2012-02-04
Again, if you use the standard, Live CD, a failure to install grub2 is what happens sometimes.

You should be able to add just grub2 by chroot-ing into the install. This link has some more info about adding grub2 on fakeraid, read carefully for the parts you need because you already have part of the job (install) done:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Becks21 on 2012-02-08
I just wanted to shout a Thx to you for helping me.

I now have a running Ubuntu on my Revodrive.. switched to Gnome3 and installed some extensions.. :D

---

### Post by darkod on 2012-02-08
No problem, glad you got it running.

In case this thread shows up in google for someone, it would be nice to say was it only adding grub2? That was the only issue?

Also, you can mark the thread as Solved in Thread Tools above the first post.

---

