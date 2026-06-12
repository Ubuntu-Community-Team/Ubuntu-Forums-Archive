---
title: "GRUB not starting"
date: 2016-10-31
forum: Installation &amp; Upgrades
---

### Post by atemic on 2016-10-31
Hi everyone. I`m totally new to Ubuntu.

I have windows 10 on my asus S46C notebook and I wanted to dual boot Ubuntu 16.04. I followed a installation guide that, in summary, told me to do this:

1. Run windows and use diskmngt.msc.
2. Allocate some HD to receive Ubuntu.
3. Download Ubuntu 16.04 .iso from Ubuntu official website.
4. Use Linux Live USB Creator to create a bootable USB disk.
5. Install ubuntu using the advanced options and:
5.1. Allocate twice my RAM memory as SWAP (logic type).
5.2. Allocate 5 MB to BIOS (logic type).
5.3. Allocate the rest to ext4 (logic type and "/").

Ok, perfect. I can`t get Ubuntu running because GRUB does not initiate. I tried Boot Repair and I got the following: [http://paste2.org/KL2KMYnf](http://paste2.org/KL2KMYnf)

The most interesting thing is that if I run the same bootable USB that was used for installation, GRUB launches and gives me the options to try Ubuntu, install Ubuntu, Recover, etc...

Any help to a newbie, please?

Thanks.

---

### Post by Bucky Ball on 2016-10-31
*Thread moved to **Installation and Upgrades**.*

Welcome. Doesn't look like you installed Ubuntu in EFI mode. Don't know where you got that tutorial, but unless you're hibernating you don't need anywhere near that amount of /swap, and even if you were you don't. No hibernation, 2Gb is fine. Hibernation: same size as the physical RAM you have installed.

There is absolutetly no need for this:  Allocate 5 MB to BIOS (logic type). Always a good idea to include links to anything you've followed if you can.

To install in UEFI, which is what Win10 is in so you MUST install Ubuntu in the same mode, you boot to Win10 and switch off hibernation, boot to the BIOS and switch off faststart and secureboot, set the boot priority to boot from the USB entry with [UEFI] or [EFI] next to it.

Choose 'Something Else' during the install and delete the install you made previously and reinstall to there. You don't need to do much else.

---

### Post by atemic on 2016-11-01
Hey, thank you for the answer.

First of all, GRUB is working fine now. That's how I made it work: 

1. I ran Ubuntu trought the option "Try ubuntu" on the bootable USB. 

2. Then, I used the following commands on Terminal:

```
$ sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update 

$ sudo apt-get install -y boot-repair && boot-repair &
```

3. Boot repair's window popped up and I chose "Recommended repair" and followed all the steps (the last time a used this option I didn't realize there was more than one step... it is necessary to paste some command lines on terminal and wait ultill the data is processed to move to the next step of boot repair). 

When I restarted the notebook, GRUB came up and everything is working fine.

> [COLOR=#000000]Don't know where you got that tutorial, but unless you're hibernating you don't need anywhere near that amount of /swap, and even if you were you don't. No hibernation, 2Gb is fine. Hibernation: same size as the physical RAM you have installed.[/COLOR]

[COLOR=#000000]There is absolutetly no need for this: Allocate 5 MB to BIOS (logic type). Always a good idea to include links to anything you've followed if you can.[/COLOR]

@[COLOR=#000000]Bucky Ball, do you think it is still necessary to reinstall Ubuntu so that I can fix the 16 GB of swap to 8GB swap? Also, I used the 5 MB for BIOS because ubuntu instalation told me to allocate at least 1 MB to BIOS. So I thought 5 MB would be fine, lol. I'm not a IT professional, sorry.

[/COLOR]Thanks again.

---

### Post by Bucky Ball on 2016-11-01
All good. You can resize the /swap partition by booting to a 'live' session (Try Ubuntu from the install media) and resizing with Gparted. No need for a reinstall. As always, though, make sure you backup anything you don't want to lose in case things get ugly. 

Shrink the /swap and expand the partition next to it. Partitions must be unmounted to resize (right click in Gparted and 'unmount'). 

As your original issue is fixed, please mark the thread as SOLVED from 'Thread Tools' at the top right of the page or see the last link in my signature at the bottom of this post. This won't close it to further discussion. Thanks and thanks for sharing your fix. *Always* appreciated here and recommended. :) Good luck. :)

---

