---
title: "Package Manager &quot;Unresolvable Bug&quot;"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by wonkycyber on 2007-08-17
Hey. My brother's been using Ubuntu for a little bit now, and he's suddenly comes up against this error message whenever he tries to fetch updates from Synaptic or uses apt-get update:

"Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing basilisk2 (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

Any chance you kind sirs might be able to tell a man just what might be up with this? 
That was it on synaptic - it's practically the same message on apt-get update:

"Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Dynamic MMap ran out of room, E:Error occurred while processing basilisk2 (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'"

let me know if there's any more information I can provide...

-Drew

---

### Post by Steveway on 2007-08-17
I had this, too.
Comment out some lines in the sources.list and ceck if it works.
Did he install Automatix?

---

### Post by wonkycyber on 2007-08-17
yeah... automatix2 is def. installed.
couldn't be giving a fifteen year old some computer magick without some multimedias, could I? 
I'm a bit of a beginner myself when it comes to hacking at teh linuxes (while I've been using some ubuntus for the past three years, I'm in fact a lowly end-user), so I'm not sure what exactly you're suggesting I try and do - elaborate, a little more? ^^;

---

### Post by Steveway on 2007-08-17
AFAIK there is an option in Automatix to disable their repos.
Search that switch and disable those repos.
That'll fix it most definitly.

---

