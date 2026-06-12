---
title: "Latest update just hosed my Grub config."
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by artmeacham on 2008-05-26
Now I have to physically visit a machine to manually reboot and reconfigure it, rather than do it remotely.

Why on earth would you rewrite everybody's menu.lst file?  Why?  Anyone can see that this will cause widespread problems.  I'm already pissed about the whole ssh thing, now this annoyance...

---

### Post by liathus on 2008-05-26
i would assume they edited grub so that the new kernel would show up properly in grub, though i have used other distros that had a "current" and "old" kernel option in grub, and they just updated the files grub pointed to for upgrades, so they didnt have to mess with grub conf, maybe that is better, i dont know, I dont design the OS ;)

---

### Post by artmeacham on 2008-05-26
Hmmm...  my installation has a bunch of symlinks named "vmlinuz", "System.map", etc.  Why not just update those and be done with it?  

Messing with people's menu.lst is just asking for trouble, IMO.  Especially if they are changing the order of the kernels in the list, which then results in the wrong kernel being in the default boot position.  Grrrr....

I am happy about the kernel update, though.  I have been having GDB problems which are supposedly related to a kernel bug, and hopefully this will fix it.

---

### Post by masonfoley on 2008-05-26
I believe I've had a very similar experience and I'm about to punt on the Kubuntu/Ubuntu adventure altogether.  Friend recommended Fedora Core...figured what the heck.

I had Hardy 8.04 up and running with everything working besides my DVD playback.  (MythTV, Cups and successfully sharing the printer on our network, MySQL, and various other configurations).  But the DVD not playing back just simply wasn't going to cut it.  Despite all attempts to try the [various suggestions]("http://ubuntuforums.org/showthread.php?t=802980"), I am still unable to get DVDs working.

So, I decided to install Gutsy (7.10) on this box, boot into it and see if I can't get DVD playback working.  

So, I went to install 7.10, resized my original partition to make room for it (this is the guided option during the setup) and the install proceeded as expected.  Grub was successfully updated as 7.10 was configured as a default set along with my 8.04 choices.

Things going ok so far...but...

...yeah...there's always but isn't there?

After reboot, as expected, Adept queued appx 266mb of updates including the kernel.  All of the packages downloaded successfully, then it proceeded into the actual update phase...somewhere along the way, Adept simply crashed.  So, I started Adept up again.  Said it couldn't read the configuration and would I like to resolve the issue for myself.  I'm thinking the database went south and got corrupted.

I decided to reboot...Error 15 when choosing any of the 7.10 choices.  Ridiculous.

My theory and hopefully those in the know will set me straight on this, my theory is that during a kernel upgrade, the devices are re-probed, including the hard drives.  This is where I believe the UUID of the partitions are getting regenerated and as such, the UUID in the menu.lst file no longer matches.  Thus, when attempting to boot/load the image file, no go...or perhaps the image file just got corrupted.  

Does that seem plausibe?  If that's not the case, what other possibilities are there for Adept just blowing up during the update of the kernel?

I'm an IT professional so don't be afraid to throw some tech at me.  I consider myself reasonably experienced with OS installs (installing Red Hat, Websphere and configuring Websphere amongst some of the more challenging tasks I've conqured) but I'm pained to admit, my recent experiences over the last week to get this Kubuntu distro up and running has been baffling to say the least.

Just trying to set-up a media server.  Didn't think it would be this much of a headache.

---

