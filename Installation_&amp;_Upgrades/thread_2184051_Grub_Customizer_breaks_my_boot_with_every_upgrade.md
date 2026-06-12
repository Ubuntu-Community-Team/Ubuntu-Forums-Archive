---
title: "Grub Customizer breaks my boot with every upgrade"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by jlh68 on 2013-10-27
I am using Grub Customizer and when I upgrade the kernel the new entry is on the bottom of the list (In Grub Customizer) and when I move it to the top spot my unit will not boot after that.  I use a Rescutux flash drive to boot and change to a known bootable kernel, so I can use my computer..  

I don't understan why Grub Customizer does not put the newwst kernel in the top spot and make it bootable.  I am unsure about removing the old kernels as that often "breaks" the Grub.

Maybe the auhor of Grub Customizer knows what is going on?  Right now it is a PTA when I add a new linux kernel from Ubuntu. Maybe others know how to correct this problem.

My laptop is out of service, so the HDD has been relocated to my Netbook temporally until a new laptop motherboard arrives.

---

### Post by danielrichter on 2013-12-13
Hi, I'am the author. I've seen your question randomly ;).

> I don't understand why Grub Customizer does not put the newest kernel in the top spot

This depends on the position you put the "(new entries)" placeholders. When moving these placeholders to the top, new entries appear on the top. In your case this placeholder seems to be on the bottom.

> when I move it to the top spot my unit will not boot after that

Please update to Grub Customizer 4.0.x. I fixed some issues in this version. This could also fix your problem. If the problem still exists, please send this by mail here: [https://launchpad.net/~danielrichter2007/+contactuser](https://launchpad.net/~danielrichter2007/+contactuser) (why not here?: I need some files to reproduce the problem. However the first step is just sending the question by mail - on launchpad you cannot send the files directly).

---

### Post by jlh68 on 2013-12-13
Hi author (Daniel).  Thans for the reply.  Here is what I had aready done prior to your post.  Removed Gub Customizer, loaded Boot Repair, then repaired my boot.  Then I installed the latest version of Grub Customizer (4.0.1).  These two actions solved my problem.  

I like the new look in 4.0.1.  I tried enlarging my font, and I have not rebooted yet.  I hope it will work OK.  The original font was very tiny.

---

