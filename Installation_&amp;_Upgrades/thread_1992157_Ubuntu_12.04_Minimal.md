---
title: "Ubuntu 12.04 Minimal"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by WannabeFantasma on 2012-05-31
Hi all

I installed 12.04 some days after it came out, but for some reason it can't play 1080P anymore on XBMC. (and it felt just really sluggish on my hardware.)

Now I wanted to have a minimal install, I did the same thing as with 10.04 being
Sudo apt-get install gnome-core
sudo apt-get install gdm

For some reason it installs  like Totem,a contacts program, some browser, so alot of programs I don't need...)

So I want to know what I should type to get just a minimal desktop enviroment without any programs?

+ I must be able to install the nvidia drivers from the .run file, since that doesn't work atm either... 
(Yes I tried Proprietary drivers before and they were worse than the Nvidia ones.)

Thanks in advance!

My Hardware:
Atom 330
Nvidia ION
2GB ram (512mb for the graphics card)

---

### Post by nothingspecial on 2012-05-31
Gnome is a Desktop Environment, that means it comes with applications for doing stuff, like browsing and watching videos etc.

What you want is a window manager. openbox is a popular one, but there are many more.

---

### Post by lukeiamyourfather on 2012-05-31
This is probably what you're looking for.

```
sudo apt-get install gnome-shell
```

Also I'd install the Nvidia drivers from the repositories if the card is a supported one.

---

### Post by mihalybaci on 2012-05-31
> What you want is a window manager. openbox is a popular one, but there are many more.
+1
I share your quest for simplicity, and its not found in the gnome desktop unfortunately. You can install openbox in Ubuntu or even try Lubuntu/LXDE, which are also relatively lightweight. 

If you really want to go small, I have #! (pronounced crunch-bang) installed on my laptop and I really like it, though everything is done through hotkeys and right clicks (no desktop icons at all) and it can take some getting used to. With no apps running (except conky) the entire OS only uses 80-90 MB of memory and there's really nothing extraneous installed. I would suggest creating a Live CD for #! and see if that works better for you.

---

