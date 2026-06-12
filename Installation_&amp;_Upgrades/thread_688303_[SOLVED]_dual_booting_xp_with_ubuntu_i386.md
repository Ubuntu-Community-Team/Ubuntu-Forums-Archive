---
title: "[SOLVED] dual booting xp with ubuntu i386"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by famous3warriors on 2008-02-05
I apologize early cause I am new to Ubuntu and its applications.  I really love ubuntu i386 gutsy. I really would like to get rid of win xp sp 2 but I need to run certain applications I need for work and school.  I have a hp pavilion dv9000 amd 64 x2 and a 120 gig hd.  When I loaded gusty onto my computer I completely removed xp.  I know the question has got answered before but I cant find the thread on how to dual boot with a single hd.  I found dual booting with two hard drives but not with a single one yet.  I also have an external hd that is 80 gig hd can I load windows into that so I can completely have my laptop with gutsy and the external with xp sp2 is that possible?  I really do appreciate you help.  Thanks.   


P.S.  A step by step would really help.

---

### Post by lswest on 2008-02-05
a useful link i find is this: [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp")
also, what programs do you need to run in XP? some of them can easily be run with wine, or, if they don't need all that many resources, you can run them in a virtual machine.  Otherwise, i haven't heard of running XP off an external hard drive, but i could be wrong.

---

### Post by zvacet on 2008-02-05
[Here](http://www.psychocats.net/ubuntu/installing) is guide you are looking for.

---

### Post by hums07 on 2008-02-05
> **lswest said:**
>  if they don't need all that many resources, you can run them in a virtual machine. 
That's right, use virtual machine. I install WinXP inside VirtualBox. Easy to install. That way, you can switch between the two OS instantly. Your computer needs to have a large RAM tho, 512 MB is minimal, 1GB will be great.

---

### Post by Mark Phelps on 2008-02-05
You say that when you loaded Ubuntu, you completely removed XP.  You sure? Or, did you just overwrite the MBR so that you were only able to boot into Ubuntu?

Before you try to load XP into a virtual machine, read over the links provided to set up the parms you need in Menu.lst to enable multi-boot.  Unless you really did wipe XP, you may be pleased to find out that it's still there and fully functional.

As to using Wine, as they say, your mileage may vary...  I've tried over a dozen apps in Wine and have had absolutely NO success!  About half of them will not even complete the installation.  The remainder either fail during startup, or crash shortly thereafter.  IMHO, don't see the value in spending hours and hours trying to tweak Wine to work when, with either dual-boot, or Virtualization, I can get a true Windows environment in which the apps WILL work.  But as I said, that's just my opinion.

---

### Post by famous3warriors on 2008-02-06
Thanks guys for all your help.  I am just going to live with ubuntu and try to figue things out little by little.  I use adobe cs2 and autocadd 2006.

---

