---
title: "Edit Window buttons?"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by candtalan on 2010-03-28
lucid beta 1
I am quite certain I will be moving the window buttons towards the right hand side, and I know how this can be done using gconf-editor.

However, most of the default (round) buttons are too small making it hard to see which is which. I will be needing to increase sizes and maybe colour detail - how can I do this?

I like the traditional box icon buttons (such as in themes  Human or Clear looks), although in the customisation facilities it does not seem possible to change from the round buttons to the square ones within themes, which I would like to do.

I have a lot of contact with (adult) novice Ubuntu users and buttons with good clarity are an important choice. Also, they have all become *familiar* with window buttons such as in Human theme. It may be no surprise that they mostly use LTS.

It would be really very useful if there was to be  methods to 

Move buttons left to right, using higher level than text inside running gconf-editor 

Choose different (the traditional boxy buttons) windows buttons as custom within themes.

---

### Post by psyke83 on 2010-03-28
> **candtalan said:**
> lucid beta 1
I am quite certain I will be moving the window buttons towards the right hand side, and I know how this can be done using gconf-editor.

However, most of the default (round) buttons are too small making it hard to see which is which. I will be needing to increase sizes and maybe colour detail - how can I do this?

I like the traditional box icon buttons (such as in themes  Human or Clear looks), although in the customisation facilities it does not seem possible to change from the round buttons to the square ones within themes, which I would like to do.

I have a lot of contact with (adult) novice Ubuntu users and buttons with good clarity are an important choice. Also, they have all become *familiar* with window buttons such as in Human theme. It may be no surprise that they mostly use LTS.

It would be really very useful if there was to be  methods to 

Move buttons left to right, using higher level than text inside running gconf-editor 

Choose different (the traditional boxy buttons) windows buttons as custom within themes.

Changing the size would not be so easy. The window buttons are pixmaps, which would need to be scaled or redrawn. After doing so, you may also need to change the Metacity theme code in order for the buttons to be placed correctly.

Take a look at the files in this folder: /usr/share/themes/Ambiance/metacity-1/
A guide on designing Metacity themes: [http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

---

### Post by Eestlane on 2010-03-28
Radiance has definitely copied the Minimize, Maximize, Close buttons from Apple Mac's OS X, defined by the left align and rounded look with fairly small buttons. It looks nice, though.

However, I too, can't see any reason, why I should change my lifetime habbit and automatic hand movement to right area. If there are plans for using the newly opened space on right, then why not share them?

I think the side switch should be in the gnome-appearance-properties as most newcomers probably come from Windows not Mac. (if someone thought it's a good idea to spend money on Mac, then (s)he wouldn't care so much about Linux).


To be more on topic:
As I said, I think that the new buttons "look" great, and remembering the order of minimize, maximize, close also isn't too hard (except when some of the buttons are left out). To me, it's important to have large enough clickable area, and it is 2-3 pixels more than the drawn buttons themselves, though they could be larger indeed, as there is some space left in titlebar, however it seems to be aligned with the title itself, instead of border (like it is Windows Vista/7). I know it's great to differ from Windows, but not on cost of usability (though I'm sure you've done usability tests, and well, Ubuntu isn't released yet, despite the fact that User Interface Freeze is past, but the final global freeze is still coming on 15th April).


Actually it might be fine if it stays as it is, maybe I just need to give it some time.

EDIT: Wait. The clickable area is larger than I thought, though minimize and maximize could be a bit more in width (height is fine - it's already to the top of the window)

---

