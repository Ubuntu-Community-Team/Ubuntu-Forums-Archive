---
title: "Microphone is not working"
date: 2012-10-07
forum: Installation &amp; Upgrades
---

### Post by matkobrcko on 2012-10-07
My microphone in skype is not working. I checked audio settings they're set to duplex. Can anyone help please???

---

### Post by akoskm on 2012-10-07
First you should check is that a skype related problem or your mic fails in general.
Open the console window and use **arecord** (the name tells you everything)
```

arecord -d 3 test

```
this will record you 3 second and save it to the file test. Play back the file with **aplay**
```

aplay test

```
and share the results with us.
Also check your input levels in Sound > Input.

[IMG]http://i49.tinypic.com/fva2xe.png[/IMG]

---

### Post by matkobrcko on 2012-10-07
ok thanks Ill try it

---

### Post by matkobrcko on 2012-10-07
[LEFT]Its not playing any sound

[/LEFT]

---

### Post by matkobrcko on 2012-10-07
/home/matkobrcko/Desktop/Screenshot.png

---

### Post by akoskm on 2012-10-07
> **matkobrcko said:**
> [LEFT]Its not playing any sound

[/LEFT]

So you mean you recorded some sounds with **arecord** and when you played it back with **aplay** you heard nothing from what you recorded earlier.

---

### Post by matkobrcko on 2012-10-07
thats my settings

---

### Post by matkobrcko on 2012-10-07
yes nothing

---

### Post by akoskm on 2012-10-07
> **matkobrcko said:**
> thats my settings

Upload the screenshot to an Image hosting site like [TinyPic]("http://tinypic.com/"), then post the [IMG][/IMG] code.

---

### Post by matkobrcko on 2012-10-07
heres audio settings

---

### Post by matkobrcko on 2012-10-07
[http://tinypic.com/view.php?pic=14b0qp&s=6](http://tinypic.com/view.php?pic=14b0qp&s=6)

---

