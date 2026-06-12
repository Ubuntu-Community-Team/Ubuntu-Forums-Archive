---
title: "Unable to Mount Jaunty disk volumes :("
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-12
I tried this yesterday and with today's update it's still "Unable to Mount xxxx Filesystem.  Not Authorized"  The "Palimpset Disk Utility" can see them,  but also says "Error Mounting Device, Details: Permission Denied"

I have been able to read Karmic volumes in Jaunty, however.

Help...

---

### Post by ranch hand on 2009-10-12
Wow, must be an Indiana thing.  I can mount and copy/paste stuff back and forth with Jaunty (several flavors), Hardy, Debian, PhatDebian and 4 flavors of Mandriva right through my "home folder".  In 9.10 I am asked for my password the first time I try to do this in a session.

---

### Post by emarkay on 2009-10-12
> **ranch hand said:**
> Wow, must be an Indiana thing.  I can mount and copy/paste stuff back and forth with Jaunty (several flavors), Hardy, Debian, PhatDebian and 4 flavors of Mandriva right through my "home folder".  In 9.10 I am asked for my password the first time I try to do this in a session.


The password is normal the first time per session.  My problem is before that - a mount permission issue.

---

### Post by ranch hand on 2009-10-12
Did you check in System>Administration>Users and Groups to see if something there got changed?

---

### Post by emarkay on 2009-10-12
I am listed and there is a path to my "home".   For "Groups Settings, my "Group ID" is 0 (zero) - no wait, it's now "1000" (It changed when I went to confirm!)  No boxes are checked for "Group Members".

My "Users Settings > Properties > User Privileges" is shown in the attachment.

I have not messed with this - it doesn't look right...  I AM on a ethernet network, and I have audio devices.  What's FUSE?

---

### Post by VMC on 2009-10-12
What does fstab look like.

---

### Post by emarkay on 2009-10-12
That was the problem - FUSE.

---

### Post by ranch hand on 2009-10-12
Sweat.

---

