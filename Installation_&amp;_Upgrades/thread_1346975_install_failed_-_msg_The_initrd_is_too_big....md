---
title: "install failed - msg The initrd is too big..."
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by Sethra on 2009-12-05
I have installed Ubuntu 9.10, then 9.04 and am stopped at the first boot with this message:
The initrd is too big...

How or where can I look to find out what this means?

If this refers to memory, I only installed 512MB because that is all I have right now.  If it needs more, I'll get it.

If not, this PC is assembled from gifted parts and pieces...  What does this message mean, and can I fix it?

Thanks,  Susan

---

### Post by Rodart on 2010-11-11
I know it's an old post, but I'm getting the same error here :(
I don't have " memory Hole" option, is there a way for solving this one?
Thanks!

---

### Post by sikander3786 on 2010-11-12
What are your hardware specs, RAM, graphics card etc.

Which version of Ubuntu are you using?

What is the exact error message?

---

### Post by Rodart on 2010-11-14
Well I installed ubuntu 10..10 first, I got this error
**kernel panic-not syncing VFS:unable to mount root fs on unknown-block(0,0)**

on the first boot, someone told me to try an older ubuntu It's working fine with gutsy but I can get any updaters for this one because they are not available anymore, so I have to update to 10.10 but I can't get past that error.... Can you help me?
thanks!.

Update: oops I forgot about the specs
it's an old computer from the year 2000
motherboard: m805lr
CPU: amd 700mhz duron Iguess
Ram: 486mb pc133 2 dimms
gpu: nvidia riva tnt2 32mb
7.10: no updates available
9.10- initrd is too big
10.10: error above

---

### Post by sikander3786 on 2010-11-14
700 MHZ and 486 MB is too low for regular Ubuntu.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

You better go for Lubuntu, an Ubuntu lightweight fork.

[http://lubuntu.org](http://lubuntu.org)

Or some other like PeppermintOS, Damn Small Linux, Puppy. You'll find many of them.

---

### Post by Rodart on 2010-11-14
uuummm, I was requesting help about the errors, Ubuntu works perfectly fine here... in fact I'm using 7.10 right now the only problem is that there's no more support for it so I can't install updates or drivers. I will try to update to 8.4 and so on until 10.10 I hope that works for some reason.

---

### Post by sikander3786 on 2010-11-14
Yep. I know you were talking about errors :-)

It might be working on that hardware but the performance will be real poor I believe.

Kernel panics, initrd is too big and those types of errors are being cause by your hardware believe me.

And since 7.10, Ubuntu has gone a long way up. New apps, new services and newer eye-candy makes it a bit more resource hungry.

I doubt if upgrade to 10.10 will work but you can still try that if you want to.

Any lightweight distro will better utilize your hardware, that was my point. I am not against the use of Ubuntu :P

---

### Post by Rodart on 2010-11-14
That's really sad to read, reminds me of windows vista...:( and M force updates.
The thing is that, I'm learning how to set up an http server for a webpage, and I had this tutorial but it's only for ubuntu, I guess I will try with DSL if I manage to install it somehow. 
THanks!!

I will try Lubuntu, apache and sql stuff still works the same? I mean if I can download them like in ubuntu.

Oh by the way, do you know how to boot from LAN? I have this netbook wich I want to install 10.10 into, but It doesn't have the usb boot option.

Thanks!

---

### Post by sikander3786 on 2010-11-15
> I will try Lubuntu, apache and sql stuff still works the same? I mean if I can download them like in ubuntu.

All the command line stuff will be the same. It is only the GUI that differs. You can use apache and sql as you'd have used with Ubuntu.

And this page lists many options for installation including network install.

[https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

---

### Post by Rodart on 2010-11-16
I will try lubuntu then ! thanks!

---

### Post by Rodart on 2010-11-27
Lubuntu failed too, as soons as I hit enter on the Install lubuntu option the PC restarts. Any other sugestion?.
Thanks.

---

### Post by sikander3786 on 2010-11-28
> **Rodart said:**
> Lubuntu failed too, as soons as I hit enter on the Install lubuntu option the PC restarts. Any other sugestion?.
Thanks.
Did you check the MD5SUM of the downloaded image and also check the disc for defects?

What if you choose the "Try without making any changes" option? Does it boot then?

You might need to put in some boot options like noacpi or apic=off by pressing the F6 key Welcome Screen. There are 6 options and you might need to try all of them one-by-one.

---

