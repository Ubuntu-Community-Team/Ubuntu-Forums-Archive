---
title: "Wonder if it is to late to get murrine updated"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Technoviking on 2009-03-18
I wonder if it too late to get gtk-murrine engine updated to 0.90.1. Was released today.

---

### Post by Bou on 2009-03-18
What would the benefits be?

---

### Post by Technoviking on 2009-03-18
Some new murrine themes have needed the svn for awhile now. This will cause people to download 3rdparty deb for this. I rather see an official deb.

---

### Post by ato on 2009-03-18
[http://www.cimitan.com/blog/2009/03/16/murrine-0900-is-out/](http://www.cimitan.com/blog/2009/03/16/murrine-0900-is-out/)

---

### Post by Nullack on 2009-03-18
You could request a free exception. Especially if the default builds dont use the engine?

---

### Post by castrojo on 2009-03-18
[https://bugs.edge.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/344154](https://bugs.edge.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/344154)

---

### Post by Technoviking on 2009-03-18
Woot!

---

### Post by castrojo on 2009-03-18
[https://edge.launchpad.net/ubuntu/jaunty/+source/gtk2-engines-murrine/0.90.2-0ubuntu1](https://edge.launchpad.net/ubuntu/jaunty/+source/gtk2-engines-murrine/0.90.2-0ubuntu1)

Done!

---

### Post by Bou on 2009-03-19
I have noticed something weird when using the human theme since murrine was updated: selected elements no longer have a dotted line but a "rubber band" resembling clearlooks'.

The weird part is, only the bottom part of the band is visible. Take a look at the screenshot. Should I file a bug about murrine or something?

---

### Post by taavikko on 2009-03-19
> **Bou said:**
> I have noticed something weird when using the human theme since murrine was updated: selected elements no longer have a dotted line but a "rubber band" resembling clearlooks'.

The weird part is, only the bottom part of the band is visible. Take a look at the screenshot. Should I file a bug about murrine or something?

does this happen with any other theme, or just human?

```
:~$ gedit
/usr/share/themes/Dust/gtk-2.0/gtkrc:708: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Dust/gtk-2.0/gtkrc:709: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.

```

It might be that theme settings are just old, and need updating.

---

### Post by Taiebot65 on 2009-03-19
yes i keep having this error in my terminal....

Edit i m using dust sand

---

### Post by Jay_Bee on 2009-03-19
> **Bou said:**
> I have noticed something weird when using the human theme since murrine was updated: selected elements no longer have a dotted line but a "rubber band" resembling clearlooks'.

The weird part is, only the bottom part of the band is visible. Take a look at the screenshot. Should I file a bug about murrine or something?
I get this too, I think it's a bug.

---

### Post by Bou on 2009-03-19
Well, I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/345410](https://bugs.launchpad.net/ubuntu/+source/gtk2-engines-murrine/+bug/345410)

---

