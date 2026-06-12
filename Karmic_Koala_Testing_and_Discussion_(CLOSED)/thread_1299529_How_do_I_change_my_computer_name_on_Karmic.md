---
title: "How do I change my computer name on Karmic?"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tzicatl on 2009-10-24
Dear Ubuntu Forum:

Ubuntu is very nice. In fact, so nice, that I am getting very very lazy these days and I don't quite feel motivated enough to fire up a console and write:

```
sudo gedit /etc/hostname
```
and
```
sudo gedit /etc/hosts
```

... just to change my laptop's default name.

I recall that going to System-> Administration -> Network and then selecting the "General" tab was the way to go to change my laptop's hostname. But for some strange reason, now that I upgraded to Jaunty, the "general" tab appears no more.

So dear Ubuntu Forum, has this option just "vanished" on Karmic? Or I should consider buying a new pair of glasses?

Kind Regards.
Noe.

---

### Post by Iowan on 2009-10-24
If(/when?) you edit the hostname manually, consider using **gksudo gedit ...** instead. [http://http://www.psychocats.net/ubuntu/graphicalsudo]("http://http://www.psychocats.net/ubuntu/graphicalsudo")

Hope you find the GUI method...

---

### Post by tzicatl on 2009-10-24
> **Iowan said:**
> If(/when?) you edit the hostname manually, consider using **gksudo gedit ...** instead. [http://http://www.psychocats.net/ubuntu/graphicalsudo]("http://http://www.psychocats.net/ubuntu/graphicalsudo")

Hope you find the GUI method...

Hi Iowan.

Yeah gksudo works  but .. you know... I just like the fancy GUI :D

Noe.

---

### Post by Longinus00 on 2009-10-24
> **tzicatl said:**
> Hi Iowan.

Yeah gksudo works  but .. you know... I just like the fancy GUI :D

Noe.

I think he means you should start gedit with gksudo, not sudo. You'll get even more fancy gui if you use gksudo instead of sudo.

---

### Post by tzicatl on 2009-10-25
> **Longinus00 said:**
> I think he means you should start gedit with gksudo, not sudo. You'll get even more fancy gui if you use gksudo instead of sudo.

Hi Longinus00

Yes, your'e right. But I want the nice lazy GUI so I don't have to execute weird commands nor edit strange system files. Just a window where I change my computer name :P

I know how to change the hostname with no GUI but I just want the GUI. :P

Sorry to insist in the GUI Method. It might sound childish, but not for non tech-savvy users.

Kind regards.
Noe

---

### Post by Longinus00 on 2009-10-25
> **tzicatl said:**
> Hi Longinus00

Yes, your'e right. But I want the nice lazy GUI so I don't have to execute weird commands nor edit strange system files. Just a window where I change my computer name :P

I know how to change the hostname with no GUI but I just want the GUI. :P

Sorry to insist in the GUI Method. It might sound childish, but not for non tech-savvy users.

Kind regards.
Noe

I know what you're talking about; I too am puzzled as to how to change the hostname via a settings window. But if you do need to run gedit as root, next time use gksudo, not sudo.

---

