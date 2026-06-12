---
title: "Karmic, Jaunty, Intrepid-Synaptic Quick Search. How does it work?"
date: 2009-10-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-10-12
OK, I see now something like "reindexing search" but I have not been able to type in, say "a7x" and have it display all the files with "7xpg" in them.  

I have to use "Search" and it's pop-up to find this.  Is this just supposed to be a filter to only display the specified items AFTER a search? All these years, and I am still confused.

Thanks.

---

### Post by emarkay on 2009-10-14
Anyone? :)

---

### Post by talkingwires on 2009-10-14
Synaptic quick search was alway broken for me (it was permanently greyed out) until I did a fresh install. As far as I can tell, it filters by title of whatever packages are currently displayed, be it the list of all packages available when Synaptic first loads, or the current search results.

---

### Post by LKjell on 2009-10-14
> **emarkay said:**
> OK, I see now something like "reindexing search" but I have not been able to type in, say "a7x" and have it display all the files with "7xpg" in them.  

I have to use "Search" and it's pop-up to find this.  Is this just supposed to be a filter to only display the specified items AFTER a search? All these years, and I am still confused.

Thanks.
Refresh the list and let it finish to rebuild the search index. It can take some time..

---

### Post by girto on 2009-10-14
There is at least a bug report where the quick search does not list except installed packages.

It bit me (in Jaunty) not a very long time ago. There was a console workaround which rebuilt the index correctly (not sure if it kept being rebuilt on each synaptic update).

---

### Post by ranch hand on 2009-10-14
The real question should be;

What in flinderation is that dog still doing in synaptic?

---

### Post by emarkay on 2009-10-15
> **girto said:**
> There is at least a bug report where the quick search does not list except installed packages.

It bit me (in Jaunty) not a very long time ago. There was a console workaround which rebuilt the index correctly (not sure if it kept being rebuilt on each synaptic update).


Can you get that bug#, and or the workaround for us, if possible?

---

### Post by ronacc on 2009-10-15
even when its working "correctly" it is pretty much worthless . misses many files and doesn't alphabetise the output .

---

### Post by philinux on 2009-10-15
+1

> **ronacc said:**
> even when its working "correctly" it is pretty much worthless . misses many files and doesn't alphabetise the output .

Never use it. Ranchhand is right the dog needs chasing out. ;)

---

### Post by girto on 2009-10-15
> **emarkay said:**
> Can you get that bug#, and or the workaround for us, if possible?

Delete the /var/lib/apt-xapian-index/ directory and rebuild it with "sudo update-apt-xapian-index"

---

### Post by emarkay on 2009-10-15
> **girto said:**
> Delete the /var/lib/apt-xapian-index/ directory and rebuild it with "sudo update-apt-xapian-index"

And this replaces what with what?  :)

---

### Post by cariboo on 2009-10-15
Quick search has always worked well for me, but then I usually know what I'm looking for.

---

### Post by wakingrufus on 2009-10-15
I love the quick search.  works well for me.

---

