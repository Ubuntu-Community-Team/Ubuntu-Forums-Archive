---
title: "Tips to customize 10.04 (Lucid Lynx) Ambient theme"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Agnus on 2010-03-20
Maybe you, like me, happen to hate the orientation of the new theme. Here are a few tips.

**Move window buttons to the right side:**

[INDENT]1. open gconf-editor from terminal
2. apps->metacity->general
   change button_layout value to **:maximize,minimize,close**[/INDENT]
   
**Move window title bar to the center:**

[INDENT]1. sudo nano /usr/share/themes/Ambiance/metacity-1/metacity-theme-1.xml
2. find the section that has **<!-- Window Title -->** comment
   change the following 2 draw elements as such:[/INDENT]

```
<!-- Window Title -->

<draw_ops name="draw_title_text_normal">
  <title color="#dfd8c8"
         x="(width - title_width) / 2"
         y="(((height - title_height) / 2) `max` 0)"/>

</draw_ops>

<draw_ops name="draw_title_text_inactive">
  <title color="#99958b"
         x="(width - title_width) / 2"
         y="(((height - title_height) / 2) `max` 0)"/>
</draw_ops>
```

**--- EDIT ---**

I also uploaded a modified version of Ambience that works with any button orientation (min, max, close)... 

:)

---

### Post by Kom-Si on 2010-03-20
thnx, what a life saver! :)

---

### Post by asmoore82 on 2010-03-20
[SIZE="4"][COLOR="Purple"]Unlock the hidden Ambiance ...[/COLOR][/SIZE]

```
cd $HOME/.themes
cp -Riv /usr/share/themes/Ambiance MyAmbiance
cd MyAmbiance
sed -i 's/Ambiance/MyAmbiance/g' index.theme gtk-2.0/gtkrc
cd metacity-1/
for file in buttontrough_*.png; do [ -f "${file/trough/}" ] || cp -v "$file" "${file/trough/}"; sed -i "s/${file}/${file/trough/}/g" metacity-theme-1.xml ; done

[COLOR="Purple"]#optional[/COLOR]
gconftool-2 --set /apps/metacity/general/button_layout --type string "maximize,minimize:close"
```

Now you can go to "System -> Preferences -> Appearance" and choose the "MyAmbiance" Theme.
See screenshot.

I love the ability to poke around in Canonical's creation.

**EDIT:** This procedure works on a bare Lucid Beta 1 install, but will not work after updates.
The Updated Ambiance has been streamlined and the mysterious unused buttons removed.

---

### Post by margazhang on 2010-04-07
How to move the "maximize, minimize, close" buttons to the right?

---

### Post by zeroseven0183 on 2010-04-07
Here's how :)

> **Agnus said:**
> 
**Move window buttons to the right side:**[INDENT]1. open gconf-editor from terminal
2. apps->metacity->general
   change button_layout value to **:maximize,minimize,close**
[/INDENT]

Don't forget the colon "**:**". It's important.

---

### Post by margazhang on 2010-04-07
> **zeroseven0183 said:**
> Here's how :)



Don't forget the colon "**:**". It's important.

Indeed, colon, that was what I missed! Now it is working!! Thank you so much!!!

---

### Post by dzleon on 2010-04-12
> **Agnus said:**
> 
**Move window buttons to the right side:**

[INDENT]1. open gconf-editor from terminal
2. apps->metacity->general
   change button_layout value to **:maximize,minimize,close**[/INDENT]
   

That still leaves out the menu button on the top left. I set it to **menu:minimize,maximize,close**

It's annoying to have these UI "experts" removing features just to be different.

Now I just have to figure out how to restore the application icon on the top left instead of the generic circle it has now...

---

### Post by BrokeMahPC on 2010-04-12
I have got used to having the buttons on the left and don't mind it at all. I even moved them to the left in my Karmic 9.10 install! :lolflag:

---

### Post by IsraeliHawk on 2010-04-21
bookmarked. you're incredible. thanks alot!!

---

