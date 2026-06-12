---
title: "Gramps 3.4.9 problem with 16.04"
date: 2016-06-29
forum: Installation &amp; Upgrades
---

### Post by Enno Borgsteede on 2016-06-29
For a couple of reasons, I'm still using Gramps 3.4.9, and not the GTK+ 3 based 4.X series. Gramps 3.4.9 works fine for me on older ubuntu versions, but not when I upgrade to 16.04.

In Gramps, I normally use a view where persons are grouped by surname, where each surname is a node that can be expanded to see all individual persons with that name. Similar views exist for sources, where a node can be a book, hiding all entries found in that book.

Anyway, in all ubuntu versions up to 15.10, this tree view works very well, but in 16.04 it does not. It actually has two problems:

1. When I expand the last surname in the view, Gramps generates an exception. When I add log statements to see what happens, it shows that in a tree with two surnames, where only nodes 0 and 1 exist, a call is made for node 2, which does not exist. I can demonstrate that in a tree with a John A and Jane B.

2. My real tree has more than 8000 different surnames, and when I expand a surname near the end, like any surname starting with a Z, Gramps freezes for a couple of seconds. This also happens when I simply select a person near the end of the alphabet for editing. And in this case logs show that, before expanding say node 8000, calls are made for all nodes from 0 to 7999 to check whether these nodes still exist in the display tree.

When I start Gramps with the -v option, it lists the versions of some loaded Python modules, and of Python itself, and between ubuntu 15.10 and 16.04, I see that GTK has changed from version 2.24.28 to 2.24.30, and Python itself from 2.7.10 to 2.7.11. And being a Gramps developer myself, I know that GTK is handling the person view, I suspect that.

And now the big question is: Does anyone know how to test this? I can add log statements to Gramps itself, but I prefer to see what GTK+ is doing. I like to know why it tries to select the non existing node #2 in a 2 surname tree, and why it needs to walk the whole tree to find node #8000, where the older version doesn't do either, and only walks the whole tree when it is really needed, like when a surname for a person is changed, and the whole thing needs to be sorted again.

I know how to compile a GTK version myself, and it's no big issue to add log statements either, but I don't want to replace the system GTK+ version 2, because many other applications still depend on it, and I don't want to corrupt my whole system. So, what I like to know is how I can push Python to work with a hacked GTK+ version 2 that sits in my home folder.

Ideas, anyone?

thanks,

Enno

P.S. I can not prove that GTK really is the problem. It may also be Python making GTK loose focus in tree views somehow.

---

