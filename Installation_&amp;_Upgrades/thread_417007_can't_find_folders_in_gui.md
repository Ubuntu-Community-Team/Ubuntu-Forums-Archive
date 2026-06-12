---
title: "can't find folders in gui"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by kinkdxm on 2007-04-21
I just upgraded to 64 bit feisty 2 days ago.
Today I wanted to watch something I had in 

/home/something/klibido/decoded

but browsing there I do not see the decoded folder at all.
It only contained

/home/something/klibido/db
/home/something/klibido/tmp

Using the terminal I can navigate to 

/home/something/klibido/decoded

with no problem at all.
I like using the gui and clicking on something I want to watch.
Any idea what happened?

---

### Post by richjoyce on 2007-04-21
Hmm, maybe a problem with permissions?
Can you post the results of `ls -al *` when you're in /home/something/klibido folder?

---

### Post by antar on 2007-04-21
It sounds like it's somehow become a hidden folder to me. But that seems really odd...

---

### Post by kinkdxm on 2007-04-21
> **richjoyce said:**
> Hmm, maybe a problem with permissions?
Can you post the results of `ls -al *` when you're in /home/something/klibido folder?

drwxr-xr-x  5 something something  4096 2007-03-30 23:44 .
drwxr-xr-x 75 something something  4096 2007-04-21 13:39 ..
drwxr-xr-x  2 something something  4096 2007-02-02 20:55 db
drwxr-xr-x  8 something something  4096 2007-04-21 12:59 decoded
drwxr-xr-x  2 something something 53248 2007-04-21 13:37 tmp

> **antar said:**
> It sounds like it's somehow become a hidden folder to me. But that seems really odd...

but it's not 
.decoded
it's
decoded

can it still be a hidden file without the . before hand?
I also in the gui file browser selected "Show Hidden Files" but it still wouldn't show.

---

### Post by richjoyce on 2007-04-21
Doesn't seem to be hidden, permissions seem to be fine, this is just really weird.  What happens if you move the folder around (by the command line, I think you have the knowhow to do this, if not let me know and I can walk you through it).

Try renaming it, moving it to another folder, I'm not sure what else to say.  Maybe make another folder named whatever and move all the files that are in decoded to it, and then rmdir decoded and rename whatever to decoded, see if that works?

---

### Post by kinkdxm on 2007-04-22
so after awhile of having my computer on the memory usage gets really really high.
if I log off and log back on it drops back to a decent range.
did that today cause it was getting crazily sluggish and the folders were available in the gui

weird.
no clue why they came back or why they weren't viewable to begin with.
thanks for the replies though.
hopefully it doesn't happen again.

---

