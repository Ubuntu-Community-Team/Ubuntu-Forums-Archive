---
title: "Tor"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by topviet on 2010-03-29
It seem to me the tor package is not available for Lucid Lynx. I issued this command:
```

sudo apt-get install tor

```
and I got this message:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate

```

---

### Post by Didius Falco on 2010-03-29
Read here about how to add the Tor repo[U]:

[/U][http://www.torproject.org/docs/debian.html.en](http://www.torproject.org/docs/debian.html.en)

---

### Post by kurros on 2010-03-29
Tor hasn't been in the ubuntu repositories since 8.10. It was decided it wasn't feasible  to stay on top of it's regular security updates. The firefox torbutton extension is still included though which is why you get that message.

Using the torproject's repository that Didius Falco linked is the best way.

---

