---
title: "Installing LTS Hardware Enablement Stack in Lubuntu 14.04.2"
date: 2015-02-27
forum: Installation &amp; Upgrades
---

### Post by roler2 on 2015-02-27
I did a dist-upgrade from Lubuntu 14.04.1 to 14.04.2 yet the Kernel remained 3.13 although updated to 3.13.0-46.

Is it best to leave well enough alone? If not, what are the Terminal commands for installing the Stack in Lubuntu?

It's running just fine right now. I don't want to break anything, which I understand could happen with the Stack installation, especially with older hardware which is what I have.

Or is it best to attempt the installation? Does the 3.16 Kernel only apply to newer Computers? I have an old P4.

Please advise if possible. Thank you!

---

### Post by ajgreeny on 2015-02-27
If everything is working well with the 3.13 kernel and graphics software It is probably best to leave as it is.  The update to the newer hardware enablement stack is usually only of great use to you if you have newer hardware that needs the most up-to-date packages in order to work, eg graphics or wifi.

I have a new machine which would run the 14.04.2 version using the new enablement stack without a problem, but it also runs like a demon with the original 14.04 fully updated, so I am not changing anything.

"If it ain't broke, don't fix it; if you do fix it and break it, you get to keep the parts"

---

### Post by QIII on 2015-02-27
If you are using an AMD graphics adapter, don't use 14.04.2 just yet.  There are significant problems associated with installation of the proprietary driver at the moment.

Hopefully I'll get some action on my bug report soon.

---

### Post by mörgæs on 2015-02-27
Just guessing here, no hard facts:

As we are dealing with a Pentium 4 I don't think the graphics processor (if it is AMD) is new enough to use proprietary drivers, buggy or not. 

Open-source drivers in 14.04.2 are generally speaking in a good shape.

---

### Post by Rex Bouwense on 2015-02-27
I thought that the 3.16 kernel was for Lubuntu 14.10 and the 3.13 kernel was for 14.04.  At least that what I have since I have them both installed.

---

### Post by ptn107 on 2015-02-27
I upgraded a test virtual machine from 14.04.1 to 14.04.2 flawlessly.  I then installed the utopic HWE stack on the test machine successfully.  However, I went ahead on doing the same with two of my three production machines and both of them now boot to black screens.  I tried all kinds of kernel options at boot but so far no success.  I'm re-installing 14.04.1 on both of them tomorrow.

Be very cautious.  Make backups beforehand.

---

### Post by roler2 on 2015-02-27
Thank you for all of the wonderful advice! I think I will leave the OS as is. Everything is working just fine. I have a Pentium P4 with Intel video. I utilize XOrg drivers (I think that is what they are) with SNA activated which work quite well.

Also I believe that there has been a new Kernel released 3.19 but I am afraid to install that too.  [http://www.itworld.com/article/2881487/linux-kernel-3-19-released.html](http://www.itworld.com/article/2881487/linux-kernel-3-19-released.html)

Further, I attempted last year to do a release-upgrade to 14.10 three times and I also got black screens all three times.

So I am sticking with 14.04 which runs quite well, for me anyway.

The terminal result when entering lsb_release-a shows 14.04.2 so I suppose there was some upgrading completed other than the Stack and Kernel.

---

### Post by ajgreeny on 2015-02-28
Normal upgrades either using apt-get, update-manager or synaptic will not upgrade you to the newer hardware-enablement-stack, so you will not see the 3.16 kernel series suddenly appear.  You could install the 3.16 kernel manually if you want and if it does not play ball with your system, you would need to boot to a previous 3.13 kernel from grub and uninstall the 3.16 version.

That should not hurt your OS in any way, and as I say, is reversible very easily.

Your choice - - -?

---

### Post by v3.xx on 2015-02-28
The 3.13 kernel is supported for the life of 14.04, the other kernels will need to be upgraded every six months.

---

### Post by deadflowr on 2015-02-28
> **v3.xx said:**
> The 3.13 kernel is supported for the life of 14.04, the other kernels will need to be upgraded every six months.

If like precise the other kernels will all be supported until 16.04.1 comes out sometime in August 2016.

---

### Post by roler2 on 2015-03-01
Well. . .I was thinking about it. However, when I actually inputted the correct info into the Terminal to install the Stack. . .all of a sudden. . .almost everything I had already installed was going to be automatically removed. . .this includes additional Programs I manually installed. . it gave me a complete list. . .and some core features, especially video drivers and other important attributes. . .so I cancelled the entire install. . .seems almost like it was going to be a completely new install where I would have to reinstall everything all over again. . .

---

### Post by roler2 on 2015-03-04
OK I have a question. Or I guess it is two. . .

By _not_ installing the Hardware Enablement Stack, will I still be able to install upgrades and distribution upgrades via the Terminal Commands without having to reinstall everything from scratch via an updated CD or DVD? In other words, will I have to go ahead and upgrade the Stack in order to install any future distribution upgrades via the Terminal commands, such as when 14.04.3 is made available?

---

### Post by deadflowr on 2015-03-04
> **roler2 said:**
> OK I have a question. Or I guess it is two. . .

By _not_ installing the Hardware Enablement Stack, will I still be able to install upgrades and distribution upgrades via the Terminal Commands without having to reinstall everything from scratch via an updated CD or DVD? In other words, will I have to go ahead and upgrade the Stack in order to install any future distribution upgrades via the Terminal commands, such as when 14.04.3 is made available?
No
There is no need to install or upgrade the hardware stack in order to keep getting updates.
Point Releases are a culmination of updates, regardless of HWE.
14.04.2 is a culmination of updates and bug-fixes that have come since 14.04.1, which was a culmination of updates and bug-fixes since the initial release of 14.04.
And 14.04.3 will be a culmination of updates and bug-fixes since 14.04.2, and so forth.

If you keep your system always up-to-date, when 14.04.3 comes, you will get it; smoothly and without notice.
Point release installs are a snapshot of all those updates.

I think the confusion comes with the inclusion of the new HWE on the install media.
But that's simply to let newer machines/hardware get better (or even any at all) support for a current LTS.
(Otherwise they'd probably have to run a normal, and much shorter, release until the next LTS comes out.

Hope that makes sense.

---

### Post by roler2 on 2015-03-07
Thank you for your insight. I think I will keep things as is and not install the Stack. I have an old P4 so it is probably just as well.

Now, hopefully, the Kernel will be fixed so when you boot up you can both hide the Splash Screen and hide the Boot Messages just like you were able to do in 13.10. Right now if you hide the Spash Screen you will get a lot of Boot Messages. The only way to hide the Boot Messages is to keep the Spash Screen. In fact I have heard that some are not even able to boot if they hide the Splash Screen in 14.04 or they receive a Kernel Panic error.

---

