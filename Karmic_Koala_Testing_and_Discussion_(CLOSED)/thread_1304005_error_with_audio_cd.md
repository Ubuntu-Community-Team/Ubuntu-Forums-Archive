---
title: "error with audio cd"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by b0b138 on 2009-10-28
If I've got an audio cd in and goto places and select the cd, an error box pops up that says

Could not open location 'cdda://sr0/'

Failed to execute child process "sound-juicer" (No such file or directory)

---

### Post by mc4man on 2009-10-28
> (No such file or directory) 

That pretty much says it all.

The icon in 'places' is coded to find a file named sound-juicer and open it.

Either install soundjuicer or ...

If you don't want sound-juicer but would like something else to open/happen it's not too hard to do.

The easiest is to either create a link in /usr/bin named sound-juicer pointing to your target or just put what you'd like to open in /usr/bin and name it sound-juicer

Ex. in screen
a link named sound-juicer, the target is a script in my ~/bin that autoplays audio cd's with audacious2

( you can have clicking on the audio cd icon do pretty much anything, doesn't have to play the cd or even be audio cd related ( I think I'll target an autorip script that runs rubyripper in background.

---

### Post by b0b138 on 2009-10-28
Thanks for your response. I guess my 1st post was a bit vague. ;) Was wondering if this was happening to just me? Is it a bug? (not sure how to report bugs properly)

Just wanted to point out it's looking for an app no longer installed by default. :D

---

