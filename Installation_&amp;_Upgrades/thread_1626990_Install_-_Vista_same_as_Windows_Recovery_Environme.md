---
title: "Install - Vista same as Windows Recovery Environment?"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by BatteryBrains on 2010-11-20
Just had a noob question...I tried googling it but couldn't find an answer...

I am wanting to dual-boot Ubuntu 10.10 and Vista (already installed)...

But when I get to the step to "Allocate Drive Space", I have two options:

One for Ubuntu, and the other for Windows Recovery Environment...

Is this right? Will I be dual-booting if I press install now? Is it just being picked up as a different name? I don't want to nuke anything.

I attached a screenshot...hopefully it works.

Thank you for your time.

---

### Post by mörgæs on 2010-11-21
It is best to defragment Windows a few times and after that free some space from within Windows. 

After that you can install Ubuntu in the free space.

---

### Post by BatteryBrains on 2010-11-21
> **mörgæs said:**
> It is best to defragment Windows a few times and after that free some space from within Windows. 

After that you can install Ubuntu in the free space.


Ok thanks, I'll go ahead and run a defrag...but to clarifiy, "Windows Recovery Environment" is the same as vista, and if I install Ubuntu, as per my screenshot, I will be able to keep Vista, yes?


I appreciate the response.

---

### Post by Mark Phelps on 2010-11-21
> **BatteryBrains said:**
> Ok thanks, I'll go ahead and run a defrag...but to clarifiy, "Windows Recovery Environment" is the same as vista, and if I install Ubuntu, as per my screenshot, I will be able to keep Vista, yes?


I appreciate the response.

Probably ... NOT.

Do NOT rely on the installer to (1) properly read the partitions on your drive, and (2) NOT wipe out work you really need to keep.

For reasons no one wants to address here, the latest version of the installer goes out of its way to be confusing, with YOU taking all the risk of wiping out your existing Windows install if a mistake or error in judgement is made.

The Recovery Environment is MOST likely to be a partition containing a restore image of Vista -- if your PC came preloaded with Vista when you bought it. IF you wipe that, and you have no alternate Vista image, and anything happens to your current install -- you'll be without ANY way to restore Vista to your PC. Period.

The safest thing to do is the following:
1) Use the Vista builtin Disk Mangement utility to shrink the Vista OS partition to make room for Ubuntu.
2) Boot into Vista a couple of times after this to ensure you can still boot OK.
3) Go to the Macrium Reflect website, download and install the Free edition.  Run that, selecting the option to create a Boot disk.
4) using Macrium Reflect, back off an image of your Vista OS partition to another drive, preferrably an external drive.
5) Goto the link below, download and burn the proper Vista Repair CD:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

NOW ... When you boot from the Ubuntu CD and run the installer, be VERY CAREFUL where you choose to install.  At least now, should you make a mistake, you'll be able to recover your Vista OS installation.

---

### Post by BatteryBrains on 2010-11-21
Thanks for the warning and detailed instruction...I'll give it a shot :)

---

