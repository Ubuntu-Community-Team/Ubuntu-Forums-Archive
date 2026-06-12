---
title: "Opinions on Dual Boot Instalation"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2005-10-10
Just thought I'd check with you wizards before I try this. I've had a taste of Ubuntu Hoary Hegehog; Had a spare hard drive which I loaded it on and all went pretty well other than getting Jave loaded (another story). I am impressed.
I have two 160GB drives. The first is partitioned in half with XP ofcourse using the first partition. I was planning on using part of the second partition for Ubuntu; was thinking of 10/15GB For Ubuntu. I am hoping to have a dual boot system. There are certain things I can't do in Linux like play Chessmaster 10th edition.
How does it sound so far? Anything I should watch out for? Will it work? Opinions?:confused: 

TIA Allan

---

### Post by aysiu on 2005-10-10
It will work. With that much hard drive space, I'd advise creating a FAT32 partition as well, so you can share files between Windows and Ubuntu. Ubuntu can't write to NTFS, and Windows can't write to EXT3.

---

### Post by AllanP on 2005-10-10
Good advice. Do I need anything else like Lilo to dual boot or does Linux or XP handle it?

Thanks again for the help.

Regards, Allan

---

### Post by SilentCacophony on 2005-10-10
Hi. As aysui mentioned it should be no problem, and it's a great idea to have a FAT32 partition as well to share data between OSes. Also, 10-15 GB is plenty of room (I use a mere 5 GB for Ubuntu, and don't see filling it.) What I do is store most of my downloads and files on the shared partition instead of the 'home' directory.

Keep in mind that you'll also need a swap partition, which is generally suggested to be 1.5-2 times your phisical RAM. Ubuntu can make that for you, or you can make the partitions yourself beforehand, and choose the 'manually edit partitions' option in the installer.

EDIT - Also, Ubuntu will ask if you want to install GRUB to the MBR, which is generally what most users want. It'll 'automagically' detect Windows, and add it as a choice to boot from.

---

### Post by AllanP on 2005-10-10
Thanks. I thought I read somewhere about problems with GRUB. What's the purpose of installing it. Being a long time Windows user and a couple of years of DOS, I am really a greenhorn here.
Ooooooooops just did a search on GRUB; the light dawns.

Regards, Allan

---

### Post by SilentCacophony on 2005-10-10
Well, I hear that you can make Windows 2000 or XP handle the dual boot, but grub just seems easier to me.

Also, someone from these forums wrote this guide to help out setting up dual-booting:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

and the is a page in the official Wiki (sift through the rest of it, too. Good info) here:

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by az on 2005-10-10
[QUOTE=AllanP]Thanks. I thought I read somewhere about problems with GRUB. What's the purpose of installing it. Being a long time Windows user and a couple of years of DOS, I am really a greenhorn here.
Ooooooooops just did a search on GRUB; the light dawns.

Regards, Allan[/QUOTE]

If you install Breezy, the default option is for it to select your WIndows partition and offer to shrink it.  You decide on the space you want to give ubuntu and it creates that free space for you.  Afterwards, just take the default and it will make a root and swap partition for you on that free space.  Also, the default grub installation will work fine for you.

---

### Post by AllanP on 2005-10-10
Thanks all; a lot of helpful advice to consider. Maybe I should wait for Breezy but, I am a bit on the compulsive side and want to do it now. I guess I could always install Breezy over Hedgehog. I see they have a preview release of "The Breezy Badger". Should one take a chance on it?

---

### Post by az on 2005-10-10
[QUOTE=AllanP]Thanks all; a lot of helpful advice to consider. Maybe I should wait for Breezy but, I am a bit on the compulsive side and want to do it now. I guess I could always install Breezy over Hedgehog. I see they have a preview release of "The Breezy Badger". Should one take a chance on it?[/QUOTE]

It will release in less than 100 hours.  You will be fine.

---

### Post by Mitt3ns on 2005-10-10
Right now i am running dual Ubuntu with Win Xp. Works totally fine. Just make sure that you are doing the default install to write over the whole disk. I accidentally did that to find Xp wiped and just Ubuntu. But, second time around, it is working fine. 

[quote="azz"]It will release in less than 100 hours. You will be fine.[/quote]

Instead of having to totally re-install, is it possible to just get updates online?

---

### Post by Chris Cromer on 2005-10-11
[QUOTE=Mitt3ns]Instead of having to totally re-install, is it possible to just get updates online?[/QUOTE]Yes you can update without having to re-install.

Open a terminal and type this:
```
sudo gedit /etc/apt/sources.list
```

Now change all of the instances of the word "Hoary" to "Breezy" and "Hoary Hedgehog" to "Breezy Badger" and save the file.

Next type this:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

Then it will download all the breezy packages and upgrade to breezy.

Remember don't do this unless your are comfortable with the fact that breezy is still being worked on and could have bugs. It should be released on the 13th though, and that's when it should be safe to do the upgrade from hoary.

---

### Post by Mitt3ns on 2005-10-16
when i try to get it to upgrade im getting an error about the cdrom. So i decided to check out the first line of the sources.

"deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20050407)]/ breezymain restricted"

As you can see, i also changeed the 5.04 to 5.10. I think that it is trying to read off of a cdrom, but im not sure :/


edit**** i changed the deb cdrom to "eb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted universe "

---

