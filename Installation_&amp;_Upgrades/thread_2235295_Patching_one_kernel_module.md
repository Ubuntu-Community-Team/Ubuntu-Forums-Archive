---
title: "Patching one kernel module"
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by cpdondo on 2014-07-20
I know this is out there somewhere but I can't find a useful howto....

What is the proper, ubuntu way to patch and build a module for the current kernel (ie the kernel that is running on the system)?  I don't want to build the whole kernel, and I don't want a custom kernel, I just want to patch one module.

---

### Post by kc1di on 2014-07-20
which module is it?   some can be done with dkms. 

[here's the page on dkms]("http://manpages.ubuntu.com/manpages/precise/man8/dkms.8.html")

---

### Post by cpdondo on 2014-07-20
thinkpad_acpi.  I ended up grabbing the source for the module as well as the makefile and building it, but as "user friendly" as ubuntu is I'm sort-of surprised there isn't some idiot-proofed system for idiots like me.  :)

---

