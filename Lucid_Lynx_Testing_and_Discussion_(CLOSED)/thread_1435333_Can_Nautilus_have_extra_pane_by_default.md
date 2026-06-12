---
title: "Can Nautilus have extra pane by default ?"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tcchris on 2010-03-21
As title suggests , I like the extra pane in the new nautilus .
I Would like that to be the default view when I open nautilus

---

### Post by knarf on 2010-03-21
Well, there is an option for it... 
```
gconftool-2 --set --type=bool  /apps/nautilus/preferences/start_with_extra_pane true
```...but is does not seem to work.

[SIZE=1][COLOR=Silver] It might have been an option in a previous version of nautilus which has been taken out by the *turtleneckbrigade* 8-| ...[/COLOR][/SIZE]

---

### Post by autocrosser on 2010-03-21
I tried that also---looks like a bug report needs to be made......

---

### Post by tcchris on 2010-03-21
I checked in gconf-editor , and that key was not there .
Is this a bug or just not implemented yet ?

---

### Post by tcchris on 2010-03-21
I should have googled first .
There was a bug report   GNOME Bugzilla – Bug 608431

"Alex agreed that the focus for Nautilus is not to be a permanent dual pane file manager. Attached patch removes the key that remembered the split view toggle status, so every new window starts "clean"."

This won't be a permanent remembered option . Too bad for me , right ?

---

### Post by SushiR on 2010-03-21
> **tcchris said:**
> "Alex agreed that the focus for Nautilus is not to be a permanent dual pane file manager. Attached patch removes the key that remembered the split view toggle status, so every new window starts "clean"."

Sometimes I just think the Gnome devs just live in their own ivory tower...

---

### Post by autocrosser on 2010-03-21
I have added to the bug report---I would suggest anyone that wants this do so also......  [https://bugzilla.gnome.org/show_bug.cgi?id=608431](https://bugzilla.gnome.org/show_bug.cgi?id=608431)

We might have a chance with this one---it's just a gconf key that is already there.....

Also--We might raise some "thought" here: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515057](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/515057)

---

### Post by NCLI on 2010-03-21
Added my support at Launchpad as well. I don't have a bugzilla account.

---

### Post by tcchris on 2010-03-21
added support at bugzilla

---

### Post by Sennaista on 2010-04-02
Added my support at Launchpad.

---

### Post by berndth on 2010-04-04
Basically, what "Adding support" does is spamming bug reports and thus making them unreadable.

---

### Post by 0004tom on 2010-04-04
What do you mean by Extra Pane?

I have the option in View > Extra Pane F3

Which open a second folder view. 

Nautilus 2.30.0

---

### Post by tcchris on 2010-04-04
Berndth , I did not know that , sorry


The deal with two panes is that we want it to be optional to have it default when you open Nautilus

---

### Post by Killigrew on 2010-04-04
yes, and they could fix it with approximately two lines of code and don't do it,
that is a shame...
We don't have another way to tell them what we want!
And once more, i don't need the default option, but i want to support the
people who want it, because it does not harm me nor any body else
but it would make them happy and give them the possibility to use there computer as they want to.

greetings :)

---

### Post by berndth on 2010-04-04
> **Killigrew said:**
> yes, and they could fix it with approximately two lines of code and don't do it,

That is not correct.

> **Killigrew said:**
> We don't have another way to tell them what we want!

The mailing list is a suitable place for design discussions.

---

### Post by kev77 on 2010-04-28
This should be a standard option in the netbook remix!

---

