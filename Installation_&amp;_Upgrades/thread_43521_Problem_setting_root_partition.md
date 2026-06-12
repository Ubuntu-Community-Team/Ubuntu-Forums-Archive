---
title: "Problem setting root partition"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by cphp on 2005-06-22
I've had an old version of SuSE running for a while, but that's a bit behind the times and I decided to switch to Ubuntu. The SuSE installation is 100% automatic, and it partitioned everything by itself.

So installing Ubuntu is a new experience for me. The guided partitioning says something about cleaning the whole disk, which I do NOT want to do (I have a main partition of Windows XP Home Edition SP1). So I did the "manually edit partition tables" and I set it to format hda6 -- where SuSE lived. Well, it formatted it, whiped it, and then told me it couldn't install because I hadn't specified a root partition. Now, I'm pretty certain I want the Ubuntu as root (so it will start up the bootloader when I boot my computer), but on going through the tables I didn't see how to do that. So now I had to reinstall SuSE because its bootloader was gone and the computer wouldn't boot into windows. . .anyway. . .I'm very excited about Ubuntu and would appreciate being able to install it :P

While I'm at it. . .one more question. . .if there's a program I want to install that's written for linux but isn't in the package repository, can I install it even if it isn't a Ubuntu package?

And I'm assuming Ubuntu includes a bootloader so I'll be able to select Windows or Linux on booting up. . .

EDIT: Also. . when trying the LiveCD it booted and then just displayed a message "Frequency out of range" for the longest time. . .is this all I'll get if I install to disk as well? My graphics card worked fine with SuSE, and I got the computer only about a year ago. . .so. . .

---

### Post by Martin Witte on 2005-06-22
- for partioning: when you get to the point where you can partition you have to specify you will use hda6 as '/' , and so make it your root partition.
- for non-ubuntu software: supposed all stuff this software is dependent on is installed on your box you can install it.
- for the screen: try to use the 'vesa' driver for /etc/X11/XF86Config-4, as this seems to work with most hardware. Later you can install the proper driver for your video card - if one exists of course.

---

### Post by mingus on 2005-06-22
*on going through the tables I didn't see how to do that*

If you mean the partition table displayed at the partitioning step in the installer, it is there.  FWIW, first time I used that partitioner, I also didn't catch on - not terribly intuitive.  As I recall, you highlight the partition and hit enter, and there is another screen with filesystem, boot flag, mount point, etc.  To change any of these values you again highlight that line and hit enter for the choices.

*if there's a program I want to install that's written for linux but isn't in the package repository, can I install it even if it isn't a Ubuntu package*

Sometimes.  Ubuntu has several repositories, each supported at a diff level.   In general, all those packages should work.  There is also the backports repository for version updates not yet included in the official repositories.  Sometimes someone builds a app .deb specifically for Ubuntu.   However, using the Debian repositories is strongly discouraged; there have been many conflicts.  So the next choice is usually compiling from source.   There is also a tool called alien that converts rpm's to deb's - I've no experience with that, but given how important it can be that the build is specific to a distro version (as is true with SuSE), I'd be hesitant to use it.

*when trying the LiveCD it booted and then just displayed a message "Frequency out of range" for the longest time. . .is this all I'll get if I install to disk as well? My graphics card worked fine with SuSE*

Getting a diff result with the Live CD and after installation - one works and the other doesn't, or the reverse - is not that uncommon (e.g., the case with SuSE, too).  On one hand, the CD has compiled into it lots of stuff that you don't want in your installed kernel (it would be too large), but are added as modules just like drivers are add-on installs in W$.  Conversely, the user may add a driver to the installed system that does not have an equiv in what was compiled on the CD.   So . . .

Beforehand, google your card name + ubuntu, search the forums, and quickly you'll find what driver your card needs and if there are any installation gotchas or tricks needed.  Virtually everything works, but sometimes it takes a bit of effort to set it up.

If when you begin the installation you see the same message, turn the framebuffer off and then let the X-server configure itself later.  Or you may need to tweak the config file.  My guess is that you'll know in advance after you google the card.

BTW, I find that 1 huge diff between SuSE and Ubuntu is SuSE's system administration ala the YaST tool (and SAX).   And there is also built in low-level tweaking tools; not as granular as Gentoo but fairly comprehensive.  SuSE is the primary distro on my SOHO for just these reasons.   Ubuntu's strength is its ease-of-use once setup, great package library, and tight interface integration - but for a lot of sysadmin, it's the command line.

---

