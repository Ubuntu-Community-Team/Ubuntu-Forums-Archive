---
title: "public key is not available"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by GuiGuy on 2007-03-09
I am frustrated by the many "<some domain> edgy Release: The following signatures couldn't be verified because the public key is not available:> blablabla...

A sources list that was well sorted and working last year now results in more than 50% or links generating this message.

Do the keys need to individually updated periodically, as some have told me?

---

### Post by zvacet on 2007-03-10
Basicly,key is authorization.Maybe in your case key is changed and you need enter new one.I belive you will find it on the site witch from you genereted your source list.
```
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
```
Replace KEY with number

---

### Post by pradeepadapa on 2007-03-10
hii didnt get u ?? what d u mean by to replace the KEY by NUMBER plse tell bec i hav the same problem too nd how to find the KEY and what that KEY contains.................

---

### Post by GuiGuy on 2007-03-10
> **zvacet said:**
> Basicly,key is authorization.Maybe in your case key is changed and you need enter new one.I belive you will find it on the site witch from you genereted your source list.
```
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
```
Replace KEY with number

That seems very tedious, especially when there is a few keys to update. Is this by design?

---

### Post by pradeepadapa on 2007-03-10
can anyone plse explain us how to find an public key nd to sort this problem

**[B]anyone plse tell us**[/B]

---

### Post by GuiGuy on 2007-03-10
> **pradeepadapa said:**
> can anyone plse explain us how to find an public key nd to sort this problem

**[B]anyone plse tell us**[/B]

I second that- I looked in on a couple of the websites relating to the invalid keys. Probably due to not being the sharpest tool in the shed I was unable to fathom where the magic number might be hidden.

---

### Post by Kateikyoushi on 2007-03-11
If you post the output can tell you what are the keys you have to enter in those commands.

But here is an example.

> W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY [COLOR="Red"]F120156012B83718[/COLOR]

The red colored text is the key. Add it to the previously mentioned commands.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

---

### Post by GuiGuy on 2007-03-11
> **Kateikyoushi said:**
> 
The red colored text is the key. Add it to the previously mentioned commands.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

Thanks. I just tried that and it it seems to work. But it doesn't overcome my criticism that this is tedious. Surely the package manager could be configured to resolve this?

So, explain again, why is Linux better than Windows?? :? ;)

---

