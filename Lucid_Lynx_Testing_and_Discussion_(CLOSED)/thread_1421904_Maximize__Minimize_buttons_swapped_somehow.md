---
title: "Maximize / Minimize buttons swapped somehow"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by crjackson on 2010-03-04
Okay, somehow I managed to get my MAXIMIZE / MINIMIZE buttons switched.  How do I put them back.  It does this no matter what theme I'm using.

Thanks...

---

### Post by Atermoon on 2010-03-04
> **crjackson said:**
> Okay, somehow I managed to get my MAXIMIZE / MINIMIZE buttons switched.  How do I put them back.  It does this no matter what theme I'm using.

Thanks...

Open *gconf-editor*, go to *apps > metacity > general* and change the value of *button_layout*.

---

### Post by crjackson on 2010-03-04
> **Atermoon said:**
> Open *gconf-editor*, go to *apps > metacity > general* and change the value of *button_layout*.

Yeah, I posted to soon.  I figured it out as you typed this reply.  Thanks though.  I just can't figure out how it got switched to begin with.

---

### Post by anders_c_ on 2010-03-04
They don't look very good with Ambiance if you have minimize first though...

---

### Post by cyberkilla on 2010-03-04
It happened to me too, the moment I tried that crazy new theme they dumped on my computer...

---

### Post by tekstr1der on 2010-03-05
Is there a bug filed on this issue? This change has propagated itself to affect all themes for me.

---

### Post by VMC on 2010-03-05
> **Atermoon said:**
> Open *gconf-editor*, go to *apps > metacity > general* and change the value of *button_layout*.

That didn't work for Terminal. Still = :maximize,minimize,close

gconf:
/apps/metacity/general/button_layout = :minimize,maximize,close

Edit:I made the mistake of issuing '_**sudo gconf-editor**_' instead of just '**_gconf-editor_**'
After 'gconf-editor', then changing '/apps/metacity/general/button_layout = :minimize,maximize,close',
the gnome-terminal is back to "normal".

---

### Post by cyberkilla on 2010-03-05
> **VMC said:**
> That didn't work for Terminal. Still = :maximize,minimize,close

gconf:
/apps/metacity/general/button_layout = :minimize,maximize,close

Edit:I made the mistake of issuing '_**sudo gconf-editor**_' instead of just '**_gconf-editor_**'
After 'gconf-editor', then changing '/apps/metacity/general/button_layout = :minimize,maximize,close',
the gnome-terminal is back to "normal".

You missed menu:)

Actually, if you look at the schema description when you select that key in gconf-editor, it gives you an example that seems to be the default.

---

### Post by emarkay on 2010-03-05
Awright, who's messin' with the code that ain't broken?

Jeez, I kn ow it's Alpha, but this is just stupid to have gotten out (if actually intended) without an announcement and commentary!

---

