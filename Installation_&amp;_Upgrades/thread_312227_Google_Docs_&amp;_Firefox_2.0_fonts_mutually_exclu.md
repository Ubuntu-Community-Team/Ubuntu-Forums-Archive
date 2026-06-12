---
title: "Google Docs &amp; Firefox 2.0 fonts mutually exclusive?"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by pumpapa on 2006-12-04
Just intalled Edgy including firefox 2.0

All Google docs display in one font: Times New Roman independently of the font used in doc itself. If I set FF default to something else they all display in THAT font.

It appears that the set of fonts offered by Google Documents and that offered by FF are mutually exclusive (this was no problem unde Dapper / FF 1.5).

Should I install fonmts (and if so, how) or should I tell FF how to map?

--
pumpapa

---

### Post by waytoogeeky on 2007-01-23
I'm having the same issue. I'd really like it if someone looked into this. I've run some searches, but so far, nothing helpful.

---

### Post by TheApe on 2007-02-14
The problem is that Ubuntu does not comes with all windows TTF fonts by default.

But it's very simple. Install the **msttcorefonts** from the Multiverse repository.

On the shel type

```
sudo apt-get install msttcorefonts
```

And after that rebuild the font cache
```
sudo fc-cache -f -v
```
:popcorn:

---

### Post by pumpapa on 2007-02-15
This did the trick for me. Great. Many thanks!!!

---

### Post by brucewagner on 2008-01-06
Just wondering ---- since this is from November 2005 --- is this still true?

I am using Ubuntu 7.10.

Does it include all Windows TTF fonts....?

Or do I still need to enter that same command to get them...?

---

### Post by pumpapa on 2008-01-07
I have no problems at this time, but the number of fonts supported in Google Docs is pathetically small. Also, cut-and-paste from other docs will result in markup that cannot be got rid of (without switching to plain text). But all these are Google Doc issues and not Ubuntu install issues.

Cheers

--pumpapa

---

### Post by lbelmond on 2008-02-29
=^.^=

---

