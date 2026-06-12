---
title: "Kurdish screen reader"
date: 2008-02-13
forum: Kurdish Team - Kurdistan
---

### Post by ASquared21 on 2008-02-13
Hi,
First of all, sorry for writing in English. I want to work with a native Kurdish speaker and the developer of the eSpeak screen reader to assist those Kurdish speakers that are visually impaired. If anyone has further questions to ask, simply reply to this thread.

All help will be appreciated.
Thanks,
Alex A.

---

### Post by erdalronahi on 2008-02-14
Hi Alex, great project. Can you give some more details?

I don't know how screen readers really work, but Kurdish should be relatively easy to code, because the correlation between the written and the spoken Kurdish is very very close. There are practically no exceptions from the pronunciation rules.

---

### Post by ASquared21 on 2008-02-14
Hi,
Sorry, but I am in a rush. I will provide further details soon.

I am in urgent need of a recording of some spoken Kurdish, something that has most of the sounds in it. Also the accompanying text stating the spelling of what you have said. Any other learning material such as pronounciation tables will be Appreciated.
Thanks,
Alex A.

---

### Post by erdalronahi on 2008-02-14
Hi,

there is a picture dictionary here: [http://www.skolutveckling.se/vaxthuset/trio/nk/nordkurdiska.htm]("http://www.skolutveckling.se/vaxthuset/trio/nk/nordkurdiska.htm")

You can click every word and listen to it. Unfortunately it's all flash, so it may be difficult to extract it. The pronunciation is quite good.

There is a [phonology of Kurdish]("http://en.wikipedia.org/wiki/Kurdish_language#Phonology") in Wikipedia, but I cannot judge how accurate that is, because dialects may differ.

Does this somehow help you, or do you need longer texts?

---

### Post by ASquared21 on 2008-02-14
Hi,
Thanks. I want to thank you for your help. I will forward this message to the developers at eSpeak. I will let you know what they require or if I need more information.

For now, any more help will be appreciated.
Thanks,
Alex A.

---

### Post by erdalronahi on 2008-02-14
Hi, 

I found a [table that correlates the alphabet with the IPA phonemes]("http://de.wikipedia.org/wiki/Kurdische_Sprachen#Schrift"). The actual Kurdish letters are in the leftmost column, the IPA-pronunciation in the fourth column. This should help a lot. 

If you (or the guys at espeak) just code these, I am sure that a well understandable result will come out of it very quickly. 

Me and the Ubuntu Kurdish team will be happy to help test further if you give us instructions on how to use test versions of espeak (which I just tried for the first time - English sounds nice).

---

### Post by ASquared21 on 2008-02-15
Hi,
I never even dreamed of such help. I am sure I can speak with the
developers at eSpeak.

This is my biggest program yet. As a volunteer techie and program
supervisor at AWEBSIGHT, and it would be nothing if not for the help
of my best friend who provided the inspiration of the program, the
Kurdish Ubuntu team, everyone who has and will contribute to this
forum, my contacts, and the people at eSpeak.
Thanks,
Alex A.
- Show quoted text -
--

---

### Post by erdalronahi on 2008-02-15
I have started a discussion thread at [http://sourceforge.net/forum/forum.php?thread_id=1940526&forum_id=538922](http://sourceforge.net/forum/forum.php?thread_id=1940526&forum_id=538922)

---

### Post by ASquared21 on 2008-02-15
Hi,
The official project page is [http://www.VisionMail.uni.cc/kurdish.html](http://www.VisionMail.uni.cc/kurdish.html)
Thanks,
Alex A.

---

### Post by ASquared21 on 2008-02-16
Hi,
This is a general question for you. Is there any one out there who is willing to fill the spot of speech wrapper programer? What needs to be done is writing an Applescript or Xcode wrapper to allow the popular Linux speech engine of eSpeak to work with Apple's Voiceover.

ESpeak is written in C++.
Any help will be appreciated.
Thanks,
Alex A.

---

### Post by jonsd on 2008-02-16
I have now added a first attempt at a Kurdish voice to eSpeak,  Try the development version (1.31.12 or later) from:
[http://espeak.sourceforge.net/test/latest.html](http://espeak.sourceforge.net/test/latest.html)

The name of the Kurdish voice is "ku".
The compiled binaries should be compatible with Ubuntu Gutsy.

I don't speak or understand any Kurdish, so much is guesses based on a little which I have read.  I based the vowel sounds on the samples at [http://www.skolutveckling.se/vaxthuset/trio/nk/nordkurdiska.htm](http://www.skolutveckling.se/vaxthuset/trio/nk/nordkurdiska.htm)

I don't know whether this represents a suitable accents or dialect. Some of the sounds there differ from their descriptions on wikipedia or omniglot.

I'm not sure whether the "q" sound is correct. We don't have this sound in English, so I'm not sure if sounds OK.  I've used strong version of "x", but again if it sounds wrong, tell me.

It puts the stress on the last syllable of each word.  I know this is wrong in some cases, but I don't know the rules.  Perhaps some word endings should be unstressed?

Probably vowel lengths need adjustment.

I don't know the names of the letters (eg. in English "see" for "c" and "eff" for "f") so I've made guesses.

I've made an attempt at numbers, but the information I found was confusing, with alternative pronunciations for some numbers.  So probably some are wrong.

The pronunciation rules are in file: dictsource/ku_rules.

The file dictsource/ku_list gives the names of letters, symbols and numbers, and will contain any words with exceptional pronunciations.  Also it should list common "function" words with attributes such as:
```

$u     unstressed
$u+   unstressed, except at end-of-sentence.
$pause  add a short pause before the word (eg. conjunctions).
$brk   add a shorter pause. (perhaps some prepositions).

```

These can help the speech to flow better.  Currently all words are stressed (except for a couple which I've already added to ku_list).

So, send me corrections, suggestions, and additions.  If we can improve it so that's it's useable then it can be included in Ubuntu and other distributions.

---

### Post by jonsd on 2008-02-16
ASquared21 wrote:
> What needs to be done is writing an Applescript or Xcode wrapper to allow the popular Linux speech engine of eSpeak to work with Apple's Voiceover.

It would be better to ask this on an Apple formum.  This is a general question about eSpeak and Apple, and not specific to any particular language.  Unfortunately I don't have an Apple computer and I don't know anything about them.

---

### Post by ASquared21 on 2008-02-16
Hi,
Thanks. I tried the appropiate mailing list for Apple accessibility and just thought i'd try here, since I believed that having a thourough understanding of eSpeak on another platform, would allow a programer to duplicate the feat on Apple's Macintosh platform.
Thanks,
Alex A.

---

### Post by ASquared21 on 2008-03-09
Hi,
A large thanks to the Kurdish Ubuntu Team and Jonsd. I can't thank the contributers to the eSpeak Kurdish Version enough. I appreciate all work from the bottom of my heart.
Thanks,
Alex A.

---

### Post by ASquared21 on 2008-03-18
Get it here, Free.
[url]Http://eSpeak.sourceforge.net/[/url

Thanks,
Alex A.

---

### Post by aiser on 2009-12-01
;)

---

