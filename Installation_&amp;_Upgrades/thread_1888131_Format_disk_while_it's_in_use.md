---
title: "Format disk while it's in use"
date: 2011-11-28
forum: Installation &amp; Upgrades
---

### Post by undrline on 2011-11-28
I installed Maverick but I need to downgrade to Lucid.  For some reason, it won't finish booting to the 10.04 live cd and hangs on the Ubuntu throbber.  So, I want to just blank the hard drive and try booting to the cd again.  How do I reformat/blank the partition of a disk while it's in use?  Gparted, understandably, wants me to unmount it first.

---

### Post by satanselbow on 2011-11-28
Boot into a live cd and use gparted from there.

---

### Post by cholericfun on 2011-11-28
well, as you say yourself, you cant format a drive that is mounted (Full stop).

Also i don't quiet see your problem. Your LiveCD isn't loading -easiest to try a different (...liveUSB) one?
I don't see how a freshly formated HD will change the behaviour of your liveCD in any way.

---

### Post by undrline on 2011-11-28
Thanks cholericfun.  I thought it might be possible because I recalled someone jokingly putting a detrimental command out there.  This forum came with warnings about running terminal commands you don't understand.  But, maybe it was a command to erase your home directory, not format your drive.

I know this live cd works when I use it with a blank drive, but for some reason no Lucid cd has ever worked on my machines if the disk had a bootable os on it no matter how much I messed with the BIOS settings or F-keys.  

I'll try the Maverick cd, which is what I think satanselbow was getting at.  Also, I do have a disk-to-usb converter, so if that doesn't work, I can just boot to the old HDD and format it as an external drive.

---

### Post by cholericfun on 2011-11-30
i can't think of any reason why your live cd doesnt boot while having a hd on. thats not no say there couldnt be one...

do i understand correctly that you can boot to the cd and select the live modus and then it gets stuck?

---

### Post by undrline on 2011-11-30
> **cholericfun said:**
> i can't think of any reason why your live cd doesnt boot while having a hd on. thats not no say there couldnt be one...

do i understand correctly that you can boot to the cd and select the live modus and then it gets stuck?

Nope, if there's a bootable drive, it doesn't even get to the try/install selection.  I can get to the F6 list sometimes, but choosing install does nothing except put me back to the loading throbber.

I used the Maverick live cd, and gparted was there but crashed on start.  I suppose I could've done it through the terminal, but I'm too much of a nervous nellie.  Instead, I put my old hard drive back in, and I used my swiss-army-knife of storage adapters ([http://goo.gl/MM17V](http://goo.gl/MM17V) NexStar Universal Storage Adapter), to mount and re-partition the new disk.  Switched back to the now-blank new disk, with the Lucid cd and all was well.

Thanks everyone for your help, and confirmation that a disk can not be formatted while in use.

---

### Post by cholericfun on 2011-12-01
very belated afterthought:
you could change the BIOS to only boot from CD and not the harddrive. This still enables you to access the HD from within the livecd.

---

### Post by undrline on 2011-12-01
> **cholericfun said:**
> very belated afterthought:
you could change the BIOS to only boot from CD and not the harddrive. This still enables you to access the HD from within the livecd.
 
lol, I lready tried that; when I said "no matter how much I messed with the BIOS settings" I meant it :)  I still have to do F9:Boot Options and select CD most of the time even for versions later than Lucid or for Windows.  I tried different optical drives, too.  Half the time, I can get it to boot to lubuntu minimal on a usb stick.  The only thing any of my machines seem to boot to reliably without intervention is a floppy disk.  Really, it's only thing you can use a floppy drive for anyhow.  Is there a "boot to floppy, then install everything else on the hdd with a sudo apt-get ubuntu-desktop --askmewhichversion" image out there for ubuntu?  That'd be nice to have in the computer cabinet for emergencies :P

---

