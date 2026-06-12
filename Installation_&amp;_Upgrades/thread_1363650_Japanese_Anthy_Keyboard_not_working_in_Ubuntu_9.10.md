---
title: "Japanese Anthy Keyboard not working in Ubuntu 9.10"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by sobana on 2009-12-24
Just did the upgrade to Karmic Koala yesterday and my anthy keyboard (icon with the crown) disappeared from my icons and from existence. I don't really know anything about linux/ubuntu. I found a site that said I needed the following packages installed, but I don't know how to install them: 

[LIST]
[*]scim (Smart Common Input Method platform)
[*]scim-anthy (Japanese input method module for SCIM)
[*]anthy (Japanese kana-kanji conversion engine)
[*]scim-input-pad (an add-on to input various symbols)
[*]kasumi (dictionary maintenance tool for Anthy)
[/LIST]
I fear that it is not supported in the new version and that's why I can't find it in the list of packages to install...

Help so I can type Japanese again!

---

### Post by Shii on 2010-01-23
I'm having the same problem. So much for Ubuntu being perfect :(

---

### Post by Shii on 2010-01-23
&#12391;&#12365;&#12414;&#12375;&#12383;&#12290;

I had installed the packages listed above, but Ubuntu uninstalled the canna package during the upgrade. I simply re-enabled it and logged out to fix the problem.

---

### Post by Leppie on 2010-01-23
try ibus, it's supposed to replace scim.

---

### Post by Shii on 2010-01-23
> **Leppie said:**
> try ibus, it's supposed to replace scim.

I'm happy to know what the Ubuntu devs recommend, but I couldn't find any indication that ibus will replace scim in Synaptic, and switching between IMEs makes me scared. :P

---

### Post by Leppie on 2010-01-23
i'm using ibus for Korean ime ;)
works very nicely

---

### Post by Irihapeti on 2010-01-24
I've had Scim and iBus installed at the same time, though only one is active at any one time. It's easy to switch between them.

Assuming that you are running Gnome, once you've got the packages installed, go to System -> Administration -> Language support. There's a box for choosing which IME you want to use. Choose the one you want (use "scim-bridge" rather than "scim"), log out and in again, and there you are. Scim doesn't show a tray icon in 9.10, but as soon as you press ctrl-space, the panel pops up as normal.

As far as I can tell, they don't interfere with each other. So you can try both and decide which you prefer.

I seem to remember that you have to specifically install anthy if you want to convert hiragana to kanji. Not ideal, as it should really be installed automatically.

---

### Post by temporos on 2010-03-17
I am trying to install the Japanese and Korean IMEs.  I used the Language Support control panel to install support for both languages.  After logging-out, I used the lBus Preferences control panel to install the IMEs for Japanese>anthy and Korean>romaja.

I used the following settings:
Enable or disable: Ctrl+Space
Next input method: Alt+Shift_L
Candidates orientation: Horizontal
Show language panel: always
Show input method name on language bar: no
Use system keyboard layout: yes

I logged-out, but I still can't switch between IMEs.  I go to gedit, and press Alt+Shift_L, but it still types in English characters.  How can I get it to type in Japanese (hiragana/katakana/kanji) and Korean (hana)?  I want to be able to type in "romanji" and have the IME convert it to Japanese and Korean characters for me (like the Microsoft IMEs do in Windows).

Any help would be appreciated.  Thanks!

---

### Post by temporos on 2010-03-19
Okay, I managed to fix the problem.  I'm using the following settings:

Control Panels > Language Support
[INDENT]Keyboard input method system: lBus
Language support installed: English, Japanese, Korean
[/INDENT]Control Panels > lBus Preferences
[INDENT]Input Method: English iSpell, Japanese anthy, Korean romaja
Use system keyboard layout: yes
[/INDENT]
After a restart, I wasn't able to get the IME working.  But after a day or-so, Ubuntu's package manager told me I needed an update to lBus.  After installing the update and rebooting, the IME works fine!

&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290; :D

---

### Post by riesengreen on 2010-03-20
> **temporos said:**
> okay, i managed to fix the problem.  I'm using the following settings:

Control panels > language support
[indent]keyboard input method system: Lbus
language support installed: English, japanese, korean
[/indent]control panels > lbus preferences
[indent]input method: English ispell, japanese anthy, korean romaja
use system keyboard layout: Yes
[/indent]
after a restart, i wasn't able to get the ime working.  But after a day or-so, ubuntu's package manager told me i needed an update to lbus.  After installing the update and rebooting, the ime works fine!

&#12354;&#12426;&#12364;&#12392;&#12358;&#12372;&#12374;&#12356;&#12414;&#12377;&#12290; :d

&#65290;&#65290;&#65290;

&#12371;&#12428;&#12391;&#12391;&#12365;&#12383;&#12382;&#65281;&#12354;&#12426;&#12364;&#12392;&#12358;&#65281;

---

### Post by BelowGrade on 2010-04-11
Anthy works for me in 9.10 UNR on my NetBook, with iBus.  But I can not find how to get to the Anthy preferences page to set up keystrokes to select Latin, Hiragana, and Katakana.   On my desktop, which I think uses SCIM instead, Anthy has its own submenu within the SCIM configuration.

Fixed: There are two versions of Anthy for iBus.  You need the one with a crown icon.

---

