---
title: "Font Sizes Survey"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rockin_goliath on 2010-03-22
With [Mark Shuttleworth's recent invitation for solid data]("http://www.webupd8.org/2010/03/ubuntu-is-not-democratic.html") with regards to the window buttons, I thought I would take this opportunity to research how Ubuntu users configure their font settings. 

I believe the default font settings in Ubuntu Karmic are Sans 10 for Applications, Documents, and Desktop; Sans 10 Bold for the Window Title, and Monospace 10 for single-width fonts (like the terminal). 

One of the first things i do when I install Ubuntu for myself and other users is decrease the font sizes to 8 point, because it saves an unreal amount of screen space, especially on my netbook. However, certain people find this hard to read and prefer the larger size. The smaller font sizes are also known to make certain applications (are you listening OpenOffice?) look a little funky and 80s.

My question to everyone is: What font size do you have your Ubuntu set to? If you have a super special setup or care to share your favorite font, please share!

To find out what your current font settings are, go to System - Preferences - Appearance, and select the Fonts tab.

---

### Post by _h_ on 2010-03-22
I have my font sizes as default, never felt obligated or bothered to change them.

---

### Post by andrek on 2010-03-22
I'm actually using 8pt font but I think it'd be too radical as a default one, so I voted 9pt.

---

### Post by rockin_goliath on 2010-03-22
The survey isn't intended to find out what people would like as a default font, just what they happen to be using, but thanks for your data!

---

### Post by cpmman on 2010-03-22
Sans 12
Sans 12
Sans 12
[B]Sans 12
[/B]Monospace 12

(Over 60!)

---

### Post by emarkay on 2010-03-22
11 on desktop, 12 on laptops.

---

### Post by linusr on 2010-03-22
8.6 on laptop!

How do I vote? 9?

---

### Post by psyke83 on 2010-03-22
> **rockin_goliath said:**
> With [Mark Shuttleworth's recent invitation for solid data]("http://www.webupd8.org/2010/03/ubuntu-is-not-democratic.html") with regards to the window buttons, I thought I would take this opportunity to research how Ubuntu users configure their font settings. 

I believe the default font settings in Ubuntu Karmic are Sans 10 for Applications, Documents, and Desktop; Sans 10 Bold for the Window Title, and Monospace 10 for single-width fonts (like the terminal). 

One of the first things i do when I install Ubuntu for myself and other users is decrease the font sizes to 8 point, because it saves an unreal amount of screen space, especially on my netbook. However, certain people find this hard to read and prefer the larger size. The smaller font sizes are also known to make certain applications (are you listening OpenOffice?) look a little funky and 80s.

My question to everyone is: What font size do you have your Ubuntu set to? If you have a super special setup or care to share your favorite font, please share!

To find out what your current font settings are, go to System - Preferences - Appearance, and select the Fonts tab.

First point: it's better to submit such proposals to the [ubuntu-devel-discuss mailing list]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss").

Second point: this has been proposed a few times already (including [by myself]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-October/009559.html")), and promptly [shot down]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-October/009560.html") by a particularly vocal (though well-informed) individual.

It's my opinion that users with older screens (1024x768) have terribly oversized fonts, and despite the opinion of certain "experts", something needs to be done. Higher resolutions are fine (for example, I'm using 10pt fonts at 1280x1024, as 8pt would be too small for my eyes).

You may want to experiment with changing the default DPI rather than font size.

---

### Post by Reiger on 2010-03-22
What is this weird OS that has only one font in use; you speak of?

My (Kubuntu, addmitedly) config consists of:

```

General: Gisha 8,
Fixed width: Consolas 9,
Small: Estrangelo Edessa 9,
Toolbar: Calibri 8,
Menu: Candara 9,
Window title: High Tower Text 14 (bold),
Taskbar: Segoe UI 8,
Desktop: Georgia 11

```

Last I looked, Gnome desktops used a configuration with values for all those categories too. And since some fonts tend to look `big' (or simply are `big') whereas others tend to look/be the exact opposite this kind of comparison over single point sizes are a bit moot. (You cannot equate 8pt of Estrangelo Edessa with 8pt Georgia in terms of size.)

Only in the JVM or similar environments do these have sufficient meaning, because the JVM actually maintains a strict 72pt to the inch ratio; thus you can measure actual sizes in terms of points.

---

### Post by Rob2687 on 2010-03-22
The default size is way too uncomfortable to look at.


I left it at the default for a while when I used 5.04 and 5.10. Once I discovered what a difference the font size made I set it to 8 and never looked back.

---

### Post by emarkay on 2010-03-22
> **psyke83 said:**
> You may want to experiment with changing the default DPI rather than font size.

Not to enter into that whole "DPI" thing (remember when scanners and printers first merged...), but can you give a quick info-bit on how this would make a difference to get larger, more readable fonts, without affecting any other graphics?

---

### Post by psyke83 on 2010-03-22
> **emarkay said:**
> Not to enter into that whole "DPI" thing (remember when scanners and printers first merged...), but can you give a quick info-bit on how this would make a difference to get larger, more readable fonts, without affecting any other graphics?

I'm talking about the DPI settings in the "Font Rendering Details" section of the GNOME Appearance Preferences dialog. Changing the font DPI will not affect other elements such as bitmap graphics.

If you leave the font size to 10pt, but change the DPI from 96dpi to 91dpi (for example), that will give more acceptable sizes for 1024x768 resolution.

The problem is that 96dpi *should* be the appropriate DPI for this resolution, but freetype's font rendering combined with the subpixel/slight smoothing seems to cause the fonts to become more more enlarged compared to the implementation on Windows (can't comment about MacOSX, as I never owned Mac hardware).

---

### Post by huygens on 2010-03-23
I'm using the default font size, but I put the correct dpi for my screen which had the effect of making the font appearing bigger, and I like it, it feels nicer because the fonts are smoother.

@psyke83: actually by setting the correct dpi, it feels more like on a Mac. Fonts are more readable and smoother.

It is easy to calculate your dpi (dot per inch). You need to measure your screen size (perhaps you have to convert it from cm to inches), and you compute how many dots (or pixel) you have per inches. Take care that the dpi might differ vertically from horizontally. In this case, I use the average.

---

