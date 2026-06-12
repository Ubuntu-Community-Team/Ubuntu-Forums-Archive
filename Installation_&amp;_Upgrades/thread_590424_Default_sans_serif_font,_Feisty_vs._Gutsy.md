---
title: "Default sans serif font, Feisty vs. Gutsy"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by jcbodnar on 2007-10-24
Can anybody else confirm that the default sans serif font in Gutsy has changed since Feisty? It seems much finer, thinner and, due to probably my bad eyes, almost appears dark green on my LCD. (I have subpixel smoothing on with no desktop effects.)

Can anybody tell me what the default sans serif in Feisty was so I can hopefully switch back to it.

---

### Post by hugmenot on 2007-10-25
Same font, different display technology. Try switching to "Slight" hinting before you revert (in Appearance&#8594;Font&#8594;Details). Otherwise use this to get the old style back:
[http://ubuntuforums.org/showpost.php?p=3483916&postcount=63](http://ubuntuforums.org/showpost.php?p=3483916&postcount=63)

---

### Post by jcbodnar on 2007-10-26
Thank you for the response. I tried slight hinting and then adding the conf file you linked to and neither get me back to what my screen looked like with Feisty. Perhaps I futzed with too many settings before I tried your suggestions.

I have to say this change is very disappointing. I was a Red Hat/Fedora user for nearly ten years when I switched to Ubuntu nine months ago. I have not had a single complaint about it and nothing but praise to my friends since. I wish a change like this could have been handled better. I guess it's my fault for not reading the release notes, but I would have thought that this could have been an option during the upgrade process (ie "New improved font rendering, click Yes to use it. You can go back to the old way at any time by doing this ...") instead of making a change automatically.

I guess I'll have to see if I can find the important config files from my Fesity install at work, copy them to my home machine and then try your suggestions. Either that or wipe the drive, reinstall Feisty, upgrade to Gutsy and then try your suggestions. I don't think I made any font changes under Feisty so its default plus the filter switch will hopefully work.

---

### Post by jcbodnar on 2007-10-26
An addenda, this lack of sharpness (that's the best term for it as it looks as if the RGB are out of phase [and I tried changing the pixel ordering to no avail]) is at its worst when viewing from about 15 inches away from the monitor (my normal viewing distance) and also seems to be most prevalent in Firefox (but that could be because that's the application I use the most and has the most text displayed).

---

### Post by hugmenot on 2007-10-26
Hm. Sounds like you don't like subpixel rendering at all.
I can offer you to upload my vanilla /etc/fonts directory. You could replace your current contents with it.

conf.avail/
conf.d/
fonts.conf  
fonts.dtd

And you would remove your local ~/.fonts.conf file as well.
The lines ```
<?xml version="1.0"?> <!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
  <!-- Use the older subpixel rendering: LCDFILTER legacy -->
    <edit name="lcdfilter" mode="assign"><const>legacy</const></edit>
</fontconfig>

```
would go into the new file /etc/fonts/local.conf.
If you would post a screenshot I could tell, if it looks as it should. What is your screen size and resolution? It might be that at your viewing distance the pixels are so visible that the phase shift (which is the intended effect, really) is too noticable.

---

### Post by iGold on 2007-10-26
I have the same problem with new subpixel rendering. All glyphs now have color "shadows" at left and at right from any line. Feisty rendering changed only some glyph's pixels to color one but didn't add new color lines. And now black text on white background looks like colored one.

Some examples from my system (I use Albany AMT font as default at 10 pt and Native hinting). The difference can by more noticable if zoom any text on pictures (i.e. in Eye of GNOME with disabled smoothing in prefs) to ~1000%. Or just look at "ll" in the word "Full".

Feisty (preferable for me):
[IMG]http://igold.pp.ru/gutsy-fonts/feisty.png[/IMG]

Gutsy:
[IMG]http://igold.pp.ru/gutsy-fonts/gutsy.png[/IMG]

Gutsy with legacy rendering enabled in local.conf:
[IMG]http://igold.pp.ru/gutsy-fonts/gutsy-legacy.png[/IMG]

I don't see any difference with or without legacy rendering on gutsy.

Listing of my /etc/fonts/ is below. local.conf is the same as written above.

```
% ll -R /etc/fonts 
/etc/fonts:
total 28
drwxr-xr-x 2 root root 4096 Oct 26 22:23 conf.avail
drwxr-xr-x 2 root root 4096 Oct 26 22:06 conf.d
-rw-r--r-- 1 root root 5231 Jan  5  2007 fonts.conf
-rw-r--r-- 1 root root 6907 Jan  5  2007 fonts.dtd
-rw-r--r-- 1 root root  222 Oct 26 22:19 local.conf

/etc/fonts/conf.avail:
total 124
-rw-r--r-- 1 root  root    250 Jan  5  2007 10-autohint.conf
-rw-r--r-- 1 root  root    257 Jan  5  2007 10-no-sub-pixel.conf
-rw-r--r-- 1 root  root    256 Jan  5  2007 10-sub-pixel-bgr.conf
-rw-r--r-- 1 root  root    256 Jan  5  2007 10-sub-pixel-rgb.conf
-rw-r--r-- 1 root  root    257 Jan  5  2007 10-sub-pixel-vbgr.conf
-rw-r--r-- 1 root  root    257 Jan  5  2007 10-sub-pixel-vrgb.conf
-rw-r--r-- 1 root  root    247 Jan  5  2007 10-unhinted.conf
-rw-r--r-- 1 root  root    943 Jan  5  2007 20-fix-globaladvance.conf
-rw-r--r-- 1 root  root    301 Jan  5  2007 20-lohit-gujarati.conf
-rw-r--r-- 1 root  root   1188 Jan  5  2007 20-unhint-small-vera.conf
-rw-r--r-- 1 root  root   1507 Jan  5  2007 30-amt-aliases.conf
-rw-r--r-- 1 root  root   4017 Jan  5  2007 30-urw-aliases.conf
-rw-r--r-- 1 root  root   1757 Jan  5  2007 40-generic.conf
-rw-r--r-- 1 root  root    545 Jan  5  2007 49-sansserif.conf
-rw-r--r-- 1 root  root    269 Jan  5  2007 50-user.conf
-rw-r--r-- 1 root  root    271 Jan  5  2007 51-local.conf
-rw-r--r-- 1 root  root    268 Jan  5  2007 52-languageselector.conf
-rw-r--r-- 1 igold igold   698 Oct 21 17:47 53-monospace-lcd-filter.conf
-rw-r--r-- 1 root  root   1064 Jan  5  2007 60-latin.conf
-rw-r--r-- 1 root  root  12559 Jan  5  2007 65-fonts-persian.conf
-rw-r--r-- 1 root  root    954 Jan  5  2007 65-nonlatin.conf
-rw-r--r-- 1 root  root    439 Mar 23  2007 65-ttf-thai-tlwg.conf
-rw-r--r-- 1 root  root    454 Jan  5  2007 69-unifont.conf
-rw-r--r-- 1 root  root    306 Jan  5  2007 70-no-bitmaps.conf
-rw-r--r-- 1 root  root    296 Jan  5  2007 70-yes-bitmaps.conf
-rw-r--r-- 1 root  root    433 Jan  5  2007 80-delicious.conf
-rw-r--r-- 1 root  root   1754 Jan  5  2007 90-synthetic.conf
-rw-r--r-- 1 root  root   1474 Jan  5  2007 README

/etc/fonts/conf.d:
total 16
lrwxrwxrwx 1 root root   39 Oct 26 20:35 20-fix-globaladvance.conf -> ../conf.avail/20-fix-globaladvance.conf
lrwxrwxrwx 1 root root   36 Oct 26 20:35 20-lohit-gujarati.conf -> ../conf.avail/20-lohit-gujarati.conf
lrwxrwxrwx 1 root root   39 Oct 26 20:35 20-unhint-small-vera.conf -> ../conf.avail/20-unhint-small-vera.conf
lrwxrwxrwx 1 root root   33 Oct 26 20:35 30-amt-aliases.conf -> ../conf.avail/30-amt-aliases.conf
lrwxrwxrwx 1 root root   39 Oct 26 20:41 30-defoma.conf -> /var/lib/defoma/fontconfig.d/fonts.conf
lrwxrwxrwx 1 root root   33 Oct 26 20:35 30-urw-aliases.conf -> ../conf.avail/30-urw-aliases.conf
lrwxrwxrwx 1 root root   29 Oct 26 20:35 40-generic.conf -> ../conf.avail/40-generic.conf
lrwxrwxrwx 1 root root   31 Oct 26 20:35 49-sansserif.conf -> ../conf.avail/49-sansserif.conf
-rw-r--r-- 1 root root  254 Dec  6  2005 50-enable-terminus.conf
lrwxrwxrwx 1 root root   26 Oct 26 20:35 50-user.conf -> ../conf.avail/50-user.conf
lrwxrwxrwx 1 root root   27 Oct 26 20:35 51-local.conf -> ../conf.avail/51-local.conf
lrwxrwxrwx 1 root root   38 Oct 26 20:35 52-languageselector.conf -> ../conf.avail/52-languageselector.conf
lrwxrwxrwx 1 root root   27 Oct 26 20:35 60-latin.conf -> ../conf.avail/60-latin.conf
lrwxrwxrwx 1 root root   35 Oct 26 20:35 65-fonts-persian.conf -> ../conf.avail/65-fonts-persian.conf
lrwxrwxrwx 1 root root   30 Oct 26 20:35 65-nonlatin.conf -> ../conf.avail/65-nonlatin.conf
lrwxrwxrwx 1 root root   35 Oct 26 20:39 65-ttf-thai-tlwg.conf -> ../conf.avail/65-ttf-thai-tlwg.conf
lrwxrwxrwx 1 root root   29 Oct 26 20:35 69-unifont.conf -> ../conf.avail/69-unifont.conf
lrwxrwxrwx 1 root root   40 Oct 26 20:41 70-no-bitmaps.conf -> /etc/fonts/conf.avail/70-no-bitmaps.conf
lrwxrwxrwx 1 root root   34 Oct 26 20:49 70-ttf-arphic-uming.conf -> /etc/fonts/conf.d/ttf-arphic-uming
lrwxrwxrwx 1 root root   31 Oct 26 20:35 80-delicious.conf -> ../conf.avail/80-delicious.conf
lrwxrwxrwx 1 root root   31 Oct 26 20:35 90-synthetic.conf -> ../conf.avail/90-synthetic.conf
-rw-r--r-- 1 root root 2171 Sep 28 14:51 CJK_aliases
-rw-r--r-- 1 root root 1553 Oct 26 20:49 ttf-arphic-uming
-rw-r--r-- 1 root root  746 Sep  7 08:41 ttf-malayalam-fonts.conf
```

---

### Post by hugmenot on 2007-10-26
The lowest screenshot looks like it still uses the newer nethod and not lcdfilter legacy. Perhaps the local.conf isn't read?
However, /etc/fonts/conf.d/51-local.conf should look at the file and include it.
Perhaps putting these lines into your ~/.fonts.conf works better?

Have you tried switching to "Slight" yet? I think it is a lot better than the old "vertical bars have to be 1px wide" paradigm.
And, it&#8217;s not releveant how it looks when you magnify it, man. You don't do that with your mp3s either, do you? It's a perceptual thing.

---

### Post by jamesford on 2007-10-29
im having the exact same problem on my freshly installed gutsy (no upgrade) and none of the suggestions above work. it might be that setting the hinting to slight or medium could work but that just screws up everything (see attached picture) all the settings on the previous dialog becomes checked and fonts in firefox radically change and become really horrible. the only hinting option that works without screwing up firefox is full hinting, and i dont like it at all cos it gives all text a greenish halo

i just want fonts to look like they did in feisty :'(

[[IMG]http://img134.imageshack.us/img134/3972/fontssc2.th.jpg[/IMG]](http://img134.imageshack.us/my.php?image=fontssc2.jpg)

---

### Post by hugmenot on 2007-10-29
> **jamesford said:**
> im having the exact same problem on my freshly installed gutsy (no upgrade) and none of the suggestions above work. it might be that setting the hinting to slight or medium could work but that just screws up everything (see attached picture)

What&#8217;s screwed up is that you used jpgs to make the screenshot. Useless for judging the appearance. Try Slight, Medium is no good here.
> 
 all the settings on the previous dialog becomes checked and fonts in firefox radically change and become really horrible. 

Where's the Firefox screenshot? People keep claiming seeing horrible stuff, but never post proper evidence. The dialog issue you see is bogus. Ubuntus Human theme displays a checked field when instead it should show a "not applicable" bullet. In Clearlooks you'll see a dash (-) for that and not a dot(·) or a checkmark. Not a bug.
> 
the only hinting option that works without screwing up firefox is full hinting, and i dont like it at all cos it gives all text a greenish halo


Slight? Different font? Larger font?

---

### Post by jamesford on 2007-10-29
the jpg wasnt meant to show the fonts, quality didnt matter, it was about showing that all the radiobuttons were checked when choosing medium. while they arent when choosing full. slight produces the same result as medium. the point is that i want it to look like it did in feisty. ive tried a bunch of different fonts, and sizes. i dont want system fonts bigger than 8

hers another screenshot. surely theres soemthing wrong with the medium hinting (as well as slight which produces similar results to medium)?


[[IMG]http://img231.imageshack.us/img231/5834/fonts2im2.th.png[/IMG]](http://img231.imageshack.us/my.php?image=fonts2im2.png)

edit: the 3 first samples are a forum in firefox

---

### Post by hugmenot on 2007-10-29
That&#8217;s still a piss-poor screenshot. There&#8217;s only one short line of black text, and it&#8217;s in italics. Still for this one line I&#8217;d go with Slight.

---

### Post by jamesford on 2007-10-29
dont u see what the firefox fonts are like with medium or slight? 
what im asking for is a patch or something that can make it look like it did in feisty. i dont care what u think about the gutsy fonts, i dont like them, just accept that. if u cant help with that then dont reply instaed of complaining about screenshots

---

### Post by iGold on 2007-10-30
My problem is the same — new subpixel rendering is not pleasant for me, but old one (used in feisty) can't be switched even with "lcdfilter legacy" (either in /etc/fonts/local.conf or in ~/.fonts.conf). Is lcdfilter works for anyone? fontconfig package version is 2.4.2-1.2ubuntu4. Syntax of ldcfilter from ~/.fonts.conf (other settings in this file works well):

```
<!-- Use legacy LCD smoothing -->
<edit name="lcdfilter" mode="assign">
  <const>legacy</const>
</edit>
```

I don't see such option (lcdfilter) and constant (legacy) in manual on fonts.conf. Maybe they were removed in gutsy release of fontconfig?

---

### Post by hugmenot on 2007-10-30
Then I guess you have to file a bug against fontconfig or ask Keybuk how it&#8217;s supposed to work. He hacked the old algorithm into fontconfig.

---

