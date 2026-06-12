---
title: "Save a failed 9.10 upgrade"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by silentbobspeaks on 2009-12-06
Afternoon all,
I was upgrading from 9.04 to 9.10 about a week ago, and during the download and installation I had to leave the computer for a while.  Unfortunately when I came back it seems like it had tried to go to sleep - but because of my GFX card, going to sleep fails and I had to do a hard-reboot.

Now, when I start up and select any of the kernel versions (e.g. 2.6.28.15), it loads up so far, then shows a screen that is a mixed up hybrid of the old 9.04 loading screen and the new 9.10 loading screen.  It then switches to terminal-view and lists all the locations in the mount list and says waiting for their respective drive (e.g. /dev/sda2).

It seems like it's waiting for the hard disk (they're all on the same drive), but the disk itself is fine as I can still run my dual-boot Vista on it.  

Is there any way to save it?  One way I thought of that might help (I don't know!) is to remove the list of mounts from the file from a live cd, but I can't remember the name or location of that file!  Any help on this would also be appreciated.

I hope I've explained it well enough - please ask for more info if it doesn't make sense!

Thanks in advance,

Jamie

---

### Post by phillw on 2009-12-06
> **silentbobspeaks said:**
> Afternoon all,
I was upgrading from 9.04 to 9.10 about a week ago, and during the download and installation I had to leave the computer for a while.  Unfortunately when I came back it seems like it had tried to go to sleep - but because of my GFX card, going to sleep fails and I had to do a hard-reboot.

Now, when I start up and select any of the kernel versions (e.g. 2.6.28.15), it loads up so far, then shows a screen that is a mixed up hybrid of the old 9.04 loading screen and the new 9.10 loading screen.  It then switches to terminal-view and lists all the locations in the mount list and says waiting for their respective drive (e.g. /dev/sda2).

It seems like it's waiting for the hard disk (they're all on the same drive), but the disk itself is fine as I can still run my dual-boot Vista on it.  

Is there any way to save it?  One way I thought of that might help (I don't know!) is to remove the list of mounts from the file from a live cd, but I can't remember the name or location of that file!  Any help on this would also be appreciated.

I hope I've explained it well enough - please ask for more info if it doesn't make sense!

Thanks in advance,

Jamie
Hi,

Others may suggest something different. But, for me - I'd backup my ~home to the Win partition (if there's room) and just do a clean install of 9.10. You'll have the advantage of ext4 and Grub2 all in one swoop - we can then put your ~home area back onto the new install. But, that's just how I'd do it. Wait for other suggestions, by all means.

Regards,

Phill.

---

### Post by silentbobspeaks on 2009-12-06
> **phillw said:**
> Hi,

Others may suggest something different. But, for me - I'd backup my ~home to the Win partition (if there's room) and just do a clean install of 9.10. You'll have the advantage of ext4 and Grub2 all in one swoop - we can then put your ~home area back onto the new install. But, that's just how I'd do it. Wait for other suggestions, by all means.

Regards,

Phill.

Hi,
Thanks for the quick reply!  I *think* my home folder is on another partition anyway; I've got a couple of computers running Ubuntu and it's hard to remember which one has what when I've not used them for a while!

Would I be right in saying that I will save my application settings in the home folder, and lose the applications themselves by re-installing?

As long as I can get all my settings out before re-installing I'm happy!  Does having the combination of Grub2 and Ext4 speed things up in boot and runtime?

Thanks,

Jamie

---

### Post by phillw on 2009-12-06
> **silentbobspeaks said:**
> Hi,
Thanks for the quick reply!  I *think* my home folder is on another partition anyway; I've got a couple of computers running Ubuntu and it's hard to remember which one has what when I've not used them for a while!

Would I be right in saying that I will save my application settings in the home folder, and lose the applications themselves by re-installing?

As long as I can get all my settings out before re-installing I'm happy!  Does having the combination of Grub2 and Ext4 speed things up in boot and runtime?

Thanks,

Jamie

Your bookmarks, docs, music, vids etc that you have saved in your login name (~home) will all be sat patiently w8ing for you.

As it quite possible that your install is corrupt - I'd really recommend a clean install. ext4 does run faster than ext3, grub2 is the replacement for grub. The fact your ~home is still in ext3 won't bother the system at all. Some have reported longer boot-times, but that seems more than off-set by a speedier response time in use.

I'd use the manual slicing option for the install - to make sure it doesn't get 'trigger happy' and nuke your exisiting ~home area !!! (A backup of that area is still recommended, but I'm ultra cautious !!)

Regards,

Phill.

---

### Post by darkod on 2009-12-06
Just to add, if you are not sure what you have on this particular pc, just boot up with 9.10 (9.04) cd, select Try Ubuntu option and use Gparted to look at the hdd. I guess you will recognize the partition layout.

---

### Post by silentbobspeaks on 2009-12-06
Thanks for the replies guys!
Looks like a fresh install is the way forward!  Downloading a livecd at the moment and will get everything backed up later hopefully and get the re-install done.

This can only go well :D

Cheers,

Jamie

---

