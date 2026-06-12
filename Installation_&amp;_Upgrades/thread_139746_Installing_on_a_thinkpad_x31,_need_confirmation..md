---
title: "Installing on a thinkpad x31, need confirmation."
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by dsp82 on 2006-03-04
Total newbie here, never tried installing any linux distribution. I've tried it severel times though through vmware, but my guess is that it's just not the same, so i'd like to give you of rundown of what i've done so far and tell me if i'm missing anything.

I'm installing ubuntu on a thinkpad x31 notebook.

Specs: PM-1400mhz, 768mb ram, 60gb 7200rpm, wifi, no optical drive.

Since it doesn't have any optical drive, i'll try to do it through a usb harddrive. I've used syslinux to create the ldlinux.sys file, so i'll be able to boot to the the usbdrive. Then i copied all the contents of the ubuntu cd to the drive and moved the content of the install and isolinux to the root. Renamed isolinux.cfg to syslinux.cfg and edited so all traces of /install/ were gone. 

Im planning on using dual boot to both have winxp and ubuntu. Since i don't plan on using ubuntu much to begin with, i only partioned a 4.7gb ext2 drive and a 300mb swap drive using partition magic.

This is basicly where i am now and i still have some question i hope you could answer.
1. I've read some pieces of how to uninstall ubuntu in case i don't wish to use it anymore and noticed some artices about GRUB og MBR. I've tried to wiki this but still don't quite understand what they are. Are the some extra appz i need to install? I didn't come across them when i used vmware, so i'm a bit confused.
2. I know the swap size should be 2xRam, but i have 768mb ram and don't plan to use any proces heavy appz, so i though 300mb should be enough. Is it enough or should i make it larger?
3. My initial though is that ubuntu won't have all the drivers for my notebook, which i don't see as a major problem. I can allways later find them on the net and install them UNLESS i can't get on the internet which is where my wifi driver comes in. How do i make sure i can get on the net as soon as i've installed ubuntu? I've found the linux wifi drivers for my notebook here

[http://ipw2200.sourceforge.net/](http://ipw2200.sourceforge.net/)

but can someone give me a quick rundown of how i install this. I now i have to unpack it, but then what???

That's about all, hope someone can help me. 

And please be kind, if i've allready could have found the answer somewhere by searching, believe me i've did, i just want to be completely sure...

Thanx.

---

