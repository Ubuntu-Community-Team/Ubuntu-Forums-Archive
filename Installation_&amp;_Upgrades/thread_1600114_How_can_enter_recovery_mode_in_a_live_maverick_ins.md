---
title: "How can enter recovery mode in a live maverick installation in a USB"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by simar.mohar on 2010-10-18
Actually I have a boot up problem in maverick. There are invalid EDID modes for my monitor. I have to fix this using a command prompt and debugging step by step, probably a recovery mode will work. Meanwhile, I don't want to install it in hard disk as installing again in a pen drive is simple, if the installation goes totally corrupted. And also I don't want to spoil my current ubuntu installation for testing...

---

### Post by simar.mohar on 2010-10-19
> **simar.mohar said:**
> Actually I have a boot up problem in maverick. There are invalid EDID modes for my monitor. I have to fix this using a command prompt and debugging step by step, probably a recovery mode will work. Meanwhile, I don't want to install it in hard disk as installing again in a pen drive is simple, if the installation goes totally corrupted. And also I don't want to spoil my current ubuntu installation for testing...

I got the problem solved by myself at last, still I would like to share with the community so that somebody else may find it useful..
**Here's the procedure**
```

1. Boot from the live installation media
2. Focus on the the 'Try ubuntu without any change to computer' with the keyboard.
3. Press f4 and esc
5. Press -> arror key on the keyboard to edit the boot parameters.
6 You will find 'quite splash' at the end of the long string.
7. Replace this 'quite splash' with 'single'
8. Hit enter

```
Now you will enter the blue recovery screen from where you can enter a command prompt..

---

