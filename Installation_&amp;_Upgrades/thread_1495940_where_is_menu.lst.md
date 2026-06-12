---
title: "where is menu.lst?"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by jiminid on 2010-05-28
Hi,
Have 12 distros multi booting happily with xp and win7 64. My usual way of making sure that all of my distro boot properly is to go into each menu.lst and change the partition number to what it is supposed to be. usually just go into root/boot/grub/menu.lst and change the partition number. but it's not there.

Please advise.

---

### Post by darkod on 2010-05-28
> **jiminid said:**
> Hi,
Have 12 distros multi booting happily with xp and win7 64. My usual way of making sure that all of my distro boot properly is to go into each menu.lst and change the partition number to what it is supposed to be. usually just go into root/boot/grub/menu.lst and change the partition number. but it's not there.

Please advise.

Ubuntu since 9.10 comes with grub2 which doesn't use menu.lst any more.

The main config file is grub.cfg but it is not designed to be edited manually like menu.lst because grub2 can autodetect other OSs and creates the correct grub.cfg by itself.

---

### Post by kansasnoob on 2010-05-28
Very little info coming from a multi-booter :)

Ubuntu has now used grub 2 since Karmic and it has no menu.lst:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Quite often adding an OS to grub 2 is as simple as booting into Ubuntu and running:

```
sudo update-grub
```

Otherwise please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

And, of course, be specific about the problem you've encountered.

Or if you want to revert to legacy grub I wrote this:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

**[COLOR="Red"]But I highly recommend giving grub 2 a chance![/COLOR]** It grows on you :)

---

### Post by jiminid on 2010-05-30
Here's my hd setup:

hd	grub	format	os type
sda2	hd1,0	ntfs	winxp xp sp3
sda1	hd1,1	ntfs	Windows 7 Home Premium 64 bit
sda3	hd1,2	ntfs	windows data
			
sdb1	hd2,0	ntfs	windows-pics
sdb5	hd2,1	ntfs	windows-video
sdb6	hd2,2	ntfs	windows-family
sdb7	hd2,3	ntfs	windows-music
			
sdc1	hd0,0	ntfs	Windows 7 bootloader
sdc2	hd0,1	swap	linux-swap
sdc3	hd0,2	ext3	Pclos 2010 KDE
sdc5	hd0,4	ext3	Ubuntu 10.04 64 bit***
sdc6	hd0,5	ext3	Ultimate Edition 2.6 64 bit***
sdc7	hd0,6	ext3	Linux Mint 9.0 Isadora 64 bit***
sdc8	hd0,7	ext3	Mepis 8.5.01-pending
sdc9	hd0,8	ext3	Pclos Minime 2009.1
sdc10	hd0,9	ext3	Hymera
sdc11	hd0,10	ext3	Pclos 2010 E17-pending
sdc12	hd0,11	ext3	Elive 2.0 Topaz-pending
sdc13	hd0,12		open
			
sdd1	hd3,0	ntfs	backup
sdd2    hd3,1   ext3    backup

sdc is boot drive so grub sees it as hd0,x but when I install any ubuntu or derivative*** gives me a black screen or grub 15 error because it looks in hd2 so I have to go into menu.lst and change it to hd0,x to fix it. If I cant edit the new grub configfile I dont know how to fix this. a linux config file you cant edit? grub 2.0 may not be ready for prime time. doing a mac thing? weld down the hood so we dont mess anything up?

Would appreciate any ideas.

---

### Post by darkod on 2010-05-30
I have few ideas, but honestly I didn't understand a thing you said. :)

First of all, no one said you can't use manual entries with grub2. It's just that manually editing grub.cfg directly is not recommended, and in a way pointless because running update-grub next time will change it.

But you can put your own manual entries in /etc/grub.d/40_custom and with running update-grub they are added to grub.cfg automatically. The syntax of the entries is slightly different from grub1 so you'll need to read some grub2 tutorial how to construct them.

If sdc is your boot disk, and it also has 10.04 on it, did you install grub2 with 10.04 on its MBR or not? If you chose not to install bootloader with 10.04, you still depend on your 'old way', manually setting things up and sorting out your error 15.

If on the other hand you have grub2 installed on /dev/sdc and it doesn't work, that's another story.

Which one is it?

Grub2 would be able to automatically detect all your OSs and create entries for them. You should not see any error 15 relating to it. To me it sounds like you tried so hard to avoid grub2, that you made a total mix-up what grub are you running, from where, and where does it look for its config files.

Otherwise, regardless whether you are running grub1 or grub2, there is no reason to get error 15 or any other error. Not if your boot process is set up OK.

PS. Running the boot info script as kansas suggested will clear all dilemmas. And for your setup, I think it's a must. It will show in details your boot process.

---

### Post by bumanie on 2010-05-30
Suggest that you read [this]("http://ubuntuforums.org/showthread.php?t=1195275"), it has nearly everything you need to know to get grub2 working.

---

### Post by jiminid on 2010-05-30
> **bumanie said:**
> Suggest that you read [this]("http://ubuntuforums.org/showthread.php?t=1195275"), it has nearly everything you need to know to get grub2 working.

thanks will check it out. :)

---

### Post by jiminid on 2010-05-30
> **darkod said:**
> I have few ideas, but honestly I didn't understand a thing you said. :)

First of all, no one said you can't use manual entries with grub2. It's just that manually editing grub.cfg directly is not recommended, and in a way pointless because running update-grub next time will change it.

But you can put your own manual entries in /etc/grub.d/40_custom and with running update-grub they are added to grub.cfg automatically. The syntax of the entries is slightly different from grub1 so you'll need to read some grub2 tutorial how to construct them.

If sdc is your boot disk, and it also has 10.04 on it, did you install grub2 with 10.04 on its MBR or not? If you chose not to install bootloader with 10.04, you still depend on your 'old way', manually setting things up and sorting out your error 15.

If on the other hand you have grub2 installed on /dev/sdc and it doesn't work, that's another story.

Which one is it?

Grub2 would be able to automatically detect all your OSs and create entries for them. You should not see any error 15 relating to it. To me it sounds like you tried so hard to avoid grub2, that you made a total mix-up what grub are you running, from where, and where does it look for its config files.

Otherwise, regardless whether you are running grub1 or grub2, there is no reason to get error 15 or any other error. Not if your boot process is set up OK.

PS. Running the boot info script as kansas suggested will clear all dilemmas. And for your setup, I think it's a must. It will show in details your boot process.

pclinuxos is main grub installed to the mbr. all other distros I install grub to their individual root partitions then point to them from the main grub. That way no matter what distro I install, all I have to do is go into my main grub and change the title.btw I'm posting from pclos e17 that I just installed with no probs. I'll check out the boot info script and see what it gives me.sounds valuable. also the /etc/grub.d/40_custom
edit as well.

Thanks for your help everybody. will post back if I get stuck. :)

---

### Post by darkod on 2010-05-30
> **jiminid said:**
> pclinuxos is main grub installed to the mbr. all other distros I install grub to their individual root partitions then point to them from the main grub. That way no matter what distro I install, all I have to do is go into my main grub and change the title.btw I'm posting from pclos e17 that I just installed with no probs. I'll check out the boot info script and see what it gives me.sounds valuable. also the /etc/grub.d/40_custom
edit as well.

Thanks for your help everybody. will post back if I get stuck. :)

I can't say for sure for all of the distros you are using, but in general the rule is: once you have one linux running and grub/grub2 on the MBR, you don't need to install bootloader (grub/grub2) with any future linux install. Except unless you want to start using this new bootloader in which case install it to the MBR also.

Grub should be able to boot all the distros you have. Chainloading from grub to grub like you are doing is pointless because grub should boot all of them directly. No need for the second, chainloaded grub to come into play at all.

---

### Post by jiminid on 2010-06-13
> **darkod said:**
> I can't say for sure for all of the distros you are using, but in general the rule is: once you have one linux running and grub/grub2 on the MBR, you don't need to install bootloader (grub/grub2) with any future linux install. Except unless you want to start using this new bootloader in which case install it to the MBR also.

Grub should be able to boot all the distros you have. Chainloading from grub to grub like you are doing is pointless because grub should boot all of them directly. No need for the second, chainloaded grub to come into play at all.

I set the timeout on the additional grubs that I install into their own distros root partition to 0 so it has the same effect as booting directly to each distro. probably just what I'm used to. been doing it for years. grub 2.0 looks pretty much greek to me at this point. when I have some extra time, I'll probably study it and see how I can use it if pclos goes with it. I would probably use ubuntu or ultimate edition instead cause I like gnome but the boot screens look like something done by a dot matrix printer from the 80's. I know it's just eye candy but it's eye candy I look at 2 or 3 times a day.
BTW, I edited the grub.cfg files in ubuntu & ultimate and all is good. will probably have to do so after each upgrade til I figure out how to create the stanzas in 40_custom. not really a big deal. no time now to learn an entire new grub nomenclature.

Thanks again for the help.

jiminid ):P
Thanks again,

---

