---
title: "Stuck at GRUB with new install of Ubuntu 7.10"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by EvilPeppard on 2008-03-06
Hello all.  My first post here.

I tested out the "live" CD version of Ubuntu 7.10 Desktop and was absolutely impressed it found all my hardware and worked great.  I decided to go ahead and install it, but after the install, when my computer starts booting, it gets to GRUB and just sits there with a blinking cursor after GRUB.

I am a total Linux "newbie", so please have some patience.  I know a little, but will need some hand-holding in the beginning.  This machine is brand new.  I just ordered it from Dell.  Optiplex 755 mid-tower:

-Quad 6700
-4GB RAM
-256MB ATI RADEON HD 2400 XT Graphics dual DVI
-Dual Dell UltraSharp 22" 2208FP Wide Flat Panels
-250GB RAID 1 SATA
-Intel 82566DM-2 Gigabit NIC
-Integrated SoundMax Audio
-multi memory card reader
-dual DVD drives, one is a burner
-Vista Business installed

I installed using the guided install and hard drive setup.  I told it to use the full disk.  What can I do to get past this GRUB issue, please?

Thank you in advance for your patience and assistance.

---

### Post by dstew on 2008-03-06
Is what you see **grub>_** ? If so, enter **root(** then hit tab. Post the output to the forum. Probably, grub needs to be re-installed or reconfigured. We can do that.

---

### Post by EvilPeppard on 2008-03-06
> **dstew said:**
> Is what you see **grub>_** ? If so, enter **root(** then hit tab. Post the output to the forum. Probably, grub needs to be re-installed or reconfigured. We can do that.

No, it isn't that prompt, it shows my POST screen then I see "GRUB _" and that is it.  The underscore represents the blinking cursor.

I now am running Ubuntu from the CD again and have a terminal open and ran "sudo grub". I get a prompt "grub>" but when I type "root (0," and use the tab key, the response is "Error 21: Selected disk does not exist".

I'm not sure what to do here. Any other ideas?

---

### Post by EvilPeppard on 2008-03-06
Ok, after typing "root (hd0," and hitting tab, I get:

Partition num: 0, Filesystem type is ext2fs, partition type 0x83

Partition num: 4, Filesystem type unknown, partition type 0x82

Does that help?

---

### Post by EvilPeppard on 2008-03-06
Hmm, so you know, I tried typing "root (hd0)", pressing enter, the typing "quit".

I rebooted and it is still at the GRUB prompt with a flashing cursor after it. :(

---

### Post by EvilPeppard on 2008-03-06
Just ran this, from info I got from another forum:

[B]Next try:
root (hd0,0)
setup (hd0)
quit[/B]

Dang it! I thought this was going to work for sure. When I ran the "setup (hd0)" part, I got a whole bunch of "succeeded" lines. Unfortunately, when I rebooted, I still and stuck at the damn "GRUB" with a blinking cursor.

---

### Post by dstew on 2008-03-06
Sorry I am not so quick to the forum. Anyway, let's look at this logically. From the Live CD, open a terminal and enter the command```
sudo fdisk -l
```That will show all your partitions. Then we can try to re-install grub, as you tried to do. But you are certainly on the right track! It seems that your reinstall steps should have worked, but we need to get more detailed information about the problem. It is possible that you have grub installed on two different partitions, and the one you are booting might not be the one on (hd0).

---

### Post by EvilPeppard on 2008-03-06
> **dstew said:**
> Sorry I am not so quick to the forum. Anyway, let's look at this logically. From the Live CD, open a terminal and enter the command```
sudo fdisk -l
```That will show all your partitions. Then we can try to re-install grub, as you tried to do. But you are certainly on the right track! It seems that your reinstall steps should have worked, but we need to get more detailed information about the problem. It is possible that you have grub installed on two different partitions, and the one you are booting might not be the one on (hd0).
Ok, you bet I will try that.

So you know, as a test I just ran an install of Fedora 8 from its Live CD, which seems to run good on my computer too.  It wiped everything and my system boots up just fine into Fedora 8.  I wonder if something about the copy of Ubuntu I have doesn't properly format and install the MBR?

I will try reinstalling Ubuntu now and post back with results.

---

### Post by logos34 on 2008-03-06
> **EvilPeppard said:**
> 
-Quad 6700
-4GB RAM
-256MB ATI RADEON HD 2400 XT Graphics dual DVI
-Dual Dell UltraSharp 22" 2208FP Wide Flat Panels
[COLOR="Red"]-250GB RAID 1 SATA[/COLOR]
-Intel 82566DM-2 Gigabit NIC
-Integrated SoundMax Audio
-multi memory card reader
-dual DVD drives, one is a burner
-Vista Business installed

I installed using the guided install and hard drive setup.  I told it to use the full disk.  

Maybe the mirrored drive setup is causing the problem.

Perhaps you should be using [this guide]("https://help.ubuntu.com/community/FakeRaidHowto#head-a019bddf36ad61bc29d9b787c95d8921ea762ba9").  Someone correct me if I'm wrong.

---

### Post by EvilPeppard on 2008-03-06
I tried reloading Ubuntu after my successful install and running of Fedora 8.  I get the same thing again....stuck at "GRUB".

We may be on to something here.  The checksums failed to match on the image I have.  I just tested it with winMD5sum.

I am now downloading UBunto from a different source and will check its checksum, then go from there.

---

### Post by EvilPeppard on 2008-03-06
Ok *sigh*.  Something doesn't seem right.  All my image checksums are failing.

I have downloaded several different images so I could test different flavors of Linux:

Ubuntu, Fedora 8, BLAG, PCLinux 2.21, Fedora 8-KDE version, CentOS 5.1, and ZenWalk.

I am running winMD5sum against them all and all of them are failing to compare. ](*,)

---

### Post by EvilPeppard on 2008-03-07
> **EvilPeppard said:**
> Ok *sigh*.  Something doesn't seem right.  All my image checksums are failing.

I have downloaded several different images so I could test different flavors of Linux:

Ubuntu, Fedora 8, BLAG, PCLinux 2.21, Fedora 8-KDE version, CentOS 5.1, and ZenWalk.

I am running winMD5sum against them all and all of them are failing to compare. ](*,)

Ok, I discovered I was doing something wrong when comparing checksums.  I used info from [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes).  In fact, they do match.

---

### Post by EvilPeppard on 2008-03-07
Well, maybe it is just my machine, but I cannot get Ubuntu to install and run on this particular machine.  I may try another machine just for fun, just to rule out my machine.  I'll post the results so we know.

I am going to move forward and install Fedora 8, which did install and run correctly.  I can tell it is a little more advanced than Ubuntu, but I suppose it will help in my learning process.

Thank you all for your help.  As always, it is much appreciated.

---

### Post by EvilPeppard on 2008-03-07
I tried installing Ubuntu on another new computer, an Optiplex 755 as well, just with less performance components, i.e. no RAID, no dual monitor video card, no quad core CPU.  It installed and seems to be running fine.

Thank you again for everyone's time and support.

---

