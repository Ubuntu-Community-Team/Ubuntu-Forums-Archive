---
title: "Karmic iBus Chinese input is awesome but..."
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by powel212 on 2009-10-04
Karmic iBus Chinese input is awesome, a huge improvement over the old system, but I would love it even more if I could use Pinyin to input Traditional Chinese.

I know Traditional Chinese is basically a dead script but I still use it on a daily basis. As it stands I must input my text in simplified and then use Google translate to convert it to Traditional. A minor inconvenience but an inconvenience none the less.

And, before you say, "Why not just use &#27880;&#38899;", let me just say that &#27880;&#38899; is a great system for teaching children Chinese phonetics but it is a horrible system for inputing Chinese. Honestly.

Respect and kudos to the iBus Team wherever you are. 

Pinyin + &#32321;&#20307;&#23383; = &#24320;&#24515;&#24320;&#24515;

Powel

---

### Post by SnappyU on 2009-10-13
Just tried iBus Chinese input ... there are two of them that supports Traditional Chinese with pinyin. :)

It has a "T ALL PY" or something as its label.
Note that it displays both simplified and traditional characters.

One thing that I would like to have is the ability to enter phrases instead of just characters.

---

### Post by Seren on 2009-10-13
Since I have had many issues with skim under KDE, is iBus compatible with KDE ? Will it somewhat work ?

TIA. :)

Answered my own question:
[http://code.google.com/p/ibus/issues/detail?id=455](http://code.google.com/p/ibus/issues/detail?id=455)

Comment 4 there seems to confirm it will indeed work.

Thanks for letting me know that iBus exists.

---

### Post by Longinus00 on 2009-10-13
> **powel212 said:**
> Karmic iBus Chinese input is awesome, a huge improvement over the old system, but I would love it even more if I could use Pinyin to input Traditional Chinese.

I know Traditional Chinese is basically a dead script but I still use it on a daily basis. As it stands I must input my text in simplified and then use Google translate to convert it to Traditional. A minor inconvenience but an inconvenience none the less.

And, before you say, "Why not just use &#27880;&#38899;", let me just say that &#27880;&#38899; is a great system for teaching children Chinese phonetics but it is a horrible system for inputing Chinese. Honestly.

Respect and kudos to the iBus Team wherever you are. 

Pinyin + &#32321;&#20307;&#23383; = &#24320;&#24515;&#24320;&#24515;

Powel

On my setup I can type traditional with the ibus plugin. I select the option that looks like "&#25340; pinyin". The only downside to this is that it seems to show both the traditional and simplified characters, but the more you type with it the more it'll learn and suggest the traditional over the simplified.

---

### Post by Zorael on 2009-10-13
ibus works in KDE, but the GTK panel will look awful as it's loaded before KDE has had time to import the "theme" it applies to GTK apps to make them look like Qt apps.

If you close the daemon and start it again (which will restart the panel), the panel will be themed correctly but then it will ignore font sizes, so the candidates in the candidates window will be written in very miniature fonts.

---

### Post by executorvs on 2009-10-15
the one thing I miss from SCIM is the smart pinyin recognition. Even when using the same packs I can't seem to get Ibus to recognise 1,2,3,4, and 5 as tone indicators to narrow my list of potential characters.

if I'm dumb and am not seeing an option somewhere let me know.

---

### Post by Longinus00 on 2009-10-15
> **SnappyU said:**
> Just tried iBus Chinese input ... there are two of them that supports Traditional Chinese with pinyin. :)

It has a "T ALL PY" or something as its label.
Note that it displays both simplified and traditional characters.

One thing that I would like to have is the ability to enter phrases instead of just characters.

You can type phrases. Type the words without pressing space and it'll attempt to match a phrase.

---

### Post by dadim on 2009-10-24
> **Longinus00 said:**
> On my setup I can type traditional with the ibus plugin. I select the option that looks like "&#25340; pinyin". The only downside to this is that it seems to show both the traditional and simplified characters, but the more you type with it the more it'll learn and suggest the traditional over the simplified.

That solution is troublesome for anybody who uses both writing systems in different contexts. The good old scim could switch between two input systems for that purpose and it would build frequency tables for both styles individually. As by now, the new IBus makes me neither &#24320;&#24515; nor &#38283;&#24515;.

---

### Post by Zorael on 2009-10-24
There's also uim if you want to try that. Not sure how its Chinese support is, but it works well enough with Anthy.

edit: fresher ibus packages available at [ppa:ibus-dev/ibus-1.2-karmic](https://launchpad.net/~ibus-dev/+archive/ibus-1.2-karmic).

---

