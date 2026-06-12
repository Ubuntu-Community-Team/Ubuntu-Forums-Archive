---
title: "triple boot with 2 drives question Ubuntu Studio/Ubuntu/Vista"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by wbm on 2009-12-18
Hello, I hope someone can help me with the following.
I have a PC that currently dual boots Vista and Ubuntu from one internal 200gb drive.
Ubuntu is the main OS used by the family for e-mail, games, web, homework etc.

I want to add a second 500 gb SATA hard drive and install Ubuntu Studio on it for my music stuff.

When I add the second drive, can I just install UBuntu Studio on it and have it show up as a third option on boot up? Currently I can choose between Ubuntu and Vista on boot.
Will Ubuntu Studio then show up as a third option?

Is there anything else I have to be aware of before I do this? E.g. where does the bootloader actually sit? E.g. in case the first drive dies some day?
Thanks!!!

---

### Post by oldfred on 2009-12-18
Near the end of regular Ubuntu is an advanced button that lets you select where to install grub. Grub is normally installed to the boot drive usually sda, but you can select sdb.

I like to have operating systems on different drives and still have their boot loader in that drives MBR. That way if the first boot drive fails I can still boot the other drive.

I would install the boot loader to the second drive. Then after you boot your main install run update-grub to find the new install on the second drive.

There is also a command that is part of the grub install that says where to install grub. Some rerun this to prevent grub from installing to the wrong drive on an update.

reinstalls grub and allows choice of which drive to install to. Choose boot drive if not sda
sudo dpkg-reconfigure grub-pc
I finally found out how to prevent the MBR to be overwritten.
I ran dpkg-reconfigure grub-pc and deselected /dev/sda which meant that the values field for grub-pc/install_devices in /var/cache/apt/config.dat is now empty. Then nothing is written to the MBR or the boot sector when grub-pc gets updated. Occasionally I should probably rerun manually grub-install /dev/sda2 after grub-pc package updates to keep stage1 install in sync.

---

### Post by wbm on 2009-12-18
Thank you.
So you do have Grub on each drive?

---

### Post by audiomick on 2009-12-18
Just a word to the wise: there is only an "alternate DVD" for Ubuntu Studio, which has the text based installer, so no "advanced button", but it still gives you the chance to say where grub should go at the appropriate moment.

---

### Post by oldfred on 2009-12-18
Because I was chainbooting and have 3 drives I have grub installed everywhere, every boot partition PBR and every MBR. I am right now using grub2 and using the grub2 menu, but it finds so many sytems that the menu is very busy. I will modify it to just have a link to my grub partition and chainboot all the other operating systems. Grub2 dows not like to be installed to the PBR but it can be.

---

### Post by darkod on 2009-12-18
> **oldfred said:**
> Because I was chainbooting and have 3 drives I have grub installed everywhere, every boot partition PBR and every MBR. I am right now using grub2 and using the grub2 menu, but it finds so many sytems that the menu is very busy. I will modify it to just have a link to my grub partition and chainboot all the other operating systems. Grub2 dows not like to be installed to the PBR but it can be.

In other words, unless you want to play with grub2 a lot, just tell Ubuntu Studio not to install a bootloader, then boot your Ubuntu and do update-grub to find and add Studio as third choice to the list, as you wanted. :)
Fred loves grub. :lolflag:

---

### Post by oldfred on 2009-12-18
I do not disagree with Darko but I have learned to like grub2, I am just not a fan of a large menu and grub2 spending lots of time searching (which it does a great job of) for all my systems.

I would still install the second install's grub to the second drive's MBR just case someday you want/have to boot from that drive.

---

### Post by wbm on 2009-12-20
Well, this is how it went.
Installed the second drive.
Installed Ubuntu Studio (all 4 options, audio, video, graphics etc.) on new drive.
During install, it installed GRUB, configured GRUB and updated the GRUB menu.
After reboot all three Operating Systems showed up already.

So everything pretty much fixed and configured itself and all three OS'es are working without me really having to do anything.

---

