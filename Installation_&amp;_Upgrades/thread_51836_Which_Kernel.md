---
title: "Which Kernel??"
date: 2005-07-25
forum: Installation &amp; Upgrades
---

### Post by jones_jj on 2005-07-25
I am installing Ubuntu in expert mode and I was wondering if anyone could tell me which kernel I should use.  I have 3 choices:

1. linux-386
2. linux-image-386
3. linux-image-2.6.10-5-386

Any help would be greatly appreciated.

Thanks

---

### Post by jasmuz on 2005-07-25
[QUOTE=jones_jj]I am installing Ubuntu in expert mode and I was wondering if anyone could tell me which kernel I should use.  I have 3 choices:

1. linux-386
2. linux-image-386
3. linux-image-2.6.10-5-386

Any help would be greatly appreciated.

Thanks[/QUOTE]
 linux-image-2.6.10-5-386

---

### Post by jones_jj on 2005-07-25
Thanks.  What are the other kernel versions for?

---

### Post by jasmuz on 2005-07-27
They are the same if you are installing from the Hoary Hedgehog CD.  But people making the install usually get confused when they have multiple options at anything.

---

### Post by az on 2005-07-27
[QUOTE=jones_jj]Thanks.  What are the other kernel versions for?[/QUOTE]


Actually, you should install the linux-image-386 package.


Actually, you shouldn't use the expert mode unless you have a hardware problem.  There is no advantage.  You end up with _less_, not more.

The linux-image-386 points to the latest version of the 386 kernel.  So if you only install the linux-image-2.6.10-5-386 package and there is a kernel security vulnerability, you will not get an upgraded package.

Any linux-image package provides linux-386 which is a dependancy for some other package.

---

### Post by jones_jj on 2005-07-27
[QUOTE=azz]Actually, you should install the linux-image-386 package.


Actually, you shouldn't use the expert mode unless you have a hardware problem.  There is no advantage.  You end up with _less_, not more.
[/QUOTE]


Just curious azz, but why do you keep insisting on not using the expert install mode?  You say it's only for issues when using the default install mode.  I have read the readme's on the different install types and they if you want full control of your install use the expert mode.  I want full and total control so I used the expert mode.  It gave me options that were hidden by using the default mode.  I am by far not a noobie when it comes to install Linux.

I'm not trying to start anything I'm just very curious why you keep saying the expert mode is bad and don't use.

---

### Post by az on 2005-07-27
Because expert mode is bad and don't use it.

Seriously, if you want to learn about ubuntu or debian you are far better off installing it properly and then tweaking it.  The expert mode really can only make you end up with *less* of a system than more.  Unless, of course, the installer fails because of some hardware issues that you have to work around "by hand".  In that case, it would be the only way to circumvent some issues.

If you want to really grok the installer, download the Woody installer.  Debian Woody was the last stable debian distribution and it's installer is a lot like  the Ubuntu installer in expert mode.  In fact, it is just enough friendlier that you may avoid breaking things.

Having been there and done that, what you are doing is inflicting a bunch of pain onto yourself with the educational payoff being almost nothing.  Trust me.  All pain, no gain.

This is not about avoiding full control.  I would suggest you spend the time you would popping the cd in and out of the drive by reading all the comments in /etc if full control is what you want.  I am not being cocky and telling you RTFM, I am telling you that there is nothing much there that you cannot learn elsewhere a lot more successfuly.

---

### Post by jones_jj on 2005-07-27
azz-

Thanks for telling me why not to use the expert mode.  I really appreciate it.  The only problem that I ever came across was my username was not in the sudoers file, and I just had to do a quick fix on that.  But beyond that everything else works just fine with the expert mode.  The next time I do a Ubuntu or a Kubuntu install I will have to try it the old vanilla way and do it as a default install.

Thanks again and I enjoy finding out why people do an install a certain way not another.

---

### Post by az on 2005-07-27
Actually, the next time you install, try installing Debian Woody and then dist-upgrading to Ubuntu or Kubuntu.

I said the Woody install is more friendly, actually, it is not really.  They whole system is simpler.  For example, it has a plain ol dev system.  No devfs, no udev.  Nothing to break.  It is just there.

You have to do everyting by hand.  You need to partition beforehand if you want to keep data on your system from another OS.  You have to load all the kernel modules by hand.  You probably would need to get the source for a wireless cand and compile the module and then configure it before you could go on the net...

Just use the bf2.4 kernel.  Avoid the default 2.2 kernel.  You do not want to experience _that_ much pain.

---

### Post by jones_jj on 2005-07-27
Isn't experiencing pain what it means to be in IT?  No pain no gain...haha

---

### Post by az on 2005-07-28
That's only what you tell the boss.

---

### Post by jones_jj on 2005-07-28
[QUOTE=azz]That's only what you tell the boss.[/QUOTE]


HAHAHA yea I guess you're right on that one  :wink:

---

