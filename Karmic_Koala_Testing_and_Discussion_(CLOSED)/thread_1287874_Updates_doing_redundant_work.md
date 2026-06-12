---
title: "Updates doing redundant work?"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-10-10
Sometimes when updating I click on "details" and read the lines, and I often notice that same tasks are performed several times during same update, i.e. grub being reconfigured twice.
Is it supposed to work this way or is it just too difficult and hence not worth the effort to avoid such double work?

---

### Post by 23meg on 2009-10-10
It's supposed to work that way. Changelogs are per source package, not per binary package, and a source package can produce multiple binary packages. When you see the same changelog on multiple (binary) packages, that means they're produced out of the same source package.

---

### Post by froggyswamp on 2009-10-10
Thanks but I'm not sure what you mean.. so I'll give an example.
The Update Manager finds new updates, lots of new packages to be updated. After downloading them, when installing, the grub bootloader sometimes gets reconfigured twice (say in the middle while installing updates and at the end), I thought it should happen only once.

---

### Post by ranch hand on 2009-10-10
Update-grub is run several times for some updates.  If you go to preferences in synaptic, on the first tab there is an option for viewing details in a terminal.  Check it.  This will allow you to scroll back and actually see what it says.

There will be warnings about the terminal not working right and falling back on the front-end.  Ignore them.

You will then be able to read what has triggered the running of update-grub.  It has to, for instance, see the new kernal, configure the new kernal, and then do it again (sometimes) to make sure it has all the kernals.

Each one of these is being triggered by a change in the /etc/grub.d or etc.default/grub.  It is run for each one as it comes along.

---

### Post by LKjell on 2009-10-10
One time for installing a new kernel and the last time is to remove a kernel. A failsafe incase the installation abort in between.

---

### Post by froggyswamp on 2009-10-10
Oh thanks ranch hand.. that's what I've been wondering about..

---

### Post by 23meg on 2009-10-10
Sorry, I seem to have misread that.

Packages can trigger post-installation actions in what's called the *postinst* script. The behavior you cite is most likely due to multiple packages triggering a reconfiguration of GRUB in postinst.

---

