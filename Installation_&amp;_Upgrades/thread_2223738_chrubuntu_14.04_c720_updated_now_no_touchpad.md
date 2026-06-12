---
title: "chrubuntu 14.04 c720 updated now no touchpad"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by Rob_Marlow on 2014-05-12
I had been running chrubuntu 14.04 on a c720 with great success until I ran updates today and now the touchpad is no longer working, Any ideas how I might be able to recover the touchpad functionality?

---

### Post by mystronyx on 2014-05-16
Tonight, I installed 14.04 on my c720 Chromebook. To fix the touchpad, I followed the steps here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1308264/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1308264/comments/9)

If you're not having any problems with the kernel, then don't bother with step one because that is for a long bootup time issue. To fix the touchpad, follow steps 2 through 7. I had to reboot for the touchpad to begin working.

Here are the critical steps:

1. Type the following into the terminal:
wget [http://goo.gl/kz917j](http://goo.gl/kz917j)

2. Then, type this:
bash kz917j

3. Reboot

If the above does not work, then try this:

4. sudo gedit kz917j

5. edit the section that says
# Grab Ubuntu kernel source
apt-get source linux-image-$mykern
cd $mykernver

Change it to

# Grab Ubuntu kernel source
#apt-get source linux-image-$mykern
#cd $mykernver
wget [http://www.kernel.org/pub/linux/kernel/v3.x/linux-3.14.4.tar.xz](http://www.kernel.org/pub/linux/kernel/v3.x/linux-3.14.4.tar.xz)
tar -xJf linux-3.14.4.tar.xz
cd linux-3.14.4

Replace 3.14.4 with whatever your kernel is. You can check it via uname -r

Repeat steps 2 and 3. After reboot, the touchpad should be working.

---

### Post by troy8 on 2014-05-25
Best thing to do is to skip all the patching BS and just grab the 4 needed files directly from Google's Peppy repo.  I just pulled them from their 3.14 kernel put them in my 3.14.4 source tree and everything works with no patching.

---

### Post by joblo2 on 2014-06-01
It would be nice if you could give a bit more detail on how to do this as I'm all for avoiding "the patching BS" which I've been through a couple of times already and found it breaks when any updates are applied.

regards,
A linux novice

---

