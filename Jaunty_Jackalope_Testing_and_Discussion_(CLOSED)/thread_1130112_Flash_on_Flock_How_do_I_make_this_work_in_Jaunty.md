---
title: "Flash on Flock? How do I make this work in Jaunty?"
date: 2009-04-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by crjackson on 2009-04-19
How do I get this to work? I've tried coping the libflash.so to the ~/flock folder and various sub folders. This isn't working for me so I need some guidance here. Thanks for your help.

---

### Post by crjackson on 2009-04-19
Anyone?

---

### Post by iaskedalice09 on 2009-04-19
Not using Flock, but I would suggest running a search for flashplugin-alternative.so and see what you find. Usually in /usr/lib/whatever.

---

### Post by crjackson on 2009-04-19
> **iaskedalice09 said:**
> Not using Flock, but I would suggest running a search for flashplugin-alternative.so and see what you find. Usually in /usr/lib/whatever.

The problem isn't finding the needed file. The problem is I don't know where to place the file so that flock will recognize it.

---

### Post by Darkshade on 2009-04-20
[http://www.hightechsister.com/68/setting-up-flock-on-ubuntu-804-64-bit/](http://www.hightechsister.com/68/setting-up-flock-on-ubuntu-804-64-bit/)
All I could find. Take a look at steps 9 - 13, hope it works.

---

### Post by crjackson on 2009-04-20
> **Darkshade said:**
> [http://www.hightechsister.com/68/setting-up-flock-on-ubuntu-804-64-bit/](http://www.hightechsister.com/68/setting-up-flock-on-ubuntu-804-64-bit/)
All I could find. Take a look at steps 9 - 13, hope it works.

Tried this already. It works for Gutsy, Hardy, and Intrepid. Sadly I can't get it working for Jaunty.

Normally you just make a symlink instead of copying the file. That way when flash is updated through synaptic it rolls over to Flock as well.

I'll keep looking and trying I guess..

Thanks for your efforts...

---

### Post by crjackson on 2009-04-20
Okay, I got it working. Here's how...

Create the following folder....

~/.flock/plugins

Then make a symlink in that folder from...

/user/lib/adobe-flashplugin/libflashplayer.so

Restart Flock and it works. I tried this last night and couldn't get it going. I think I must have made a type in the folder name.

---

