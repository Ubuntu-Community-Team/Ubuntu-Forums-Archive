---
title: "Error updating from 9.10"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lobfredd on 2010-04-22
I tried updating from 9.10.
When i did that it was the beta 2 that was out i think.
I got an error massage i cant remember when i was done.
I rebooted and was stuck on the purple Ubuntu boot screen.
If i spam Esc when it boots i actually get into ubuntu and everyting seems to work except for Mouse and the Keyboard! lol
I have tried drfferent keyboards and mouses with no luck.
so how to fix this? :D

---

### Post by cariboo on 2010-04-22
Without knowing what the error message was, it is pretty hard to help. Does your keyboard work if you start in recovery mode? To get to the grub menu hold down the shift key during startup. You should then be able to select recovery mode. Once at the menu select drop to root prompt with networking. Once at the prompt type:

```
apt-get -f install
```

next type:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

to see if you can get the upgrade to finish.

---

### Post by lobfredd on 2010-04-22
Really thanks!
this worked flawlessy! :D

---

