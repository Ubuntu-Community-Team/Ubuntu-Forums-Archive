---
title: "Upgrading from Version 6.10 to Version 8.04"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by chemjeff on 2008-08-08
Hi,
I am trying to upgrade from Version 6.10 to Version 8.04.  However I get the following errors in the upgrade procedure:

W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Hash Sum mismatch
, W:Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2)  Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or old ones used instead.

How can I resolve this error?  Any help you could provide would be greatly appreciated.

Thanks,
-Jeff

---

### Post by Pumalite on 2008-08-08
You have to go step by step:
6.10>7.04>7.10>8.04
6.10 I think is not supported any more.
Why don't you do a clean install of 8.04? Less headaches

---

### Post by tuxxy on 2008-08-08
Yes I agree, a clean install is the way I would go too, be quicker if anything :)

---

### Post by chemjeff on 2008-08-08
Okay!  Does this mean I should start from a boot CD or is there a way I can download Ubuntu 8.04 to my hard drive and upgrade from there?

---

### Post by Pumalite on 2008-08-08
Download the iso from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by ChrisNY on 2008-08-08
I too will be attempting to do a clean install this weekend to update my 6.10 server to 8.04.  I believe I've heard about issues regarding permissions when you do a clean intall.  Is there a rule of thumb when setting up user accounts to keep everything in sync?  I have a separate partition for my home directory and want to make sure I don't screw up permissions during the upgrade.

Thanks!

-Chris

---

### Post by chemjeff on 2008-08-08
Hi,
I downloaded the ISO and burned it to a CD but when I reboot the computer it does not boot from the CD.  What is wrong?

---

### Post by Pumalite on 2008-08-08
CD has to be first in the boot order in BIOS. Did you do md5sum? Did you burn at 4x or less Did you check CD integrity? Did you burn the iso as 'image'?

---

### Post by chemjeff on 2008-08-08
1. The CD drive is first in the boot order in the BIOS.
2. I did md5sum on the downloaded image but I could not figure out how to do md5sum on the burned CD.
3. I followed the instructions on the page you gave but the option for changing the burning speed was greyed out and it didn't give me an option to burn as an image as opposed to some other format.  I just assumed it would automatically burn as an image?
4. I wasn't able to check the CD integrity because I wasn't able to boot from the CD.

I'm sorry if my questions seem pretty stupid, this is the first time I'm installing Ubuntu on my own.

---

### Post by Pumalite on 2008-08-08
Post your complete specs, especially memory and graphics. Give me the name of the iso you downloaded.

---

### Post by chemjeff on 2008-08-08
I downloaded the ISO named ubuntu-8.04.1-desktop-i386.iso.

I tried posting the results from the Device Manager but the forum rejected it because it had too many images.  I don't understand that one at all.  My computer has 512 MB of memory and an Intel Pentum 4 3.20 GHz processor.  I don't know exactly what kind of graphics card I have but I know it is an Nvidia-type card.  Is there a command I can run that can give me more information about my video card?

Thanks again for your help,
-Jeff

---

### Post by Pumalite on 2008-08-08
Your specs are OK. You should be able to boot a Live CD It's probable a bad burn. If you have Windows; download ImgBurn
[http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install. Go to Mode>ISO>Burn. Select 1x for speed.

---

