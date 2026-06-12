---
title: "And window onto a ubuntu as a duel boot"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by protocal on 2008-03-16
Hi 

I have be running Ubuntu 7.10 on my computer as the main operating system and it great
But I need to load window vista on my system for some programs that  need for work

I would prefer to do a duel boot operating system but I do not Like to remove my Ubuntu and lose all my work setting it up to run as well as it does

Can I setup window as the second duel boot  with out altering my operating system

Big Help needed And how to do this or save my system and reload it.

---

### Post by mikemc87 on 2008-03-19
I would also like to know this. Thanks

---

### Post by Herman on 2008-03-19
I don't know anything about Windows Vista, but it used to be possible for most people to install Windows XP after Ubuntu.
It depends a great deal on what kind of Windows Vista installation disk you have or can get. Some kinds of Windows installation CDs can understand hard disk partitioning and be told to install in a partition, while others can't be controlled and will overwrite your entire hard disk. You will need to know beforehand which type of Windows CD you have, and have Ubuntu well backed up just in case.

Another thing you won't be able to control is the installation of the boot loader. Windows will install it's boot loader to MBR whether you want it or not. All Windows installations do that.
You can make a backup of the boot loader part of your MBR beforehand if you want, here's how,  [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd").
It's just as easy to allow Windows to install its boot loader and then re-install GRUB later, it's easy to re-install GRUB to MBR, there are lots of way to do that. Here's my favourite way, [Re-install GRUB with a GRUB shell]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD"). - re-install GRUB from anywhere to anywhere with anything.

If you want to be really safe and to be able to do it the simplest way, if you have a little money you could go buy another hard drive and install Windows on its own hard drive, that might be an idea worth considering too. Hard drives are pretty cheap nowadays and it only takes a few minutes to plug one in if you know what you're doing.

Regards, Herman :)

---

