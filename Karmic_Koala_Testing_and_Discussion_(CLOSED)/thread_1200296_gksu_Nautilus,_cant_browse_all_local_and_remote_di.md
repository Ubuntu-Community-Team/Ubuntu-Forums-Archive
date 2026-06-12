---
title: "gksu Nautilus, cant browse all local and remote discs"
date: 2009-06-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-06-29
Hi,
I wonder why I can't browse all local and remote discs (Computer icon in Nautilus tool-bar) from "gksu Nautilus" or as root? 
Error message says: Nautilus cannot handle "computer" locations.
Is this a bug or a feature?

Cheers, Mike

---

### Post by budluva04 on 2009-06-29
i get the same error

---

### Post by chrisccoulson on 2009-06-30
That is because there is no gvfs daemon in the root session for Nautilus to communicate with.

---

### Post by mdurham on 2009-06-30
> **chrisccoulson said:**
> That is because there is no gvfs daemon in the root session for Nautilus to communicate with.

Thanks for your explanation chrisccoulson, so I guess it's a feature!
Of course, my question now is: why is the .gvfs daemon not running in the root session?

Cheers, Mike

---

### Post by chrisccoulson on 2009-07-02
Discussion of the change that introduced this can be viewed [here]("http://bugzilla.gnome.org/show_bug.cgi?id=526454").

Basically, it is considered a bad idea to autospawn a dbus-daemon and gvfs daemon from system processes that use some functions from GIO.

---

### Post by mdurham on 2009-07-02
If it's considered a bad idea, it seems silly to have a button in the tool-bar that just gives an error message and is of no use, don't you think?

Cheers, Mike

---

### Post by ranch hand on 2009-07-03
I have been wondering apout this very problem as I have had it since installing A1.

As of updating today, though, I am not having thisproblem at all.

---

