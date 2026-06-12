---
title: "Pretty Grub?"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by karlosantana on 2010-02-01
Hello again guys and gals! 
I have another bugging question for you. I'm well into my multi operating systems and all that I love it! However something so obvious is smacking right between the eyes. Is there a pretty nicer looking version of grub? I realise you can change colours etc but what about the actual look of it? If not is there such a thing as a pretty boot menu?
Cheers
Kyle

---

### Post by zvacet on 2010-02-01
Read [this]("https://help.ubuntu.com/community/Grub2") and see if that is what are you looking for.

---

### Post by Leppie on 2010-02-01
you can install background images for grub2. a more graphical inteface is not there yet.

---

### Post by drs305 on 2010-02-01
If you go to the "Splash Images & Theming" section of the link posted by zvacet you will find guidance on how to place an image of your choosing in the Grub 2 background.

If you are using a later version of Grub 2 than 1.97beta (the standard for Karmic) the line in /etc/grub.d/05_debian_theme has changed so read the note near the start of the section. You can see which version of Grub 2 you are using from the menu during boot or running "grub-install -v".

Just for your information, there is an alternative to Grub 2 called "BURG". It is a spinoff of Grub, for lack of a better term, and can produce much enhanced graphics/theming. Think of it as an alternative to Grub 2 or a preview of what Grub 2 may someday become. You can view a thread about it here. Originally it was about Grub 2 but the last month the posts have dealt mostly with BURG.
[GRUB2 theming for lucid?]("http://ubuntuforums.org/showthread.php?t=1371288")

---

