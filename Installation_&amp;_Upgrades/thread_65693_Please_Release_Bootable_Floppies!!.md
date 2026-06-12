---
title: "Please Release Bootable Floppies!!"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by fordfan753 on 2005-09-14
I've been switching back and forth between Ubuntu and Debian on my desktop, they're both great! Ubuntu when I want stuff to just work, and Debian when I feel like beating my head against a wall, but somehow feeling much smarter from doing so.

One thing I love about Debian is that you can download a few floppy disk images which will download Debian from the net and install it without needing CDs. While I realise that this is probably because Debian has about a million CDs it is also really handy for people without CD drives. Enter my laptop...PIII 600 M, 192MB RAM, it *should* be able to comfortably run Ubuntu, but it's an ultralight so it has no CD drive.

I tried a few things, I tried installing very basic Sarge from floppy disk and the net, and tried dist-upgrading to Hoary, but that proved to be a bit dodgy, and ran like crap, my next attempt I guess will be via mounted image on hard drive....but it would just be a million times simpler if there was a Debian way!

Please, someone out there with a bit of skill, someone that knows what they are doing, make a set of floppy disks that will download and install Ubuntu from the repositories, why not use the Debian disks and modify them a little? I don't see it being too hard to do for someone that knows what they are doing...They would look good when Breezy is released too, many different ways of installing it should bring more people over from other OSes. It shouldn't be that hard, I would do it myself, but I have no idea what I'm doing.

---

### Post by mlomker on 2005-09-14
All of those projects take a whole lot longer than it sounds.  It's also really tough to fit anything on a floppy.  The kernel alone (without *any* modules for network drivers, etc) fills a floppy.

At work we have such machines but we also have a PXE server that allows us to boot through the network card and install whatever operating system that we need.

---

### Post by fordfan753 on 2005-09-14
[QUOTE=mlomker]All of those projects take a whole lot longer than it sounds.  It's also really tough to fit anything on a floppy.  The kernel alone (without *any* modules for network drivers, etc) fills a floppy.

At work we have such machines but we also have a PXE server that allows us to boot through the network card and install whatever operating system that we need.[/QUOTE]


Would it be possible to modify the Debian set to download from Ubuntu repositories instead?

If it does prove too hard to do what is the easiest way to get Ubuntu on there? Is network booting difficult to set up? And has anyone had any success booting an image on the hard drive?

---

### Post by Galoot on 2005-09-14
[QUOTE=fordfan753]If it does prove too hard to do what is the easiest way to get Ubuntu on there?[/QUOTE][This HOWTO](http://ubuntuforums.org/showthread.php?t=28948) might help.

---

### Post by fordfan753 on 2005-09-15
[QUOTE=Galoot][This HOWTO](http://ubuntuforums.org/showthread.php?t=28948) might help.[/QUOTE]

Thanks, I was thinking of giving this a shot, but I decided against it, and decided to set up a PXE server on my desktop, the server is working fine, but I have one niggling problem...the installer can't find the Release file in the mirrors, which is weird because it actually is there...it doesn't matter what address I give it, it comes up with errors...

---

### Post by fordfan753 on 2005-09-15
Got it!
The DHCP server on my desktop that I used to PXE boot from was not telling the ubuntu installer about my internet connection...solution: instead of buggering about with config files I just disabled the DHCP server on my desktop as soon as my laptop booted, so that when the installer configured DHCP it used my ADSL modem, which obviously told it about my internet connection...it is currently downloading packages! I'll write back if I have any more problems, if not assume it worked perfectly  :)

---

### Post by mlomker on 2005-09-15
[QUOTE=fordfan753]if not assume it worked perfectly  :)[/QUOTE]

Awesome!  I haven't set up a PXE server, myself, but they are very handy to use.

---

### Post by mr_mop on 2006-08-02
> **mlomker said:**
> The kernel alone (without *any* modules for network drivers, etc) fills a floppy.

Debian does it with 4 floppies.
One for boot, one for root, one for network drivers and another for cd drivers. here:
[http://ftp.debian.org/debian/dists/etch/main/installer-i386/current/images/floppy/](http://ftp.debian.org/debian/dists/etch/main/installer-i386/current/images/floppy/)

It then gives you the prompt to type in linux, or expert.

This is the main problem I have with ubuntu.  I only want to do a server install, but all these alternative methods of netbooting etc do not give me that prompt.

---

