---
title: "Ubuntu on 8Gb USB Not Booting"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by bearslumber on 2008-06-03
Hi,

I have installed Ubuntu 8.04 LTS Desktop version on my 8gb USB, but I am unable to boot into it.

I get the following errors:
Error 17: Cannot mount selected partition, when loading any of the ubuntu options, and
Error 13: Invalid or Unsupported executable format.

I used the (from the live CD) guided Install to entire disk and chose /dev/sdb which is my USB stick.

In the advanced options I chose to load the boot loader on to /dev/sdb (I am beginning to think that this was a mistake and I should not have installed the bootloader at all as I explain if you read on). 

I did not want to erase the current boot loader on the main hard drive. It automatically attempts booting from the USB if it is plugged in, otherwise it boots from the hard drive which has windows XP. This is a work machine so do not want to mess with any of these settings, but I wish to use UBUNTU for my own private use when I am not working.

Where have I gone wrong?

How can I recover?

Any help would be greatly appreciated.

Regards

Bearslumber

---

### Post by IndyGunFreak on 2008-06-03
I tried this once, got a lot of Grub errors, etc.  Eventually, I got it to work.  How, I really don't know.  Anyways, once it worked, I found running an OS through an external USB drive, was SLOW.  Just didn't work as well as I'd hoped.  I don't know what the problem was, I'm guessing the speed of the USB port might have been the bottleneck.  If you're ever in the IRC channel, a lot of people have issues running Ubuntu like this.  Also, I'm almost positive you need to use the Alternate Install CD to install like this(at least I did)

Why not just use a Live CD?

IGF

---

### Post by bearslumber on 2008-06-03
Thank you IndyGUnfreak.

The reason why I chose a USB was so that I could have a persistent OS. Can you have a persistent OS with the Live CD? Can the boot options be changed so that you boot into RAM? I have 2GB of RAM?

I take your point that it was too slow, and that is discouraging. I was hoping I could find a way of loading Ubuntu directly into RAM from the USB to speed this up. Perhaps a bit ambitious, but I guess I got the idea from the small print Linux distributions Nimblex and Slax.

I will definitely try the alternate install CD, and see if I can progress.

I shall also be paying a visit to the IRC.

Many thanks for your support.

Cheers

Bearslumber

---

### Post by bearslumber on 2008-06-09
Okay,

I am a happy man.

Resolved the issues. Please see [http://ubuntuforums.org/showpost.php?p=5146763&postcount=1214](http://ubuntuforums.org/showpost.php?p=5146763&postcount=1214) for details.

I am happy to inform you that after success I have to say that I do not see any performance decrease whatsoever.

Thoroughly recommended.

Thanks to IGF for your help. 

Bearslumber.

---

