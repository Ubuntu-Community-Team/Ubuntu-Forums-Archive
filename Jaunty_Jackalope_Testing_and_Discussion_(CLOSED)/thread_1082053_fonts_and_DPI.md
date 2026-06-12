---
title: "fonts and DPI"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by garba on 2009-02-27
I really can't understand what this option in the fonts preferences menu is supposed to mean... the DPI is not something you can set, it depends on the screen size and resolution, you just can't change the "fonts DPI" (or whatever it's called in the gnome pref menu im running kde now can't check sorry)... what's that supposed to mean? I remember windows XP having a similar option ("want your fonts to look bigger? move the slider and increase the DPI ratio"), I think this thing should be called something like "font magnification" or the like, really, DPI has absolutely nothing to do with it... or perhaps its just me who's missing the point here ^^ thoughts?

---

### Post by smani on 2009-02-27
It defines how many dot's per inch should be used to render a font, this is purely on software level. On the other hand pixels per inch or per cm or whatever refers to the physical property of your screen.

---

### Post by MacUntu on 2009-02-27
IIRC the font size measure is of fixed size (point, pt.), so it does make sense to set a DPI value for the font rendering.

---

### Post by garba on 2009-02-27
I don't get it, font size is expressed in typographical units, if I want the fonts to be displayed on screen in their actual size then the renderer needs to know both my screen resolution and physical size and then compute the corresponding DPI: in other words, it now knows the size of a pixel on your screen. You CANNOT set the DPI, "setting the DPI" is a non-sense IMHO.

---

### Post by MacUntu on 2009-02-27
The renderer doesn't need to care about your screen. All the renderer needs to know is the resolution for the font to draw. 

The resolution is determined by a given DPI (or better PPI) value and the physical size of the font (point).

Font height 2", font width  1".

PPI: 100

=> draw it with 200px height and 100px width.

PPI: 250

=> draw it with 500px height and 250px width.

---

### Post by garba on 2009-02-28
> **MacUntu said:**
> The renderer doesn't need to care about your screen. All the renderer needs to know is the resolution for the font to draw. 

The resolution is determined by a given DPI (or better PPI) value and the physical size of the font (point).


Provided the renderer only knows about the screen resolution, supplying the correct DPI value for your display actually makes it aware of the PHYSICAL size of your display. It's just basic maths. I can't understand how you could state that the renderer doesn't need to care about the physical size of your screen, I want things to be, say, 3 cm wide and NOT x pixels wide. It's way different. Unless the renderer knows about the physical size of your screen there's no way around it.

---

### Post by MacUntu on 2009-02-28
Think of it as a chain:

Size x of the font --(DPI for renderer)--> pixel size y of the font --(DPI for display)--> size z of the font.

If you set the DPI for the renderer according to the DPI of your screen a 10pt font will be drawn as 10pt font:
3" --(20 DPI)--> 20*3 = 60px --(20 DPI)--> 60/20 = 3" font

If you set the DPI for the renderer lower (higher) than the DPI of your screen the 10pt font will be drawn smaller (larger).

3" --(10 DPI)--> 10*3 = 30px --(20 DPI)--> 30/20 = 1.5" font
3" --(30 DPI)--> 30*3 = 90px --(20 DPI)--> 90/20 = 4.5" font

It's all for scaling purpose and right as it is.  :)

---

### Post by garba on 2009-02-28
> **MacUntu said:**
> 

If you set the DPI for the renderer according to the DPI of your screen a 10pt font will be drawn as 10pt font

That's perfectly clear to me, but the point is, setting the DPI option to a value other than your screen's is NOT the proper way to change the font size. Because of the "chain rule" you mentioned above, toying around with the "DPI value" in the fonts preferences dialog DOES make your fonts bigger or smaller that's true.... But that option should be inteded as a way to OVERRIDE the actual DPI detected based on your screen size and resolution as reported by the x server. Here, take a look at the xdpyinfo output on my system:

screen #0:
  dimensions:    1920x1200 pixels (524x321 millimeters)
  resolution:    93x95 dots per inch
  depths (7):    24, 1, 4, 8, 15, 16, 32

I am just saying that users tend to abuse that setting and it should be made clear what the purpose of that option is.

I remember a dialog in windows xp which read something like "if you want to make your fonts look bigger increase the DPI setting" i know that actually makes them bigger but that sentence is just RETARDED.

---

### Post by The Cog on 2009-02-28
garba, you are right. The option is there for those cases when the actual physical size is not detected correctly. Like on the Dell laptop I use at workm where it thinks it's 96 dpi and I have to manually correct it to 125 dpi which is the real value. When it thinks it's 96 dpi, it makes the text so small I have trouble reading it.

Actually, the setting also comes in handy as a way of generally increasing all the fonts on the screen (by lying about the screen dimensions) if your eyesight is not what it used to be. It's quicker than setting all the different font preferences separately.

---

