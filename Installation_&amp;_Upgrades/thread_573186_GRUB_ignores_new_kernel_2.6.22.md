---
title: "GRUB ignores new kernel 2.6.22"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by raydar on 2007-10-11
I've had Gutsy beta installed for a while now, but even though the new kernel 2.6.22 shows up many times in my menu.lst file (see attached), the menu of kernels I'm presented with at boot does not offer it.  (This may have been causing my nvidia woes; see [http://ubuntuforums.org/showthread.php?t=567710&page=2](http://ubuntuforums.org/showthread.php?t=567710&page=2) ).

I dual-boot, with two hard disks in this box, one that boots Ubuntu 7.10 beta (upgraded from 7.04) and one that boots UbuntuStudio 7.04.  GRUB shows me two separate lists of kernel 2.6.20 and its predecessors when I boot, so I can boot either Ubuntu Gutsy beta or UbuntuStudio Feisty with that version of the kernel.  But shouldn't kernel version 2.6.22 now be at the top of one section of the kernel list, namely the Ubuntu Gutsy beta section (as opposed to the UbuntuStudio Feisty one, which I haven't upgraded)?  

I ran update-grub both with sudo in a terminal and, after that didn't help, in recovery mode as root.  I thought the upgrade might update my GRUB automatically, but since even doing it manually doesn't help, I'm wondering what else I can do except wipe the drive and do a clean install.  Could my dual-boot configuration, booting two Linux versions, be frustrating the process somehow?

---

### Post by dreadlord_chris on 2007-10-11
How about removing all the kernels that you don't need any more?

Just to start off - you really should clean up your menu.lst - get rid of all the extraneous kernel listings that you don't use any more....

---

### Post by raydar on 2007-10-11
That definitely sounds like a good idea to me.  Would it entail just opening menu.lst and deleting the blocks of lines referring to the old (pre-2.6.20) kernels?  Elsewhere in the forums, I ran across a caution not to manually edit anything inside the "automagic kernels list" area of menu.lst, but maybe I need to do that--either for a precise fix or to create a "clean slate" for update-grub to work with.

I'm still newbie enough that I'm (1) not sure what all update-grub is supposed to do (I watched it add 2.6.22, but apparently it doesn't delete any obsolete entries); (2) unaware whether there's some other counterpart to update-grub that will remove old entries automatically; and (3) afraid of breaking my grub so I can't boot at all.

I don't think any pre-2.6.20 kernels (the kernels themselves, as opposed to grub entries) are still hanging around on my machine, 'cause they come up as file-not-found if I try to boot them.  Is there a limit to the number of entries grub will display on boot, such that there's no "room" for the 2.6.22 kernel despite the following entry in my menu.lst?

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

Thanks for your help!

---

### Post by dreadlord_chris on 2007-10-11
> **raydar said:**
> That definitely sounds like a good idea to me.  Would it entail just opening menu.lst and deleting the blocks of lines referring to the old (pre-2.6.20) kernels?  Elsewhere in the forums, I ran across a caution not to manually edit anything inside the "automagic kernels list" area of menu.lst, but maybe I need to do that--either for a precise fix or to create a "clean slate" for update-grub to work with.

I'm still newbie enough that I'm (1) not sure what all update-grub is supposed to do (I watched it add 2.6.22, but apparently it doesn't delete any obsolete entries); (2) unaware whether there's some other counterpart to update-grub that will remove old entries automatically; and (3) afraid of breaking my grub so I can't boot at all.

I don't think any pre-2.6.20 kernels (the kernels themselves, as opposed to grub entries) are still hanging around on my machine, 'cause they come up as file-not-found if I try to boot them.  Is there a limit to the number of entries grub will display on boot, such that there's no "room" for the 2.6.22 kernel despite the following entry in my menu.lst?

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

Thanks for your help!
first thing - back up menu.lst:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old

```
***# howmany=all*** would be the option to change...

first open **menu.lst**, _as root_, in your prefered editor:

Now, I'd recommend changing it to:
```

# howmany=2

```

This will pare down your GRUB menu to just your 2 most current kernels - useful when the newly installed kernel doesn't boot.

Now save the file, then run update-grub:
```

sudo update-grub

```
Hopefully no errors...
take a look at the new **menu.lst** - a little cleaner?

As for all those old kernels - open up Synaptic and search for _linux-image_
From there you can remove all the old kernels that you won't be needing....

---

### Post by Pumalite on 2007-10-11
Don't go crazy. You'll need at least 1 old one to boot from in case and update or upgrade goes wrong.

---

### Post by raydar on 2007-10-19
Very sorry I've been neglecting this thread.

I began to think there's something I really, really don't understand about grub.  I have two hard drives, each with Ubuntu and no other OS installed, each with its own /boot menu and its own menu.lst file.  When I boot, the system must have to choose one or the other drive's grub or menu.lst to generate the list of kernels from.  My "straight Ubuntu" drive, as opposed to my UbuntuStudio drive, is the one whose menu.lst is chock full of separate kernel listings, so it seemed reasonable to conclude that's the one whose menu.lst I should edit.  But what I found was that no matter what I did to that drive's menu.lst (including running update-grub afterward), it had no effect on the list of kernels I saw at boot.  I even tried deleting all but one kernel from that list, and still at boot every single one showed up that had showed up before.  

So, I decided that straight Ubuntu drive classified as haunted for the moment, and I turned my attention to the UbuntuStudio drive instead.  I had upgraded the straight Ubuntu drive from Feisty to Gutsy, and I did the same to the UbuntuStudio drive, which was a much more recent creation (Feisty was the first OS installed on the drive, where my straight Ubuntu drive had been sequentially upgraded since Dapper).  Everything turned out fine with the upgrade of the UbuntuStudio drive, so I just copied all my files over from the obstinate straight Ubuntu drive and started using the UbuntuStudio drive as my main one.

Thus, for me, this problem is academic now, though I still would very much like to get to the bottom of what was going on with the straight Ubuntu drive and grub and menu.lst, if anyone's curiosity-driven enough to be interested in pursuing the issue.

Thanks for your help!

---

