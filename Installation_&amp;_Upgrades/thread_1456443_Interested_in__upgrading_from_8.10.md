---
title: "Interested in  upgrading from 8.10"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by SVEN1 on 2010-04-17
Looks like the next step is to 9.04.Then to...

So if I upgrade, everything that is already installed will still be there and work? What about Virtualbox will it still run in 9.04?

Also, would upgrading from update manger possible get my DVD drive to burn discs?
Right now I cannot back up onto a CD or DVD.

I would like to move up to 10.10 eventually.

---

### Post by amsterdamharu on 2010-04-17
Hi Sven,

Ubuntu 10 (lucud) will be out in 12 days, if you have fast internet you can download the iso and try it. I always use untetbootin and stick it on a usb drive (1 GB will do).

Then try out the live cd mode and see if there are any hardware troubles. When it's running from a usb (or unetbootin to harddisk) then you can use your CD/DVD to see if it works.

Last Lucid I've tried was 2 months ago, Virtualbox worked fine on that. Now trying out mint 8, this one is based on Ubuntu 9.10 (Karmic) and it works fine for me on both computers. The live cd mode is good to see if there are any troubles with your hardware. Mint detected my videocard and installed drivers for it. It had my wireless working without a problem.

For many people it doesn't work that easy so it's a good idea to try it out and see if any problems can be fixed before installing it. If you have an older computer with not so much memory maybe you can do a normal install (reserve about 8GB for it) work on that for a couple of days and see if everything works ok.

---

### Post by Greg Xix on 2010-04-17
Not to hijack the thread, but I have never liked untetbootin.

Here is how I do it with 1GB flash

1. Download the ISO of the Ubuntu you want 9.04, 9.10, or 10.04

2. Go to System > Administration > USB Startup Disk Creator

3. In the top white box, locate where you downloaded the ISO

4. Format the flash listed in the lower white box

5. I usually select Discarded on Shutdown button

6. Click Make Starup Disk


Now you should have a a bootable Live USB. As long as your motherboard is set for USB Booting.

---

### Post by howefield on 2010-04-17
To get to 10.10, you will need to upgrade to each edition in turn 8.10 > 9.04 > 9.10 > 10.04 > 10.10

A lot of work and time, and potential for something to go wrong.

To answer your question though, yes all your current applications and settings should work and still be there. As always, before doing something like this backup everything you wouldn't want to lose before starting.

Virtualbox should still work, although you may be prompted to install a newer version of guest additions if you are currently using them.

It may help you burn to a CD/DVD, however you should be able to do that now, so the issue may not be with Ubuntu, but as each edition has incrementally better hardware support and software is updated to newer versions, you have a better chance of it working.

If it were me, I'd backup my files and do a clean install with 10.04, (after it is released) taking the opportunity to install with a separate /home if you don't already have that set up.

---

