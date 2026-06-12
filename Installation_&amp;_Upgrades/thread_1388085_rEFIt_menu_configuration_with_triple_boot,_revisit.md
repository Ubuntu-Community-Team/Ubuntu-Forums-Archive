---
title: "rEFIt menu configuration with triple boot, revisited"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by qixote on 2010-01-22
I have read previous posts dealing with the rEFIt menu, but have not yet solved my current problem.  Thanks to numerous online resources here and elsewhere I was able to install Windows 7 64 bit and ubuntu 9.10 along with Mac OS X (10.6) to my MacBook Pro 3,1 (Santa Rosa).  Some minor issues remain to be addressed, but all three OSs are functional.

My question relates to the rEFIt menu where I only see Mac OS X and Windows as available options, unless I happen to have the ubuntu Live CD inserted or my external drive attached which result in Penguin and/or additional Mac icon, respectively.  I get to ubuntu or Windows through the Windows icon in rEFIt, then select one or the other from a long menu in grub, with ubuntu set as the default.  BTW: The included OS X option doesn't work from here, of course, and I'd like to remove it at some point since I can't use it, but that's even less important at the moment.

I get "Error 15: File not found" when I try "find /boot/grub/stage1" or "find /grub/stage1" from within the grub utility, as suggested by a previous poster as a start to discovering and relocating the grub loader in order to change the boot behavior.  Manually I can navigate to /boot/grub, but I am not at all sure if this is the same thing.

With everything essentially working, I don't want to trash what I have.  But it would be convenient if I could select Mac OS X, Windows, or ubuntu directly from the rEFIt menu.

I am not frightened by command line work but have somewhat limited experience and will welcome any constructive input.  I saw posts on this topic dating back to 2008 or early 2009, but current topics didn't seem to match up.  I'm also new to posting here and ask for you patience if I am not approaching the forum in the correct way or location.

---

### Post by lmoerer on 2010-01-31
I am in a similar situation.  In rEFIt I have three icons: mac os x, windows, and then legacy.  Both the windows and legacy icons take me to grub where I can then pick either ubuntu or windows 7.  Ideally I'd be able to select all three from the rEFIt menu and avoid grub altogether but for now this works.

What it sounds like to me is that your partitions are out of sync.  Try syncing them using the rEFIt partitioning tool, otherwise do some searching on this forum.  I had the same problem after resizing the windows partition to install Ubuntu, but couldn't boot either afterward.

---

### Post by qixote on 2010-01-31
Thanks for the sync suggestion.  I have tried that and aside from a need to sync right after creating the partitions for ubuntu the rEFIt partition sync tool always says that everything is synced.  I am able to boot, though I sometimes get a hang in grub when launching Windows or ubuntu.

I did read of a triple boot that bypassed Boot Camp, which is picky about having only a single partition of a certain type before it will run.

---

### Post by kev0153 on 2010-02-02
be interested in any possible solutions to this.  I have a similar situation.

---

