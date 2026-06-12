---
title: "Minimal install to USB HDD"
date: 2010-12-28
forum: Installation &amp; Upgrades
---

### Post by pumkinut on 2010-12-28
I'm trying to figure out how to perform a minimal install to a USB attached hard drive.  A full install works just fine, when I start the install from the LiveCD desktop, all the USB drives are visible and can be installed to. In the minimal install, the requisite kernel modules for USB storage don't seem to be loaded, therefore, my USB hard drive is not visible and cannot be mounted, partitioned, or installed to.

The reason behind this is I'm trying to build an XBMC install on a USB hard drive and want only the minimum backend OS that's necessary as some of the Ubuntu desktop software causes issues with some of the XBMC software.  I've posted on the XBMC boards about this, but my questions have gone completely unanswered, so I'm looking here for some help.  Thanks.

---

### Post by Herman on 2010-12-29
I think you need to use the Ubuntu 'Alternate Installation' CD, rather than the 'Desktop'.

Here's a link to the best website I know of about how to perform a minimal install, [Modest Specs]("http://www.psychocats.net/ubuntu/minimal") - by aysiu, who is one of the moderators here at Ubuntu Web Forums.

I always thought the minimal install just meant minimal software, I didn't know it affected the kernel and initrd.img as well.  

I haven't tried a minimal install in a USB myself, so I'm not really sure if it will make any difference which CD you use, I didn't know it was possible to perform a minimal install with the Desktop CD. :)

---

### Post by pumkinut on 2010-12-29
Thanks for the info, I'll do some reading and give it a shot.  As far as a minimal install with the Desktop CD, I wasn't really expecting it to, it's just that the Desktop LiveCD is the only one that will recognize an external HDD due to all the USB modules beaing loaded by initrd.  Every minimal install method/disk I've played with doesn't load all of the USB modules.

---

### Post by pumkinut on 2010-12-29
I just looked at the link provided.  The minimal install CD that the page uses is what I've already tried, and it does not work.

---

### Post by Herman on 2010-12-29
:-k Hmm.
Well I read that in this page, 
[Ubuntu Documentation]("https://help.ubuntu.com/") > [Ubuntu 10.04]("https://help.ubuntu.com/10.04") > [Ubuntu Installation Guide]("https://help.ubuntu.com/10.04/installation-guide/i386/index.html") > [Using the Ubuntu Installer]("https://help.ubuntu.com/10.04/installation-guide/i386/d-i-intro.html") > [Using Individual Components]("https://help.ubuntu.com/10.04/installation-guide/i386/module-details.html"), under 'Installing the Base System', that 

> As part of the installation, a Linux kernel will be installed. At the default priority, the installer will choose one for you that best matches your hardware. In lower priority modes, you will be able to choose from a list of available kernels.So with that information it would appear as though you are probably correct and I'm wrong.

I'm installing Ubuntu in a RAID array at the moment and I have one of my hard drives for the RAID array pluged in by USB because the 'Alternate Installation CD wouldn't work when the CD drive was plugged in by an IDE/USB adapter. It works for me but I'm not doing a minimal install. It's not working for you apparently because of the different kernel version the installer wants to give you. I have just learned something. 

I don't know if there a way you can force the installer to use a different kernel. If I find out I'll let you know, it should be possible. 

For now all I can suggest is to try installing anyway, and then chroot into the install from your Live CD and try installing a different kernel.
Here's a link to my favorite way to chroot, [How to chroot]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#chroot"). I hope that helps.

---

### Post by Herman on 2010-12-29
> In the minimal install, the requisite kernel modules for USB storage  don't seem to be loaded, therefore, my USB hard drive is not visible and  cannot be mounted, partitioned, or installed to.#-o Oh, okay, sorry, I just re-read your original post.

In that case you might need to perform a full install and then remove software from it to strip it down to meet your needs I guess. 

Sorry to be occupying your thread and not being able to be more help.
I didn't know there were a few things I didn't know, and now I'm aware I don't know as much as I thought I knew. :oops:

---

### Post by Herman on 2010-12-29
You could try pressing F1 for help at the boot screen of the 'Alternate Installation CD' to see if you can find out how to boot the installer in 'Expert Mode'. That will ask you a lot more questions and give you a lot more choices than a regular install. It will be more work and take longer but it might help you. It's such a long time since I tried expert mode I have forgotten if there's any choice about what kernel to use. 

I can also tell you that trying to install with /boot in RAID1 and /root in RAID5 with the Ubuntu Maverick Meerkat's 'Alternate Installation CD keeps failing on 'select and install software', resulting in a nice minimal installation that boots to a bare command-line only system. Too bad it's not what I'm trying to achieve right now. (LOL). :)

---

### Post by Herman on 2010-12-29
Some people are comfortable with the idea of handling computer hardware while others are not so hardware oriented.

Can you remove the USB external HDD from its case and put it inside your computer?

I would not recommend anyone touching computer hardware unless they know what they're doing and have the right tools and training. In some computers it's easier to change hard disk drives than others, depending on the case design.

EDIT: Then put it back in the USB external drive case when you're done.

---

### Post by pumkinut on 2010-12-29
> **Herman said:**
> Some people are comfortable with the idea of handling computer hardware while others are not so hardware oriented.

Can you remove the USB external HDD from its case and put it inside your computer?

I would not recommend anyone touching computer hardware unless they know what they're doing and have the right tools and training. In some computers it's easier to change hard disk drives than others, depending on the case design.

EDIT: Then put it back in the USB external drive case when you're done.
That's an idea I might try, hadn't thought of that.  I have an old PC in my garage that I use as a test box.  The thing is, the USB drive is a 2.5 inch laptop drive, I need to see if I still have an adapter to have it work with a regular PATA cable.

---

