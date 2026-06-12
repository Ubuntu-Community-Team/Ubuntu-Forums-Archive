---
title: "Freeze during install - how to recover?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by nash black on 2011-10-14
Hi all,
 
My mom tried to use firefox while I was upgrading to 11.10 and the computer froze up. I left it on overnight to see if it would work itself out, but no such luck.
 
I've rebooted, but, of course, the install failed. I can use GRUB and my windows partition, but cannot boot into Ubuntu.
 
Most of my important files are backed up on another drive, but I would really like to fix this installation up without losing any files. What is the best way to do this?
 
Thanks a lot!
 
Nash
 
 
edit: just to clarify, I wouldn't mind reinstalling; I just don't want to reformatt the whole drive and lose my personal files. Reinstalling applications is no big deal if necessary.

---

### Post by sussexslanter on 2011-10-14
I got a freeze as well.  It didn't even finish preparing.  Its happened twice now.

I got some messages telling me that it failed to fetch things.

Maybe I wait a couple of weeks and try again?

---

### Post by nash black on 2011-10-14
This wasn't just a freeze during the install, it froze up because firefox was opened while the files were being installed - everything seemed to be going fine before that.

It sounds like your install just had problems downloading the install files - maybe due to server overload from everyone installing the new version or from a faulty internet connection.

Anyway, mine got the files okay; we just screwed it up after that (:

any advice would be appreciated!

---

### Post by hreichgott on 2011-10-14
I've totally done this a few times, due to laptop deciding it was idle and ought to go into hibernate mode in the middle of a dist-upgrade. My sympathies.

If you backed up all your necessary files before upgrading, you should just reinstall Ubuntu 11.10 from a freshly downloaded Live CD, wipe the hard drive, and later re-copy your backed up files. For a non-expert that's really the simplest solution.

If not, you'll have to use a Live CD or some other method to get the computer booted, figure out which packages got updated and which ones didn't, and manually install the needed ones in the proper order. This is hard. I did it once but mostly by luck. (Someone with more knowledge than I can help you out here.)

---

### Post by MAFoElffen on 2011-10-14
> **nash black said:**
> This wasn't just a freeze during the install, it froze up because firefox was opened while the files were being installed - everything seemed to be going fine before that.

It sounds like your install just had problems downloading the install files - maybe due to server overload from everyone installing the new version or from a faulty internet connection.

Anyway, mine got the files okay; we just screwed it up after that (:

any advice would be appreciated!
That's the thing... Do you really know where it crashed?

If you can get to a Grub menu, then you could go back to a Menu Item previous to 3.0, then press "e".  This would get you into an edit mode.  If you then arrowed down until you get to the line that begins with "linux".  If you then arrow right until you get to where it says "quiet splash" and replace it with "--verbose text" it should boot into a TTY text mode.  Login.

```

sudo apt-get update
sudo apt-get -f
sudo apt-get dist-upgrade

```That should restart your upgrade process back up.  That process has several stages.  Evaluate what is there and what needs to be changed (to include dependencies). Download packages. Install and configure packages.

---

### Post by nash black on 2011-10-14
in edit mode, there is this: "splash quiet vga=773 quiet \ splash vt.handoff=7"

i tried switching both instances of quiet splash (or the two similar places, it doesnt say exactly that) but neither would allow me to boot. It fails as it did before on the splash screen. I am not sure Ill be able to log in at all.

I do have an 11.10 install disc if that could help

---

### Post by MAFoElffen on 2011-10-15
> **nash black said:**
> in edit mode, there is this: "splash quiet vga=773 quiet \ splash vt.handoff=7"

i tried switching both instances of quiet splash (or the two similar places, it doesnt say exactly that) but neither would allow me to boot. It fails as it did before on the splash screen. I am not sure Ill be able to log in at all.

I do have an 11.10 install disc if that could help
Sidenote on this-- Post your /etc/default/grub file.
After the "ro  ", that is incorrect:
```

splash quiet vga=773 quiet \ splash vt.handoff=7

```
It should be more like
```

splash quiet vga=773 vt.handoff=7

```

Here is another way (of many) to do this:

1. Boot a Live-CD. Open a terminal session.
2. Find your installed Linux partition, e.g. /dev/sda5 (where you've installed Ubuntu ... the "/" or root mount partition)
```

sudo mount /dev/sda5 /mnt

```3. If you have a dedicated boot partition: sudo mount /dev/sda3 /mnt/boot
```

sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -t proc /proc /mnt/proc

```4. "changeroot" to /mnt
```

sudo chroot /mnt /bin/bash

```5. Now you're "on" Oneiric, see chnageroot man page for details
```
[FONT=monospace]
[/FONT]sudo apt-get update 
sudo apt-get clean
sudo apt-get -f 
sudo apt-get dist-upgrade

```

---

