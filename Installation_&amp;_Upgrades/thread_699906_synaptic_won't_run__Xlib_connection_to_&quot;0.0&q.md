---
title: "synaptic won't run : Xlib: connection to &quot;:0.0&quot; refused by server"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by Psykotik on 2008-02-17
Hi all,

I don't know why since a couple of days I'm experimenting some issues to run synaptic. Whenever I try to run it, I get this:

```

$ sudo synaptic
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(synaptic:6989): Gtk-WARNING **: cannot open display: 
```

I can temporarily bypass this (and allowing my to actually launch synaptic) using a

```
xhost local:root
```

but is there a mean to definitely fix this issue?

---

### Post by Psykotik on 2008-02-18
no idea? Is there any additional information I can provide?

---

### Post by Psykotik on 2008-02-18
Strangely enough, it was related to a change made in visudo. I had to remove 
```

user ALL = NOPASSWD:/usr/sbin/synaptic
```

and everything is back. Don't understand why, still...

---

