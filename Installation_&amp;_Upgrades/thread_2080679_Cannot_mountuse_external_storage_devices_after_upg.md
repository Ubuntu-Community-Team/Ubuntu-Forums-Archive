---
title: "Cannot mount/use external storage devices after upgrading to 12.10"
date: 2012-11-04
forum: Installation &amp; Upgrades
---

### Post by celsofaf on 2012-11-04
Hello

I upgraded my Ubuntu from 12.04 to 12.10 some days ago. Apparently, no problems, but I can no longer mount external devices as a normal user. For example, when I try tell Nautilus to access one of my external HDDs, it returns the following error message (the words may not be exactly these in English, as I use my system in Portuguese):

"It is not possible to show /media/celso/My Book
The location is not a folder."

The same happens with DVDs, memory cards and so on. But I am still able to mount and use these devices as the root user - which is not good, of course. For example, I just returned from a trip and I only could download the pictures from my camera's memory card to my external HDD because I did this as the root user.

I have no idea about what caused this and of the solution. Has anyone already had this trouble before, or could anyone give a hint?

I don't want to do a fresh Ubuntu install on my computer. The last fresh install was the 11.04 version I think, and I upgraded from one to another since then without major issues.

Thanks!

---

### Post by celsofaf on 2012-11-06
I ended up "solving" it by opening Nautilus as root and giving read/write permissions to all users on the /media folder and children. Still wondering what caused this trouble.

And now I tried printing something; Ubuntu can't find my printer. :(

---

