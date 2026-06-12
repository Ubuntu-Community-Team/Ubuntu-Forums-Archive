---
title: "Problem with this website. Screenshots show difference."
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-07-31
The url is this. [DPR]("http://forums.dpreview.com/forums/forum.asp?forum=1033") You can see the corrupt menu on the left and the weird spacing in the main body.
First one is with Karmic and second is with Jaunty. Not seen this on other websites.

---

### Post by tekstr1der on 2009-07-31
Renders correctly here (firefox-3.5, karmic).

---

### Post by philinux on 2009-07-31
> **tekstr1der said:**
> Renders correctly here (firefox-3.5, karmic).

I'm on a clean install from alpha2 daily build. Is yours an upgrade from Jaunty?

---

### Post by tekstr1der on 2009-07-31
> **philinux said:**
> I'm on a clean install from alpha2 daily build. Is yours an upgrade from Jaunty?

Yes, I have upgraded from Jaunty, but been using shiretoko from karmic repos since beta (around karmic alpha 2 release). Not sure how that would impact your page render. Do you have the same extensions installed on both browsers? Have you checked the site by starting firefox in safe-mode?

```
firefox-3.5 -safe-mode
```

---

### Post by psyke83 on 2009-07-31
It seems that one of these screenshots is using Deja Vu Sans, and another is using Arial (or another font from ttf-mscorefonts-installer).

---

### Post by philinux on 2009-07-31
I get same result in safe mode. Very odd.

Karmic with firefox or firefox3.5 displays this site well wrong. Epiphany bad too.
Jaunty is fine with both browsers.

---

### Post by zekopeko on 2009-07-31
zoom level? ctrl + "+" or "-".

---

### Post by NCLI on 2009-07-31
Ctrl + 0 should reset the zoom level, if that's it.

---

### Post by psyke83 on 2009-07-31
Make sure that both installs are rendering with the same font - otherwise you're comparing apples to oranges.

See my previous comment...

---

### Post by philinux on 2009-08-01
> **psyke83 said:**
> Make sure that both installs are rendering with the same font - otherwise you're comparing apples to oranges.

See my previous comment...

Checked the fonts and zoom levels normal. Both installs have the restricted packages installed. I'm missing something.

It is only this website so...

---

### Post by philinux on 2009-09-03
Still not fixed.

Jaunty displays this website correctly.

---

### Post by taavikko on 2009-09-03
> **philinux said:**
> Still not fixed.

Jaunty displays this website correctly.

Have you accidentally installed some other font that may cause corruption in fonts?
```
dpkg -l ttf\* |grep ^ii
```
for a list of fonts installed.

EDIT// I'm also seeing this with Arora & FF

---

### Post by ronacc on 2009-09-03
I am also seeing this with arora and FF , but Opera 10 and chromium render it correctly .

---

### Post by philinux on 2009-09-03
> **taavikko said:**
> Have you accidentally installed some other font that may cause corruption in fonts?
```
dpkg -l ttf\* |grep ^ii
```
for a list of fonts installed.

EDIT// I'm also seeing this with Arora & FF

Not installed any fonts at all. But here goes.
```

dpkg -l ttf\* |grep ^ii
ii  ttf-arabeyes                          2.0-2                                      Arabeyes GPL TrueType Arabic fonts
ii  ttf-arphic-uming                      0.2.20080216.1-3ubuntu2                    "AR PL UMing" Chinese Unicode TrueType font 
ii  ttf-bitstream-vera                    1.10-7                                     The Bitstream Vera family of free TrueType f
ii  ttf-dejavu                            2.29-2                                     Metapackage to pull in ttf-dejavu-core and t
ii  ttf-dejavu-core                       2.29-2                                     Vera font family derivate with additional ch
ii  ttf-dejavu-extra                      2.29-2                                     Vera font family derivate with additional ch
ii  ttf-freefont                          20090104-2                                 Freefont Serif, Sans and Mono Truetype fonts
ii  ttf-indic-fonts-core                  1:0.5.4ubuntu2                             Core collection of free Indian language font
ii  ttf-kacst                             2.0+mry-1                                  KACST free TrueType Arabic fonts
ii  ttf-lao                               0.0.20060226-2                             TrueType font for Lao language
ii  ttf-liberation                        1.04.93-1                                  Free fonts with the same metrics as Times, A
ii  ttf-mscorefonts-installer             3.0                                        Installer for Microsoft TrueType core fonts
ii  ttf-opensymbol                        1:3.1.1-1ubuntu1                           OpenSymbol TrueType font
ii  ttf-sazanami-gothic                   20040629-4ubuntu1                          Sazanami Gothic Japanese TrueType font
ii  ttf-sazanami-mincho                   20040629-4ubuntu1                          Sazanami Mincho Japanese TrueType font
ii  ttf-thai-tlwg                         1:0.4.12-1                                 Thai fonts in TrueType format
ii  ttf-unfonts-core                      1.0.1-7ubuntu1                             Un series Korean TrueType fonts
ii  ttf-vlgothic                          20090612-2                                 Japanese TrueType font from Vine Linux
ii  ttf-wqy-zenhei                        0.8.38-1ubuntu1                            "WenQuanYi Zen Hei" A Hei-Ti Style (sans-ser

```

---

### Post by taavikko on 2009-09-03
Don't know for sure how much this causes the issue:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd"><html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en"><head>
    <meta http-equiv="X-UA-Compatible" content="IE=8">
<link rel="SHORTCUT ICON" href="/favicon.ico">
<script src="/inc/dprmain.js" type="text/javascript"></script>
<meta name="MSSmartTagsPreventParsing" content="TRUE">
```

From the page source....

---

### Post by philinux on 2009-09-03
Just tried chromium and epiphany.

Only chromium displays it correctly. Could it be a gecko problem or their site.

---

### Post by taavikko on 2009-09-03
> **philinux said:**
> Just tried chromium and epiphany.

Only chromium displays it correctly. Could it be a gecko problem or their site.

Not likely a gecko, since arora is webkit, and it doesn't display correctly.
So would point my finger to the site.

That however doesn't explain why it works on Jaunty...

---

### Post by philinux on 2009-09-03
> **taavikko said:**
> Not likely a gecko, since arora is webkit, and it doesn't display correctly.
So would point my finger to the site.

That however doesn't explain why it works on Jaunty...

Jaunty yes now there's the thing. Should I bug this then?

---

### Post by scradock on 2009-09-03
> **philinux said:**
> Still not fixed.

Jaunty displays this website correctly.
Just to confuse the issue, I checked the site with Juanty, and Firefox 3.0, and got the same problems - overlapping in the left-hand menu and poor registration in the main list......

I had Firefox Preferences | Content | Fonts and Colors set to DejaVu Serif 16, with the "Allow pages to specify their own fonts" (in Advanced) set to OFF.

Setting that preference to ON gave a perfect rendering of the menu and main list.

Have you tried that? I suspect that the design of the page elements is too tight, in the sense that there is no allowance for minor differences in space requirements for different fonts.

---

### Post by philinux on 2009-09-03
Allow pages to choose own fonts is ticked in both Jaunty and Karmic.

This is the default isn't it?

If I untick it in Karmic the main page looks ok but the menus on the left are still overlapped.

---

### Post by tekstr1der on 2009-09-03
> **scradock said:**
> 
...I had Firefox Preferences | Content | Fonts and Colors set to DejaVu Serif 16, with the "Allow pages to specify their own fonts" (in Advanced) set to OFF.

Setting that preference to ON gave a perfect rendering of the menu and main list.


ON is the default for this setting and should be left that way unless the user has a very specific reason to override. Disabling this option will lead to similar issues as the OP on a variety of websites.

---

### Post by scradock on 2009-09-03
> **tekstr1der said:**
> ON is the default for this setting and should be left that way unless the user has a very specific reason to override. Disabling this option will lead to similar issues as the OP on a variety of websites.
Checked the site with Karmic 64-bit - same pattern: with "Allow pages.." ON it displays correctly, with the setting OFF it causes problems. FF 3.5.

I know the default setting is ON, but sometimes I don't find the fonts chosen by site designers look as good as my settings,so I keep it off unless there's a problem.

But the OP had it ON in both cases, so there hasto be another problem for him.

Just put me down as someone who DOESN'T experience this problem with the default FF settings, Jaunty or Karmic, FF 3.0 or 3.5.

---

### Post by philinux on 2009-09-25
Whatever happened this is now fixed for me. Must have been yesterdays updates.

---

### Post by psyke83 on 2009-09-25
> **philinux said:**
> Whatever happened this is now fixed for me. Must have been yesterdays updates.

Your problem was ttf-tahoma-replacement which got installed from WINE. It previously didn't allow proper hinting/subpixel filtering, but that got fixed.

There was already a thread: [http://ubuntuforums.org/showthread.php?t=1252689](http://ubuntuforums.org/showthread.php?t=1252689)

---

