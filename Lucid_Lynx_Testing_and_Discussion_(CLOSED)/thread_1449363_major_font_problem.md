---
title: "major font problem"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sandyd on 2010-04-07
hey guys. I need some help w/ solving [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/554935](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/554935)

---

### Post by dcstar on 2010-04-07
> **carlee said:**
> hey guys. I need some help w/ solving [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/554935](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/554935)

10.04 issues should be in the relevant development forum, **not** in the forums for released versions.

---

### Post by djchandler on 2010-04-08
> **carlee said:**
> hey guys. I need some help w/ solving [https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/554935](https://bugs.launchpad.net/ubuntu/+source/fontconfig/+bug/554935)

Another item that can be adjusted is the dpi setting. You may need to adjust that so that the dpi matches the size of the monitor more closely.

I use a 27" widescreen (16x9) with my mythbuntu setup. The monitor has a viewing area 23.5 inches in width. The default is 96 dpi but the actual dpi that matches the width of the screen with 1360x768 is ~58 dpi. That could be messing with the calculations for the display of the font because of the hinting data. There was a lot of artifacts until I made that adjustment.

The other thing I want to know is if just one font is causing the problem, the default Sans used as the application font on a fresh install. Does changing the font used in applications, desktop, documents, etc. make a difference, or does this problem apply to one letter regardless of the font? What happens if you take another synaptic screenshot after changing the Application font to something like DejaVu Sans?

This could be as simple as the hinting information for a single font being corrupt, and re-installing that font could fix it.

---

### Post by mcduck on 2010-04-08
> **djchandler said:**
> Another item that can be adjusted is the dpi setting. You may need to adjust that so that the dpi matches the size of the monitor more closely.

+1 to this. There is no universal setting for DPI value, you always have to adjust it based on your display's size and resolution (since it's about the actual, physical density of the pixels on your display).

And also make sure to set the subpixel order to fit your display.

With wrong settings on these values there's no way how the fonts could be rendered correctly, as font rendering depends on knowing the correct values for your display. And typically when the settings are slightly, but not ridiculously, wrong you'll see some letters being rendered clearly wrong and others just not looking as smooth as they should. It's pretty much about the shape of the letters, and the hinting information contained in the font, and how that plays together with your display's physical features (density of pixels and order of subpixels).

---

### Post by sandyd on 2010-04-08
[s]oh hey, thanks! 120 dpi did the trick [/s]

still, it should detect properly...
edit: it still has the issue after trying a lot of font dpis.

its just a random character thats corrupt accross the entire app, so I dont think its the dpi

---

### Post by scradock on 2010-04-08
> **carlee said:**
> [s]oh hey, thanks! 120 dpi did the trick [/s]

still, it should detect properly...
edit: it still has the issue after trying a lot of font dpis.

its just a random character thats corrupt accross the entire app, so I dont think its the dpi
Don't have any huge insights to offer - but I'm curious if it's always the "w", or does it vary, as implied by your phrase "some random character".

If it varies, when? I mean, what do you change to get a different character corrupted? Close the app, open another one, shutdown and restart?????

---

### Post by djchandler on 2010-04-08
> **carlee said:**
> [s]oh hey, thanks! 120 dpi did the trick [/s]

still, it should detect properly...
edit: it still has the issue after trying a lot of font dpis.

its just a random character thats corrupt accross the entire app, so I dont think its the dpi

Have you tried looking at the font in Character Map? It could be more  than the one character and you just haven't seen it. What happens if you look at the font with Font Viewer?

Have you tried different subpixel orderings, BGR, vertical VRGB or VBGR

Have you tried using a different font for the application font? Have you tried re-installing the package ttf-freefont? 

Is the exact same character (like the "w" in your screen shot) corrupt even if you have multiple fonts being used in an OpenOffice Writer document, not only corrupt in the menus and dialog boxes but the document too? How about the the title bar? Show us a screenshot of an OO Writer document with a sans, sans-serif and monospace font in the body of the document using two different font families please.

If what I described above is the case, we could be looking for a bug in the freetype font engine, perhaps in conjunction with fontconfig. But the random letter being corrupted changing from one application window to another is baffling.

What size is your monitor? I can't imagine 120 dpi would be proper for any laptop. The fonts get too big on my laptop at 1200x800. 120 dpi is pretty high, indicating a fairly small monitor at a very high resolution. Displaying 1600x1050 at 120 dpi would give you monitor that's only 13.33 inches wide. At 16:10 ratio, that's a 16" diagonal screen. If its a 4:3 1600x1200, that's a 16.66, probably would call it a 17". How low of a dpi setting did you try?

---

### Post by mcduck on 2010-04-08
> **djchandler said:**
> What size is your monitor? I can't imagine 120 dpi would be proper for any laptop. 120 dpi is pretty high, indicating a fairly small monitor at a very high resolution. Displaying 1600x1050 at 120 dpi would give you monitor that's only 13.33 inches wide. At 16:10 ratio, that's a 16" diagonal screen. If its a 4:3 1600x1200, that's a 16.66, probably would call it a 17". How low of a dpi setting did you try?
I was thinking about the same thing. But it's not worth *trying* different DPI values, since there's only one correct value and that can be calculated, so better just set it directly to correct value and see if that fixes the problem.

Even if it doesn't, at least there's actually some realistic change of getting nice-looking fonts when the DPI is set to correct value, so it's never a bad thing to do.. ;)

---

### Post by sandyd on 2010-04-08
> **djchandler said:**
> Have you tried looking at the font in Character Map? It could be more  than the one character and you just haven't seen it. What happens if you look at the font with Font Viewer?

Have you tried different subpixel orderings, BGR, vertical VRGB or VBGR
**yup. no difference**
Have you tried using a different font for the application font? Have you tried re-installing the package ttf-freefont? 
**ive installed ALL of the TTFs already + I added some ones from the net to see if it was really a font issue, or a packaged font issue**

Is the exact same character (like the "w" in your screen shot) corrupt even if you have multiple fonts being used in an OpenOffice Writer document, not only corrupt in the menus and dialog boxes but the document too? How about the the title bar? Show us a screenshot of an OO Writer document with a sans, sans-serif and monospace font in the body of the document using two different font families please.
**im going to have to wait on this one because the corruption is very random.**

If what I described above is the case, we could be looking for a bug in the freetype font engine, perhaps in conjunction with fontconfig. But the random letter being corrupted changing from one application window to another is baffling.

What size is your monitor? I can't imagine 120 dpi would be proper for any laptop. The fonts get too big on my laptop at 1200x800. 120 dpi is pretty high, indicating a fairly small monitor at a very high resolution. Displaying 1600x1050 at 120 dpi would give you monitor that's only 13.33 inches wide. At 16:10 ratio, that's a 16" diagonal screen. If its a 4:3 1600x1200, that's a 16.66, probably would call it a 17". How low of a dpi setting did you try?
[B]down to 90 its a dell 17' laptop, the only laptop that has this issue.
ive reinstalled it like 4 times already, and these problems should not exist in beta 2[/B] 

THe corrupt_1.png is the sans serif fonts (thats the default font atm)
.

---

### Post by sandyd on 2010-04-08
ok, it seems that changing the font back to dejavu fixed it... so far.

however, this_is_still_an_issue because people should be able to use whatever font they want without this type of corruption going on.

---

### Post by djchandler on 2010-04-08
> **carlee said:**
> ok, it seems that changing the font back to dejavu fixed it... so far.

however, this_is_still_an_issue because people should be able to use whatever font they want without this type of corruption going on.

Agreed, it is still an issue. I don't think anybody is disputing that. What I was questioning is whether or not I could duplicate it due to differences in my installation, mostly the graphics card, its driver and monitor combination. So that's why I was asking you to perform the testing or experiments.

But it could be that the hinting information in Freefont Sans Serif is where the problem is. The purpose of changing the fonts was to see if the corruption occurred with a different piece to the puzzle in place.

I troubleshoot a lot of hardware. One method I use is to replace a suspected bad part with a known good part. It works most of the time, or it points you directly to the problem if that part isn't bad.

---

### Post by sandyd on 2010-04-08
> **djchandler said:**
> Agreed, it is still an issue. I don't think anybody is disputing that. What I was questioning is whether or not I could duplicate it due to differences in my installation, mostly the graphics card, its driver and monitor combination. So that's why I was asking you to perform the testing or experiments.

But it could be that the hinting information in Freefont Sans Serif is where the problem is. The purpose of changing the fonts was to see if the corruption occurred with a different piece to the puzzle in place.

I troubleshoot a lot of hardware. One method I use is to replace a suspected bad part with a known good part. It works most of the time, or it points you directly to the problem if that part isn't bad.

hmm. I just noticed some issues still going on, so I tried disabling subpixel smoothing. set the hinting to full, and everything turned back to normal. :)

something is deffinately wrong here, cause I tried that combination of settings for 40 other fonts.

---

### Post by djchandler on 2010-04-10
> **carlee said:**
> hmm. I just noticed some issues still going on, so I tried disabling subpixel smoothing. set the hinting to full, and everything turned back to normal. :)

something is deffinately wrong here, cause I tried that combination of settings for 40 other fonts.

I'm assuming this is an LCD screen by the settings you describe.

Have you noticed any pixel dropout other than with fonts, i.e., bit-mapped or vector graphics? Any pixel dropout when running any of the OpenGL screensavers?

I'm starting to wonder what your GPU is and what graphics driver you are using. But I won't insist--I can't see what you are seeing, plus that doesn't explain your screen captures unless it's the driver. But then we should be seeing that others are filing bug reports or asking for help with the issue.

This is a real head scratcher. But when you started talking about fonts, you hooked me. I'll stick with you until you decide it's finished. I used to do a lot of digital typesetting, with thousands of pages under my belt. My sister and I were in the business of laying out custom textbooks for a few years. Font issues are fascinating as well as something most people pay very little attention to. This is kind of my bailiwick.

Hang in there--we'll solve this one too.

---

