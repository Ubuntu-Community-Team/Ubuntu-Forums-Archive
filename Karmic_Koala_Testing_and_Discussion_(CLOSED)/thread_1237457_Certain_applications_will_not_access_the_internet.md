---
title: "Certain applications will not access the internet"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ki4jgt on 2009-08-11
I'm running ubuntu 9.10 fully upgraded, with wifi. I can't get certain apps to access the internet. Last.fm and FBReader will not go online

---

### Post by The Toxic Mite on 2009-08-11
Hey! Just out of interest, can you post the outputs of the following Terminal commands please?

```

sudo lshw -c network
lspci (lsusb if it's a USB dongle)
iwconfig
ifconfig

```

(To get to the Terminal, it's Applications > Accessories > Terminal)

:)

---

### Post by ki4jgt on 2009-08-11
[deleted]

---

### Post by The Toxic Mite on 2009-08-11
[deleted]

---

### Post by Bucky Ball on 2009-08-11
I would think those apps might need to work through an open port on the router? In other words, if it was your router, you would forward a port for that app (a secure line out and through the firewall if you like). If you are in an internet cafe, they may not have that port open or could be using a different port for that app so you are getting blocked by their firewall. You might want to check. :)

---

### Post by The Toxic Mite on 2009-08-11
<snip>l, he just needs to a few things!

[http://ubuntuforums.org/showpost.php?p=6895635&postcount=2](http://ubuntuforums.org/showpost.php?p=6895635&postcount=2)

;)

---

### Post by Bucky Ball on 2009-08-11
Beg your pardon?

---

### Post by ki4jgt on 2009-08-11
[deleted]

---

### Post by The Toxic Mite on 2009-08-11
> **Bucky Ball said:**
> Beg your pardon?

Hey hey hey! It was meant to be a joke, no offence meant :|

@OP you might wanna look here:
[INDENT][http://ubuntuforums.org/showpost.php?p=6895635&postcount=2](http://ubuntuforums.org/showpost.php?p=6895635&postcount=2)

EDIT: Just noticed you're running Karmic, do realise it is UNSTABLE. ;)
[/INDENT]

---

### Post by ki4jgt on 2009-08-11
Yes, but I consider myself as an (independent tester) I like reporting the bugs, and making suggestions. It's more fun when the release comes out and you want to know if one of your ideas has made it or not. Not that any of them have, but hey, I can dream can't I?
OK, that sounded a little wierd, but life isn't about staying with the crowd, it's about breaking away from it.

---

### Post by bapoumba on 2009-08-11
Moved to Karmic & one post edited.

---

