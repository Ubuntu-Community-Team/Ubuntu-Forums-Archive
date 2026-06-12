---
title: "[SOLVED] Minimal encrypted Ubuntu 8.04 install with easy upgrade possibilities"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by scooterpd on 2008-07-21
I have a laptop with two seperate 80gb hdd's, currently running xp pro sp2.  i am looking to dual boot ubuntu 8.04 with this, but i have some serious questions.

Notes:
-I know that i want the entire ubuntu install encrypted, using this guide ([http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04-p1](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04-p1)).
-i know that i want to use the minimal cd iso and build my ubuntu from there.
-i know that i want a seperate /home partition.
-i know that i want to be able to install the newer releases of ubuntu as they become available (move from hardy to intrepid without losing /home data)
-i think i want my partitioning scheme as follows

hard drive one
	partition 1 - windows xp - ntfs
	partition 2 - ubuntu - ext3 - encrypted
	partition 3 - ubuntu /home - ext3 (i would also like to be able to access these files from my windows partition using...) - encrypted
	partition 4 - swap
	
if i create the partitions using the menu that comes with the minimal iso installer, will it erase my existing windows partition?
i am still contemplating which formats to use (ext3, xfs, reiser)
	
1.  when the time comes, how would i install intrepid on top of hardy without affecting /home?
2.  will the answer to question 1 completely remove all of the apps that i installed on hardy and/or install apps not on my hardy installation?
3.  is there a way to write a script to reinstall the apps that i had on hardy onto intrepid?
4.  since i am building from the minimal cd anyway, is there going to be that much of a difference between hardy and intrepid, other than kernel and themes)
5.  once i get the perfect install, what is the best way to create an iso of my custom install so that i can burn a cd and install the same setup(not partitions, just apps and themes and stuff) on other computers for different users?
6.  any other problems that may occur?

thank you in advance for all of your help and suggestions.  i am looking forward to perfecting this.

---

### Post by mpb_ on 2008-07-26
I've never used the minimal CD.  As I type this I'm using the 8.04 Alternate CD to do my first encrypted install of Ubuntu.  In the past I did an encrypted install of Gentoo (which was a ton of work to set up - I decided never to do a manual encrypted install again).  When I switched from Gentoo to Ubuntu around 7.04, I just encrypted my /home partition, as Ubuntu did not support full system encryption at that time.

So I may not know the exact answers to your questions, but since no one else has answered, here goes...

1) I doubt any Ubuntu installer will delete existing partitions unless you tell it to.  (But be sure to back up and valuable data just in case.  I use separate hard drives so I can physically remove valuable data from the system before installing/upgrading.)

2) I think you'll need one more partition than you list.  You will need a small /boot partition.  /boot will be unencrypted.  It sole purpose is to boot the kernel, mount the encrypted drives and then pivot into the encrypted drive, and then unmount the boot partition.  I could be wrong about this, but that is how things worked in the past.  The Alternate install CD creates a 255MB /boot partition.  I use ext2 as it works better on small partitions.

3) I would recommend ext3.  I haven't had problems with it.  I heard rumors that reiser and maybe xfs are more susceptible to corruption, especially if they are encrypted.  These rumors could be wrong - I am not an expert.

4) If you want to mount encrypted drives in Windows + Linux, you may have to use TrueCrypt.  TrueCrypt is a joy to use on Windows, but is not supported by Ubuntu, and as a result I've never tried using in with Linux.

5) I never upgrade, I always do fresh installs of new versions.  But if /home is a separate partition, there should be no problem upgrading while leaving it in place.  I always mount my /home partition manually, or via an rc.local script that I write by hand.  I don't want Ubuntu to try to touch it automatically.  If I were to upgrade, I would probably unmount /home first.

6) Regarding writing scripts to install Intrepid versions of your Hardy aps, I know you can tell apt to dump a list of installed packages.  Then you could just tell Intrepid to install those apps.  If you upgrade (instead of doing a clean install), I believe all you packages will automatically get upgraded.  I use a different method.  I have a script that installs all the package I want.  So I just run it after every install.  Again, I'm doing things manually (or via my own scripts) rather than using the infrastructure that apt provides.  That's just my style.

7) The below page talks about adding/removing packages to an ISO.  I have never tried it.  (I have converted the ISO to a bootable USB drive, with occasional success apparently primarily depending on the capabilities/compatibility of the motherboard I want to install on.)

[http://edoceo.com/liber/ubuntu-live-usb](http://edoceo.com/liber/ubuntu-live-usb)

8) If you have a spare PC (and/or spare hard drives lying around) I strongly recommend doing some practice installs on it before working on your primary machine/hard drives.

9) You might also want to look at LVM a bit.  LVM lets you create one encrypted partition, and then nest virtual "sub-partitions" inside it.  I believe the default encrypted install uses the whole disk and puts / and swap (and /tmp and others?) inside a single LVM partition.  The advantage is that there is just one encryption layer (and one password) wrapping all the partitions.  I have no experience using LVM.

-mpb

---

### Post by scooterpd on 2008-07-29
Thank you for all of the useful info mpb.  Real quick though...> **mpb_ said:**
> I use a different method.  I have a script that installs all the package I want.  So I just run it after every install...That's just my style.

Interesting.  How do you go about creating a script like this.  I know how to create a list of all installed packages using the following code```
dpkg --get-selection > installedpackages.txt
```but how do you create a script from that that will install those packages.  I would want to create a script so that i can easily install the same setup on a different computer in the house.

---

