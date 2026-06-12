---
title: "Ubuntu Install not working"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by Keetar on 2012-04-19
Hi Guys, I have completed a new install of Ubuntu via a CD.  I have completely wiped the Hard drive and completed a fresh install, I changed the 'quiet splash' to 'nomodeset' as it kept going into a blank black screen.

Everything installed perfect and it downloaded all the updates, now after the reboot it wont work?

It either loads up into a blank, black screen again or I press shift and get the 'GNU GRUB version 1.99-12ubuntu5'
again I change this to 'nomodeset' for the first option which is Ubuntu, with Linux 3.0.0-12-generic and after it running this it just stops at 'mountall: Disconnected from plymouth'

I'm now stuck and unsure what to do, can anybody offer me any help please?

Its a new HP A6 Vision AMD Quad Core and Radeon Dual Graphics

---

### Post by Keetar on 2012-04-20
Still no joy with this issue, I'm out of ideas :(

---

### Post by tmaranets on 2012-04-20
Stop trying to install via CD and do it direct from Ubuntu.com. Or get a CD, if you must, off Canonical.
[http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)

---

### Post by Keetar on 2012-04-20
Hi thanks for your support answer, I did get the ISO from the Ubuntu website, I think my issue is more about the display drivers than the install?

---

### Post by strask on 2012-04-20
If you press shift to get to the grub menu, you should have (usually on the second line) a recovery boot option. Try using that option, without changing it at all, and then give us as much detail as you can about what happens right before it stops booting.

Also: Which version of ubuntu are you using?

One thing that helps to diagnose boot problems is the boot info script located at [http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)

To use the script, boot from your ubuntu install CD and use the "try ubuntu" option. Open up firefox and go to the address above to download the bootinfoscript. Extract it from the .tar.gz and then open a terminal, cd Downloads, and 'sudo ./bootinfoscript'. When it finishes post the contents of the RESULTS.txt file to the forums here.

---

### Post by Keetar on 2012-04-20
Hiya, I have installed Ubuntu 11.10 64 Edition

I have tried the various options and it will either load into a blank screen or give the command:

To run a command as administrator (user "root"), use "sudo <command>". See "man sudo_root" for details.

ubuntu@ubuntu:~$

I'm sorry from here I don't know how to load a graphical version up to try your advice. 

When I try the recovery option I get presented with x4 options, resume, fsck, remount and root.  When I select Resume normal boot I get:

initctl: Event failed

---

### Post by oldfred on 2012-04-20
from recovery options try root.

This will refresh and update which may help, # are comments do not copy or type them.

#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

---

### Post by Keetar on 2012-04-20
hey oldfread, from the root option I get:

root@thewilson-HP-Pavilion-dv6-Notebook-PC:~# (and a flashing cursor)

---

### Post by oldfred on 2012-04-20
then can you type in the commands posted above?

---

### Post by jones27557 on 2012-04-20
Guess I got lucky with my HP G62.  Ubuntu just installed and worked.  I am pleased with it.

---

### Post by Keetar on 2012-04-21
Good Morning, I just wanted to thank you for your support - I have installed Ubuntu 12.04 Beta 64 and it installed perfect 1st time no issues at all.

Thanks again :)

---

### Post by MonkeyPaw on 2012-04-21
It was highly likely your A6 APU was giving you trouble. Ubuntu has a hard time installing and running until you get the proprietary graphics drivers installed for Llano. Sounds like the Ubuntu team may have merged the fix into the latest beta version. From what I gather, Llano needs a pretty new version of the Gnome3 kernel or all you get are blank screens.

---

### Post by Bluphx on 2012-04-23
I'm also having this issue, when I got to the precise tty1 login I hit cntr alt f7 n got...

Rack from until-Linux 2.20.1
/dev/sda1: clean, .....files, .....blocks
Initctl: event failed
Cound not write bytes: broken pipe
Skipping profile in /etc/app armor.d/disable: use.shin.rsyslogd
*starting apparmor profiles   [ok]

Then sits unresponsive. Usually cntl alt f7 gives me a blank black screen. I am also trying to install on an AMD and is my first attempt at installing ubuntu as the main and only OS. I have dualboot'd 2 intel machines (iMac and HP). I have one more old single core intel tower that I don't need the info on, I'll try installing ubuntu natively on that instead of slamming my head against this AMD issue ^^ thanx in advanced

---

### Post by Bluphx on 2012-04-23
Update - 

GRUB > recovery mode > repair packages > 1 new package 2 upgrades > y enter > remove obsolete > y enter > recovery menu > normal boot

Back to tty1 login but instead of percise dev it's 12.04 lts

Cntl alt f7 shows me a whole list of *stopping/starting

*starting load fallback graphics devices [fail] is the only one I can see that failed

The last listed is

* stopping system v run level compatibility [ok]

---

### Post by Bluphx on 2012-04-23
Update again. Sorry if this is annoying having them as seperate post but I need beans for an avatar I feel like a real scrub ^^

So I think the problem was I couldn't fit the iso on the USB thumb drive after using the USB install setup on my other comp running ubuntu. My USB was only 1gb so I hacked a MacBook Air recovery USB [8GB] n formatted it to fat, used Ubuntu USB setup, n click n dragged the iso to the root of the USB, ran install again with no problems. It's the only OS on the CPU, also it uses an AMD processor. 

**Make sure to try the main "PC" iso n not the AMD iso (I tried the AMD iso w/ no success I didn't fully read website first time I tried install when it says that the first iso works for most-to-all, just saw AMD n clicked I guess lol ^^)

---

