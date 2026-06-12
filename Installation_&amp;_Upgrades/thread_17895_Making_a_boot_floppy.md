---
title: "Making a boot floppy?"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by Wok on 2005-03-03
I've about given up on getting Ubuntu to work in a three-OS setup, at least through Grub. (The story is over at [http://www.ubuntuforums.org/showthread.php?t=14119](http://www.ubuntuforums.org/showthread.php?t=14119) ). But I'd still like to be able to check out an installed version.

I'm thinking I'll try a new Ubuntu install, but this time just use a boot floppy to access it. As I recall, I tried to install the MBR to a floppy during a few of my Ubuntu install attempts, but that didn't work, either. I don't think there's any specific option to make a boot floppy -- just some useless words about how you can install the MBR anywhere. Tried all the floppy locations I could think of, but nothing worked.

So can I either make a boot floppy from the installed but inaccessible Ubuntu, or during a new install?

This seems like something I should have found in some howto or forum, but I swear I looked first. Is there a place where the installer is discussed? I think it's the weak point that will limit Ubuntu's ultimate popularity with folks used to other systems, including most Linux distros. I've installed 8 or 10 systems, and Ubuntu's installer is the most difficult -- I guess it's pretty much the straight Debian installer? It wouldn't take much to make it a lot more usable.

---

### Post by pigpen on 2005-03-03
I'm not an expert here, but you might find this howto article on using Grub helpful.
[http://home.nyc.rr.com/computertaijutsu/grub.html](http://home.nyc.rr.com/computertaijutsu/grub.html)

He explains how he installs Grub to a floppy to test his OS installations before commiting his changes to the hard drive (MBR).  He's using redhat, but its still applicable to Ubuntu.  I imagine you can just run Grub from the Ubuntu Live CD, if not, you can use Knoppix.

This thread, while it describes installing grub manually to the MBR, might help you to understand how grub works (and how to run Grub from the command line). 
[http://ubuntuforums.org/showthread.php?t=7043&highlight=grub+install](http://ubuntuforums.org/showthread.php?t=7043&highlight=grub+install)

I also found this helpful, while its for Gentoo, it did help me to understand how to use Grub's commands and install it:
[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#grub-install-auto](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10#grub-install-auto)

One last point, if you run a live CD, sometimes they prevent you from writing to external devices so you have to change permissions. If you're using the Ubuntu Live CD then maybe this won't be an issue. I just know with the Knoppix Live CD, I had to figure out how to enable "write" permissions so I could write to my hard drive. Not sure if it applies to floppy disks as well.

I had a hell of time trying to figure out how to mount my floppy drive because it's a USB external drive. I had to mount it by: mount /dev/sda /mnt/floppy
I think the normal way for floppy drives is: mount /dev/fd0 /mnt/floppy

---

### Post by pigpen on 2005-03-07
Heh, I also just noticed this from Ubuntu's very own support section.

[How to make a GRUB boot floppy](http://www.ubuntulinux.org/support/documentation/howto/Randy%20Magee)

---

