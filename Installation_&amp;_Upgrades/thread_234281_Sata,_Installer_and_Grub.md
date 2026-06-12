---
title: "Sata, Installer and Grub"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by Pablo El Vagabundo on 2006-08-11
Hi Guys, 

I've run into a problem with my new SATA drive. The ubuntu installer did not install grub and when I try to run grub-installer manually from liveCD I get: 

/dev/sda not a block device
<in work so I do not have the exact error>

I have bounced around the forums and it seems to be a common problem. I do have an IDE drive installed and from the fourms it seems grub might be installed there. I will have to check this when I go home.

Some posts have suggested that using grub rather then grub installer will work better. 

Is there a bug in grub or the liveCD registered?? I checked launchpad but could not find anything.

I'll try a few things tonight to get it working, if it doesnt I might install a different boot manager.

Pablo

---

### Post by Saubazi on 2006-08-11
Mmm...I have a mixed set-up in my machine too and it works. The grub is installed on MBR of the first IDE disk, however one has to be careful with the locations - for instance /boot/ which is in my case on the SATA disk and the (hdx,y) has to point into this one...

I give an example when installing grub I wrote grub then
grub>root (hd2,0)
grub>setup (hd0)
grub>quit

The first command links to /boot directory on the SATA drive
second one writes installs grub to MBR of the first drive (IDE in this case)

In my case I have /dev/hda and /dev/hdb as IDE devices - SATA is /dev/sda hence (hd2,0) ~ /dev/sda1

now in /boot/grub/menu.lst you've got  
to re-enter the root(hd2,0) and later in the line describing kernel insert the actual device of root partition - in my case I had it as root=/dev/sda3

---

### Post by Pablo El Vagabundo on 2006-08-11
Thanks for the reply.

I will try that when I get home tonight. My linux boot partition is on the SATA drive and I want the MBR there too. 

from reading around a:

find /boot/grub/stage1

in grub should return two hits for me. One on the old installation on the ide drive and another on the new installation on the SATA.

Maybe I was using it wrong but I tried the following after chrooting to the new linux install from the livecd:

grub-installer /dev/sda

It told me that /dev/sda is not a block device.

pablo

---

### Post by Pablo El Vagabundo on 2006-08-12
Hi All, 

Finially got dapper booting from my SATA disk.

I installed an MBR on the SATA disk<using root (hd1) and then setup(hd1). But it would not boot, saying error 15: file not found.

After some messing around in the Grub shell I found that it and the grub bootloader where getting confused about the naming scheme.

Grub shell <and the menu.lst> called my disks:

/dev/hda -> hd0
/dev/sda -> hd1

But the boot loader on the sata disk believed that:

/dev/sda -> hd0
/dev/hda -> hd1

So I altered my /boot/grub/menu.lst and setup gruib on the sata disk and bingo!! It worked.

Not sure if this is a bug or the way it is suppose to work. But there should be some change for edgy to make this easier. Possibly using the bios settings.

Note: I could have been asked in the installer where it wanted to put grub, but I do not rememeber it appearing.

Thanks for all your help...

Hopefully this post helps out some other poor soul.

Pablo

---

