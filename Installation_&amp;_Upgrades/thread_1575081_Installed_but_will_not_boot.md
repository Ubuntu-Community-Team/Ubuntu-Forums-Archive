---
title: "Installed but will not boot"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by Tim Marriott on 2010-09-15
I have just followed the procedure to install Ubuntu in VirtualBox on a host running Windows 7 Professional.  The install went smoothly and I seemed to have full capability within the Ubuntu VM.  
 
I then closed down Ubuntu and VirtualBox and came back later.  But when I try to start the Ubuntu VM I get "FATAL: No bootable medium found! System halted."
 
I have changed the Storage Settings so that the DVD/CD device is "empty".
 
I'm sure I've missed a simple step somewhere.

---

### Post by quixote on 2010-09-17
It does sound like you "installed" it to a drive that isn't there.  I did something like that once, and it's much easier to do than it should be.  Unfortunately, I don't remember exactly how I got myself in trouble.  I'm pretty sure I did select "Create new hard disk", which is right, but messed up later during that disk creation process.  One thing I do remember is that vbox populates the boxes that need to be filled in with whatever you used last, which generally is exactly what you *don't* want to enter.  I'm not sure any of this helps much.  I guess what I'm saying is just, "Try again." :D

---

