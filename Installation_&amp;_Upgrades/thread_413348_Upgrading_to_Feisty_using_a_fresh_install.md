---
title: "Upgrading to Feisty using a fresh install?"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by Corvo78 on 2007-04-19
First of all: I started using Edgy EFT since somewhere in the beginning of this year.
Which means, I'm quite new to upgrading my Ubuntu installation.

Having given it some thought, I think it would be best to do a fresh install of Feisty Fawn.
At the moment I have a seperate /home partition and mounted 1 drive as /home/user/Downloads and 1 drive as /home/user/Videos.
I also mounted my Windows drive as a readonly partition.
Last but not least, I use the following apps:[list][*]Thunderbird
[*]Firefox
[*]XMMS
[*]Nautlius
[*]VLC player
[*]HellaNZB and HellaHella
[*]Crossover (for World of Warcraft)
[*]Beryl[/list]Other then that, I remember configuring my Logitech mouse MX1000 and my video settings (Nvidia driver).
So, what would be the best way to do a clean install?


I'm guessing:[list][*]Backup all hidden /home folders (the ones that start with a dot) in a seperate new folder
[*]backup the /boot folder (kernels updates always break my grub)
[*]backup my fstab
[*]backup my HellaNZB.conf (which resides outside the /home, iirc)
[*]backup my xorg.conf, just in case
[*]Download 7.04
[*]Install 7.04 using a format of my / partition and remount 'the rest' without formatting
[*]Boot grub and manually edit the command in order to boot-up
[*]Feisty booted
[*]Fix grub
[*]Start installing apps
[*]Enjoy Feisty[/list]


Would this be a correct guestimate?
Are there any other things I should be aware of?

---

### Post by Corvo78 on 2007-04-19
In case my guess is correct, a simple yes would do aswell ;)

..
*(A shamefull bump of this topic, to be honest :-? )*

---

### Post by xyz on 2007-04-19
Check this out:
[Things you might want to back up before upgrading to Feisty]("http://ubuntuforums.org/showthread.php?t=412933")

---

### Post by Corvo78 on 2007-04-19
Thanks for the link!
I allready noticed something I forgot in my list, namely: backing up SMB.conf (totally forgot about Samba)

---

