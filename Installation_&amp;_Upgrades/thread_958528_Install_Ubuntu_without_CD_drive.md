---
title: "Install Ubuntu without CD drive"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by T4_ on 2008-10-25
I had an Ubuntu installation on an external USB hard drive (internal hard drives kept dying due to rough transport), which I managed to screw up (long story).

Unfortunately, the laptop's CD drive is broken too.

I do have a USB floppy drive I can boot off, and access to (wired) internet. I can also put the Ubuntu iso on the hard drive.

I've googled and found some things, but they all failed (Debian boot floppies, uNetBoot). I think the partition I can't get rid off or the fact that it's an external drive come into play into some of these failures.

On the Ubuntu wiki there was a page about floppy install using TomsRstb, but - I forgot why - that didn't work :(

What I'd prefer is to boot from a floppy, and then either do a netinstall or read the iso from the hard drive. Is there such a way?

Any other/better suggestions are more than welcome, too!

---

### Post by htmlland on 2008-10-25
On this tutorial ([http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)) it talks about installing from a local network however if you use this same tutorial and only follow the parts on creating a netboot disk or USB stick then you can download stright from the online repositry.

Is this any help?

Michael

---

### Post by MikeSho on 2008-10-25
Hello,

You can install Gmount from the Synaptic package manager to mount the ISO of the file in your USB.
:guitar:

---

### Post by T4_ on 2008-10-25
> **MikeSho said:**
> Hello,

You can install Gmount from the Synaptic package manager to mount the ISO of the file in your USB.
:guitar:Thanks, but unfortunately I no longer possess a working version of Ubuntu. Or any distro :) All of this typing is coming from my girlfriend's Vista (ergh) laptop.

> **htmlland said:**
> On this tutorial ([http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)) it talks about installing from a local network however if you use this same tutorial and only follow the parts on creating a netboot disk or USB stick then you can download stright from the online repositry.

Is this any help?

MichaelIt seems good, except that it requires a USB stick (which I don't have - forgot it in another country!) or CD. I could of course use the external hard drive, but how can I boot from it without first erasing it completely? Grub is still installed and active, unfortunately.

Do external HDs have an MBR? I could give that a try...

Ah well, if all else fails I can manage tomorrow using her laptop (when she allows me :p) and get a USB stick on Monday.

---

### Post by T4_ on 2008-10-25
Ah, poop!

I found a USB stick in a drawer (turns out I did pack it!) but... I'm in a hotel pending finding permanent accommodation. The internet here is "connect to our unsecured network" and then "authenticate in your browser window". The second you close your browser, the connection goes.

The installer, of course, has no browser let alone a way of authenticating in this hotel system. Crap.

Ah well, at least it works - I should be able to install Ubuntu this way (mini.iso on USB stick) the second I get a proper internet connection...

I guess Vista will have to do for the next few weeks - another reason to find a decent apartment very, very soon!



[edit]

Unless, of course, someone can tell me how to install Ubuntu booting from a floppy or USB stick and using the .iso which is on an external USB hard disk!

I tried that TomRstbt again... I can boot into "real" DOS, but how am I going to execute/read 2+MB of files on a floppy? I don't get it.

---

