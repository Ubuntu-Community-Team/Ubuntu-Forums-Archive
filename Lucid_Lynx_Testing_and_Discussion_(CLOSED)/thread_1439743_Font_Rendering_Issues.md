---
title: "Font Rendering Issues"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jaoc223 on 2010-03-26
Are font rendering issues being addressed by Ubuntu devs?
Do they have anything to do with firefox and chromium browers
for Ubuntu? also do different themes affect font rendering.
This has been deal breaker for me. I love Ubuntu, but ff and
chromium are almost unbearable for my eyes. It's sad to have 
such font issues with such a great beta release.
Thanks, Jaco

---

### Post by psyke83 on 2010-03-26
> **jaoc223 said:**
> Are font rendering issues being addressed by Ubuntu devs?
Do they have anything to do with firefox and chromium browers
for Ubuntu? also do different themes affect font rendering.
This has been deal breaker for me. I love Ubuntu, but ff and
chromium are almost unbearable for my eyes. It's sad to have 
such font issues with such a great beta release.
Thanks, Jaco

See: [http://ubuntuforums.org/showpost.php?p=9010164&postcount=10](http://ubuntuforums.org/showpost.php?p=9010164&postcount=10)

Although the linked bug is for Firefox, the PPA which includes patched cairo packages may fix your Chrome issue.

---

### Post by jaoc223 on 2010-03-26
psyke83 you mean if I install cairo dock, which I just did, may resolve the font issue in chrome? or is there a separate patch. I just installed cairo 
2.1.3-7

---

### Post by psyke83 on 2010-03-26
> **jaoc223 said:**
> psyke83 you mean if I install cairo dock, which I just did, may resolve the font issue in chrome? or is there a separate patch. I just installed cairo 
2.1.3-7

No. I was referring to the libcairo packages with LCD patches. Cairo Dock is not related in any way (the only relation is that it uses cairo for rendering).

---

### Post by jaoc223 on 2010-03-26
psyke83, thanks I installed the patch, I see a bit of improvement, some websites render better than others, is that generally the case?
I notice on the forums here I still get a little blue hinting, but better than before, should this be expected as a general rule? psyke, also do themes have an affect on the way font's are rendered on the desktop?
thanks again. Jaco

---

### Post by mdurham on 2010-03-26
> **jaoc223 said:**
> ...I love Ubuntu, but ff and
chromium are almost unbearable for my eyes

How about a screen-shot of what you mean, I'll see if my eyes can bear it.

---

### Post by jaoc223 on 2010-03-26
mdurham, since I installed that patch it seems a bitbetter, I will try to upload a screen shot.

---

### Post by jaoc223 on 2010-03-26
mdurham how do i upload the image?

---

### Post by psyke83 on 2010-03-26
> **jaoc223 said:**
> psyke83, thanks I installed the patch, I see a bit of improvement, some websites render better than others, is that generally the case?
I notice on the forums here I still get a little blue hinting, but better than before, should this be expected as a general rule? psyke, also do themes have an affect on the way font's are rendered on the desktop?
thanks again. Jaco

Have you also made sure to activate **both **PPAs I referenced in the other thread? I suspect that you didn't enable the firefox-smooth-scaling PPA. You should see the Firefox branding change back to the blue globe and "Namoraka" application name (because Mozilla prohibit unauthorized builds from using the official artwork). The usual advice also applies: restart Firefox and/or log out and back in for changes to take effect.

Themes can change the colour of text and its background in desktop applications, so it can change your perception of how the fonts appear to your eyes, yes.

Technically speaking, however, changing the theme cannot affect the font type, size, or hinting method used; only you can do that through the settings in System -> Preferences -> Appearance -> Fonts.

---

### Post by jaoc223 on 2010-03-26
mdurham here's a screenshot. pyske83 check my screenshot tell me what you think.

---

### Post by psyke83 on 2010-03-26
> **jaoc223 said:**
> mdurham here's a screenshot. pyske83 check my screenshot tell me what you think.
It's impossible to tell - your screenshot is scaled and full of artifacts due to jpeg compression.

You should upload these kind of screenshots as unscaled and with a lossless filetype (such as .png).

---

### Post by jaoc223 on 2010-03-26
screenshot

---

### Post by psyke83 on 2010-03-26
> **jaoc223 said:**
> screenshot

Same problem. It's a scaled jpeg.

---

### Post by jaoc223 on 2010-03-26
is this better, though it's just a corner of the screen

---

### Post by jaoc223 on 2010-03-26
another

---

### Post by mdurham on 2010-03-27
I'm no expert but unless I'm missing something, the font in those two pics look okay to me. They look the same as mine always have.
Cheers

---

### Post by Roosje on 2010-03-27
> **jaoc223 said:**
> another

Had some similar problem then noticed that for one reason or another in System>Preferences>Appearance>Fonts - Rendering - The detailed setting for LCD was Grey-scale, changed that to appropriate and all was well again, dunno if it counts as a bug, but seems it sets it to the wrong rendering as standard.

Wilco

---

### Post by jaoc223 on 2010-03-27
Perhaps the issue is with Chromium browser then.

---

