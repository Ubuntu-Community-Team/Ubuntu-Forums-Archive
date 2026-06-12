---
title: "Keyboard layout issues after upgrading 16.04 -&gt; 18.04"
date: 2018-06-05
forum: Installation &amp; Upgrades
---

### Post by martijntje on 2018-06-05
After performing an upgrade earlier today I have been having issues with my keyboard layout. There are two issues. The first is that the tilde key won't work anymore. The system shows a key press but no character is written. The second is that no matter what I do, quotes need an extra space after them before appearing.

Under Region & Language I have English (US, alt. intl) and English (US, alt. intl., with dead keys). Neither of which do what I expect them to do.

How can I get my keyboard functioning again? This is driving me nuts!

---

### Post by martijntje on 2018-06-06
I have managed to partially solve this. Apparantly I needed a non-international layout. Why it was changed during upgrade I still have no idea, but I removed all the international options from the list and used the one with "euro on 5" (whatever that means).

The tilde key will still not work, however. Other keyboard shortcuts have stopped working too, like Ctrl-Alt-L for locking the system. The tilde one is especially onerous as I need that key as an escape sequence for SSH. How to solve this? It registers the key click (I see the cursor briefly change in the terminal) but nothing happens.

---

