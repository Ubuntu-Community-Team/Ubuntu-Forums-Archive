---
title: "Trying to install Ubuntu 9.10 won't recognize hard drive"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by Djdubx2 on 2010-03-24
Ok so I have a Acer Aspire E380-UD440A. 

My friend gave it to me because it crapped out on him. So I took it and tried to install Ubuntu 9.10. I Think I did a big no no when I got to the partition part, because I tried to install it all over the hard drive. Then I got a error saying not enough space on the harddrive.

I then restarted my computer and retried. When it go to the partition part again, it didn't show anything. I looked around the whole system (in the BIOS, Boot setup, and system setup) and nowhere did it recognize the hard drive. 

I've tried in the liveCD boot typing "fdisk -l" in the terminal and got nothing. 

sudo fdisk -l

nothing

sudo fdisk -u /dev/hda

"unable to open /dev/hda"

sudo fdisk -u hda

"unable to open hda"

sudo fdisk /dev/hda

"unable to open /dev/hda"

And I can't quite get it to open up with F6 at the beginning to try typing in "all_generic_ide" (something else I saw on another thread.)

I've also tried reseting the BIOS and everything. I don't know if I acceidently the partition with the driver for this hard drive. And Acer Support wasn't any help either.

---

### Post by bumanie on 2010-03-25
You have probably rendered the hard drive/partition into an unrecognised filesystem (ie, a filesystem that is completely corrupted). From the live cd, go to terminal (Applications --> Accessories --> Terminal) and in terminal, type > sudo gpartedThis will open a gui-based partitioning tool - you should be able to delete the partition/s that are there and then format to ext4. After that, an installation of ubuntu should work OK. [Here's a page]("http://gparted.sourceforge.net/docs/help-manual/C/gparted.html") that may help if you have trouble working out gparted, but it is fairly straight forward.

---

### Post by Djdubx2 on 2010-03-25
I tried the "sudo gparted" and still nothing, not even that this is a hard drive installed.

---

### Post by Mark Phelps on 2010-03-25
If I read your post correctly, you said that even in the BIOS screens, there is no entry for the hard drive.

If that is the case, you're totally hosed!!

The BIOS has to see the drive first, and if it does not, NOTHING you do once you boot into ANY OS is going to make any difference.

If possible, you should remove the drive from your machine and see if you can connect it to another machine to determine that any other machine can see the drive.

---

### Post by Djdubx2 on 2010-03-25
**** that's no bueno . . . well I just see what I can do with. Maybe I'll just customize on top of everything, and make it into a totally new SUPER ACER!

---

### Post by Slim Odds on 2010-03-25
> ...My friend gave it to me because it crapped out on him. So I took it and  tried to install Ubuntu 9.10....

So what was "crapped out" and what did you do to fix it?

Most operating systems will have a hard time installing on a "crapped out" computer.

---

