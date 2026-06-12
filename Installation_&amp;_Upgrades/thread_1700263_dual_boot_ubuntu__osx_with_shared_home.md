---
title: "dual boot ubuntu / osx with shared /home?"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by the.drizzle on 2011-03-04
Hiya!

So I got a brand new macbook pro yesterday, and I like it!  But I really don't want to go "all mac" at this point, so want to make this machine dual boot with Ubuntu.

it occurs to me that what I *should* be able to do is partiton the hard drive something like so:

/dev/sda1 --> /boot
/dev/sda2 --> / (Ubuntu)
/dev/sda3 --> / (OSX)
/dev/sda4 --> /home

and a /swap partition in there as well, of course.  The point being that I'm thinking it should be possible to edit /etc/fstab to mount sda4 (above) to /home when I boot up under Ubuntu, and have OSX mount the same partition to /Users when I boot into OSX, thus allowing me to access all user data easily in either OS.

However, I don't know much about macs...

So I'm thinking I'm looking at two issues.  First, what filesystem should I format /dev/sda4 (above) as if I want this to work?  Does OSX support ext4, or would I be better off trying to get HFS+ support under Ubuntu?

Second, what would be required to get OSX to mount /dev/sda4 to /Users at boot?  That is, what is the OSX equivalent of editing /etc/fstab?

Secret third issue, is this even a reasonable plan?

Thanks!

---

### Post by kidders on 2011-03-06
Hi there,

Yep... It's a perfectly reasonable plan. There are a few alternatives to dual booting your Mac though, which might or might not be suitable ...

**Do Nothing**
Darwin is very Linux-like. If you're used to working with Ubuntu server installs, you should find OS X's terminal interface very familiar, and capable of most of the things a typical Linux server can do. I use Linux in work, but get along quite happily on a Mac at home, with a few extras installed on it (eg Apple's developer tools & X11 server, and a handful of basic command line utilities OS X just happens to lack).

**Mac Ports**
There are Darwin ports available of a whole pile of Linux software. For example, Fink has a Gnome 2.26 port that you could install, if you wanted to. In theory, you could install a fairly complete Linux stack right alongside your OS X. It's been a while since I went down this particular road -- I just don't find it especially useful -- but *you* might. Plenty of other bits & pieces (eg OpenOffice, Firefox, etc.) that you might help you feel more at home also offer Mac versions of their software on their own sites.

**Virtualisation**
You could run a virtual Linux installation in MacOS (eg with VMWare Fusion), or a virtual MacOS one inside your Linux (eg with VirtualBox). The main advantage would be to avoid having to reboot to switch between them. If you're clever about it, you ought to be able to set Ubuntu up so it can boot both natively *and* inside a virtual environment, but it takes a little work to get it right.

Anyhow, assuming none of those take your fancy, the first things I would do to set up a MacOS/Linux dual boot environment are ...[LIST]
[*]Either change your MacOS uid to 1000 before you begin, or plan on setting yourself up a Linux account with a uid of 501. It's vital that your Mac & Linux accounts have the same uid (and preferably the same username).
[*]Split your MacOS partition a few times, so the table is more or less the shape you want it. Don't be afraid to leave space unallocated; there's no point in allocating disk space you don't need, just because you have it to spare.
[*]Disable journaling on one of your new partitions (to become your home directory). Call it something sensible (like "Users") ... MacOS will mount it automatically at /Volumes/Users. (In Linux terms, that's like having your "home" partition at /media/home instead of /home.)
[*]Filesystem choices for your Ubuntu root & swap filesystems don't matter at this point ... You can reformat them when you install Linux.
[*]If you want, install a bootloader (eg rEFIt). It can be handy.
[/LIST]

Although you will probably find one or two files called fstab on your Mac, I wouldn't suggest messing with them. Apple seems to be in the process of phasing out their use, so they may not behave the way you expect. I have a separate "home" partition on my Mac, and I get along just fine by symlinking /Volumes/Users to /Users. There are plenty of howtos available on this subject, but in broad strokes ...[LIST]
[*]Go to System Preferences -> Users & Groups -> Login Options, and change your configuration to allow you to *type* the name of the user you want to log in as, rather than simply clicking a name on a list. Then log out, and back in again as **>console** to descend to a terminal interface. Alternatively, you can boot your Mac in single user mode, to achieve roughly the same effect.
[*]Change directory out of /Users (eg just type **cd /**), and su to root (sudo su).
[*]Rename /Users to something like /Users.old.
[*]Use chmod & chown to alter the permissions of your new "home" partition (eg /Volumes/Users) to reflect /Users.old exactly.
[*]Symlink /Volumes/Users to /Users and copy (do not move) all the data from /Users.old to /Users. Be sure to preserve your permissions ... This is very, very important!
[*]Hitting CTRL+D twice should be enough to restore you to a graphical login Window.
[/LIST]

Your Mac should now quite happily work off your new unjournaled HFS+ home partition. A couple of reboots later, when you're happy everything is working, you can erase the backup /Users.old.

Once you've installed Linux (which sounds like it'll be much more familiar territory for you!), you can perform a similar procedure there ...[LIST]
[*]Kill your entire GUI, drop to a terminal, and use **lsof** to ensure that little or nothing inside /home is open.
[*]Su to root, rename /home and mkdir a new one with the correct permissions.
[*]Add /dev/sdaX to your /etc/fstab and run **mount -a** to activate it. If your Ubuntu install is reasonably fresh, there won't be any data worth copying, so you should just be able to fire up your GUI & log in.
[/LIST]

What you'll end up with is ...[LIST]
[*]An OS X system partition that's not fully accessible from Linux. This is no harm, since none of it is especially Linux-compatible anyway, and you won't be able to accidentally damage it.
[*]A Linux system partition that's not *at all* accessible from MacOS ... again, no particular loss!
[*]A home partition that's not journaled (ie it'll be a bit more sensitive to sudden power loss than the rest of your system), but should work hassle-free with both OSs, without any weirdness.
[*]A Mac that will no longer run Boot Camp. If you ever want to use Boot Camp (eg to make a triple boot system with Windows on it), you need to run it *before* you start adding extra partitions to your hard disk.
[/LIST]

I hope that answers your questions. Just so you're forewarned, there are a few gotchas you'll discover before long. For example, it'll take more time & work than you might be used to, to get all of your Mac's hardware to cooperate with Linux. That said, the one major advantage of working on a system with such a specific hardware configuration is that you'll never be the first person to encounter any given problem. You should be able to find well maintained howtos covering pretty much everything.

---

### Post by the.drizzle on 2011-03-08
Thanks, those are some very clear directions!  I'll have time early next week to try them out, but it seems quite straightforward.  I'll let you know how it goes then...

Cheers!

---

