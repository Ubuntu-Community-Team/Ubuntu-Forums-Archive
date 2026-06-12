---
title: "Humanity icon theme - strange - everything ticked!"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jjccaatt on 2009-10-13
Hi,


Updated Karmic beta this morning, and all my icons have a green "tick" in the top right corner.

I tried all three variations of the Humanity icon themes, and they're all the same.
Other themes seemed to be ok.

What's happening here?!



Cheers,
jcat

---

### Post by matcram on 2009-10-13
When you right click on an element with a green tick you see that it is used to mark the files synced by ubuntuone.

I logged in on my ubuntuone account to verify this and none of the files were synced.

I don't know how they got ticked but it doesn't happen to all my files...

****, i checked other folders and they are all ticked this way.... Lame.

Any info from power users ? :-D

---

### Post by jjccaatt on 2009-10-13
Ok, thanks.

Now I know what it is, I know how to remove it.. :)
..install got rid of them.  I can't see myself using the ubutnuone service anyway!



Cheers,
jcat

---

### Post by Peter09 on 2009-10-13
How did you get rid of the arrows?

---

### Post by jjccaatt on 2009-10-13
There may be a proper way fo configuring UbuntuOne not to tick icons, but I don't want UbuntuOne at all.  So I just

aptitude purge ubuntuone-client  #(accept solution to remove ubuntuone-client and ubuntuone-client-gnome)
aptitude safe-upgrade



Cheers,
jcat

---

### Post by Peter09 on 2009-10-13
Thanks

---

### Post by joey-elijah on 2009-10-13
Is it just me or has UbuntuOne got a new panel icon?

---

### Post by taavikko on 2009-10-13
[https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/450112](https://bugs.edge.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/450112)

---

### Post by emarkay on 2009-10-13
Duplicate post - OP Please mark as "Solved"
[http://ubuntuforums.org/showthread.php?t=1289829](http://ubuntuforums.org/showthread.php?t=1289829)

FWIW, this bug is marked with the rare "Critical" !

---

### Post by Junior_Sampa on 2009-10-13
According to the launchpad information, the fix is already committed.

Best regards,

---

