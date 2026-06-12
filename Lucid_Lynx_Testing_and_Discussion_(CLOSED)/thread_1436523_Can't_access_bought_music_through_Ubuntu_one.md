---
title: "Can't access bought music through Ubuntu one"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by themusicalduck on 2010-03-22
So I just bought an album with the music store. The files uploaded to my Ubuntu One storage, but the files don't show up in my Ubuntu One folder in home. I managed to download the files through the web interface, which has worked fine, but it'd be nice to access them without having to download them manually.

Normal folders I upload can be seen fine, but the Ubuntu One folder seems to be in a folder "User Defined Folders" on the web interface rather than "My Files" and it doesn't show up in nautilus.

There doesn't seem to be anything from the store in my Music folder either.

Is this a current problem or might there be something up with how Ubuntu One storage is set up?

---

### Post by joey-elijah on 2010-03-22
You'll find your purchased music in your home folder in .ubuntuone/purchased music (or something to that effect)

You can easily play downloaded tracks from within Rhythmbox without even needing to know where they are - just click the "+" under 'Music' in the side pane to see a "purchased music" entry that shows your bought music and lets you play away.

---

### Post by castrojo on 2010-03-22
It's possible your file syncing daemon isn't running. Try running "u1sdtool -c" for it to connect, and then wait a minute to see if it downloads the songs.

(I think there's a fix to have the connection turn on but I don't have the bug # handy)

---

### Post by themusicalduck on 2010-03-22
Ahh thanks joey-elijah, found them there.

Having a hidden folder makes it a bit difficult to add them to the collection on Amarok.. but making a symbolic link and adding it works at least.

---

