---
title: "Boot from live CD, but install from USB?"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by crc294 on 2011-09-15
Ok guys, I have a strange one for you. My friend has an old, POS dell "slim desktop" that we're trying to install Ubuntu on. The keyboard (whether we use a USB keyboard or a PS2 keyboard) does not become enabled until after the OS starts to boot (read: can't get into the BIOS. Can't change the boot order. Can't select which boot device to use).

So, we are trying to install Ubuntu 10.04 from a Live CD (luckily, CD drive is first in the boot order). The CD drive barely works, but it is able to boot to the desktop environment after some effort. Once there, we can browse the net, etc without too much trouble. The trouble comes when trying to install: it fails halfway through, due to "disk errors" (even though the live CD was verified and has been used to successfully install Ubuntu on other computers). In other words, the CD drive is just not in good enough health to get us all the way through installation.

So my question is: can we boot into the desktop environment with the liveCD, then insert a USB stick and install Ubuntu from the stick? 

Once in the desktop environment, the computer will read a USB stick. I just don't know how to kick off installation from the USB stick when we didn't actually boot from it.

Any ideas?
Thanks,
Rob

---

### Post by mörgæs on 2011-09-15
If the CD drive can read only 15-20 MB successfully, then you can install a full Buntu using this:

[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by crc294 on 2011-09-15
Thanks morgaes ... I can try that if nothing else works, but the internet connection is not reliable enough to download hundreds of MB worth of packages after installing minimal. I really need to source the installation from a local USB stick.

---

### Post by oldfred on 2011-09-15
I might try this:

How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html](http://members.iinet.net.au/~herman546/p27.html)

There is the plop boot loader that lets you boot and then use USB. Not exactly sure how it works as I have not had to use it.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

Some other other things that I have not tried.
Use unetbootin to copy  iso to partition and install (example is window, but should also work with Ubuntu or any ISO:
[http://ubuntuforums.org/showthread.php?t=1480974](http://ubuntuforums.org/showthread.php?t=1480974)
You can also use unetbootin to boot a Ubuntu ISO from windows without the CD
Howto: Easy GRUB Bootloader Repair without external media -unetbootin & grub4dos
[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)

---

### Post by haqking on 2011-09-15
> **crc294 said:**
> Thanks morgaes ... I can try that if nothing else works, but the internet connection is not reliable enough to download hundreds of MB worth of packages after installing minimal. I really need to source the installation from a local USB stick.

Dodgy keyboard, dodgy CD-ROM, unreliable internet connection ?

Is it worth it ;-)

Is this a personal project or requirement ?

does it have a network card and do you have access to another machine, or can you swap out the CD Rom drive ? they are only cheap

---

### Post by MAFoElffen on 2011-09-15
> **oldfred said:**
> I might try this:

How to clean CD lens:
[http://members.iinet.net.au/~herman546/p27.html]("http://members.iinet.net.au/%7Eherman546/p27.html")

+1 on oldfred.

I've got a older dell laptop that was circa Windows NT 4.0... BIOS has it as booting from CD as an option, but it didn't come with a CD drive option and set set to boot Flooppy-CD-HDD. I have a CD Drive coming for it...In the meantime, I've tried to get around this-- ergo the advise to you.

Problem with the Dell BIOS on mine, is that it's old enough that the BIOS doesn't support booting from USB, even when booted and redirected from PLOP, Grub or other ways.  My older Dell doesn't even recognise USB mass storage in the BIOS, so I can't even copy files over from a USB drive or storage.

I think it's really worth getting the CD working again.

As for whom asked "why load Linux on old equipment?"  To breath new usable life to something that would other be...

---

### Post by mörgæs on 2011-09-16
No matter how you manage to install, you will need to download a bunch of updates afterwards. I doubt that you will get below 200 MB.

By the way, how much memory is in the computer?

---

### Post by haqking on 2011-09-16
> **MAFoElffen said:**
> 

As for whom asked "why load Linux on old equipment?"  To breath new usable life to something that would other be...


If you are referring to my post, i never said old equipment, i said equipment that was clearly not working.

Linux wont make a dodgy CD-rom work, or stabilise an unreliable Internet connection.

Linux is great for older hardware, but it works better if the hardware works ;-)

I just meant was it worth it as the hardware seemed on the way out, if its important it might be better to change some of the hardware thats all i meant.

---

### Post by coffeecat on 2011-09-16
@crc294, another option for you - so long as the old PC has enough RAM. Remove the hard drive from the old Dell, put it in a USB enclosure and plug this into a more reliable PC. Run the install CD from the reliable PC but install to the old HD in the USB enclosure. It doesn't matter if the reliable PC has different hardware, simply make sure you are running the 32-bit installer if the old PC has a 32-bit processor. You'll need to select the advanced option at the partitioning stage of the installer so that you can tell it to install grub to the mbr of the old HD. You don't want the installer to put grub in the mbr of the reliable PC's internal drive!

When you've finished, simply put the old HD back in the old PC and boot up.

If you don't have a USB enclosure to use, and the reliable PC is a desktop, then you could temporarily fit the old HD as a secondary drive, but be very, very careful where you install grub! Actually, it would be best to disconnect the reliable PC's own hard drive while you do the install, otherwise you'll get a grub menu with entries for any OSs on the reliable PC. 

You may have seen discussions in threads about migrating a hard drive from one machine to another with someone objecting that installing on one machine will prevent Ubuntu from booting on another. This is simply not so. I've done this myself, I've helped someone else do this on this forum successfully, and I've often migrated installs from one machine to another - successfuly. This is an old chestnut. Linux probes hardware on bootup and loads appropriate drivers. The only real issue is if you install a proprietary video driver. Also - the ethernet card will probably come out as eth1 on the old PC, but this is easily fixed with an edit of /etc/udev/rules.d/70-persistent-net.rules.

---

### Post by crc294 on 2011-09-16
Thanks for the suggestions everyone. Coffee - luckily, I do have one of those old enclosures that allows you to hook up a standard 3.5" HDD. I will boot my laptop with the live CD, hook up the enclosure, install to that, then replace it in the Dell.

I'll give it a try this afternoon and let everyone know how it goes.

---

