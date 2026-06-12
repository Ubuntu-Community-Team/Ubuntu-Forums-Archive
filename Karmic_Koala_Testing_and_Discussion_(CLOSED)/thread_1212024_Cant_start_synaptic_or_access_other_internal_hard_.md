---
title: "Cant start synaptic or access other internal hard drive. Security error."
date: 2009-07-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-07-13
I can start synaptic with gksu from a terminal but not from the menu's, it keeps saying incorrect password try again.

[edit] Make that any gui that needs the admin password.

Also trying to access sda1 from places gives this error. It dont even ask for my password.

Any suggestions. I've not messed with anything only updates.

---

### Post by taavikko on 2009-07-13
Devicekit is little b0rked, which is visible to users while trying to mount drives or partitions.

hmm, I couldn't even start synaptics via console with gksu{do}

So confirming your findings...

---

### Post by philinux on 2009-07-13
> **taavikko said:**
> Devicekit is little b0rked, which is visible to users while trying to mount drives or partitions.

hmm, I couldn't even start synaptics via console with gksu{do}

So confirming your findings...

Aha, ok. Is it bugged. I hate filing duplicates and it's not always easy at launchpad.

---

### Post by autocrosser on 2009-07-13
phillinux--please post your bug link--I'l got the same problem......

I can open things with sudo "app" in a term....

---

### Post by philinux on 2009-07-13
> **autocrosser said:**
> phillinux--please post your bug link--I'l got the same problem......

I can open things with sudo "app" in a term....

Ok, if it's a dupi I'll soon find out.
[https://bugs.launchpad.net/bugs/398811](https://bugs.launchpad.net/bugs/398811)

---

### Post by taavikko on 2009-07-13
Minimal testing indicates that gksu is b0rked.
Try to launch anything with gksu ends up in fail.

also, you've reported two issues on a same bug (that's not an forum support area ;) )
Tried to change the affected package, with no avail...

---

### Post by philinux on 2009-07-13
> **taavikko said:**
> Minimal testing indicates that gksu is b0rked.
Try to launch anything with gksu ends up in fail.

also, you've reported two issues on a same bug (that's not an forum support area ;) )
Tried to change the affected package, with no avail...

I assumed devicekit was to blame for both problems.

But **gksu synaptic** works fine.

---

### Post by hgergo on 2009-07-13
Yes same problem here to after the update

---

### Post by taavikko on 2009-07-13
> **philinux said:**
> I assumed devicekit was to blame for both problems.

But **gksu synaptic** works fine.

for me gksu works only in terminal if I've started something via sudo (timestamp is still on default 5 min.))

The mount issue is either gvfs or devicekit-disks related. this happens only on trying to mount USB-stick,
but if I remember correctly there already was thread concerning that one...

---

### Post by philinux on 2009-07-13
> **taavikko said:**
> for me gksu works only in terminal if I've started something via sudo (timestamp is still on default 5 min.))

The mount issue is either gvfs or devicekit-disks related. this happens only on trying to mount USB-stick,
but if I remember correctly there already was thread concerning that one...

Cheers for that. I cant mount sda1 or sda3, not tried usb.

---

### Post by jpeddicord on 2009-07-13
> **philinux said:**
> Ok, if it's a dupi I'll soon find out.
[https://bugs.launchpad.net/bugs/398811](https://bugs.launchpad.net/bugs/398811)

It is. :mrgreen: Marked as duplicate of [lpbug]398849[/lpbug].

The DeviceKit issue may or may not be the same issue, and is probably more PolicyKit related. I think there might be a bug open on that; I remember having the same issue a week or so ago.

---

### Post by philinux on 2009-07-13
> **jacobmp92 said:**
> It is. :mrgreen: Marked as duplicate of [lpbug]398849[/lpbug].

The DeviceKit issue may or may not be the same issue, and is probably more PolicyKit related. I think there might be a bug open on that; I remember having the same issue a week or so ago.

Yes interesting. I reported the bug 2 hours ago but mine is a duplicate of one raise one hour ago.

How odd.

---

### Post by jpeddicord on 2009-07-13
> **philinux said:**
> Yes interesting. I reported the bug 2 hours ago but mine is a duplicate of one raise one hour ago.

How odd.

Bugs are generally marked based on which bug was *triaged* first and, more importantly, has the most complete information. The one I marked it against was filed on gksu, had already been triaged by someone on the bugcontrol team (and set to High priority), and had more complete debugging info.

Anyway, looks like a fix was committed and it should be available soon.

---

### Post by philinux on 2009-07-13
> **jacobmp92 said:**
> Bugs are generally marked based on which bug was *triaged* first and, more importantly, has the most complete information. The one I marked it against was filed on gksu, had already been triaged by someone on the bugcontrol team (and set to High priority), and had more complete debugging info.

Anyway, looks like a fix was committed and it should be available soon.

Ta very much for the insight.

---

### Post by jppr on 2009-07-13
[https://launchpad.net/ubuntu/karmic/+source/libgksu/2.0.12-1ubuntu3](https://launchpad.net/ubuntu/karmic/+source/libgksu/2.0.12-1ubuntu3)

---

### Post by jppr on 2009-07-13
it works again

---

