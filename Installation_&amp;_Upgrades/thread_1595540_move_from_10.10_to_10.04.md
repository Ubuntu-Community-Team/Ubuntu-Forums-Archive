---
title: "move from 10.10 to 10.04"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by md10 on 2010-10-13
Is there a way to easy go back to 10.04? After upgrade my vmware wkst 7 does not work and I really need it, tried all solutions/scripts... no luck. 

thanks!

---

### Post by pmlxuser on 2010-10-13
in as much as i know, OS tend to be + sided and not -, ie easy to upgrade than down grade. for the task you are seeking easiest if you have a separate data partition is doing a clean install with 10.04...

---

### Post by lukeiamyourfather on 2010-10-13
From my understanding of it, the upgrade path is one way. Reverting back to 10.04 would require installing it again. If using the system as a workstation I'd suggest sticking with 10.04 anyway because 10.04 is a LTS release.

---

### Post by mörgæs on 2010-10-13
Yes, a new install is the way to go, if you want 10.04. 

If 10.10 did not work well when upgraded online, you could also to try a fresh install of this one.

---

### Post by timefly on 2010-10-13
> **md10 said:**
> Is there a way to easy go back to 10.04? After upgrade my vmware wkst 7 does not work and I really need it, tried all solutions/scripts... no luck. 

thanks!

I know of no operating system that allows you to truly downgrade, but if you still have older kernel versions installed, then you can boot with an older kernel at least. This may or may not help you, depending on the reasons why you want to downgrade, but in case it's something you want to try, this is how:

By default (at least on my installation) the boot manager, grub, quietly picks the most recently installed (or most recently used?) kernel. To get it to pause, show you all the available kernels, and let you pick one, you'll have to modify the system file /etc/default/grub and comment out (with a # at the start of each line) the two entries dealing with a *hidden* timeout.

Then, regenerate from that file the actual grub config being used by grub (execute "sudo update-grub") and restart the computer.

Caveat: Some installed libraries or other software may depend on features in the kernel and could misbehave or fail outright if you boot with a kernel that's too old. YMMV.

---

### Post by Mark Phelps on 2010-10-13
> **timefly said:**
> I know of no operating system that allows you to truly downgrade ...

Not picking a fight here, but since the intro of Vista, and now Win7, BOTH of these OSs provide exactly that capability as part of an in-place "upgrade".

They squirrel off the old OS-related stuff into an archive, store that in a folder (known as windows.old), and provide the ability to completely restore that information from that folder.

For those interested, the details on HOW to do this are contained in the following MS technote:  

[http://support.microsoft.com/kb/933168]("http://support.microsoft.com/kb/933168")

It would be REALLY NICE if Canonical would provide this SAME capability to save folks who have "upgraded" to 10.10, now have an unusable (or otherwise, undesirable) result, and want to roll-back to their previous, working perfectly, 10.04 setup.

---

### Post by libssd on 2010-10-13
I always cringe when I read a question like this. One of the few gripes I have about Canonical is that they do not give enough emphasis to the possibility of problems occurring, or to recovering from them. No matter how unlikely, disasters happen, and if you are doing something as critical as upgrading from one version of an OS to another, it is **your** responsibility to have a restorable system backup prior to upgrading or doing a fresh install. 

Remastersys is one tool that makes it relatively easy to backup your system, and then to re-install it back to its state when the backup was made. In the past 30 years, I have borked an uncountable number of systems, mostly Macintosh, some Linux, and backups have saved my sorry butt many, many times.

---

