---
title: "Disk Sizing Issue"
date: 2017-06-26
forum: Installation &amp; Upgrades
---

### Post by baguk on 2017-06-26
Hi, ):P

I'm relatively new to Ubuntu admin work although I have been using Ubuntu GUI for some time with no issues.

I made the jump and installed Ubuntu 14.? a while ago and everything was OK. I ended up with a 512Mb boot device and a 300Gb encrypted drive using the default settings. I use USB and NAS drives for storage which means I don't really have issues with backup of the system. A few weeks ago I patched my system using the in built patcher and it jammed my system, it had run out of disk space on the root drive. I backed up my encrypted drive which had about 100Gb of files on it and proceeded to re install the latest version of Ubuntu from the website.

When I was finished I still had a 512Mb boot drive and despite everything I did, creating new partitions using the two tools available it refused to generate a 2Gb boot while encrypting my drive. I had swap errors failure or running out of disk space. I run out of disk space on a 2Gb drive while the default uses a 512Mb drive successfully. Clearly it copied different things to different places and without the right drives I run out of space.

How can I create a 2Gb, or whatever the minimum must be, while creating an encrypted drive for the remaining space similar to what is created when I use install, select delete disk and an encrypted partitions.

I'm tearing my hair out with what seems to be a simple task. Any help would be appreciated. I'm clearly making fundamental errors.

Thank you in advance.

---

### Post by CatKiller on 2017-06-26
You'll want a /boot partition for UEFI. As you've found, the default is 512 MB, which is fine as long as you don't keep dozens of old kernels around. Otherwise, you can make that bigger if you want. That needs to be FAT32.

You'll need a / partition. If you were trying to squeeze that into 2 GB, it's not surprising you ran out of space. At least 15 GB for that, I think, is the recommendation. ext4 is a sensible choice for that.

Having a /home partition is useful. It means you can keep all your data and settings if you need to reinstall the OS. ext4 is, again, a sensible choice. As big as you can spare.

Having a swap partition used to be essential. I'm not sure if it still is. Twice the size of your RAM used to be the rule of thumb.

---

### Post by baguk on 2017-06-26
Thank you for the response. So I'm clear. I'm fine with the 512Mb as boot which then loasd the encrypted drive. This encrypted container contains / /usr /home and everything else, including Swap then.

That sound like what I had and makes sense. So how do I automatically purge the old kernels. Running out of space in the /boot was the issue and it was manually deleting them that screwed me up first time. is there a script or setting I should use?

---

### Post by CatKiller on 2017-06-26
I just uninstall the old ones with the package manager once I've successfully booted the new one once or twice. There is a setting somewhere, I think, to determine how many old kernels are kept, but it's not something I've looked into since I tend to keep them tidy through OCD and I don't have a /boot partition in any case. I think each kernel image is somewhere on the order of 100-200 MB. [This page]("https://askubuntu.com/questions/620266/how-does-apt-decide-how-many-old-kernels-to-keep") suggests it's controlled through the apt-get autoclean mechanism.

I don't know for sure that your swap partition would necessarily be part of your other encrypted partition, or if it would be encrypted separately. A swap file would definitely be part of your encrypted / partition though. A swap partition definitely used to be the way to go, but I've got a feeling that at some point a swap file was thought to match it in terms of utility. Possibly because of ease of inclusion in an encrypted partition.

It sounds like you're back on track now.

For the sake of completeness, some of the space on the / partition is reserved so that if you otherwise run out of space, you can still boot to a recovery console to free up some space. Bit late for the information for you now, but it'll be useful for next time ;)

---

### Post by baguk on 2017-06-26
Catkiller, 

I'll find out what the command are now I understand what is going on. It would have been nice not to have to reinstall but I didn't lose any data and it has been a learning experience.

Thanks again. Your help is very much appreciated.

:popcorn:

---

