---
title: "Edgy to Feisty Broke My Computer"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by lousyd on 2007-05-05
Late last week I got the "updates available" icon on my Kubuntu Edgy
Eft desktop.  I updated the one package and let it go.  But then it
came back saying "There's a new version of Kubuntu available!  Feisty
Fawn is da bomb!  Download Now!"  So I did, and the fawn pooped all
over my hard drive.

It got only part way through and said there were problems.  It tried to
back out but then screwed up that too.  I was left with a
non-operational computer.  When I'd start up, it would dump me to the
kernel's built in shell, busybox or ash or something.  Well, I'm in no
state of knowledge to go mucking about manually trying to fix the
problem and I don't even know what went wrong anyway.

I spent several days pouting and searching the Internet for fixes, to
no avail.  I resigned myself to re-installing from scratch (separate
/home partition!).  I even had Feisty downloaded and a blank CD
sitting next to my computer, when quick as lightning a flash of insight
struck.

From my Gentoo days I remembered having installed the distro chrooted
to the new root, but with the kernel and environment of the LiveCD.  I
thought maybe I could boot into my Ubuntu Edgy CD, chroot to my borked
install, and fix it.  And so this is what I did:

1. Boot to the Ubuntu 6.10 LiveCD.
2. Set up networking, wireless in my case.
3. 'mount /dev/hda5 /media/hda5' (hda5 is my root)
4. 'mount -t proc proc /media/hda5/proc'
5. 'cp -L /etc/resolv.conf /media/hda5/etc/resolv.conf'
6. chroot /media/hda5 /bin/bash
7. apt-get dist-upgrade
8. Reboot.
9. Drink a cup of coffee.  Happy dance!

When doing the dist-upgrade, I got a bunch of these:
"cp: cannot stat `/etc/udev/rules.d/85-brltty.rules': No such file or directory"

But apparently it wasn't a problem.

I got the idea for chrooting from my Gentoo days.  When installing
Gentoo it used to be that you'd boot into the LiveCD and then chroot
to where you wanted to install everything and then do it.  After three
or four times of installing Gentoo I started to understand what was
going on.  Well, the idea came back to me here and I tried it.  It
worked!

Lesson 1: All hope is not lost.
Lesson 2: The thing about Gentoo teaching you Linux is at least partially true.

---

### Post by finalzero on 2007-05-05
Install 6.10, once you have the basic clean system booted up, upgrade to 7.04, seems to work fine then.

---

### Post by mocha on 2007-05-06
Take a look at my post [[COLOR="Blue"]Here[/COLOR]]("http://ubuntuforums.org/showpost.php?p=2601573&postcount=3")

---

