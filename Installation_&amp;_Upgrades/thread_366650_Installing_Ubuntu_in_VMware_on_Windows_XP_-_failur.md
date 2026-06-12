---
title: "Installing Ubuntu in VMware on Windows XP - failure after tools install"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by snapbox on 2007-02-21
Hi,

I have a windows xp box that I have installed VMware server on.  I installed Ubuntu 6.10 into it but when I unpack and run the script to build and install the vmware tools, the script says everything is okay but restarting ubuntu exhibits the following:

[LIST]
[*]Boots to Ubuntu splash screen with progress bar - gets to about 90% then freezes there.  
[*]The cursor changes to the busy cursor and if you type blind, it appears to log in - but the screen never changes.
[/LIST]

Has anyone any ideas?  How can I see what is going on?

Many thanks.

---

### Post by gasull on 2007-02-21
Maybe I'm not answering your question, but there is a [related post]("http://ubuntuforums.org/showthread.php?t=34323") and a [howto]("http://johnbokma.com/mexit/2005/11/07/vmware-player-ubuntu-installation.html").

Also, you might be interested in [OpenVZ]("http://en.wikipedia.org/wiki/OpenVZ").

HTH.

---

### Post by snapbox on 2007-02-21
gasull,

Thanks for your post.  The other post relates more to disk and installation problems - I don't have that problem, Ubuntu installs correctly, the vmware tools appear to install correctly as well.

The tutorial that was referenced doesn't cover installation of the tools.

OpenVZ has to be installed on Linux for Linux.  The laptop I have is a work one and I'm not allowed to re-partition and/or dual-boot it hence why I'm using VMware to host Ubuntu.

Still stumped.  Any logs or anything I could try to get hold of that might provide some insight to anyone?

Thanks.

---

### Post by snapbox on 2007-02-21
I have just noticed that if boot in recovery mode then run gdm manually, Ubuntu comes up fine - though the mouse is still jerky?

Ideas?

---

### Post by gasull on 2007-02-21
> **snapbox said:**
> I have just noticed that if boot in recovery mode then run gdm manually, Ubuntu comes up fine - though the mouse is still jerky?

Ideas?

You should look the logs.  I don't know wich one.  But maybe you should make a new post with the subject like "Mouse not working on Ubuntu within VMWare", because this is a different problem.

---

### Post by geek6oy on 2007-03-22
snapbox,

This might be coming a bit late for you, but FWIW...

I had exactly the same problem installing a kubuntu edgy (6.10) guest under vmware server on Linux - the progress bar on the graphical boot screen would hang when almost complete and the login screen would never appear.  The system was, however, running!  I could login to the guest via ssh and, as you discovered, X would start OK if you booted through the recovery console.

All of this would only occur after installing vmware tools.  The guest would boot OK without them, but it's much easier to use a guest OS with the tools installed.

The solution I found after a couple of hours of intensive Google-ing was to disable the graphical splash screen.  Boot into the recovery console in the guest and edit /boot/grub/menu.lst, removing the boot parameter "splash" from the appropriate kernel boot line.  Save, quit, reboot.  Et voilà!

Enjoy.

---

