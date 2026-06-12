---
title: "Multiple OS Configuration Needed - Install Suggestions Requested"
date: 2018-07-26
forum: Installation &amp; Upgrades
---

### Post by vector3 on 2018-07-26
I recently learned of some software I need for work that was developed for W95/W98/W3.1.  My laptop currently features Win7 Pro yet, I had planned to install Ubuntu on it for some time.  However, now that I need to install and additional MSOS I wonder if this additional burden suggests I take an different path with my laptop (ThinkPad X201, 2.67 GHz Intel M560 i5, 8 GB RAM, 64-bit OS, 300 GB Hitachi HD).

I have prior experience performing similar actions on smaller Atom laptops and the distribution I used at the time(i.e., Bohdi) made this easy during installation (after Windows).  Will Ubuntu act in a similar manner during the install? Given my current needs, should I consider a more compact distribution?

---

### Post by TheFu on 2018-07-27
Make a full system backup and try it.  Have you considered using virtual machines?  An i5  has plenty of CPU to make most programs run fine. The only trouble would be with high-end GPU programs and games. Office applications work nicely.

---

### Post by vector3 on 2018-07-27
Not until you mentioned this to be an option.  I know of these (e.g. VMWare) yet, have never needed to consider this for my own use.  Are you referring to any particular application?  Solid, known good software is best followed closely by freeware if feasible.

---

### Post by TheFu on 2018-07-27
You really are new.  On Linux, it is highly unusual NOT to use F/LOSS software.  Commercial software isn't really used, especially by end-users.  The F/LOSS tools are usually better or the basis for commercial tools.  

For desktop-on-desktop, the most popular F/LOSS choice is virtualbox.  Use a PPA to install it.
I would avoid VMware anything.  My company used to deploy using ESX and ESXi, but that all changed when VMware management decided to screw around with their pricing.  These days, the commercial solutions aren't actually better than the F/LOSS answers.

If you want more capabilities, stability and better performance at the cost a little more complexity, KVM+QEMU is built as part of the Linux kernel.  This is the same technology used by Amazon, NASA, Linode and others.  It is enterprise scale or 1 computer ready.

But most non-technical people should probably start with virtualbox.

You will need legal licenses for whatever OS you want to run inside the virtual machine. Nothing can change that requirement ... er ... except using a F/LOSS OS instead of a commercial one.

---

