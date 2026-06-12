---
title: "Boot Issues &amp; No Windows CD"
date: 2011-11-24
forum: Installation &amp; Upgrades
---

### Post by turboscrew on 2011-11-24
I have the same kind of problem.

Because most of the problems in start-up I have encountered, seem to be windows problems, I decided to use windows boot manager as the primary boot manager so that the windows rescue can do its job. I've never seen a windows vista or windows 7 machine sold with the install CD in Finland, so the rescue partition is my only fixing possibility.

The problem was that the normal Ubuntu install didn't allow putting the grub(2) on the root partition - I had to use the alternative installation.

Now an update came, and it complained about the boot. I selected the option not to change the boot (stupid me) and now the Ubuntu
is not bootable at all. It goes to the rescue prompt. The kernel and initrd are not found where they are supposed to be. I guess I might be able to fix the boot, but I also think the next update will trash it again.

---

### Post by drs305 on 2011-11-24
> **turboscrew said:**
> I have the same kind of problem.

Because most of the problems in start-up I have encountered, seem to be windows problems, I decided to use windows boot manager as the primary boot manager so that the windows rescue can do its job. I've never seen a windows vista or windows 7 machine sold with the install CD in Finland, so the rescue partition is my only fixing possibility.

The problem was that the normal Ubuntu install didn't allow putting the grub(2) on the root partition - I had to use the alternative installation.

Now an update came, and it complained about the boot. I selected the option not to change the boot (stupid me) and now the Ubuntu
is not bootable at all. It goes to the rescue prompt. The kernel and initrd are not found where they are supposed to be. I guess I might be able to fix the boot, but I also think the next update will trash it again.

I think you are saying you installed Grub to the partition instead of the MBR. As you theorize, one of the problems with installing Grub to a partition is that if files are moved around during an upgrade Grub may not be able to find them and thus only provides the Grub rescue prompt. 

If you haven't solved this yet, you can see if the [_Grub Rescue_]("http://ubuntuforums.org/showthread.php?t=1594052") thread helps you boot or you can boot the LiveCD and try the Boot Repair app. The Boot Repair link is in my signature line. 

[s]If you need further help please start a new thread so we don't confuse replies.[/s]  Posts moved to this thread.

---

### Post by darkod on 2011-11-24
@turboscrew
I understand that by not shipping a install dvd MS makes things harder, but in your place I would reconsider using grub2, and in fact the whole strategy.
You say your restore partition is the only way if fixing things. But most restore partitions I have seen are "back to factory state" partitions. In other words, it wipes your hdd and restores it as it was from factory. That would wipe not only all your ubuntu data but also windows data and custom created partitions.
That hardly counts as fixing.

You have a number of options:
1. Usually there is a backup software that can help you create restore DVDs from the restore partitions, but this also doesn't help much because again it does the same, wiping the disk.
2. You can try downloading and storing the win7 repair CD image, like this for example:[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
That can help with boot issues, but you can't completely reinstall the OS with that.

By using the windows bootloader you are trying to use the bootloader that natively doesn't support linux, and on the other hand not using the bootloader that natively supports both linux and windows (grub2).

Anyway, it's up to you. My main opinion is that the restore partitions are worthless and don't fix anything. Wiping disks is no fix for me.

---

### Post by turboscrew on 2011-11-24
One more response on this thread...

The problem is - like I have tried to say - I don't have any
installation media for any currently supported windows.
My last installation CD is Windows2000.

I have never got an XP-machine, and neither Vista- nor Windows-7
-machines have any installation media. If the rescue partition goes
and there is something fatal in the windows, that's it.
No more windows in that machine ever.

Even if the windows is not fixed, at least I have a change of reinstalling it.

I can always get Linux from web (and I will :D ).

The boot/rescue disks can fix the start-up, but not corrupted windows itself (maybe due to disk problems).

BTW, Windows 7 has boot editor that can be used to include
grub(2) as chained boot loader "BCDedit".

---

### Post by drs305 on 2011-11-24
Moved to own thread. It was formerly part of:
[http://ubuntuforums.org/showthread.php?t=1885637]("http://ubuntuforums.org/showthread.php?t=1885637")

P.S. I agree with *darkod* that you would probably have fewer problems, once you get Windows booting normally, using Grub 2 as your primary way of booting your OS's.

---

### Post by turboscrew on 2011-11-25
I doubt that.

I have had my share of windows problems such that boot CDs haven't been able to boot the windows. That's why I keep the most important data on a specific partition on a certain HD shared via local network.

(I have 4 machines)

Bad power lines makes you cautious after you experience some power breaks during windows updates.

---

### Post by efflandt on 2011-11-25
Many computers come with no OS media (DVD or CD), but should have a utility to create recovery/utility discs to restore Windows.  So one of the first things you should do with a new PC (unless you never need to go back to Windows) is create those discs.

Some Win7 programs (like on my Dell) store some data in what they "think" is an unused part of the mbr.  But grub2 is larger than the Windows mbr, so that can end up stepping on grub2 and make it not boot.  So I usually put grub2 on a primary Linux partition and mark that as the boot partition for Window's mbr, instead of mucking about with the Windows boot loader.  For some reason grub complains when you do that, or might even need to be forced.  Not sure if grub works if its initial boot loader is on an extended or logical partition (lilo used to work from an extended partition).

One thing that always helps for troubleshooting is also having bootable Linux with grub on a different internal or external drive or flash to be able to get back into your system to fix it if something messes up the mbr or grub.

---

### Post by turboscrew on 2011-11-25
The thin is: Vista-boot works. It boots windows and it starts Grub2 on the Linux root
partition. That's why the grub2 rescue prompt.

What doesn't work is the Grub2 itself. I doesn't find the configuration files
after update.

Why was Grub2 updated in the first place?
Why didn't it update it on the Linux root partition regardless of anything outside the Linux?
If the Grub2 on the Linux root partition is changed, it could have been added into
the Vista boot loader using EasyBCD.

Windows7 contains its own boot editor, so you don't even need the EasyBCD.

---

### Post by drs305 on 2011-11-25
We still don't have a lot to go on other than you get a grub rescue prompt. I can give you some basics about booting from the rescue prompt. Substitute the correct numbers for all (hd0,5) entries:

Info and investigation:
```
ls # Shows the known drives (hd0) (hd1) and partitions (hd0,1), (hd0,2), etc
ls (hd0,5)/ # Should find the vmlinuz and initrd.img shortcuts (used in booting commands)
ls (hd0,5)/boot # Displays the kernels and initrd images in sda5
ls (hd0,5)/boot/grub # Displays the Grub modules and grub.cfg file
```

Booting from the Grub Rescue prompt (change hd0,5 to the appropriate values):
```

set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
insmod linux
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot
```
If it boots:```

sudo update-grub
```

---

### Post by turboscrew on 2011-11-26
Thanks, I'll try.
I just wonder if that will be in front of me again after the next
kernel update.

---

### Post by turboscrew on 2011-11-26
Sorry, sorry, sorry... I've been wasting everyone's time.
Stupid me!
The update was fine. It was just that the alternate install installed Grub.
What was needed, was adding a new Grub2 entry in the Vista boot with updated version of EasyBCD.

(BTW, how do I get the terminal better at hand in Ubuntu 11.04? Now have to open menu after menu.)

---

### Post by drs305 on 2011-11-26
> **turboscrew said:**
> 
(BTW, how do I get the terminal better at hand in Ubuntu 11.04? Now have to open menu after menu.)

If you are opening the terminal via Applications, Accessories, Gnome-Terminal method, when you see the Gnome-Terminal just drag it to to top panel to create a shortcut.

Once you have your questions answered, please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post.

---

### Post by turboscrew on 2011-11-26
Thanks again.

---

