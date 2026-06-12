---
title: "Have dual boot working, want triple or multiple boot. Using gparted."
date: 2007-04-08
forum: Installation &amp; Upgrades
---

### Post by noah_parkcity on 2007-04-08
Greetings and salutations,

I am a n00b that has 6.10 32 bit and xp coexisting peacefully, but alas, i want more. i want to use my 64 bit hp pc with a 64 bit non-ms OS, so i download 7.04 64 bit and burned a iso cd. i also install gparted and carve out 60 gigs from xp that is now unpartitioned space. Now i cannot install another distro of Ubuntu b/c i have four primary partitions already! I know the easiest thing to do would be to totally hose windows xp and / or its rescue partition, but i am not ready to do that yet. So, the only idea i can come up with thus far would be to increase the size of the only extended partition that has the swap partition, but gparted will NOT let me do that. any ideas?

If i could have a big 'ol extended drive then i believe i could try out multiple versions of ubuntu as they come out, yes? 

Attached is a screenshot of gparted

i am not sure of what terminal output would be useful in this instance

thank you in advance for helping this n00b break free from the ms empire

cheers!

---

### Post by Jose Catre-Vandis on 2007-04-08
Yep

To do this, big up your extended partition and create some logical partitions inside it. You can then install additional distros to each of these logical partitions.

Remember that some of them will only allow grub to install to the root mbr of the drive, so this will overwrite your existing grub settings. You can get these back (oodles of help on the forum about this). If you are lucky your additional distros will offer you the option to install grub to the partition. In this case you will have to identify the boot settings in the menu.lst file for that distro, and add this to your main menu.lst file.

---

### Post by noah_parkcity on 2007-04-08
Thank you Jose Catre-Vandis, for your quick reply.

I am afraid that I understand some of what you say, but do not have the knowledge to implement the change that i do understand

you say:

To do this, big up your extended partition and create some logical partitions inside it. You can then install additional distros to each of these logical partitions.

This part i do understand. However, i know that i cannot tell gparted to change a mounted partition, so i reboot to the 6.06 LTS live cd and terminal-> gparted, However, even then i cannot change the size of the extended partition.

once i get beyond that basic, yet show-stopping problem i can worry about the
changes to grub (like what) that you speak of.

---

### Post by noah_parkcity on 2007-04-08
this solution to this problem must have to do with the extended partition. from my screenshot in the first post i can see i have one extended partition already and so i can only have one extended partition. how do i, using gparted, make the extended partition bigger when gparted has it greyed out???

---

### Post by noah_parkcity on 2007-04-08
check out the screenshot

there is a LOCK beside the extended partition and the swap

and it says status: BUSY.

so, how do i get it unbusy so that i can modify it???

---

### Post by noah_parkcity on 2007-04-08
Ok...does anybody out there know gparted?

here is a screenshot..

as you can see, i deactivated the locked extended drive

i then deleted the swap drive

i keep trying to up the size of the extended drive but it does not cooperate as

you can see by the screenshot

---

### Post by noah_parkcity on 2007-04-08
Ok... i learned that i can deactivate the swap and that way i can unlock the extended drive and the swap drive. then i can delete the swap drive. then i can move away from the 2.7 gig partition and then click on the over 60 gig partition and then make that the new extended partition. the old extended partition is now just grey unalocated space as the 60 gig just was before. since there can be only one extended partition, now the 60 gig is it.

i went all the way to this point, but then chickened out BECAUSE

i dont know if ubuntu 6.10 will recreate the swap in my new 60 gig extended partition

and i dont know how to point it in the right direction by being able to specify a label that is just like before /dev/sda4 extended 2.70 gig /dev/sda5 swap.

any takers on this? otherwise i'm now stuck up to the axle because i dont want to hose my 6.10 32 bit on my 64 bit system.

---

### Post by confused57 on 2007-04-08
I don't really know, I'm not that experienced with partitioning, but I can give some suggestions that may or may not work.  You could possibly reduce the size of your current extended partition to 2.70 Gb, then click on partition in the menu at the top & select format as swap...this should designate the extended partition as sda4 and the new logical partition as sda5 for swap.

To create additional partitions within the extended partition, highlight the extended partition, choose resize to the size of the partition you're adding, then go through the procedure again of clicking partition, format, but choose ext3.

The gparted live cd is an excellent partitioning tool:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)

Here's some screenshots for resizing with gparted:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

I'm putting my 2 cents worth, since you haven't received any other replies...your other reply was correct, but a little  general.  I think at that point, you could have clicked on the extended partition, select resize, partition, format, etc.  Like I said, I'm not that experienced with partitioning, so I'm not sure how you'd join the 2 unallocated partitions, unless you delete your current extended partition, create another with the 2.70 Gb, format as swap, etc.

---

### Post by Jose Catre-Vandis on 2007-04-09
Yeah, sorry noah-parkcity, becuae i always use the gparted live cd i made an assumption you were to.

Using the gparted live cd is the best way to do things as you can work on all your partitions.

from what i could see from your original screenshot, once booted up with gparted, you should be able to resize your extended partition to take over the unallocated space. Then you can create new logical partitions within.

Sorry for the confusion

---

