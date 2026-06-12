---
title: "Installing russian keyboard"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by btdown on 2005-05-06
I'm attempting to add a Russian keyboard to Hoary without much success. I dont want to completely change the locale to Russian, just be able to read, and type in Russian (from the regular us keyboard) when necessary. I've looked through a lot of FAQs and other postings and have done the following:
 
1. 'dpkg-reconfigure locales' to make sure all the russian entries were checked.
 
2. Used synaptic to install the following: t1-cyrillic, xfonts-cyrillic, keyboards-rg
 
3. Attempted to add a Russian keyboard using the gnome keyboard adder thing, but the +Add layout button is greyed out and wont let me click on it to add anything or attempt to pick from a list it might provide. 
 
Any ideas? 
Ps. Im looking to add both a regular and yawerty keyboard.

---

### Post by sethmahoney on 2005-05-06
I haven't tried actually doing it yet, but I'm running Ubuntu Hoary (not Kubuntu), and when I go to System->Preferences->Keyboard->Layouts, the "Add..." button is clickable, and under Russian I have the options "Phonetic", "Typewriter", and "Winkeys".  I also don't have either of the fonts you mentioned (I can still view Cyrillic fonts in web pages, though), or the keyboard layouts package.

I do, however, have language-support-ru, language-pack-ru, language-pack-ru-base, mozilla-firefox-locale-ru-ru, myspell-ru, and openoffice.org-hyphenation-ru installed (some of these may be part of language-pack-ru-base).  Hope this (somehow!) helps.

---

### Post by btdown on 2005-05-06
Ah ha! I think I found my problem. My ubuntu box is headless and I usually access it by freenx. When you login with via freenx, it will not let you add a keyboard. I wonder if I login locally to the box, add a keyboard, if I will be able to change it remotely via freenx.

---

### Post by sethmahoney on 2005-05-09
[QUOTE=btdown]Ah ha! I think I found my problem. My ubuntu box is headless and I usually access it by freenx. When you login with via freenx, it will not let you add a keyboard. I wonder if I login locally to the box, add a keyboard, if I will be able to change it remotely via freenx.[/QUOTE]
 Did logging in locally end up fixing the problem?

---

### Post by btdown on 2005-05-22
Yes and no......logging in locally allowed me to add the Russian keyboard/etc, and all is well. However, after I've added the keyboard locally, then logged back out and logged back in using FreeNX, it wont allow me to select/use the russian keyboard.

Its sorta annoying...Hopefully this will be resolved in future versions.

---

### Post by artemstar on 2005-05-24
Did you check all the tabs in "Add keybord layout" GUI?
After I added the russian keyboard the default was set to use both Alt keys to switch modes. Did you try that? Or you can set it to your preferrence. There is no clickable indicator at the desktop.
Both Alts works fine for me, except that russian font in xterm is too small and my emacs is still not displaying the characters correctly - but these are separate problems - I'll keep looking for an answer.

---

