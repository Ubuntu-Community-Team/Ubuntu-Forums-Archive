---
title: "Xserver doesn't start and the keyboard doesn't work in recovery mode"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by pandabeer on 2009-11-28
Hi all,

I updated xserver today (in the updates)
since then I couldn't startup again (blank screen instead of login)
This happend before so i know hof to fix, (installing ati drivers again should work)

But for that i need to go in recovery mode, and I found out my keyboard doesn't work anymore in recovery mode (it still does in grub :s:s)

Can someone please help me

---

### Post by lemming465 on 2009-11-29
In the regular boot, does Ctrl-Alt-F1 get you to a text console, or is that equally inaccessible?  If you can get directly to a text console, you can log in and do stuff using apt-get or aptitude at the command line.

Otherwise, boot a live CD, mount your root partition, and get into a chroot environment.  Something like:```

sudo -i
mount /dev/sda3 /mnt
cd /mnt
for f in sys dev proc; do mount -o bind /$f $f; done
chroot .
```
If you have more partitions, you might have to add something like *mount -a* to get the rest of them.

Now use the command line tools to fix stuff (the GUI desktop is still running off the live CD, but the chroot is running on your real system, but using the live CD kernel.)

---

### Post by pandabeer on 2009-11-29
thanks alot, for now it just started working, (with some difficulties) but i will use your way if this happens again

---

