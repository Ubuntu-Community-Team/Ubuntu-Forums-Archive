---
title: "AMSN wont install..."
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by mattmagician on 2006-12-28
im a newb when it comes to all this, but i want AMSN, and heres what happens when i try to install it:

i go to Add/Remove Applications.
search AMSN
see the AMSN icon, try to check the box.
message pops up:
Cannot install 'amsn'

This application conflicts with other installed software. To install 'amsn' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.
i switch to advanced mode
search AMSN
try to mark it for instalation.
Message:
[IMG]http://i92.photobucket.com/albums/l32/mattmagician/Screenshot-2.png[/IMG]
i hit Mark
message:
[IMG]http://i92.photobucket.com/albums/l32/mattmagician/Screenshot2.png[/IMG]
So what should i do???
thanks!
please remember i am still somewhat new at all this.](*,) ](*,) ](*,)

---

### Post by jclmusic on 2006-12-28
check that you have all the repositories enabled.

if you do and still get this problem, you could try installing the autopackage from the amsn website.

---

### Post by mattmagician on 2006-12-28
ok, how do i do that? lol.

---

### Post by mattmagician on 2006-12-28
I still need help people!

---

### Post by jclmusic on 2006-12-28
sorry been busy today. ok here goes...

open the terminal and type this:
```

gksudo gedit /etc/sources.list

```

this will open a text file. for every line with a web adress in it that begins with a #, delete that # from the beggining of that line. save the file and then close it.

then open synaptic again and click the reload button at the top. it should then work.

if it doesn't work let me know and i'll explain the second option.
if neither of those work, i'm afraid you'll need someone with more knowledge than me!

---

### Post by mattmagician on 2006-12-28
did so, the terminal says:
[IMG]http://i92.photobucket.com/albums/l32/mattmagician/Screenshot3.png[/IMG]
sources list is empty...

---

### Post by jclmusic on 2006-12-28
sorry, my mistake, it's 
```

gksudo gedit /etc/apt/sources.list

```

---

