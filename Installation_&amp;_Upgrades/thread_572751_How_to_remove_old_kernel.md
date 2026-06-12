---
title: "How to remove old kernel"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by mrsurf on 2007-10-10
I updatd UBUNTU 7.04 and after update I found there are now 4 headers for selection during boot i.e. kernel 2.6.20-15 generic,kernel 2.6.20-15 recovery,kernel 2.6.20-16 generic,kernel 2.6.20-16 recovery. 
Now I am confused to boot with which one and is it necessary to use older and how can i remove either of these . Is it necessary to update to newer version???

---

### Post by logos34 on 2007-10-10
Don't delete them, just 'comment out' the older -15 kernels so they don't show up on the grub menu screen.  Put a hash mark (#) in front of each line

[http://users.bigpond.net.au/hermanzone/p15.htm#ubuntu_OS_entry](http://users.bigpond.net.au/hermanzone/p15.htm#ubuntu_OS_entry)

---

### Post by mrsurf on 2007-10-11
Thanks for nice tutorial to tweak grub.
But let me is it necessary that I should update everytime to new kernel that is released.Can I stick to the default kernel which is there during UBUNTU release??
If i keep updating kernel then it will increase in disc space???:(

Thanks in advance

---

### Post by floke on 2007-10-11
You can delete them in synaptic - it'll warn you if you try to remove any kernel parts you're using - so you can't screw it up.

** EDIT - yes disc usage will increase - and you can stick to your old kernel - simply mark it in synaptic as not upgradable

---

