---
title: "Is antialiasing broken for certain websites and fonts in Firefox?"
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-08-29
I have a sneaking suspicion that somebody has been messing around with fontconfig or the antialiasing/hinting settings.

[http://img141.imageshack.us/img141/40/exampleq.png]("http://ubuntuforums.org/attachment.php?attachmentid=126696&d=1251543128")

---

### Post by froggyswamp on 2009-08-29
Same here, fortunately Chrome isn't affected.

---

### Post by rudenko_ruslan on 2009-08-29
Just checked cnn.com and everything looks OK to me (antialiasing works perfectly).

---

### Post by qamelian on 2009-08-29
It looks perfect for me in Firefox.

---

### Post by Starks on 2009-08-29
> **rudenko_ruslan said:**
> Just checked cnn.com and everything looks OK to me (antialiasing works perfectly).
I never said the problem was limited to CNN...

---

### Post by jpeddicord on 2009-08-29
Thankfully I'm not the only one who noticed this. The fonts look terrible, but the lack of smoothing seems to only affect the Microsoft fonts (mostly [s]Arial[/s] Tahoma).

Look at this pile of ugly! (Not the site, mind you. ;) ) Note the text under the forum descriptions.
[ATTACH]126782[/ATTACH]

---

### Post by psyke83 on 2009-08-29
The problem is that wine1.2 also pulls in a Tahoma replacement TTF (tahoma-replacement-ttf) which seems not to support antialiasing. Remove the package and your fonts will return to normal.

---

### Post by SunnyRabbiera on 2009-08-29
I never had any issue with the linux fonts personally.

---

### Post by jpeddicord on 2009-08-29
> **psyke83 said:**
> The problem is that wine1.2 also pulls in a Tahoma replacement TTF (tahoma-replacement-ttf) which seems not to support antialiasing. Remove the package and your fonts will return to normal.

Where is that Thanks button when you need it? Guess I'll have to try the manual way...

Thanks, that solved it. :)

---

### Post by Starks on 2009-08-29
Here's the bug report on Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/412195](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/412195)

---

### Post by jpeddicord on 2009-08-29
> **Starks said:**
> Here's the bug report on Launchpad.

[https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/412195](https://bugs.launchpad.net/ubuntu/+source/wine1.2/+bug/412195)

Confirmed it.

---

### Post by scradock on 2009-08-29
> **psyke83 said:**
> The problem is that wine1.2 also pulls in a Tahoma replacement TTF (tahoma-replacement-ttf) which seems not to support antialiasing. Remove the package and your fonts will return to normal.
That's bad! I tried to remove the font - ttf-tahoma-replacement - but it says it will remove Wine 1.2 as well. How can a font required for one program Wine) be allowed to take over in others (eg Firefox)?

Fonts are resources; I should be able to specify whatever font I want for each program!

---

### Post by Starks on 2009-08-29
Don't use the wine1.2 package. Use the wine package provided by the Wine team for Jaunty.

---

### Post by scradock on 2009-08-29
> **Starks said:**
> Don't use the wine1.2 package. Use the wine package provided by the Wine team for Jaunty.
Well, I'm using the wine 1.2 package provided by Ubuntu - it's actually 1.1.28-0ubuntu1

In fact, the fonts used in Firefox ARE configurable; anything but Tahoma seems to be OK. I still think that allowing a tahoma-replacement to take over from tahoma is a step back, if it doesn't work correctly.

---

### Post by psyke83 on 2009-08-30
> **scradock said:**
> Well, I'm using the wine 1.2 package provided by Ubuntu - it's actually 1.1.28-0ubuntu1

In fact, the fonts used in Firefox ARE configurable; anything but Tahoma seems to be OK. I still think that allowing a tahoma-replacement to take over from tahoma is a step back, if it doesn't work correctly.

I agree that it's bad to have the Tahoma replacement font used system-wide. It should be isolated only for use within Wine (perhaps by embedding in the executable, or preloading into the ~/.wine configuration).

---

### Post by Starks on 2009-08-30
Even after purging the packages, manually removing the remnants, and restarting my laptop, the fonts are still screwed up.

---

### Post by psyke83 on 2009-08-30
> **Starks said:**
> Even after purging the packages, manually removing the remnants, and restarting my laptop, the fonts are still screwed up.

Manually update the font caches, perhaps. The font must still be lingering on your system somewhere.

---

### Post by Starks on 2009-08-30
I did that 10 times before even commenting.

---

### Post by NCLI on 2009-08-30
How does it look for you on a Livecd with the latest daily?

---

### Post by Starks on 2009-08-30
I can really care less how it looks since I reinstalled Karmic due to an unrelated issue.

Also, creating a Live USB is broken, so what should've taken me only 15 minutes to reinstall took 4 hours.

---

### Post by bobince on 2009-09-22
I think the problem is much worse than just ttf-tahoma-replacement.

Namely: all fonts now seem to use embedded bitmaps where available. Embedded bitmaps are supposed to be &#8220;optimised&#8221; for given font sizes, but in practice since they're non-anti-aliased they look much worse than just rendering the outlines in almost all cases(*). The results are that for these fonts, the rendering looks like WinXP with ClearType off (yuck).

I'm not sure whether this is new in Karmic; I only noticed it when I updated my user copy of Calibri to one that, it would seem, gained embedded bitmaps. I fixed it by adding a ~/.fonts.conf file containing:

```
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <match target="font">
        <edit mode="assign" name="embeddedbitmap"><bool>false</bool></edit>
    </match>
</fontconfig>
```*: but not quite all. In particular many Chinese and Japanese fonts practically *require* embedded bitmaps because of the complexity of the characters and the relatively poor hinting making them unreadable at small font sizes. Newer fonts such as Meiryo, that render nicely from their outlines, are needed to fix this. In the meantime, perhaps Ubuntu should ship with &#8216;embeddedbitmap&#8217; set to &#8216;false&#8217; for all except the bundled bitmap-dependent CJK fonts.

---

