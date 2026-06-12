---
title: "triple boot iMac Core Duo"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by LicensedLuncay on 2006-11-29
I am attempting to make a triple boot system, my understanding is the I need to install grub to the linux partition instead of to the MBR. To do that, I got the alternate install CD.
The problem is that the installer crashes as soon as I choose "text based install" this is the error message:

ata2: disabling port
hub_port_status failed (err -71)
connect-debounce failed, port 3 disabled
cannot disable port 3 (err -71)

is there something I can do? should I go back to the live cd? If I do use the live cd, is there a particular procedure I should use to get this to work? Am I going about this completely wrong?

---

### Post by ingo on 2006-12-01
I am not familiar with linux together with OSX, but GRUB would definitely be my bootloader of choice (meaning I'd put it in the MBR). Why wouldn't you want to do that?

---

### Post by LicensedLuncay on 2006-12-05
well... heh... My understanding is that I need rEFIt to deal with the fact that this is an intel mac. also... um... it looks WAY nicer. Also, I seem to be able to get either windows/osx or ubuntu/osx installs to work fine, using rEFIt, just not all three, so it must be capable of pulling this off. It even correctly detects the ubuntu partition, and recognizes that there is a windows partition. it's just that when it tries to point to them, if I have done the default install of ubuntu, putting grub on the mbr, it still won't boot.

---

### Post by ingo on 2006-12-05
you're right, grub doesn't cut the mustard on this one, lilo would, though. a quick google came up with this wiki page:

[http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp)

---

### Post by LicensedLuncay on 2006-12-05
Heh, that's actually the main one I've been trying. The problem is, I'm using a kinda specialized setup to get this to work. In this install, everything besides Ubuntu has been imaged so I can return it easily. Since I need to install lilo, I assume I'll need the alternate cd, I downloaded it, but unlike the live install, it doesn't run. I was wondering, would it be easier to just find commands to get lilo off the internet and onto the live cd so that it could then install it instead of grub than it would be to troubleshoot the alternate cd? does anyone know the commands to install lilo from the live install 6.10 disk instead of grub, and only on one partition?

---

### Post by ingo on 2006-12-05
in order to install lilo all you have to do is:

sudo apt-get install lilo

and Bob's your uncle :)

---

### Post by Hartimer on 2007-10-09
i have a similar problem.

I'm installing Ubuntu 7.04 on a imac 20'', i've followed the guide mentioned and some more like [this](http://wiki.onmac.net/index.php/Triple_Boot_via_BootCamp_Ubuntu)

That walkthrough has a part for [grub/lilo instalation](http://wiki.onmac.net/index.php/Talk:Triple_Boot_via_BootCamp_Ubuntu) but it is for edgy.

So, the problem seems to be, during instalation of ubuntu, grub should throw a bunch of errors (because IMacs use EFI systems to boot) and not get installed, although, it was installed for me with no errors what so ever. What i get in the end is a nice rEFIt boot screen, and when i choose either windows or linux i get into a second bootloader choice screen (grub).

what i want to do is keep MRB the way windows left it, install lilo on ubuntu partion and run a syncronization tool from rEFIt (which i've used before), but i don't know how to install lilo to the partition! could someone help me with this part? (removing grub seems easy... win cd, R botton and type "FIXMBR")

---

