---
title: "Updating Lucid alpha3 leads to &quot;GRUB _&quot;"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lifelessdead on 2010-03-27
[B]Updating *packages* in Lucid alpha3 leads to "GRUB _"

[/B]Hi,

I've got an "exotic" configuration where:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612        5613    24113565   83  Linux

NTLDR is installed on sda1 and has an entry containing the 'dd'-ed bootsector of sda2.

This works brilliantly after installing Lucid from the LiveCD (including Grub2 on /dev/sda2), unfortunately, it come crashing down completely after installing the Grub update that's part of the post-alpha3 updates.

Once that update is installed Grub gets stuck on a "GRUB _" (with blinking underscore) prompt and nothing seems to help.

I tried doing some 'grub-install's from the live CD (including forced ones to get round the warning that installing grub on a partition is bad). This does not seem to help a bit.

I'd really like it if someone could point me to a way to fix this without yet another reinstall.
(I'd like it even better if some one fixes the problem with that update, this should not happen. If anyone needs any more info, just ask. I'll leave it stuck as it is for now.)

Note: it is the Grub update, if I update all other packages -except grub-, the system boots fine!

---

### Post by lifelessdead on 2010-03-28
Update; tried the following:

- Tried all the magic grub keystrokes to get it to boot. It doesn't get that far.
- Checked grub.conf -> looks fine 
- Tried update grub from LiveCD -> doesn't help
- Tried (re)install grub using 'forced' -> doesn't help
- Re-dumped the boot sector -> doesn't help

You know what, I'm getting fed up with this, I'm going to do another reinstall.
(note: I have to explicitly reformat that disk, otherwise the first boot after install doesn't work. Apparently the installer misses something in the mbr)

And yes, I *could* install Grub on the main partition, but to be honest, I don't want to, and I should not *need* to do that. Windows sucks for overwriting other partitions, OSX does the same, and now Ubuntu seems to prefer that as well.

---

### Post by lifelessdead on 2010-03-28
Update 2; 

Apparently it is no longer allowed in the Beta1 installer to manually edit the boot loader location to /dev/sda2 (in 'Ready to install', 'Advanced...'). The 'OK' button remains grayed out if the string has been edited.

That kind of sucks because I hate touching the MBR of my other OSses...

---

### Post by kansasnoob on 2010-03-28
Yeah, I think grub2 does balk about being installed to a partition.

Now, I use grub2 to boot with anyway but quite often on my multi-boots I just "uncheck" the install bootloader box in that final Advanced screen. Then I can use my existing grub2 to find and boot the new OS.

I don't really understand what "other" bootloader you're using but I have reverted some grub2 installs to legacy grub for certain specific reasons:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

There's even a link there for using a chroot if needed:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

Something I haven't bothered writing up yet is how to use wget and dpkg to install packages thru a chroot if package management let's you down. It goes something like this:

wget <link-to-package>
sudo dpkg -i '<location/package-name'

Example only:

```
wget http://security.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta4-1ubuntu4.1_i386.deb
dpkg -i '/home/lance/grub-pc_1.97~beta4-1ubuntu4.1_i386.deb'
```

Of course you can always find the packages here:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by psusi on 2010-03-28
Are you getting this before the windows boot menu or after?  If before then grub tried to install itself to your MBR.  Grub does not like being installed to the partition boot sector since it has to embed the block addresses of the core file directly, which breaks if the file is ever moved, for instance, after a resize or defrag.

---

### Post by kansasnoob on 2010-03-28
Adding also: you shouldn't be worried about changing the mbr of a drive. Just know ahead of time how to change it back ;)

I think you'd honestly like the new grub2 if you just tried it. I generally multi-boot a bunch and it just works great for me:

[ATTACH]151710[/ATTACH]

---

### Post by sgage on 2010-03-28
I use a similar setup (booting Lucid from the Windows bootloader).

I always use EasyBCD (free download, just google it up). Get the recent beta version - it works better with grub2. One caveat: it will only work if the Linux installation is in a primary partition.

Other than that, it works great. Once in a while, after a raft of updates, I'll get the same grub _ thing, or just a black screen. I just boot to Windows, run EasyBCD, delete the Linux entry and add another right back in, and all is well.

---

