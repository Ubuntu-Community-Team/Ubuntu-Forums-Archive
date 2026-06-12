---
title: "Drive will not partition!?"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by totallylost on 2006-03-11
Im doing an install of kubuntu and i can get to the point where i need to format and partition the hd (200gb ide) so that windows xp and kubuntu can live happily together.  however when i go to downsize my xp partition the installer doesnt show any change at all- i type in the 150gb value to make it that size and have 50gb for linux but it shows no change on the main manual install page.  its still a single 200gb partition with a small 8.2mb partition of freespace (no idea how that got there-but it was there along with the single 200gb partition before i attempted to change the size).  What should i do
? i really want to have a dual boot system but i dont see how that is possible if my drive isnt partitioned correctly.  Does it matter if im not using the partition #1 and i just partition the main drive instead?? Or will that just ruin a bunch of xp files and leave both OS's inoperable? please help!

---

### Post by az on 2006-03-11
[QUOTE=totallylost]Does it matter if im not using the partition #1 and i just partition the main drive instead?? Or will that just ruin a bunch of xp files and leave both OS's inoperable? please help![/QUOTE]

No, it does not matter.  Perhaps you need to defragment your windows partition first.

Perhaps there are unshown erros that are cropping up.  You can switch your console to the error console by hitting CTRL-ALT-F3.  Anything interesting there?

CTRL-ALT-F1 to get back....

---

### Post by totallylost on 2006-03-11
i dont know if there are errors or not.

a bunch of what i see on that ctrl-alt-f3 screen is this:

Reading all physical volumes. This may take awhile.....
file descriptor 3 left open
file descriptor 4 left open
file descriptor 5 left open
file descriptor 6 left open
No matching physical volumes found 
file descriptor 3 left open
file descriptor 4 left open
file descriptor 5 left open
file descriptor 6 left open
No volume groups found

No idea what any of that means- maybe you understand it.
And should i partition the main 200gb disk instead of partitioning the /media/hda1 200gb partition? or would that erase the /media/hda1 file partition already there and thus delete windows xp too?

---

