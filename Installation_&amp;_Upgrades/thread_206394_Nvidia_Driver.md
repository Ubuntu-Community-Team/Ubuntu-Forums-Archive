---
title: "Nvidia Driver"
date: 2006-06-30
forum: Installation &amp; Upgrades
---

### Post by thepocketdrummer on 2006-06-30
I just needed to know what I needed to install the Nvidia Drivers. I get to the gcc check and it fails. What do I need to finish the installation?

---

### Post by woedend on 2006-06-30
it depends.
The EASIEST way by far is to install the package nvidia-glx if you can.  No compiling, just point and click.  If this does not work, you can do it your way also but its messy.
You would need the package build-essential(contains your make/gcc stuff) and I think the kernel headers for your particular kernels.  Its been a while since ive done it this way, so let me know if you hit another bump.

---

### Post by thepocketdrummer on 2006-06-30
Is the easy way the most recent drivers?

---

### Post by woedend on 2006-06-30
yes, 8762 I think it is?  But yes, the most recent.
you have to enable the repos first(can be done in synaptic...I think its in multiverse)

---

### Post by tseliot on 2006-06-30
Have a look at Method 1 of my guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

