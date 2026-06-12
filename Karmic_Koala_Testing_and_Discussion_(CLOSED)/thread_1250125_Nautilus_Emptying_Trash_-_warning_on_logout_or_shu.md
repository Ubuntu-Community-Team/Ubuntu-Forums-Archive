---
title: "Nautilus Emptying Trash - warning on logout or shutdown"
date: 2009-08-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kylea on 2009-08-26
I am experiencing an issue when I logout or shutdown the system warns that Nautilus is still emptying trash.

I have the option to Lock the Screen, Cancel or Shutdown.

Trash is empty and there are no files in ~/.local/share/Trash/expunged etc.

2.6.31-7-generic #27-Ubuntu SMP Mon Aug 24 19:18:31 UTC 2009 x86_64 GNU/Linux
------------------
Description:	Ubuntu karmic (development branch)
Release:	9.10

---

### Post by ashwinhgtx on 2009-08-26
You could try this. It cleans out the trash properly plus fixes a lot of other things too. Have a go at it.
[http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html](http://www.ubuntugeek.com/bleachbit-cleans-unnecessary-files-to-free-disk-space-and-maintain-privacy.html)

---

### Post by drs305 on 2009-08-26
It could also be root's trash. You can try deleting root's trash with:
```
gksudo nautilus /root/.local/share/Trash
```
Use SHIFT-DEL to delete the Trash folder (and it's subfolders. If you don't use SHIFT-DEL, the folder will be deleted and moved to ... Trash ;-)

---

### Post by kylea on 2009-08-26
Thanks guys - tried both those suggestions - no change

There are now 4 instances of Nautilus doing these functions?

Deleteing Files
Moving Files
Moving Files
Copying Files

I'll leave the PC running overnight and see what its doing in the morning.

This is new behaviour - last two days with Karmic 64 Bit

---

### Post by drs305 on 2009-08-26
I don't know if it's possible, but it could be that nautilus is caught in an endless loop trying to delete trash, which is going into the trash bin, which is then trying to be deleted again. That's why SHIFT-DEL is needed to delete Trash when using a file browser.

I'd just kill nautilus - it's most likely not going to do anything overnight that it can't in a few minutes.

---

### Post by Perfect Storm on 2009-08-26
Note, that you're using alpha version. You might check if there's any bug report on it or do a bug report. If you're new to Linux and Ubuntu it's not recommendable running alpha and early beta.


Thread moved to 9.10 development forum.

---

### Post by rogerdean on 2009-08-26
I'm getting same symptoms since today's updates I think. I'm logging out regardless with no problems noted yet...

---

### Post by froggyswamp on 2009-08-26
I can confirm, same "trash" issue here. Plus the computer won't shut down, but this is another bug I guess has been reported.

---

### Post by tekstr1der on 2009-08-26
> **kylea said:**
> There are now 4 instances of Nautilus doing these functions?

Deleteing Files
Moving Files
Moving Files
Copying Files


Yup. Seeing this now too for the first time. Happens on clean user profile also. Did you file a bug on this?

---

### Post by kylea on 2009-08-26
"Did you file a bug on this?"

Not yet - wanted to see if "it cleared" - but as its confirmed behaviour I'll file a bug - under Nautilus?

Yeap - aware its Alpha - just doing testing - my small contribution :)

------------------
Here is the bug report

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/419582](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/419582)

also

This is actually a duplicate of 

[https://bugs.launchpad.net/bugs/419184](https://bugs.launchpad.net/bugs/419184)

---

