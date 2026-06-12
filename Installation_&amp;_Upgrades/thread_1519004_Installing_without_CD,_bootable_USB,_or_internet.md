---
title: "Installing without CD, bootable USB, or internet"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by stoogiebuncho on 2010-06-27
I've got an interesting little challenge.

Someone gave me a quite old Sony laptop with Windows 98, 64mbs of ram, and I think a Pentium II processor.

I want to try doing a minimal Ubuntu install to try to turn it into an internet machine.

Here's the problem:  It doesn't have a CD drive, and I don't have a USB CD-rom drive, so I can't boot from the CD.  It has a usb port, but I can't boot from it.  And currently I can't connect to the internet because it doesn't have a place to plug in an ethernet cable and my wireless card doesn't work with it.  So the only way I have of transferring files to this machine is with a usb drive, and I have to work from within Windows 98 because I can't boot it into anything else.

I've been looking at this page:
[https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")

This makes it look possible.  But it sounds like it will leave me with a command-line only installation, and I will still have no access to the internet to download additional packages.

Would it work for me to download the packages I want and put them on a USB key and run them from there once I have the command line installation going?

Is there a better way of going about this?

Sorry for the wall of text.  Thanks for any advice you have to give.

---

### Post by Old_Grey_Wolf on 2010-06-27
You could use WUBI to install Ubuntu. There is a link on the page you linked to. Then you could try using LVPM to move the WUBI install to a real partition...Link to instructions [http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)...you may need to look at some of the newer replies to the thread.

---

### Post by stoogiebuncho on 2010-06-27
That's a good idea, but this machine doesn't have nearly enough ram to run a Wubi install.  I think they're asking for 384 MB now, and I've only got 64 MB.

---

### Post by Old_Grey_Wolf on 2010-06-27
> **stoogiebuncho said:**
> That's a good idea, but this machine doesn't have nearly enough ram to run a Wubi install.  I think they're asking for 384 MB now, and I've only got 64 MB.

I would think that anything you did manage to install by Googling on 'floppy linux install', 'floppy OS install', 'floppy dos install', etc. would be disappointing. Be merciful and put the old machine out of its misery. :):)

---

### Post by stlsaint on 2010-06-27
You can try a pxe boot off another linux machine. Or even a floppy with a very small distro. A few suggestions include: DSL, puppy linux, or yellow dog. DSL is the best choice though. DSL stands for damn small linux!

---

