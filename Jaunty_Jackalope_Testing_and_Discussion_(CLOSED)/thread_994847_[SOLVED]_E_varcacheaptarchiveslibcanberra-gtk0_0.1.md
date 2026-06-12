---
title: "[SOLVED] E: /var/cache/apt/archives/libcanberra-gtk0_0.10-1ubuntu2_amd64.deb"
date: 2008-11-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by philinux on 2008-11-27
E: /var/cache/apt/archives/libcanberra-gtk0_0.10-1ubuntu2_amd64.deb: trying to overwrite `/usr/bin/canberra-gtk-play', which is also in package libcanberra-gnome

Anyone else got this.

---

### Post by randiroo76073 on 2008-11-27
Ya, I got it too.

---

### Post by Ric_ on 2008-11-27
I had something like that a long time ago. Have you tried:

 apt-cache clean 
 apt-get update

then reinstall?

---

### Post by klim8 on 2008-11-27
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libcanberra-gtk0_0.10-1ubuntu2_amd64.deb

---

### Post by philinux on 2008-11-27
Sorted cheers.

---

### Post by dakkar9999 on 2008-11-27
Is this to solve the libcanberra-gtk0 update install?  That didn't work for me.

---

### Post by philinux on 2008-11-27
Yes this did the trick
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libcanberra-gtk0_0.10-1ubuntu2_amd64.deb

I had previously been into synaptic reloaded and marked all upgrades.

---

### Post by dakkar9999 on 2008-11-28
I get "no such file or directory"

Could you specify which files you chose in synaptic to install?

Thanks!

---

### Post by philinux on 2008-11-28
Cant remember now. I just hit reload as normal then Custom Filters then Upgradable upstream. Marked all the upgrades. 
Also further down this thread [http://ubuntuforums.org/showthread.php?t=995073](http://ubuntuforums.org/showthread.php?t=995073)
canberra is the topic again.

---

### Post by dakkar9999 on 2008-11-28
Followed these instruction [https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/302251/comments/21]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/302251/comments/21") after login out of the gnome session and it worked!

Now my sound is fixed as well!  All is well again! Except flash... I'll have to reinstall that.

---

### Post by Eclipse. on 2008-11-28
> **dakkar9999 said:**
> I get "no such file or directory"

Could you specify which files you chose in synaptic to install?

Thanks!

Remove the amd64 part and replace it with i386.

---

