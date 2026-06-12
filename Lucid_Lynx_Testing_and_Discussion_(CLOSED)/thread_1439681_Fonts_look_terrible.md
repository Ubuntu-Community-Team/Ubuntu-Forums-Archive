---
title: "Fonts look terrible"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ffi on 2010-03-26
Has anyone noticed, it's almost like the freetype autohinter is being used instead of the bytecode interpreter. It's especially bad in Opera

---

### Post by Sslaxx on 2010-03-26
They look OK here...

---

### Post by ffi on 2010-03-26
Look compare Opera with Chrome, I have used this version of Opera for ages and it always looked fine before

[[IMG]http://img231.imageshack.us/img231/2961/screenshotest.th.png[/IMG]](http://img231.imageshack.us/i/screenshotest.png/)

---

### Post by wkulecz on 2010-03-26
At least for US English, I think the Fonts in 10.04Beta are some of the best defaults yet.

---

### Post by ffi on 2010-03-26
Look at those bolds on this forum

[[IMG]http://img707.imageshack.us/img707/975/screenshot1nk.th.png[/IMG]](http://img707.imageshack.us/i/screenshot1nk.png/)

---

### Post by Rob2687 on 2010-03-26
Are you trying to troll or something? I don't see anything wrong with the forum fonts.

---

### Post by Sslaxx on 2010-03-26
I doubt he's trolling, I had the same problem too (also had the 6s and 9s look pretty bad, and Cs). I fixed it (with Firefox) by making sure the DejaVu font family were used as default and then unchecking the box that allows sites to choose what fonts they can use.

[http://ubuntuforums.org/showthread.php?t=1434434](http://ubuntuforums.org/showthread.php?t=1434434)

---

### Post by jaoc223 on 2010-03-26
I just posted a thread asking about font rendering, ff and chromium fonts are awful, a big strain on the eyes with the blue and red hinting. I don't
understand why the devs over at ff and chrome do not address these issues.

---

### Post by ffi on 2010-03-26
I haven't tried FF but Google-Chrome (that's the official package from Google) looks goods, Opera 10.10 (a qt4 app) looks terrible Opera 10.50 (doesnt use a toolkit) looks okay (but has as a known issue font rendering problems to begin with)

edit I also noticed when changing font settings the fonts in gnome don't look anti-aliased at all for a while until you refresh

---

### Post by psyke83 on 2010-03-26
See: [http://ubuntuforums.org/showpost.php?p=9010164&postcount=10](http://ubuntuforums.org/showpost.php?p=9010164&postcount=10)

---

### Post by ffi on 2010-03-26
thanks these package work for Opera too

---

### Post by volanin on 2010-03-26
Does anyone else has this feeling:

The default FONT RENDERER in Karmic and Lucid is Subpixel Smoothing (LCD).
You can check that by right-clicking the Desktop and selecting Change Desktop Background.
It's right there, in the FONTS tab.

Well, back to the discution.
If you click in the Details button, you see that Subpixel Smoothing uses SUBPIXEL smoothing
and SLIGHT hinting. But SLIGHT hinting is _very, very poor_.
Try selecting FULL hinting to see the difference.

In my opinion, FULL hinting should be default.
After all, it's already used when you select the Best Contrast FONT RENDERER.
Is there any reason this is not default?
:confused:

---

### Post by psyke83 on 2010-03-26
> **volanin said:**
> Does anyone else has this feeling:

The default FONT RENDERER in Karmic and Lucid is Subpixel Smoothing (LCD).
You can check that by right-clicking the Desktop and selecting Change Desktop Background.
It's right there, in the FONTS tab.

Well, back to the discution.
If you click in the Details button, you see that Subpixel Smoothing uses SUBPIXEL smoothing
and SLIGHT hinting. But SLIGHT hinting is _very, very poor_.
Try selecting FULL hinting to see the difference.

In my opinion, FULL hinting should be default.
After all, it's already used when you select the Best Contrast FONT RENDERER.
Is there any reason this is not default?
:confused:

It's highly dependent on your screen type, and personal preference. I much, much prefer slight hinting. The full hinting gives inconsistent thickness in lettering on my TFT/LCD screens, but looks ok on an old, fuzzy CRT.

---

### Post by ffi on 2010-03-30
Last weekend I updated a box which hadn't been updated since the weekend before and after the updates fonts regressed, so I think some update from last week caused the problem

---

