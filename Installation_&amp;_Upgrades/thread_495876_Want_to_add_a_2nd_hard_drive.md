---
title: "Want to add a 2nd hard drive"
date: 2007-07-08
forum: Installation &amp; Upgrades
---

### Post by New-In-Ohio on 2007-07-08
I have many newbie questions, i have done some research, but still feel the need to ask.  I have a dual boot machine (XP and Ubuntu) using GRUB as the OS loader.  I bought a 120G hard drive and will be installing it soon.  My plan is to partition it for multiple "tryout" distros and I dont want it to be bootable.  I would like to select from my already intalled GRUB the kernel i'm interested in at any given reboot.  Questions:

Can I install debian, slackware, etc. on the 2nd harddrive without overwriting the boot program?
How do I get GRUB to automatically recognize new kernels?  Or do I have to manually enter the data?
If I'm running another Linux distro, can I still mount my /home directory from ubuntu on the first hard drive? (/home is currently its own partition on the first drive)
Will programs that i have used apt-get to install still run under other linux distros by simply starting them from the command line (this demands another question as to wether or not i can add to $PATH something thats on the first hard drive?, and if so how does linux know which gcc to run, as an example? the one in XXX distro or the one in ubuntu?)
Is there a way to keep the ubuntu installation clean?  I mean never having any installed program write files to the original installation directories (wether its from synaptic, apt-get command line, or "./configure-make-make-install from a source tarball)

I feel like i've been drinking from a fire hose with all the info on linux available (for which i'm very grateful!)

Any response is appreciated.

Thanks,
Andrew

---

### Post by kidders on 2007-07-09
Hi there,

I'll try to answer your questions. Some of them are more complicated than others ...

> **New-In-Ohio said:**
> Can I install debian, slackware, etc. on the 2nd harddrive without overwriting the boot program?That depends on the installers. Some installers (eg Ubuntu's) seem *insistent* on installing bootloaders, which I find rather stupid, personally. My advice would be to always assume that installing an OS will break a pre-existing bootloader. (That way, you might at least be pleasantly surprised on occasion hehe.)

Another issue that will crop up is that most OSs tend to assume *they* installed your bootloader in the first place, and may try to reinstall or reconfigure it during sotware updates, without asking permission. If I were you, I would elect one OS to take charge of things, and learn how to use its configuration tools to fix screw-ups. Bootloaders are notoriously delicate ... thankfully they're easy to manage.

> **New-In-Ohio said:**
> How do I get GRUB to automatically recognize new kernels?You can't. You could make it *appear* to do so, if you really wanted to, by configuring it to fly blind. Imagine...
[LIST]
[*]Your menu.lst contains menu entries for a variety of disk partitions (not all of which necessarily need to exist), eg /dev/sda1, /dev/sda2, /dev/sda3...
[*]Suppose you always arranged your Linuxes so they all booted in exactly the same way (ie you could accurately predict kernel parameters, etc).
[*]Now, any time you installed a new distro, a bootloader entry for it would always be there waiting for you, no matter where you put it.[/LIST]Personally, I wouldn't bother though.

> **New-In-Ohio said:**
> If I'm running another Linux distro, can I still mount my /home directory from ubuntu on the first hard drive?Yes, but with caution. You may or may not want all your Linuxes to share the same application settings ... especially if each uses different versions of the same software.

> **New-In-Ohio said:**
> Will programs that i have used apt-get to install still run under other linux distros by simply starting them from the command linePossibly, but don't try. As a guideline, it is not advisable to mount a distro's applications/libraries into another distro's filesystem in read/write mode. If you find yourself doing something that *requires* write access to another distro's system files, you're making a (possibly serious) mistake ... unless you're experienced, and know what you're doing.

> **New-In-Ohio said:**
> Is there a way to keep the ubuntu installation clean?  I mean never having any installed program write files to the original installation directories (wether its from synaptic, apt-get command line, or "./configure-make-make-install from a source tarball)Again, possibly ... but don't try. If I understand you correctly, it would defeat the purpose of installing an OS to begin with.

I hope that helps.

---

### Post by New-In-Ohio on 2007-07-09
This helps immensely.  Thanks for the answers, warnings, and cautions.  I know I need a new strategy.  I'll back up important items to usb pendrive, install some "let's really learn linux by fire" distros, and save ubuntu as a possible very last fresh install (only because i know it will load GRUB and recognize other os's).  I hope the likes of slackware, gentoo, and debian don't actually wipe out the MBR!?

---

### Post by kidders on 2007-07-10
They *can* do, but that doesn't pose a problem of any kind. The worst case scenario is that you might have to reinstall your bootloader on occasion ... something that most Linux users do on a regular basis anyway. It's perhaps the one place in the Linux world where the Microsoft approach works best hehe.

Your overall strategy seems fine to me though. :-) There's nothing at all wrong with throwing lots and lots of OSs onto your PC ... and it's certainly smart to keep your /home on a separate filesystem. Just remember...[LIST]
[*]With the possible exception of per-user applications (ie ones that exist entirely within your home directory), don't try to share apps between multiple operating systems.
[*]Keep an eye out for things that are ... well ... just plain stupid. A simple example might be installing 32-bit Thunderbird in Gentoo, and 64-bit Thunderbird in Ubuntu, and trying to manipulate them both into using the same settings & mail folders.
[*]Also, be wary of sharing swap space. Doing so can create complications, and effectively forces you to give up hibernating an OS.
[/LIST]

As one final (and totally random!) thought, I have developed a habit of performing all my disk partitioning and filesystem formatting manually. As well as protecting you from falling victim to buggy installers, it gives you the opportunity to label all your partitions intelligently ... something many installers won't let you do. Just think ... Debian, Ubuntu, Slackware, Gentoo ... say, maybe 3 disk partitions apiece ... things could get quite confusing without any labels!

---

### Post by luvr on 2007-07-10
> **kidders said:**
> Some installers (eg Ubuntu's) seem *insistent* on installing bootloaders
If I wanted to be nit-picking, I would say that **all** installers insist on installing a boot loader. Some may insist on writing the boot loader to the **Master Boot Record** of your boot disk (which will destroy your existing boot infrastructure), while others will give you the option to select where the boot loader should go (e.g., *Master Boot Record,* or *Boot Sector* of your root, or boot,  partition, possibly other options as well).
Until recently, I, too, believed that Ubuntu didn't let you choose where to install the boot loader, but I discovered that at least Ubuntu 7.04 does---see [this post of mine.]("http://ubuntuforums.org/showpost.php?p=2746942&postcount=5") (Keep in mind, though, that you will have to be familiar with the GRUB notation for identifying hard disks and their partitions in order to use this feature.)


> My advice would be to always assume that installing an OS will break a pre-existing bootloader.
Sound advice, indeed!

---

