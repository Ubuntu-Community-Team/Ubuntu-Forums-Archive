---
title: "Recommend Mac/ubuntu repair USB setup"
date: 2015-04-04
forum: Installation &amp; Upgrades
---

### Post by Tim_Johnson on 2015-04-04
I have recently installed ubuntu 14.04 on a Mac Mini via a usb stick.
I used the instructions found here : [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx).
I would like to prepare a rescue setup ahead of time, should a problem occur (and they have with an earlier ubuntu dual-boot on this machine).
From [http://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable/](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/super-grub2-disk-stable/), I have downloaded the
recommended hybrid **iso**. Currently, that is super_grub2_disk_hybrid_2.00s2.iso
Questions :
**1)** To create a USB bootable setup of supergrub2, would I use the same instructions as for the install stick?
**2)** Are there any recommendations for alternative repair setup?

I have noted that there are rescue schemes using the live install usb or cd also.[B]
3)[/B] Can the live install USB stick mount the exisiting ubuntu partitions with write privileges?

Thanks
tim

---

### Post by Tim_Johnson on 2015-04-06
Well gee whiz. Stumped the chumps again.

---

### Post by oldfred on 2015-04-08
Are you booting with UEFI?

I do not know Mac, but my PC would not boot super grub ISO in UEFI mode.

All my repair flash drives are multiple ISO loopmount with grub2. Then I have mulitple tools on one flash drive. I have Ubuntu, gparted, parted magic, and some others. 
I am finding it is a bit more difficult to UEFI boot and loopmount as ISO has to be both a loopmount configured and UEFI bootable.

---

### Post by Tim_Johnson on 2015-04-08
Hello Oldfred.

 I know little about UEFI. The operative use for Mac is  EFI. I've installed ubuntu successfully a couple of times using the  method here
[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx), which is a little scary because **dd** is scary, 
and should only be used while stone-cold sober and with a full night's sleep :wink: (IMHO).

 I'm going to use dd on the supergrub2 iso (converting first to .dmg)  and see if that boots. I also note that I can modify files on the hard
disk if I boot with the install stick, go to "try ubuntu" and sudo an editor ...

I'll report back after I try the supergrub->dd method.

thanks for the reply ... Mac issues are new ground for me.
"*Preparation is the best repair*."
stay tuned.

---

### Post by oldfred on 2015-04-08
If you have a bootable Ubuntu, I consider that all the repair I usually need. 
But I also like to have others, more of a belt & suspenders type I guess. Although I never have worn both. :)

---

### Post by Tim_Johnson on 2015-04-08
> **oldfred said:**
> If you have a bootable Ubuntu, I consider that all the repair I usually need. 
But I also like to have others, more of a belt & suspenders type I guess. Although I never have worn both. :)
Good analogy. Being so new to the Mac, I guess I'm going with both belt and suspenders.
Haven't go to dd'ing supergrub yet, be some time later today.
cheers

---

### Post by Tim_Johnson on 2015-04-08
I was able to burn the supergrub2 rescue disk to a thumb drive, using the dd method
referenced earlier in this thread. It boots successfully. 

I wanted to make a couple of comments, since I know that not a lot of dual-booting is done with Mac computers.
**1)** I first attempted to make a sd card bootable - dd would not write to it. Note: I've booted slax from an sd card
before, but that was on a pc or netbook, not a mac.
**2)**You can select the device by holding the option key down as the computer starts up. This (I think) is called *Startup Manager*.
   But, if I leave an external usb drive (which is used for backup) plugged in, for some reason the Mac does not "see" the bootable USB device,
   so I unplug the non-bootable external USB drive before starting up.

I guess, in Oldred's terms, I have both belt and suspenders, so I'm going to mark this as ***solved***.
cheers
tim

---

