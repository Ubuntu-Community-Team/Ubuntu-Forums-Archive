---
title: "Kernel update - won't boot- possible solution?"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by quixote on 2007-09-01
Grub did not find the Ubuntu boot partition (Error 22), so I figured I had to reinstall grub, like I'd done once before.  Instructions [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

However, reinstalling grub did not solve the problem.  I pulled out my trusty bible (Hitchhiker's Guide, of course) and re-read the relevant page: Don't Panic.

After using another computer to access this thread, and looking at /boot/grub/menu.lst, I saw that it had listed Ubuntu as being on (hd0,10).  On my system it's actually /dev/hda9.  So, it should have had it as (hd0,8 ) [no space after 8, inserted to avoid smiley!] given grub's numbering convention.  These are the steps I followed:

I booted from a LiveCD.
opened a terminal window
entered sudo -i at the command prompt.
root@ubuntu# mkdir /mnt/good-ubuntu         [you can use any name for the dir] 
root@ubuntu# mount -t ext3 /dev/hda9 /mnt/good-ubuntu    [insert your own location for "hda9"]
root@ubuntu# cd /mnt/good-ubuntu/boot/grub
root@ubuntu# cp menu.lst menu-lst-bak.txt            [so you have a copy just in case]
root@ubuntu# gedit menu.lst

that brings up gedit, and then I changed all the references to (hd0,10) to (hd0,8 ) in my case.

Saved.  Closed everything.  Rebooted.  And it all worked.

Hopefully I have all the commands listed right.  A real Ubuntu expert: please vet!

My guess is that in the update files, the relevant variable was either initialized at 1 instead of 0, or  maybe there's a minus sign missing somewhere, to subtract 1 instead of add it to the existing partition numbers.

Hope this is useful!

[I posted this at the end of another thread, but maybe it needs to be more obvious.  If not, my apologies!)

---

### Post by crbennett on 2007-09-01
> **quixote said:**
> 
that brings up gedit, and then I changed all the references to (hd0,10) to (hd0,8 ) in my case.

My guess is that in the update files, the relevant variable was either initialized at 1 instead of 0, or  maybe there's a minus sign missing somewhere, to subtract 1 instead of add it to the existing partition numbers.

Hope this is useful!

[I posted this at the end of another thread, but maybe it needs to be more obvious.  If not, my apologies!)

Extremely so!  Thanks for sharing it.

In my case, the result of the update was grub throwing "Error 18: Cylinder referenced is beyond that supported by BIOS."  Or words to that effect. Given what you've shared, I'd say it's a different presentation of the same problem.

As to the cause, I did watch the update and saw warnings during the grub configuration. One of the warnings was that the script was calling /sbin/update-grub and the warning was most emphatic in saying "Don't use /sbin/update-grub!  Use /usr/sbin/update-grub instead!"

Or rather, again, words to that effect.

Another notion for some:  While you're in the menu.lst file, stop by the section holding grub configuration and make sure keep=all is set for how many kernel images to keep.  I've fallen back to a previous kernel image to find your excellent advice.

I'm off to see what I can find in menu.lst.  Good luck to all with this one!

Ross

---

