---
title: "Canceled 11.4 Upgrade and now I can't boot"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by scuba617 on 2011-05-02
I was in the middle of upgrading to 11.4 (in the update packages step) and I had to shutdown to move my computer. I cancelled the upgrade process and it completed reverting back to it's previous state and then shutdown.

I just tried booting it back up to complete the update but now it won't boot. It is unable to mount my file system. I am currently running from a 10.10 live CD and I still cannot access my file system. Is there any way for me to either get back to 10.10 and keep all my files or upgrade to 11.4 and keep all my files or should I just reformat the partition and install a clean version of 11.4 from a CD? I'm still relatively new to Linux so if there's any information that I should provide to help find a solution, provide just let me know.

---

### Post by alexend on 2011-05-02
If You Reinstall, It Will Keep Your Files And Settings and Apps! Just Select Upgrade on 11.04 Boot Cd or USB.

---

### Post by scuba617 on 2011-05-02
I've started the upgrade using the live CD. part way through the package update step it gave me a notification that it was unable to mount one of my partitions (the same one from before). Hopefully I am able to boot from my HD after this update is done. I will reply again with the outcome of this.

---

### Post by scuba617 on 2011-05-02
Well, the install froze, exploring other options at the moment. Let me know if anyone has any input as to what may be causing the issue with not being able to mount my file system.

---

### Post by Hedgehog1 on 2011-05-02
We need to get a look at your partitions.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by scuba617 on 2011-05-03
Should it be running fast? Because it's stopped on "searching sda2 for information".

---

### Post by Hedgehog1 on 2011-05-03
It should have finished in under 15 seconds.

This may be an indicator of how damaged the data in /dev/sda2 is.

If it doesn't come back soon, please run gparted on that disk and post a screen shot. You can use FireFox from the LiveCD/LiveUSB to post it (you may already be doing this).

**EDIT:** ALSO, please check the SMART status of that drive using the Disk Utility.

***The Hedge***

:KS

---

### Post by scuba617 on 2011-05-03
How do I run gparted on that disk?

The result from the SMART Check was [COLOR=SeaGreen]Good[/COLOR] or N/A on everything except a [COLOR=Red]Warning[/COLOR] on the Reallocated Sector Count.

Figured out gparted, this was what happened...

ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...

---

### Post by Hedgehog1 on 2011-05-03
Gparted is right below the disk utilities in the menu from the LiveCD/LiveUSB.

Run it and select the drive you are working on in the upper right hand corner.  Don't change anything, just get a screen shot.

The sector count warning is not a good thing - depending on where the bad sectors happen to fall is ***might*** be the cause of this.

Is this system a dual-boot with windows?

***The Hedge***

:KS

---

### Post by scuba617 on 2011-05-03
Gparted won't even start from System >> Administration >> Gparted Partition Editor. It tries to start then nothing happens.

And yes, it is a dual boot with Windows XP

---

### Post by Hedgehog1 on 2011-05-03
Are you running off a CD - or a USB?  There was a bug with running gparted on some brands of USB (I know it sound crazy, but it was really happening)

---

### Post by scuba617 on 2011-05-03
Nope, it's a 10.10 Live CD.

---

### Post by Hedgehog1 on 2011-05-03
Well, that may indicate a bad burn of the CD or a damaged ISO.

Hey - I have to shut down here.  Bed time and all...

Hopefully other forum member can pick up from here...


***The 'sleepy' Hedge***

---

### Post by scuba617 on 2011-05-03
Thanks Hedge, Sleep well. I'm going to switch to windows so I can burn an 11.4 CD from an iso I have and try an install from that. I don't have much hope for it but it's worth a shot. I'll still be checking the forums. 

Quick thought, could the problem with the script freezing be because I have my windows partition hibernated?

---

### Post by scuba617 on 2011-05-03
So, I burned the 11.04 CD and tried to "update" from 10.10 to 11.4 in the hopes that I wouldn't lose all my files by choosing that option. No such luck. Lost everything.

At least all my code is stored on github so it's not a total loss. I'll mark it as solved cause there's nothing left to do but reinstall everything and get all my files back. Still probably the most smooth update process I have ever had with Ubuntu as it usually takes about 3 days to even be able to start my computer again after trying to update (I have a lot of bad luck on upgrade days).

Thanks for taking the time to try and help me out Hedge, I really appreciate it. Just wish I wouldn't have lost all my files again.

---

