---
title: "Installation problem (new to linux)"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by alexinexile83 on 2012-07-15
I'm a big fan of open source in general and when it seemed like vista was about to finally die on my laptop I decided to give Ubuntu a go.

I downloaded the files and put it on my usb stick - no real problems there - and restarted so I could install. This is where things went wrong...

I have 3 partitions on my HDD. One for program files and doc's and two small ones that are the vista recovery files.

My plan was to leave these alone and install Ubuntu over the main drive (220ish gb's) and have the option to go back to vista (I cant imagine doing it after using linux for a few weeks but I like options).

But I have just realised that Ubuntu installed itself on a tiny 20gb partition... and all my old windows files are still there. I don't want them as I backed up everything to my galaxy s2 AND I actually reformatted the drive before installing!

Obviously it didnt reformat... obviously I messed up!

So my questions is;

How do I reinstall Ubuntu and wipe the old info out creating a nice clean linux partition with the 220gbs and not 20!

I didnt do the default install option as I wasnt sure if it would then use the whole hard drive and wipe vista? Would it have asked which drive to use?

Help would be much appreciated!

---

### Post by darkod on 2012-07-15
You should have deleted the 220GB partition, in case you didn't. Ubuntu (and linux in general) doesn't install on ntfs partitions.

First boot the ubuntu cd in live mode (Try Ubuntu). That will also show you whether the particular version will work fine on your hardware (usually if the live desktop loads fine, it will work fine).

Once it's loaded, open Gparted and delete all partitions you DON'T need. Leave the space as unallocated.

Then start the install process and either use one of the auto methods (depending what it offers you), or the manual way (option Something Else). But you will need to create your own partitions if going the manual way.

---

### Post by Laiquendi on 2012-07-15
Your post is little ambiguous ^^'
If you want to use all hard drive there is an option like this, something like "use all disk space" and not the "us all free space" option.
If you want to install linux on one partition, you can choose it manually during installation, you should check it and choose option "mount as /" and an ext4 type.

edit:
I see someone has overtaken me, sorry for double post, maybe you'll use both ;D

---

### Post by alexinexile83 on 2012-07-15
> **darkod said:**
> You should have deleted the 220GB partition, in case you didn't. Ubuntu (and linux in general) doesn't install on ntfs partitions.

First boot the ubuntu cd in live mode (Try Ubuntu). That will also show you whether the particular version will work fine on your hardware (usually if the live desktop loads fine, it will work fine).

Once it's loaded, open Gparted and delete all partitions you DON'T need. Leave the space as unallocated.

Then start the install process and either use one of the auto methods (depending what it offers you), or the manual way (option Something Else). But you will need to create your own partitions if going the manual way.

I used some sort of partition manager thing in the installation options and deleted the partition and reformatted it. Well... thats what I thought I did.

I am running ubuntu now. Can I use Gparted now to reformat the main drive?

---

### Post by darkod on 2012-07-15
> **alexinexile83 said:**
> I used some sort of partition manager thing in the installation options and deleted the partition and reformatted it. Well... thats what I thought I did.

I am running ubuntu now. Can I use Gparted now to reformat the main drive?

If you are running ubuntu from it, no. You can't format a disk if an OS is running from it at that time.
Otherwise yes, if ubuntu is running from another disk or from live cd/usb, you can format any disk it's not running from.

But note that depending on your current partition layout, we are not always talking about simply reformatting partitions. If you want another layout you need to delete one or more partitions, and then during the install the necessary partitions will be created. Writing a new partition table I mentioned, deletes all partitions, which is not strictly reformatting, depending how you look at it. :) It's not reformatting and keeping the same partition sizes.

---

### Post by OM55 on 2012-07-15
alexinexile83, GParted can reformat only unmounted partitions. So if you want to make changes to your working partition, you will have to put GParted on a bootable USB drive (or CD) and boot to it. 

Ubuntu installer can suggest automatically what partitions to create and where, or you can select during installation to do it manually. But for the manual option you need to know what you are doing.

If you want in a way, to enjoy both worlds, you can first use GParted to remove un-needed partitions and leave an 'unused' drive space as you like. The Ubuntu installer will automatically try to use that space and create the right partitions there.

---

