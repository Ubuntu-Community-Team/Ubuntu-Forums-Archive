---
title: "Where's Menu.lst?"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Don1500 on 2009-08-20
I using Kubuntu Karmic Koala (9.10 alpha) and want to modify menu.lst. I found Boot>Grub> but menu.lst is not there. What gives, is it called something else?  ](*,)

---

### Post by Keen101 on 2009-08-20
it should be there...

try copying and pasting this into a terminal:

```
sudo gedit /boot/grub/menu.lst
```


edit: ooopss. im not a kubuntu user. sorry. someone else should be able to help you soon...

---

### Post by Don1500 on 2009-08-20
> **Keen101 said:**
> it should be there...

try copying and pasting this into a terminal:

```
sudo gedit /boot/grub/menu.lst
```

No, Kubuntu, Gedit doesn't work. 

I did a search for menu.lst and came up empty. I can find the one for Ubuntu, but that's not the one I'm using.

---

### Post by bacardiandwatermelon on 2009-08-20
in kubuntu the text editor is called kate

---

### Post by Don1500 on 2009-08-20
> **bacardiandwatermelon said:**
> in kubuntu the text editor is called kate

Yes, got it. I also found that, at least with Karmic Koala, menu.lst does not exist, it is now called grub.cfg. I did the mod that I wanted to do and it worked, so that is still good.

---

### Post by jrox717 on 2009-08-20
Right, because Karmic is going to be distributed with Grub2.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
However, watch out, because it says:
>  Unlike Grub Legacy's menu.lst file, grub.cfg is NOT MEANT TO BE EDITED!!! 

---

### Post by overdrank on 2009-08-20
Moved to Karmic Koala Testing and Discussion

---

### Post by Don1500 on 2009-08-20
OOOOHHHH NOOOOO! Mr. Bill
I did it and it worked, I just moved the start menu a bit, and made sure the Kubuntu entries said Kubuntu, instead of Ubuntu. So  I know which is what.

---

### Post by inportb on 2009-08-20
> **jrox717 said:**
> Right, because Karmic is going to be distributed with Grub2.
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
However, watch out, because it says:

So like... what's the alternative method? =p

---

### Post by jrox717 on 2009-08-20
>  So like... what's the alternative method? =p 

On the wiki it describes how to edit the files in the /boot/grub.d/ directory

---

### Post by ranch hand on 2009-08-21
Use the search in this (testing) forum for grub2.  This is well discussed and works very nicely, if a little rough around the edges.

---

### Post by Don1500 on 2009-08-21
> **Don1500 said:**
> OOOOHHHH NOOOOO! Mr. Bill
I did it and it worked, I just moved the start menu a bit, and made sure the Kubuntu entries said Kubuntu, instead of Ubuntu. So I know which is what.

Well, according to what I read, no matter what I did to the grub.cfg file it will be changed back as soon as it updates for any reason.

I'll force an up date and see what happens. Then I'll try to figure a way to modify the menu so Kubuntu is identified as Kubuntu, and make Ubuntu 9.04 the default.

---

### Post by Miguel on 2009-08-21
Debian testing also moved recently (like last week or so) to grub2. Although you shouldn't edit /boot/grub/grub.cfg, the configuration files are now where they should be: /etc/grub.d/. The files there seem to use a different syntax, though.

*EDIT:* From my karmic partition, the config folder is actually /etc/grub.d/

---

### Post by RaZoR1394 on 2009-08-21
/etc/default/grub

is the file that should be edited then a 

sudo update-grub

should be run

---

### Post by ranch hand on 2009-08-21
> **RaZoR1394 said:**
> /etc/default/grub

is the file that should be edited then a 

sudo update-grub

should be run
OK, since  you won't look where this is actually being dicussed or look at the documentation;
/etc/default/grub   is where you edit for a hidden menu and time out for hidden menu and menu time out

etc/grub.d   is where you do your menu editing.

After doing anything in grub2 you must run update-grub for it to take effect.

There are a number of good guides now.  Get a search engine and use it.

Or, of coarse, you are welcome to reinvent the wheel.

---

### Post by Don1500 on 2009-08-21
> **ranch hand said:**
> OK, since  you won't look where this is actually being dicussed or look at the documentation;.....Or, of coarse, you are welcome to reinvent the wheel.
I will look at all the guides, research as much as I can, then re-invent the wheel so I know how it works.
As always I will read the books, then start with ```
print "hello" 
```

---

