---
title: "Upgrade to Gutsy RC broke Graphics Card (At Radeon 200mi, fglrx)"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by lazyrussian on 2007-10-15
Heya,

So I upgraded over night - I woke up in the morning, rebooted my computer and I cant start the x server. I try starting it from recovery and I'm having the same problem.

I proceed to uninstall my fglrx drivers (I have a Radeon 200m), and try to reinstall them, but when I run apt-get update, I get a "Failed to Fetch" error for every address in my sources.list. Keep in mind I'm editing everything via Vi. I'm not worried about fixing my sounds problem at the moment, but I'd like to know how fix the following:

1) Sources.list (Only the default ubuntu addresses are in the sources.list  repository) - It keeps syaing it cannot resolve archive.ubuntu.com (and failed to fetch the corresponding address)

2) How to activate my 3D card drive. I knwo you can do it thrugh the GUI Restricted Manager option, but again, I'm stuck with bash and Vi.

I can't export any of the errors at the moment in a text document because I'm on a different computer typing this up.

At the moment, a fresh install is not an option - I have a dual boot laptop, and I rather not try messing around with that.

Thanks in advance.

---

### Post by lazyrussian on 2007-10-15
I also should not that everytime I try to install one of the xorg packages, I get the following message:

"Package is not available but is referred to by another package"

The other packages is not mentioned

---

### Post by lazyrussian on 2007-10-15
Ok Update:

I just got the fglrx packages installed. All I did was open sources.list in Vi, delete a few old repos t(that were commented out) and saved. Restarted my computer and ran sudo apt-get update and it worked. I was able to startx from the recovery mode and reactivate my 3d driver.

Now lets see what happens....

---

### Post by lazyrussian on 2007-10-15
Alright, fixed the graphcis card problem, the 3d-driver problem, and temporary fixed the gdm greeter problem.

Lesson I learned: Ctrl-Alt-F2 will let you run apt-ger update while recover mode wont.  Also make sure to get rid of the legacy repo's, even if they're commented out. Logical? No. But it worked, and until I learn more about Ubuntu, I'll try to keep my system as clean and up to date as possible.

---

