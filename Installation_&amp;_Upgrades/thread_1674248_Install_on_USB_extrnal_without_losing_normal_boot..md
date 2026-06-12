---
title: "Install on USB extrnal without losing normal boot."
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by GrahamM on 2011-01-23
I have Ubuntu 10.04 installed on my desktop on it's own hard drive. The other drive has XP. Grub is on the Ubuntu drive. Everything works fine from the Grub menu. but I have lost the ability to boot from the XP drive. This would be a problem if the Ubuntu drive failed or if I wished to remove it. I would like to repair this, but my immediate problem is with a new install on my laptop:

We are going away for 2 months and I want to be able to continue to learn Ubuntu while away. I want to install it on a new external USB drive on my Win 7 based Toshiba Satellite (ADATA Superior SH93). I did a trial run up to where I have to choose the drive to install to. But based on my experience with my Desktop, I stopped there. I can't afford to have the Win 7 boot disabled.

My question: How do I install 10.10 (or 10.04) to a laptop USB drive without affecting the ability to boot from Windows when the usb drive is removed?

In other words, when I remove the usb drive, the laptop should be 100% as it was before the install.

Any help appreciated!

---

### Post by GrahamM on 2011-01-24
I was hoping for some guidance :(

If it was desktop, I would totally disable the drive I want to protect. Not so easy on the laptop.

---

### Post by jeannacav on 2011-01-24
I have not done this but I think it is a cool plan.
I do not understand your concern.
(Maybe your concern IS a valid one, but, I cannot see what can be wrong with your plan.) 

Again, I have not done this and I do not know how well ubuntu would work from a usb drive. I would predict that it would be very slow. So, if you know the answers to those questions, then there should not be a problem.

It seems that if you change the BIOS to check the USB drive BEFORE the hard drive, it will simply bypass the empty usb drive and go onto the hard drive and boot your Windoze system and never know the dif.


So, you need to find out how to get to the BIOS, then go there and change the boot order.

...and even if it doesn't work or works badly, the windows part of your system will remain unchanged.

jeanna

edit
see next post.

---

### Post by kansasnoob on 2011-01-24
You'll need to be certain that you install grub to the MBR of the external drive! So how well do you understand Ubuntu device designations?

There are some big differences between the 10.04 installer and the 10.10 installer. I pointed out some of the changes to the 10.10 installer here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

With the 10.10 installer:

> The option to choose where to install grub is now only available if you choose “Manual partitioning”, and there is no option to not install grub. AFAIK if you don’t want to install grub to the mbr of a drive you must now install grub to the pbr of the new "/" (aka: root) partition or the “/boot” partition if one is being created.

As shown here:

[http://members.iinet.net.au/%7Eherman546/p22/035.png](http://members.iinet.net.au/%7Eherman546/p22/035.png)

With the 10.04 installer there's a final review screen with an advanced button:

[http://members.iinet.net/%7Eherman546/p28/032_install-now.png](http://members.iinet.net/%7Eherman546/p28/032_install-now.png)

If you click on the advanced button you can select where to install grub.

Clear as mud?

---

### Post by GrahamM on 2011-01-24
> **kansasnoob said:**
> You'll need to be certain that you install grub to the MBR of the external drive! So how well do you understand Ubuntu device designations? 

I think I understand them enough and I realize grub should go to external drive. But somehow when I installed on my desktop, I lost the ability to boot from the Windows drive, even although I have grub and 10.04 on a separate drive. But that could have happened during an unsuccessful install of 10.10 to the Desktop. Maybe it messed up the C: drive.

> There are some big differences between the 10.04 installer and the 10.10 installer. I pointed out some of the changes to the 10.10 installer here:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
With the 10.10 installer:

As shown here:

[http://members.iinet.net.au/%7Eherman546/p22/035.png](http://members.iinet.net.au/%7Eherman546/p22/035.png)

With the 10.04 installer there's a final review screen with an advanced button:

[http://members.iinet.net/%7Eherman546/p28/032_install-now.png](http://members.iinet.net/%7Eherman546/p28/032_install-now.png)

If you click on the advanced button you can select where to install grub.

Clear as mud?

I have run through both installs in past and your explanation of the differences is very useful. I did in fact install 10.10 to a different small external USB HD on my laptop and that did work even although I had no clue of possible problems! But now, after messing up my Desktop Windows drive boot capability, I am being wary of any possible pitfalls!

Maybe I will just go ahead. Maybe stick with 10.04? But I would like to check out 10.10 and see what is "better" about it. Sort of a second chance, because it would not install on my Desktop whereas 10.04 installed smoothly with no tweaks required.

PS: I am told I can use the XP repair disk to fix my Desktop windows drive, but Windows says I must uninstall various stuff before that can be done! Maybe just do an MBR or Fixboot?

PPS: jeannacav - Thanks for responding - As you see, my concern is to avoid anything that will corrupt my laptop HD.

---

### Post by GrahamM on 2011-01-28
I installed 10.04 to usb drive on laptop. Drive is old laptop HD in USB case 6GB. 10.04 with some of my files takes about 4Gb, so not much left. Keep getting error messages due to lack of HD space. 

Maybe I should buy a 16Gb SD card and use that. Or maybe get rid of all files that I can access on win drive. This is just to mess with while away from home for 2 months. 10.04 works fine on my old Athlon 1Gb, 900Mb RAM desktop, even although 10.10 would not install. Hopefully next LTS will also run on this machine.

Have a 320Gb usb drive, but using that for backup of win 7 at present. Could use that for ubuntu on laptop an get a 1 or 2 Tb drive for backups.

---

