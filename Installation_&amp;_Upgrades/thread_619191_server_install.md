---
title: "server install"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by tekkie123 on 2007-11-21
can someone point me to what i should read to re-install 7.10 server?

i installed it once and the system is up and running, but i want to wipe the disk and re-install, this time choosing Samba and LAMP and a few others.

when i reboot, i don't see an option to boot off the cd/dvd drive.

also, does the server have a desktop i can install? i only get a text shell.

thanks!

---

### Post by coolguy2006delhi on 2007-11-21
After inserting the cd of Ubuntu server , just check in the bios that first boot device is set to cd/dvd rom . Then you can see the cd booting . Also , since server edition of ubuntu is kept to minimal , therefore there is no GUI in it. On the other hand , you can install one , if you like.

---

### Post by tekkie123 on 2007-11-21
> **coolguy2006delhi said:**
> After inserting the cd of Ubuntu server , just check in the bios that first boot device is set to cd/dvd rom . Then you can see the cd booting . Also , since server edition of ubuntu is kept to minimal , therefore there is no GUI in it. On the other hand , you can install one , if you like.

the machine was a winbox. i set the bios to do cd first. that's how i did the first install. would that install have changed the bios? i'll check it again.

can you tell me the name of the most popular desktop? we have a few rhel5.0 servers and their desktop is pretty friendly.

thanks again.

---

### Post by mellowd on 2007-11-21
What exactly do you want to install a desktop on a server for?

---

### Post by tekkie123 on 2007-11-21
> **mellowd said:**
> What exactly do you want to install a desktop on a server for?

Are you asking what applications I plan to run from the desktop on the server?

---

### Post by mellowd on 2007-11-21
> **tekkie123 said:**
> Are you asking what applications I plan to run from the desktop on the server?

I'm asking why you would want a gui on the server?

---

### Post by tekkie123 on 2007-11-21
> **mellowd said:**
> I'm asking why you would want a gui on the server?

Since you first asked "what" and not "why" I assumed (and hoped) the best.

Sorry, I'm not interested your religious persuasions. If you have an answer to my original q, great.

If you have some valid reasons why one would never want a gui on a server, I'll listen. You won't convince me, but I'll listen.

Since you didn't give any reasons, I'll assume it's just flame bait for a holy war. Fair enough?

---

### Post by mellowd on 2007-11-21
> **tekkie123 said:**
> Since you first asked "what" and not "why" I assumed (and hoped) the best.

Sorry, I'm not interested your religious persuasions. If you have an answer to my original q, great.

If you have some valid reasons why one would never want a gui on a server, I'll listen. You won't convince me, but I'll listen.

Since you didn't give any reasons, I'll assume it's just flame bait for a holy war. Fair enough?

?
No, not fair enough, its a simple question. I'm simply wondering what purpose a gui would be on a server.

---

### Post by tekkie123 on 2007-11-21
> **mellowd said:**
> ?
No, not fair enough, its a simple question. I'm simply wondering what purpose a gui would be on a server.

For the same purposes they server on client machines / workstations. Have you ever asked that in a forum?  *G*raphic *U*ser *I*nterface.

Whether you admit it or not, your wonderings are loaded questions. No holy war, please.

---

### Post by mellowd on 2007-11-21
> **tekkie123 said:**
> For the same purposes they server on client machines / workstations. Have you ever asked that in a forum?  *G*raphic *U*ser *I*nterface.

Whether you admit it or not, your wonderings are loaded questions. No holy war, please.

I'm well aware of what a gui is. You are the one who seems to be jumping the gun here. To install gnome all you need to type is this

```
apt-get install gnome-desktop
```

You can also install lamp and samba on a desktop install, this is the reason I was asking

---

