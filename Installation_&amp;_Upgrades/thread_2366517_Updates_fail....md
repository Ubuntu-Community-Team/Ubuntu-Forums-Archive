---
title: "Updates fail..."
date: 2017-07-18
forum: Installation &amp; Upgrades
---

### Post by starwars-geek98 on 2017-07-18
Hello all,

I'm most likely encountering a bug while trying to install updates from the terminal, information in the screenshot.

Using Ubuntu 17.04

---

### Post by QIII on 2017-07-18
Hello!

When providing terminal commands and their results, please copy from the terminal and place the text between code tags rather than attaching images -- particularly ones with questionable names.

To use code tags:

1.  Click on the # button in the tool bar above the text entry box, place your cursor between the code tags and paste or type your text.

2.  Type or paste your text, highlight it, and then click the # button.

3.  Type [noparse]```
[/noparse] before your text and [noparse]
```[/noparse] after your text.  The square brackets are required.

---

### Post by starwars-geek98 on 2017-07-19
```
**dpkg: error processing package bsdutils (--configure):**** package is in a very bad inconsistent state; you should**
** reinstall it before attempting configuration**
**&#928;&#961;&#959;&#941;&#954;&#965;&#968;&#945;&#957; &#963;&#966;&#940;&#955;&#956;&#945;&#964;&#945; &#954;&#945;&#964;&#940; &#964;&#951;&#957; &#949;&#960;&#949;&#958;&#949;&#961;&#947;&#945;&#963;&#943;&#945; &#964;&#959;&#965;:**
** bsdutils**
**E: Sub-process /usr/bin/dpkg returned an error code (1)**
```

That's the error.

---

### Post by starwars-geek98 on 2017-07-19
Problem solved. 

Went to synaptic and reinstalled the problematic package.

---

