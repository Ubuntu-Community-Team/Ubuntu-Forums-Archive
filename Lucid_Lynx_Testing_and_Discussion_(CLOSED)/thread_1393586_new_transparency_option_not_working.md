---
title: "new transparency option not working?"
date: 2010-01-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by FraggedLocust on 2010-01-29
I've heard there was a new transparent menu style ("aero"). All I've heard how to enable it is by adding the Ubuntu Desktop PPA. After doing so, I don't see any new options or themes. Is this actually implemented, or are people just passing around hacked GTK+ theme screenshots?

---

### Post by Merk42 on 2010-01-29
There's a thread about it [here.](http://ubuntuforums.org/showthread.php?t=1349674)

I get the impression that since they didn't make the Alpha 2 deadline, it won't be in Lucid at all. I hope I'm wrong.

---

### Post by joey-elijah on 2010-01-29
> **FraggedLocust said:**
> I've heard there was a new transparent menu style ("aero"). All I've heard how to enable it is by adding the Ubuntu Desktop PPA. After doing so, I don't see any new options or themes. Is this actually implemented, or are people just passing around hacked GTK+ theme screenshots?

You need to use a theme that supports RGBA, The default themes in Ubuntu don't.

---

### Post by snkiz on 2010-01-29
Actually the default Ubuntu theme is based on Murrine, and it does support RGBA. Ubuntu just has it turned off. see the human gtkrc line 97:
```

rgba		    = FALSE # FALSE = disabled, TRUE = enabled

```
between that and Compiz or xcompmgr or {insert composite manager here}
it isn't hard to do trasparent menus or any thing else you want. I personally use xcompmgr with Murrine RGBA, works nicely without all the gee-wiz of Compiz.

---

### Post by phillw on 2010-01-29
> **Merk42 said:**
> There's a thread about it [here.]("http://ubuntuforums.org/showthread.php?t=1349674")

I get the impression that since they didn't make the Alpha 2 deadline, it won't be in Lucid at all. I hope I'm wrong.

I'm not sure if it will be ready for 10.04 , but I do remember some of us testing it out ... it did not go well. But, the consensus seemed to be, that if they got back with a new trial having fixed the problems we had, that we'd not be totally averse to giving it another try. It is only by trying the 'stuff' out can the developers of it can fine-tune it. As Lucid is an LTS, they're going to have to be pretty strict on cut-off times.

Regards,

Phill.

---

### Post by FraggedLocust on 2010-02-02
I see now that the transparency is working when I set it to true. It's just not a crazy new theme like that screenshot I've seen. I don't think it's too intrusive on 9.10 Human theme.

---

