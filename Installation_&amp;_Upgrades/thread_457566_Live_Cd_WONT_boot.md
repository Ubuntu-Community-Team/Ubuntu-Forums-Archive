---
title: "Live Cd WONT boot"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by 1337newb on 2007-05-28
i have tryed numerous times with the 7.0.4 release of ubuntu, with new discs, downloaded from different sources, and, it just wont boot, it goes straight to the windows xp loading screen.


my bios is set to read from BOTH of my dvd drives before it loads from hard drive, and, i have tryed the cd in both of them, and, i still get the xp login screen...


its almost as if the cd is not bootable for some reason, and, i have no idea as to why this could be.....if any one has any idea, i would like to hear it, i have a 30 gig partition waiting for this release....

---

### Post by merlinus on 2007-05-28
Did you burn your download as a data disk rather than a disk image?

-merlin

---

### Post by rsambuca on 2007-05-28
Yeah, my guess is that you burned the cd as a data disc, whereas you need to burn it as a cd image.  Open the cd in the windows explorer - if you see a bunch of files and folders, it is burned correctly.  If you only see one big file, you will have to burn another disc.

Here is a link to the [[COLOR="Red"]Burning iso files how-to[/COLOR]]("https://help.ubuntu.com/community/BurningIsoHowto").

If that doesn't work, let us know!

---

### Post by ice60 on 2007-05-28
this program will burn it correctly -
[http://www.snapfiles.com/get/burncdcc.html](http://www.snapfiles.com/get/burncdcc.html)

when you look at the burned cd it shouldn't have the iso any more, but a few other files instead \\:D/

---

### Post by 1337newb on 2007-05-28
wow, i love how you guys automatically assume that i know nothing about burning a disc

going back over the 3 discs...this is what i have

disc one
extracted with winrar, and then burnt using explorer (winrar supports iso extraction)

disc two
extracted with winrar, burn with nero

disc three
burnt the image to disc using the option in nero...


so, they are all burnt correctly......none of them work.....

---

### Post by rsambuca on 2007-05-28
> **1337newb said:**
> wow, i love how you guys automatically assume that i know nothing about burning a disc

going back over the 3 discs...this is what i have

disc one
extracted with winrar, and then burnt using explorer (winrar supports iso extraction)

disc two
extracted with winrar, burn with nero

disc three
burnt the image to disc using the option in nero...


so, they are all burnt correctly......none of them work.....

Actually, if you extracted the iso with winrar first, then you have done it incorrectly.

How many files do you see when you look at the disc(s) in explorer???

---

### Post by rsambuca on 2007-05-28
Looking a little closer at your methods of burning the CD's, #'s 1 and 2 definitely will NOT work.

For method 3, what process did you use in nero?

---

### Post by merlinus on 2007-05-28
First of all, I doubt that anyone assumed anything.  I have seen this issue more than several times on the forums, so it seemed like a good place to start.  No insults intended....

Sometimes I have had this same problem, and ctrl-alt-del when windows starts loading has re-started the system, and then it booted from the live cd.

Otherwise, short of checking the computer bios (which you probably already did), I can't think of any way to install Ubuntu, except via an Internet connection, which will be a very lengthy process.

Good luck!

-merlin

---

### Post by 1337newb on 2007-05-28
lol....im sory, but, i think, in this aspect rsambuca i know that what i did WILL work, because, all discs ARE exactly the same.....

anyways, im starting to get a little ticked at this, but, w/e, i have time to waist, and, i want to get this to work

im using nero 7 ultra edition, i start by going to nero start smart, the, over to backup, then, burn disc image, like ive done over 500 times on this machine....(with different things of course)...

as far as what the cd's look like, and what is in them, here, let me show you....

[http://i30.photobucket.com/albums/c332/killtakular/ubuntudisc.jpg](http://i30.photobucket.com/albums/c332/killtakular/ubuntudisc.jpg)
dont know the proper way to link on this forum, so, its just the url...

and, when i put the cd's in, they run the browser program that starts up with windows....dont know how else to describe it, except, that it is the preveiw kinda thing......


i have tryed the ctrl+alt+del, and, it reboots the system, but, goes back to the xp start up screen, and, i know the bios is set right, because, i just went and booted off of my DSL live cd....

---

### Post by teistiz on 2007-05-28
The discs are not the same, you certainly did the first two wrong. Burning them as a collection of files like that does not preserve the data required for the disc to be bootable, although they may look the same in explorer since it only displays the files and not the boot data.

---

### Post by rsambuca on 2007-05-28
OK, you apparently know exactly what you are doing.   I was just trying to help.

Good luck with that.

---

### Post by 1337newb on 2007-05-28
fine, w/e, those two are junk any way *flings accross room*


that still doesnt answer any of the issue of why the other one, the one that was "done correctly" wont boot.


i have apsolutly no idea, and, im sure none of you do......


no wonder i used fedora before......

---

