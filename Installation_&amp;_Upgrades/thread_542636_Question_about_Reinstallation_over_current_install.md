---
title: "Question about Reinstallation over current install"
date: 2007-09-04
forum: Installation &amp; Upgrades
---

### Post by GumbyX on 2007-09-04
I am having some problems with Ubuntu 64bit, and after a month of them, need to do a re-install. My question is general install one: Is it better for me to just to format and do a fresh install, or just reinstall over the current installation? I believe that using the uPure64 repository caused my system to become unstable and I am not sure if a simple re-install will be able to get me back to square one. 

I know a format will do that for me, but I have about 6GB of data (mostly mp3s) that I do not want to have to move to my external and back again (which will take [if I copy all the folders over, including the hidden config folders] about 5 hours). If someone can give me a heads up, I'd appreciate it. I am at my wits end after having random crashes every day at the worst possible times (you spend an hour re-tagging converted mp3s and then lose it all and see how happy you are). I have not gotten an resolutions from the x64 forum, so this might be my only hope.

Thanks ahead of time for the help.

---

### Post by logos34 on 2007-09-04
How big is your hard disk?

---

### Post by GumbyX on 2007-09-04
> **logos34 said:**
> How big is your hard disk?

120 GB. I bought a separate drive to install Ubuntu on.

---

### Post by logos34 on 2007-09-04
Ok, so you've got a big drive and more than likely plenty of unused space.

Here's my idea (assuming you don't have a DVD burner, because otherwise that's the first thing you would have thought to use):

Use Gparted on the ubuntu live cd to shrink your root partition down as much as possible.  Then use [this guide to create a separate /home partition]("http://www.psychocats.net/ubuntu/separatehome") in the freed up space.  If the mp3's are in your home dir they'll be copied over too.

Shrink root down again, leaving as much space as you think you'll need. (Edit: and then expand /home back into the free space).

Now you can reinstall over the old root and your mp3's will be safe and sound on the separate /home.

---

### Post by logos34 on 2007-09-04
you say you bought a separate hard drive for linux...if your main drive has windows and there's room, your can write/copy to NTFS, you just need the ntfs-3g driver for linux...(or use fs-driver on the windows side)...just some thoughts

---

