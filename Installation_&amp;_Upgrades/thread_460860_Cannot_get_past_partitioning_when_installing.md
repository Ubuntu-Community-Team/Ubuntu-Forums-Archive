---
title: "Cannot get past partitioning when installing"
date: 2007-06-01
forum: Installation &amp; Upgrades
---

### Post by mettu on 2007-06-01
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/ubiquity/+bug/90949](https://launchpad.net/ubuntu/+source/ubiquity/+bug/90949)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				
I'm a newbie and keen to install Ubuntu. I have Windows XP installed on my hard drive which is already partitioned (about 15GB on the (second) partition I want to use). I tried following various tutorials about how to install from the CD (I downloaded and burned) and all goes well until I try to make the partition changes to the disc final - I get the message:

"no root file system is defined please correct this from the partitioning menu"

One time I got past it by choosing simply the mount (/) for the first primary partition but then the intall didn't work - the GRUB program wouldn't install, presumably because there was no boot flag.

This message has been reported before - [https://launchpad.net/ubuntu/+source/ubiquity/+bug/90949](https://launchpad.net/ubuntu/+source/ubiquity/+bug/90949) . however, the answers aren' much help.

Would using the alternate CD (what's that?) help or running the Qtparted program off the resue disc help?

Thanks.

---

### Post by richardjennings on 2007-06-01
Do you get the same problem running gparted from a live session in Feisty?

The alternate cd does not boot into a live session, making it suitible for comps with low amounts of ram.

if you have enough ram to use the live session, you could run gparted from there. Then when you go into installation you will already have the partitions you need, swap, root, and possibly a home partition if you want one.

If that doesnt work, try using an edgy live session to run gparted to create the partitions.

---

### Post by coxy on 2007-06-01
The alternate CD is a text based installer that allows you to install a command line system or full desktop system. In the earlier days of Ubuntu it was the only install method available so I have always used it and still prefer it. You could give it a try if your confident in doing so.

You need to create a minimum of 2 partitions when installing:

SWAP - This should be either 1.5x the amount of RAM you have or 2x the amount of RAM you have. Different people have different views. If you have 512MB of RAM then create a 1024MB SWAP partition and you will have plenty. Make it a logical partition. You specify it as SWAP under the file system type menu.

/ - The root partition can take up the rest of your disk space that is available. It should be set as a primary partition. You can use any file system you see fit; most people seem to use ext3 round here as this is the standard Ubuntu selects. I always use JFS because that is my preference. XFS is also another good choice.

/home - You can choose to have a separate home partition if you wish but this is not necessary. If you do then set your root partition at around 10GB and use the rest for the home partition. Make your home partition a logical partition and use the same file system that you used on the root partition.

Steer clear from adjusting anything on your Windows partition.

I hope that is not to confusing.

---

### Post by mettu on 2007-06-02
Thanks guys . All well, in fact spiffing I would say. Took your suggestion and repartioned - 2 only this time. Didn't bother with a boot marker and used JTS (JFS?). Not sure why it worked this time. Manybe I was setting my swap as a primary not logical.

Anyway, happy as Larry now. Thanks a bundle.

---

