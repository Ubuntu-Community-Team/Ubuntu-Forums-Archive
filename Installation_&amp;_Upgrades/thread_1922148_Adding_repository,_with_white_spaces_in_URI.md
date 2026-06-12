---
title: "Adding repository, with white spaces in URI"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by radiobert on 2012-02-08
My repository URI has whitespaces in it, e.g. "file:/media/my documents/software dev/debs". How should I add it as an entry in sources.list file?

I tried following but it doesn't work:
```
deb 'file:/media/my documents/software' lucid main 
```The 'apt-get update' simply outputs strange errors when the APT line above is used. 

Seems like a bug to me anyway......;)

---

### Post by kc1di on 2012-02-08
> **radiobert said:**
> My repository URI has whitespaces in it, e.g. "file:/media/my documents/software dev/debs". How should I add it as an entry in sources.list file?

I tried following but it doesn't work:
```
deb 'file:/media/my documents/software' lucid main 
```The 'apt-get update' simply outputs strange errors when the APT line above is used. 

Seems like a bug to me anyway......;)

I haven't tried it yet but think it will work
try placing an * in the space and try again
so your entry would look like this 
> deb 'file:/media/my*documents/software' lucid main

---

### Post by drmrgd on 2012-02-08
You might try to use an escape character for the space like this:

```
deb 'file:/media/my\ documents/software' lucid main]
```

For some things - like fstab if I'm not mistaken - you need the ocatal character escape for the space character.  If the above doesn't work, you could try this to see if it works:

```
deb 'file:/media/my\040documents/software' lucid main
```

---

### Post by Lars Noodén on 2012-02-08
Space is 20 in hexadecimal.  So, for URI's the space should be [escaped](http://en.wikipedia.org/wiki/Percent-encoding#Percent-encoding_in_a_URI) as %20.  If you need to escape a lot of strings then you might turn to CPAN's [URI::Escape](http://search.cpan.org/dist/URI/URI/Escape.pm) module or a corresponding module in the scripting language of your choice.

```

deb 'file:/media/my%20documents/software' lucid main

```

---

### Post by drmrgd on 2012-02-08
> **Lars Noodén said:**
> Space is 20 in hexadecimal.  So, for URI's the space should be [escaped](http://en.wikipedia.org/wiki/Percent-encoding#Percent-encoding_in_a_URI) as %20.  If you need to escape a lot of strings then you might turn to CPAN's [URI::Escape](http://search.cpan.org/dist/URI/URI/Escape.pm) module or a corresponding module in the scripting language of your choice.

```

deb 'file:/media/my%20documents/software' lucid main

```

Thanks Lars!  I never know what type of escape to use under different circumstances (i.e. '\ ' vs. '\040' vs '%20').  That Wikipedia page is quite informative!

---

### Post by kc1di on 2012-02-08
Thanks Lars, 
Good info :)

---

### Post by radiobert on 2012-02-09
Thanks all, the "%20" escape character works! Now I don't need the single quotes at all, which doesn't work...

---

