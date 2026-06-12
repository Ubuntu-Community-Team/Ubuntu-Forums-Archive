---
title: "Key-Touch Editor"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by SammyR on 2007-03-26
Hi there Guys

I am trying to get my multimedia keys to work on my new Logitech S510. I installed Key-Touch 2.2  and Key-Touch Editor. I can open the key touch application through Systems,  Administration. However Key-Touch Editor doesn't seem to appear there. I tried opening it through the terminal but it doesn't work. 

Anybody have any ideas!!!

:confused:

---

### Post by greybirds on 2007-05-30
I have an s510 as well. The multimedia buttons worked out of the box for me, although the left-hand ones do not. I installed keytouch and keytouch-editor as well but didn't have the problem you're describing with the missing icon. 

However, try this. Open a terminal (Applications > Accessories > Terminal) and type 
```
keytouch-editor
```

This is the same as selecting its icon from the menu. See if the editor starts. If it does, it means the application installed but for some reason the icon's entry didn't get created. There's a couple solutions to that, depending on your comfort level, but it's important to see if the editor is actually there and working first.

---

