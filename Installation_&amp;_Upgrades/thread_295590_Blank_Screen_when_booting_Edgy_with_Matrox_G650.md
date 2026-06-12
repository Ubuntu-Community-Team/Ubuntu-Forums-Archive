---
title: "Blank Screen when booting Edgy with Matrox G650"
date: 2006-11-08
forum: Installation &amp; Upgrades
---

### Post by Scrambler on 2006-11-08
Hello,

since upgrading to Edgy, my LCD screen connected to DVI on a Matrox G650 remains blank after having loading the kernel image. After GDM starts, I get some lines on the bottom of my screen but nothing to work with.

I have compiled and installed the newest MTX drivers and at least now, after GDM starts with that driver, the screen comes alive as it should with the correct resolution. So I guess it has something to do with the "normal" driver delivered with Edgy...

Does anybody know how to trick Edgy upon boot to use a display mode which supports the Matrox card whilst booting? Or perhaps which grub parameter I can use to force a text mode boot before starting the GDM?

Thanks for your help. Sincerely,

     Scrambler

---

### Post by nlp on 2006-11-08
Unfortunately, Matrox video card support is completely borked in Edgy at the moment.  See:

[http://ubuntuforums.org/showpost.php?p=1676815&postcount=5](http://ubuntuforums.org/showpost.php?p=1676815&postcount=5)
[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721](https://launchpad.net/distros/ubuntu/+source/xserver-xorg-video-mga/+bug/58721)

You could try installing pjssilva's user-created .deb to see if that solves your problem, or if you have a widescreen display that you need to get working, you should probably look at dmBriarwood's fixes, described here:

[http://ubuntuforums.org/showpost.php?p=1729666&postcount=2](http://ubuntuforums.org/showpost.php?p=1729666&postcount=2)

Personally, I'm holding off on upgrading to Edgy until this mess is cleaned up and there's an official fix for this in the Edgy repo's.

It amazes me that Edgy was released with a showstopper bug like this -- an entire manufacturer's line of video cards rendered unusable!  And it's not as though Matrox cards are uncommon on Linux systems -- they've traditionally had excellent driver support (that's why I bought my G400).  The bug report for this was posted TWO MONTHS prior to release, along with a user-supplied fix, yet no one even looked at it until Edgy was out the door.  wtf?

Did NO ONE test Edgy on a system with a Matrox card prior to release?  What does this say about the QA processes at Canonical/Ubuntu?

I'm sorely disappointed. :-(

---

### Post by Scrambler on 2006-11-09
Hi nlp,

thank you kindly for the input. I have gotten around the blank screen upon boot by removing the "splash" from grub.

BTW, the new MTX drivers work just great, using the newest Parhelia package:

[http://www.tuxx-home.at/projects/mtx/1.4.4/matroxdriver_mtx-x86_32-1.4.4.3-installer.run](http://www.tuxx-home.at/projects/mtx/1.4.4/matroxdriver_mtx-x86_32-1.4.4.3-installer.run)

What I am wondering is: When the kernel is loaded, Ubuntu goes to a graphic mode which does not actually seem to load the mtx driver that I've installed. The Matrox driver splash screen is displayed _after_ the boot process is over and the login window is displayed shortly thereafter. How does the internal use of X differ shortly after boot to the way it is used in my xorg settings?!

So at least, after being able to install the MTX drivers (via ssh) the system is usable albeit the fact that during boot the screen is blank :)

Sincerely,

    Scrambler

---

### Post by nlp on 2006-11-09
> **Scrambler said:**
> 
What I am wondering is: When the kernel is loaded, Ubuntu goes to a graphic mode which does not actually seem to load the mtx driver that I've installed. The Matrox driver splash screen is displayed _after_ the boot process is over and the login window is displayed shortly thereafter. How does the internal use of X differ shortly after boot to the way it is used in my xorg settings?!

Unfortunately, I don't know much about this, but my guess would be that Ubuntu is using the Linux framebuffer interface:

[http://en.wikipedia.org/wiki/Linux_framebuffer](http://en.wikipedia.org/wiki/Linux_framebuffer)

to draw the startup text and graphics, then loads X and thereby switches to a different driver and/or configuration.  It sounds like you've got the X driver configured and running properly, but the framebuffer settings are still messed up, which is why you can't see the system boot messages, etc.

I have no idea how you'd go about fixing this, however.  Maybe someone else here can suggest how to get the framebuffer working properly with your card (assuming that's the problem -- as I said, I know next to nothing about this...)

---

