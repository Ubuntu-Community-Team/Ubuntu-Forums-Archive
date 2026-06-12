---
title: "Hal and fdi files"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mister_pink on 2009-04-18
Can anyone explain whats changed with these? I have one using the the instructions here: [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB) which enables using a mouse button and the ball to scroll. However since upgrading to jaunty it no longer works.

I've seen some information around other people have had some problems but couldn't find anything helpful. Hopefully someone can point me in the right direction.

Cheers.

---

### Post by ddrichardson on 2009-04-18
Are the amended fdi files still there if you've upgraded - has the package overwritten them?

---

### Post by mister_pink on 2009-04-18
Well the plot thickens.

The file is there, and I think it is being applied, but that somehow it is now wrong.

If I hold down the button and scroll up it does the action you would expect from a middle click. So I guess one of the button numbers is wrong or that something else is remapping them.

Edit: I always seem to solve things myself shortly after posting them...

For anyone else with this issue: I removed the button mapping line and now all works fine. I noticed in those instructions that it gave that line, then mentioned underneath that hal seemed to ignore it. It seems that hal no longer ignores it, but why its was there in the first place is a mystery to me...

---

### Post by ddrichardson on 2009-04-19
Did you edit the wiki?

---

### Post by mister_pink on 2009-04-19
I haven't, although I think I'll add a small comment to it. I'm not sure if its the wiki that is incorrect or if I've got something else changing my button mapping elsewhere in my mess of fiddling around with things...

Edit: As I suspected, it was because xmodmap and hal were both swapping buttons around.

---

