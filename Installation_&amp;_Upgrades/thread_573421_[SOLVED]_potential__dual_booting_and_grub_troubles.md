---
title: "[SOLVED] potential  dual booting and grub troubles??"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by offline on 2007-10-11
I've very recently dual booted with windows 2000pro on master disk(fat32) and ubuntu6.06 on the slave disk.

I used the automatic option(of the original ubuntu live cd) to  completely reformat and use all of the second disk by ubuntu.

Now when I reboot grub shows me a selection list ubuntu being the first item and windows the last.

Everything seem to work well(except that ubuntu can't recognize microcom router AD2636 because I have usb cable attached(network card not working) but that is another story).

So, after the installation I run on some articles and discussions stating how(POTENTIALLY?) dangerous is for grub to overwrite windows MRB.

Will I have problems?

If one of the two OS "stucks" is there a way(either way) to overcopme this?

Should I change or do anything now?

---

### Post by Herman on 2007-10-11
Well I don't think it's dangerous at all to write GRUB to MBR.

Most of the people who are afraid of writing to their MBR probably don't understand properly what the MBR is exactly. Fears and superstitions take over where human knowledge reaches it's limits. That's the main reason we find so much illogical retoric about the MBR.

The MBR is in the first sector of a hard disk once it has been formatted, and it is made of the same material as the rest of the hard disk. 
Hard disks can be written to and erased (including the MBR) pretty near an infinite number of times, so if you can always change your MBR again if you are ever not happy with it.

The MBR does not belong to any particular operating system, it belongs to the owner of the hard disk, and is used to address any operating ssytems the owner might want to put in the disk.

You can back up and restore your MBR if you want,  [MBR backup and restore]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd"), 

Here's a page listing some softwares you can use to change your MBR, most of these are for reverting it to point to Windows again since that's what most people seem to worry about the most, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm") 

Look, drive a fast car, dive underwater, fly an airplane, ride a horse, ride a bull out of a rodeo chute, do something exciting! All of those things involve an element of risk or they wouldn't be any fun.
What's so scary about writing a few bytes of data to a hard disk? It's not even any fun, it's just boring, It doesn't scare me.

Regards, Herman :)

---

### Post by offline on 2007-10-11
Thanks Herman for claryfing some matters and for your good work regarding your site.

Being clear, precise and respectful for newbies, man, that is setting standards.

Cheers for being a free spirit, teach us that(you Australians to Europeans).

sotiris

---

### Post by dabl on 2007-10-11
> **Herman said:**
> 

Look, drive a fast car, dive underwater, fly an airplane, ride a horse, ride a bull out of a rodeo chute, do something exciting! All of those things involve an element of risk or they wouldn't be any fun.
What's so scary about writing a few bytes of data to a hard disk? It's not even any fun, it's just boring



ROFLMAO! -- I think I'm going to have that embroidered, and framed!


:lolflag:

---

### Post by Herman on 2007-10-11
Hello again offline,
Sorry, I didn;t answer your last questions yet,
>  Will I have problems?

 If one of the two OS "stucks" is there a way(either way) to overcopme this?

Should I change or do anything now?
Once you have your operating system installed successfully and your operating system (Ubuntu) boots okay and your other operating system (maybe Windows or another Linux or something else), boots okay, it's unusual to have any problems. Certainly it would be very rare to have any problems that start by themselves. When problems do occur they are normally caused by the user trying to learn how to do something like install a splashimage in GRUB for example, and making a simple mistake.

These days you can downlaod for yourself a free copy of adrian 15's [Super Grub Disk]("http://geocities.com/supergrubdisk/") and that will help you to boot either Ubuntu or any other Linux or Windows. You can even use Super Grub Disk to help you fix quite a lot of booting problems too, or at least boot your operating system for you so you can get help, and/or fix it yourself from inside the operating system.

Super Grub DIsk takes helps newbies take care of the boot loader code area of the MBR, so now you don;t need to know how to use the command line already, before you even get started with Linux. 

Another part of the MBR that people can have trouble with (but it's rare), is the partition table. Nowadays we have another free download, [GParted -- LiveCD]("http://gparted.sourceforge.net/"), which features Partimage (for backups), and Testdisk, (for restoring the partition table).

When you know you can use these great softwares for fixing most things that might go wrong, thinks are not as scary anymore as they were in the old days before those handy programs were developed.
Now more people can have a chance to try out Linux without having to worry so much.

Regards, Herman :)

---

