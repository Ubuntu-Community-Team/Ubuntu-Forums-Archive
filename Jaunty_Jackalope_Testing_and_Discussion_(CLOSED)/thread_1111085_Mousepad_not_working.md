---
title: "Mousepad not working"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by RadicalRaid on 2009-03-30
Howdy yall,
A friend of mine just installed 9.04, only problem is, his mousepad isn't working.. When I plug in a usb mouse it works like a charm, but as soon as I unplug, it's gone. 
Any packages that can be recomended to try? It's recognized as a PS/2 mouse in Windows..

Cheers!

---

### Post by steeleyuk on 2009-03-30
> his mousepad isn't working

His mousepad isn't working? Am I reading that right?

---

### Post by Therion on 2009-03-30
> **steeleyuk said:**
> His mousepad isn't working? 
There's a lot of moving parts in a mousepad my friend...  Yup.  Lot of moving parts.

<cough>

---

### Post by FraggedLocust on 2009-03-30
I think touchpad is the word they're looking for.

---

### Post by damis648 on 2009-03-30
Yes, I believe you are looking for trackpad or touchpad. :popcorn:
Does
```
synclient -m 100
```
show any output when touching the trackpad?

---

### Post by steeleyuk on 2009-03-30
I was thinking trackpad but he says if he plugs it in on Windows its recognised as a PS/2 mouse.

---

### Post by damis648 on 2009-03-30
> **steeleyuk said:**
> I was thinking trackpad but he says if he plugs it in on Windows its recognised as a PS/2 mouse.

He said
> It's recognized as a PS/2 mouse in Windows..
Laptop keyboards and trackpads are on a PS/2 interface, I have never seen one otherwise. :popcorn:

---

### Post by steeleyuk on 2009-03-30
Good point, I wrongly presumed he was using a desktop... its been a long day.

---

### Post by RadicalRaid on 2009-03-30
Lol my bad, apparently my English sucks. Yes I mean touchpad for his laptop, somehow I couldn't find the word..
I'll test some stuff and get right back!

---

### Post by RadicalRaid on 2009-03-30
When trying: ```
synclient -m 100
```
We get the output:
Can't access the shared memory area, SHMConfig disabled?

..
This may perhaps be n00bish, BUT WHAT DO WE DO NOW? :O

Cheers!

---

### Post by FraggedLocust on 2009-04-01
[Enable SHMConfig]("https://help.ubuntu.com/community/SynapticsTouchpad")?

---

