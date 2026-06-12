---
title: "VMware Tool Install Kills Ubuntu"
date: 2007-01-04
forum: Installation &amp; Upgrades
---

### Post by jfourie on 2007-01-04
Hi There

I am running Ubuntu Edgy in the latest VMWare Server downloaded in the past week. When I install the VMware tools and reboot the startup runs up to about 80% on the progress bar. The CD spins once and then the startup gets stuck with a line accross the screen. (It looks like it is trying to change video modes) I am running the latest upgraded Ubuntu with Kernel 1.6.17. I have also installed the latest headers and the build essentials before running the vmware tools install. The install ran perfectly and installed without any errors except for having to rebuild the kernel (or something like that) at the end of the install. Everything works untill the reboot and then all gets stuck there. I fortunately made a snapshot before the install so I was able to recover my system to the atate it was in before the VM Tools install. Any Ideas on why this is happening and how I can get the VMWare tools working?

Thanks
Johan

---

### Post by AaronD on 2007-01-07
Hello all - I just wanted to say I am having the exact same problem.  I am using VMWare Workstation 5.5.3 on XP and I am trying to load Ubuntu Desktop 6.10.  I can load the OS and load the VMWare Tools as long as I choose 800x600 resolution.  If I choose 1024x768 during the VMWare Tools install, I get the same symptoms.  Thanks!

Aaron

---

### Post by riven0 on 2007-01-07
jfourie said everything worked fine *except* for rebuilding the kernel headers? That'll definitely bork up the Ubuntu install unless you have a fallback kernel. 

Hopefully someone more knowledgeable will come in and post the solution...

---

### Post by jfourie on 2007-01-08
I am also selecting 1024 x 768 as my resolution when it fails. So it seems it does have something to do with resolution....

---

### Post by AaronD on 2007-01-08
I am going to play with it some more today.  I can run the Ubunutu VM in 800x600 so that is what I am doing for now.  I am taking snap shots along the way and making an off line copy of the VM before every step so I won't lose too much time.

Up until this experiment I am a Windows guy so I have no idea how to troubleshoot this or recover.  I just go back to the last snap shot and try something different.

I am going to try these instructions today to see if this works a little better.  Updates to follow.

Aaron

---

### Post by AaronD on 2007-01-10
I haven't had a chance to try it because of work projects.  It will be a few more days until I find time to play again.  I have an idea how to possibly make it work.  More later...

---

### Post by jfourie on 2007-01-15
Please Do! It seems more people might be having this problem if I look at how many times this thread has been viewed. I hope your idea works!

---

### Post by AaronD on 2007-03-19
Hello - Well, I solved the problem, but in a different way.  On a hunch I downloaded the VMWare Workstation 6 Beta and I extracted the VMWare Tools from that build and loaded them on the VM and it works!

I now have 1024x768 resolution and a seamless mouse.

The details are a little difficult as to how I got it all going so let me know if you are still stuck and I will try to put something together.

Thanks!

Aaron

---

