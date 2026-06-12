---
title: "Which directories to give their own partitions?"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by PeggySue on 2009-12-04
I am about to have a major partition tidy up on both my hard drives.
I will still keep a windows partition for old times sake but I want several partitions for different linux versions.

In particular I want all my files (documents etc.) to be accessible from all versions.  A 2008 thread suggested that I should have at least: /, /Home and /Swap. But I still have two questions:

Is it sensible (and possible) to have a partition just for user loaded applications like (Anjuta, Banshee etc.) so they can be used by all versions or are there conflicts with installs by different linux OS's on the same machine?

Is it sensible (and possible) to use a separate /boot or is that confusing with multiple root partitions?

I assume that /tmp is so small it doesn't help much to have a single /tmp.

Any ideas?

---

### Post by phillw on 2009-12-04
Hi,

different versions and releases of *nix may use different releases of applications.
/swap needs only creating once -- all installed *nixs will see it and use it.
/home is also a good one to have seperate, it will 'herd' all your docs, music etc into one area that you can 'see' from all installs. Just bear in mind that profiles created within mozilla applications (firefox etc) will be shared with users of the same name accross *nix's - This can either be a good thing (book-marks etc) or may become a bad thing if you don't keep your FF on the same release accross the *nix's.
The applications don't take up a lot of disk space - so you need not worry about things like OpenOffice, etc.

So, /home is good to share. /swap will share itself.
Install your various *nix's on their own / partition, which you can call whatever you want when you partition up.
Regards,

Phill.

---

### Post by audiomick on 2009-12-04
Re Phill's advice, yes, correct as always ;)

I have seen a few suggestions to give each installation it's own /home, and use a dedicated data partition for files you want to share between installs. You can easily change the default store path for most things so that your files all land there, and tell your Firefox to put bookmarks and so on there.

The reason was that it is apparently possible to get configuration conflicts if you use the same home for different distributions.

I would be interested to see what Phill has to say to the above.

---

### Post by PeggySue on 2009-12-04
It appears there might be things to sort out just by having a separate /home so maybe I will shelve the idea of separating out other partitions for now and just stick to /, /home and /swap.

I have two disks so I will have a swap area on each and set them to equal proiority in fstab.  The kernel can then use them in parrallel, speeding things up, allegedly!

---

### Post by phillw on 2009-12-04
hi ... 

Yes, there are pro's and cons of shared /home -- the main ones being FFox and other hidden profiles (like .history etc.)

The safest way round this is to create seperate profiles for each FFox, but this means different login names, or - possibly much simpler, using the profile manager to select a profile of the name of the *nix distro you are using.

Another option is to keep a /home for each distro (This gets around the curse of the hidden files problems) and, instead, make a /data partition upon which to place your documents, audio, video etc. you then only need a link on each distro's desktop to it and 'train' your self to save docs and audio etc there. This disadvantage there, is that you'll not be able to share things like book-marks automatically. (People are very protective about bookmarks !!).

It is entirely upto the person what they wish to do - Linux does not say that you HAVE to it THIS way -- you're free to wander off & explore -- heck, we even help out when, inside, we're screaming "YOU DID WHAT ????!" - lol

As I only use Ubuntu's, I share my entire /home - If you are mixing and matching different *nix's it's only fair to point out one little, possible 'gotcha'. Decide if you JUST want to share Docs, Muzic, Vids etc. - In which case, you can go with shared /data - If you want the easy sharing of bookmarks / profiles etc. - go with shared /home.

Phill.

Phill.

---

### Post by PeggySue on 2009-12-04
Thanks for the inputs.  Much appreciated.

I will definetly put aside ideas of separate /boot, /tmp etc and play with a separate /home.

Most installs will be differnet versions of Ubuntu and I would like to share mail folders and favourites across the partitions.

I will try Gentoo for its source code approach to distributions and Slackware for its speed and reliability but, at the first signs of problems, I will do a reinstall with their own /home.

---

### Post by Hagar Delest on 2009-12-05
Personally, I've set up a dedicated partition for profiles only (FF, TB and OOo). I first make a copy of them in the new /home from the new distro I want to test. If it works fine, I replace it by a link to the partition.

The advantage is that the profiles are no longer hidden since on a dedicated partition and they're easy to backup. The only disadvantage is that you need to make the symlink for each profile at every install.

---

