---
title: "Bitmapped fonts"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by isecore on 2009-08-20
I've just installed the Alpha 4 of Karmic and would like to enable Bitmapped fonts, so I can keep using the lovely Artwiz fonts.

However, what I did under Hardy, Intrepid and Jaunty no longer works.

Doing dpkg-reconfigure fontconfig-config to enable bitmapped fonts no longer gives me the configuration options. Instead, nothing happens.

What gives?

---

### Post by pferraro on 2009-08-20
I can think of 2 ways:

1. Manually perform the steps previously performed by fontconfig-config:
sudo rm /etc/fonts/conf.d/70-no-bitmaps.conf
sudo ln -s /etc/fonts/conf.avail/70-yes-bitmaps.conf /etc/fonts/conf.d/70-yes-bitmaps.conf

2. Enable only those bitmapped fonts you intend to use:
Edit /etc/fonts/local.conf:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <selectfont>
  <acceptfont>
   <pattern>
    <patelt name="family"><string>insert-font-name-here</string></patelt>
   </pattern>
  </acceptfont>
 </selectfont>
</fontconfig>
```

Method #2 has the advantage of preserving your changes even after updates to the fontconfig packages.

---

### Post by isecore on 2009-08-20
Thanks man! That did the trick. Gotta remember that in the future :)

Only problem now is that while my desktop looks slick again, Firefox apparently refuses to use the bitmapped fonts in it's menus, so it looks like crap.

This was fine in 3.0.whatever. Why did that have to change?

---

### Post by twosev on 2009-08-24
Well, what the thing is? If I try to reconfigure fontconfig-config I just get a bash prompt again. Then if I check a result code returned by dpkg-reconfigure, it will be equal to 10 (it means "No child processes"). So this is supposed to be a bug.

---

### Post by Zorael on 2009-08-24
Fontconfig seems to work differently in Karmic compared to earlier releases, to the extent that my homebrew .fonts.conf file no longer works.

Basically I want to enable font bitmaps for CJK (Chinese/Japanese/Korean) characters, since their complexity makes them fuzzy to the point of illegibility at lower sizes. But if I just enable bitmaps (either in .fonts.conf or in /etc/fonts/conf.d/) and use a font with good unicode coverage (Kochi family, Sazanami family), normal western characters look ugly as sin.

In earlier releases I could easily set up a font order for the virtual fonts Sans, Sans-serif and Monospace, where it first tried to display any given character in a "[COLOR="Lime"]nice[/COLOR]" font ([COLOR="lime"]DejaVu Sans[/COLOR]), and if that font didn't contain the character in question, proceeded down the list and tried the next font, which I'd set up to be a font with good [COLOR="RoyalBlue"]unicode[/COLOR] coverage ([COLOR="RoyalBlue"]Kochi Gothic[/COLOR]). Excerpt from a Feisty/Gutsy/Hardy/Jaunty .fonts.conf;
```
 <alias>
  <family>serif</family>
  <prefer>
[COLOR="lime"]   <family>Times New Roman</family>
   <family>DejaVu Serif</family>[/COLOR]
[COLOR="RoyalBlue"]   <family>Kochi Mincho</family>
   <family>Sazanami Mincho</family>[/COLOR]
  </prefer>
 </alias>
 <alias>
  <family>sans-serif</family>
  <prefer>
[COLOR="lime"]   <family>DejaVu Sans</family>[/COLOR]
[COLOR="RoyalBlue"]   <family>Kochi Gothic</family>
   <family>Sazanami Gothic</family>[/COLOR]
  </prefer>
 </alias>
 <alias>
  <family>monospace</family>
  <prefer>
[COLOR="lime"]   <family>DejaVu Sans Mono</family>[/COLOR]
[COLOR="RoyalBlue"]   <family>Kochi Gothic</family>
   <family>Sazanami Gothic</family>[/COLOR]
  </prefer>
 </alias>
 <match target="font" >
  <edit mode="assign" name="embeddedbitmap" >
   <bool>true</bool>
  </edit>
 </match>
```

But suddenly in Karmic this doesn't work. It just defaults to some vertex font, possibly the one symlinked at /etc/alternatives/ttf-japanese*. Excerpt;
```
  <!-- FALLBACKS
	Only *one* entry per family seems to work. For several fallbacks you need one entry *each*.
	So if A>B>C, then A and B needs separate entries as opposed to one big A entry. -->

  <!-- depth 1, virtual fonts -->
  <alias>
    <family>serif</family>
    <prefer><family>Times New Roman</family></prefer>
  </alias>
  <alias>
    <family>sans</family>
    <prefer><family>DejaVu Sans</family></prefer>
  </alias>
  <alias>
    <family>sans-serif</family>
    <prefer><family>DejaVu Sans</family></prefer>
  </alias>
  <alias>
    <family>monospace</family>
    <prefer><family>DejaVu Sans Mono</family></prefer>
  </alias>

  <!-- depth 2, unicode fallbacks -->
  <alias>
[COLOR="lime"]    <family>DejaVu Sans</family>[/COLOR]
[COLOR="RoyalBlue"]    <prefer><family>Kochi Gothic</family></prefer>[/COLOR]
  </alias>
  <alias>
[COLOR="lime"]    <family>DejaVu Sans Mono</family>[/COLOR]
[COLOR="RoyalBlue"]    <prefer><family>Kochi Gothic</family></prefer>[/COLOR]
  </alias>
  <alias>
[COLOR="lime"]    <family>Arial</family>[/COLOR]
[COLOR="RoyalBlue"]    <prefer><family>Kochi Gothic</family></prefer>[/COLOR]
  </alias>
  <alias>
[COLOR="lime"]    <family>Times New Roman</family>[/COLOR]
[COLOR="RoyalBlue"]    <prefer><family>Kochi Mincho</family></prefer>[/COLOR]
  </alias>
```
That's the only way I've so far been able to make it behave in Karmic as it did earlier releases, but using this method I can't define more than one unicode fallback or it'll freak out and use that ugly vertex font anyway. I don't understand it.

---

